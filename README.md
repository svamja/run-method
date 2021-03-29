# run-method

Run any function from any NodeJS module and pass arguments

    npx run-method SampleModule say_hello


## Install (Optional)

    npm install run-method

This will add run-method as dependency in the project.

## Usage

    npx run-method <module_name> <function_name> [ <arg> .. ]

## Complete Example

    npx run-method --debug maths factorial 5

Optionally, include the run-method in your code to control various levels of output:

    # maths.js
    const RunMethod = require('run-method');
    const maths = {
        factorial(n) {
            n = parseInt(n);
            RunMethod.debug('input = ', n);
            let m = 1;
            for(let i = 1; i <= n; i++) m*= i;
            RunMethod.debug('output = ', m);
            return m;
        }
    }
    module.exports = maths;

Different levels of output functions:

    RunMethod.output(); // Level 1 = reserved to display the return value
    RunMethod.info();   // Level 2 = informational
    RunMethod.debug();  // Level 3 = debug

Also, see help

    npx run-method --help

