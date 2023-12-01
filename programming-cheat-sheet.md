# Programming cheat sheet
A cheat sheet with the highlights of the Pon development standards.

# Constants 

## Constants and magic numbers

Constants: Named variables holding a value that does not change.
Magic Numbers: Direct usage of numbers in code without explanation of their meaning.

## The use of constants

In software development, constants play a crucial role in enhancing both
readability and maintainability of code. A constant is a named variable 
that holds a value which does not change throughout the program. Using 
constants instead of literal numbers makes the code more self-explanatory 
and less prone to errors.

For example, consider the difference between using the literal number 7 
and a constant like const int DAYS_IN_WEEK = 7;. The latter clearly 
communicates its purpose and meaning, making the code more accessible and
understandable. This practice aligns with Pon's principles of 
clarity and self-descriptive code, minimizing ambiguity and enhancing the
educational value of the code.

Furthermore, constants facilitate easier maintenance. Should the need 
arise to change a value, it can be done in one place, reflecting throughout 
the code, rather than changing every instance where the number appears. 
This not only saves time but also reduces the risk of introducing errors 
during modification.

In summary, constants are a preferred choice in coding due to their 
ability to make code more readable, understandable, and easy to maintain, 
embodying Pon's advocacy for simplicity and precision in programming.

### Do:

* Use Constants for Fixed Values: Utilize constants for values that remain 
constant throughout the program.
* Name Constants Clearly: Choose names that clearly describe the value and 
its purpose.
* Declare Constants Globally if Used Across Multiple Files: For values used 
in multiple places, declare constants in a global scope.
* Use Constants for Configuration: Employ constants for configuration 
settings that could change between environments.

### Don't:

* Don’t Use Magic Numbers: Avoid using literal numbers directly in the code.
* Don’t Reuse Constants for Unrelated Purposes: A constant should have a 
single, clear purpose.
* Don’t Define Constants for Values That May Need Regular Updates: While 
constants are for unchanging values, avoid using them for data that might 
need frequent updates or vary significantly between different environments 
or contexts. Instead, consider other methods like configuration files for
such value
* Don’t Overuse Constants: While useful, not every number needs to be a 
constant, especially if it's self-explanatory like 0 or 1 in certain contexts.

### Examples

```
// Good Practice
const DAYS_IN_WEEK = 7;
const MAX_LOGIN_ATTEMPTS = 5;

for (let day = 1; day <= DAYS_IN_WEEK; day++) {
    console.log(`Day ${day} of the week`);
}

// Usage of MAX_LOGIN_ATTEMPTS in a function
function checkLoginAttempts(attempts) {
    if (attempts > MAX_LOGIN_ATTEMPTS) {
        console.log('Account locked due to too many attempts');
    }
}
```

```
// Bad Practice
for (let day = 1; day <= 7; day++) {
    console.log(`Day ${day} of the week`);
}

// Using a magic number directly in a function
function checkLoginAttempts(attempts) {
    if (attempts > 5) {  // What does 5 signify here?
        console.log('Account locked due to too many attempts');
    }
}
```