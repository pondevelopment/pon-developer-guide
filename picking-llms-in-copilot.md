# Picking the Best LLM in VS Code with GitHub Copilot

A one-page guide for developers on choosing the right model for the task.

## The core idea

Don't hunt for one "best" model. **Route by task type.** Copilot's pricing and
latency vary enormously across models, so matching the model to the job beats
brand loyalty or a single-model policy.

## Why tiering exists (2026)

The market split into a **two-tier** shape: high-reasoning *Pro* models
(complexity, depth, large context) and velocity-optimized *Flash/Lite* models
(throughput, low latency, low cost). The general-purpose monolith is gone — so
your workflow should mirror the market and route between tiers. This is exactly
what the three agents below do. Two more 2026 shifts make routing pay off:

- **Context caching is standard** and can cut input cost by up to ~75%, so
  keeping a stable repo prefix is now a first-class cost lever.
- **Copilot moved to metered AI credits** (as of June 1, 2026), so model choice
  directly affects spend even inside Copilot.

## Two things you (almost) never need to optimize

- **Inline code completions & next edit suggestions** are *not* billed in AI
  credits on paid plans — leave them on a fast model for flow.
- **Copilot Code Review** picks its model automatically — optimize it with
  better review instructions, not manual model choice.

## Three agents

| Agent | Use for | Example models | Cost posture |
|---|---|---|---|
| **Fast / cheap** | Explanations, docstrings, comments, changelogs, release notes, tiny edits, summaries | GPT-5 mini, MAI-Code-1-Flash, Gemini Flash/Haiku | 0× or low |
| **Balanced** | Everyday implementation, bug fixes, tests, refactors, normal debugging | Claude Sonnet 4.6, Gemini 2.5 Pro | 1× / mid |
| **Deep reasoning** | Architecture, multi-file/cross-service debugging, large-context work, repeated failed fixes | GPT-5/5.5, Gemini 2.5/3.1 Pro, Claude Opus, o3 | High premium |

These three agents map directly onto the 2026 "Pareto router" pattern:

- **Fast / cheap → Level 1 (Flash):** routine completions, tool dispatch,
  sub-second iteration.
- **Balanced → Level 2 (Pro):** high-stakes planning and architectural review at
  a sane cost.
- **Deep reasoning → Level 3 (Frontier):** novel algorithmic problems and
  infrastructure-critical refactors — escalate to here, don't live here.

## Pick by benchmark proxy

When comparing models, match the *benchmark* to the *task* — a single
leaderboard rank hides the multidimensional reality.

| Task | Proxy benchmark | What it tells you |
|---|---|---|
| Fix real repo issues (patch + tests) | SWE-bench Verified | Engineering reliability; top frontier models cluster ~80–94% |
| Multi-tool / agentic workflows | MCP Atlas | Tool-coordination quality (where Pro/agentic models lead) |
| Large-codebase understanding | Context window | Fits repo maps/logs without extra turns (up to ~1–2M tokens) |
| Throughput-bound generation | Tokens/sec | Inner-loop responsiveness for cheap, high-volume work |

The lesson: use strong-SWE-bench models for the balanced/deep agents, strong
tool-use models for agentic work, and fast/cheap models for narrative and
high-volume chores.

## Default policy

- Keep **Copilot Chat on Auto** for everyday work.
- Keep **inline suggestions on a fast model**.
- Create a named **deep agent** (architecture/hard bugs) and a **cheap agent**
  (narrative/docs) only where the economics clearly matter.

## Escalation rule

Escalate from balanced → deep only when **one** is true:

- you are touching many files (>5),
- the bug spans layers or services,
- you need long context (large logs, repo maps),
- the first fix already failed.

De-escalate to the cheap agent for "summarize commits", "write the changelog",
"draft the README".

## Extra levers (beyond model choice)

- **Reasoning effort**: use more "thinking" only when the task needs it — high
  effort costs far more time and tokens for marginal quality gains.
- **Prompt caching**: keep stable repo context/standards at the top of the
  prompt for big latency and cost wins.
- **Batch/Flex**: for non-interactive jobs (doc generation, evals, migrations).

## How to switch models in VS Code

- **Chat model**: language-model picker in the Chat view.
- **Completion model**: Command Palette → "GitHub Copilot: Change Completions
  Model" / "Configure Inline Suggestions…".
- **BYOK** (chat & utility tasks only — *not* inline): add other providers or
  local models.
- **Repo-wide steering**: `.github/copilot-instructions.md` and path-specific
  files under `.github/instructions`.
- **Reusable agents**: custom agents under `.github/agents` (selected from the
  agent picker in Chat).

## Hands-on: setting up agents

A custom agent is a reusable **chat mode** plus a deliberate model choice. You
set up each agent once, commit it to the repo, and pick it from the agent picker
in the Chat view — it stays selected for the whole conversation.

### 1. Where custom agents live

Custom agents are `*.agent.md` files under `.github/agents/`. VS Code picks them
up automatically and lists them in the agent/mode picker at the top of the Chat
view — no setting to enable.

### 2. Create the deep agent

Create `.github/agents/deep.agent.md`. The `model` field pins this agent
to a deep-reasoning model so you don't have to remember to switch manually:

```md
---
description: Architecture, hard debugging, and large-context work
model: Claude Opus 4.8
---

You are working on a complex, high-risk change.

Before writing code:
- Restate the problem and the constraints you infer.
- List the files and layers likely involved.
- Propose two options with trade-offs (latency, maintainability, migration risk).
- Recommend one and give a file-by-file execution checklist.

Only then implement. Keep the change minimal and explain risky decisions.
```

Use it for: architecture, multi-file/cross-service bugs, repeated failed fixes.

### 3. Create the cheap agent

Create `.github/agents/cheap.agent.md` and pin it to a fast/cheap model:

```md
---
description: Changelogs, release notes, summaries, docstrings
model: GPT-5 mini
---

Produce concise, user-facing narrative output only.

Rules:
- Keep only what a reader needs; drop internal detail.
- No speculative refactors or code changes.
- Group changes under Added / Changed / Fixed when relevant.
- Return Markdown only.
```

Use it for: changelogs, release notes, commit summaries, READMEs, comments.

### 4. Create the balanced agent (your default working agent)

Create `.github/agents/balanced.agent.md`:

```md
---
description: Everyday implementation, bug fixes, tests, refactors
model: Claude Sonnet 4.6
---

Implement the requested change with the smallest safe diff.

Always:
- State a short definition of done.
- Add or update tests for changed behavior.
- Run/describe the validation commands (test, lint, typecheck).
- If the task spans more than ~5 files, stop and propose a plan first.
```

### 5. Keep inline completions fast

Leave inline suggestions on a fast completion model (they are free on paid
plans). In Chat, default to **Auto** and only switch to the **deep** or
**cheap** agent when the task clearly warrants it.

### 6. Add shared context once (so agents stay cheap)

Put repo-wide rules in `.github/copilot-instructions.md` so every agent inherits
them without you re-typing context (this is what makes the cheap agent viable):

```md
- Prefer the smallest safe change over broad rewrites.
- Match existing code style; do not reformat untouched code.
- Validation commands: npm test, npm run lint, npm run typecheck.
- For risky areas (auth, migrations, CI, dependencies), propose a plan first.
```

> Note: the exact `model` names shown above are examples — use whatever your
> Copilot plan exposes in the model picker. If a `model` value isn't available,
> the agent still works; it just falls back to your selected Chat model.

### Ready-made agents in this repo

These custom agents are already scaffolded — pick them from the agent picker in
Chat:

- [`deep`](.github/agents/deep.agent.md) — architecture, hard
  debugging, large-context work.
- [`balanced`](.github/agents/balanced.agent.md) — everyday
  implementation, bug fixes, tests, refactors.
- [`cheap`](.github/agents/cheap.agent.md) — changelogs, release
  notes, summaries, docstrings.

## Skills vs agents

Custom agents and skills solve different problems and work best together.

| Mechanism | Loaded | Controls | Best for |
|---|---|---|---|
| `copilot-instructions.md` | Always | Global rules | Short, always-true conventions |
| Skill (`SKILL.md`) | On-demand when its description matches the task | Knowledge | Deep, topic-specific domain knowledge |
| Custom agent (`*.agent.md`) | When you pick it in the agent picker | Model + working style | Task + model presets |

- A **custom agent** picks the *model* and sets the *working style*. You select
  it deliberately from the agent picker. This is your main **cost** lever.
- A **skill** packages *"how we do X here"* knowledge. The agent pulls it in
  **automatically** when a task matches the skill's `description`, so it does
  not bloat every prompt.
- They compose: a skill supplies the knowledge, the agent controls the spend.
  Running the **deep** agent on an architecture task can auto-load a matching
  skill.

### Set up a skill

Create `.github/skills/<name>/SKILL.md` with front matter. The `description` is
what the model uses to decide when to load it, so make it specific:

```md
---
name: pon-coding-standards
description: Pon coding standards and conventions. Use when writing or
  reviewing code in this repo — covers constants over magic numbers, secure
  logging (ECS), commit message format, and pull request expectations.
---

# Pon coding standards

When writing or reviewing code in this repository, apply these rules.

## Constants
- Never use magic numbers; name them as constants with a clear purpose.

## Logging
- Log through a library using ECS levels (error/debug/notice).
- Never log secrets or PII.

## Commits & PRs
- Use Conventional Commits (`type(scope): subject`).
- Keep PRs small and focused on a single issue.
```

An example skill is scaffolded in this repo at
[.github/skills/pon-coding-standards/SKILL.md](.github/skills/pon-coding-standards/SKILL.md).

## Multiple chats: one chat per role

VS Code lets you run several Copilot Chat sessions at once, and **each chat
keeps its own model, context window, and history**. That makes a "chat per
role" setup the simplest way to route — no custom agents required.

Why it helps:

- **No context pollution.** A focused changelog chat is not dragging your
  architecture discussion (and its tokens) into every request.
- **Sticky model choice.** Set the model once per chat; it stays until you
  change it. Your commit chat stays cheap, your debugging chat stays deep.
- **Cheaper and faster.** Short, single-purpose chats keep prompts small, which
  lowers token cost and latency.

A practical set of standing chats:

| Chat | Model tier | Typical use |
|---|---|---|
| **Commits & changelogs** | Cheap | Commit messages, changelog/release notes, PR summaries |
| **Implementation** | Balanced | Day-to-day coding, tests, refactors |
| **Architecture / deep debug** | Deep | Design, cross-service bugs, repeated failed fixes |
| **Explain / learn** | Cheap | "What does this do?", onboarding, reading docs |

### Set it up

1. Open the Chat view and start a chat. Pick its model in the model picker.
2. Open a **second** chat (the `+` / "New Chat" action, or drag it into its own
   editor tab so several are visible at once). Pick a different model.
3. Name or pin the tabs by purpose so you can tell them apart.
4. Reuse the same chat for that purpose instead of starting fresh each time.

### Combine with agents and skills

Chats, agents, and skills stack:

- **Chat** = a persistent workspace with a sticky model and its own history.
- **Custom agent** (e.g. `cheap`) = a model + working-style preset you
  pick from the agent picker.
- **Skill** = auto-loads the right knowledge regardless of chat or agent.

So a clean setup is: a **commits chat** kept on the **cheap** agent for
changelog generation, while the `pon-coding-standards` skill
auto-applies the commit-message conventions.

> Tip: for commits specifically, keep that chat scoped to just the staged diff.
> The smaller the context, the cheaper and faster the message generation.

## When NOT to trust the cheap agent

Fast/cheap models are great for throughput but have sharper failure modes — keep
a human or a validator in the loop for anything that matters:

- **Unknown-answer tasks**: some high-volume models hallucinate badly when they
  should abstain (reported failure rates as high as ~94% on unknown-answer
  benchmarks). Never let the cheap agent invent facts, APIs, or config values.
- **Complexity curse**: reasoning accuracy drops sharply as problem complexity
  grows. Escalate multi-step logic to the deep agent rather than pushing a cheap
  model past its depth.
- **Always validate**: tests, lint, and review are the real acceptance gate —
  route to the cheapest model that still passes them on the first try.

## One-line takeaway

**Use the cheapest model that will still pass your validator (tests, lint,
review) on the first try — and only pay for reasoning depth when the task
proves it needs it.**
