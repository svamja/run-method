# run-method

Run any function from any NodeJS module and pass string arguments

    npx run-method SampleModule say_hello


## Install (Optional)

    npm install run-method

This will add run-method as dependency in the project.

## Usage

    npx run-method <module_name> <function_name> [ <arg> .. ]

## Examples

Display the help:

    npx run-method --help


Run the `random` function from `maths.js` file in current directory:

    npx run-method maths random


Run the `random` function from `maths.js` file in `lib` directory:

    npx run-method lib/maths random


Run the `multiply` function from `maths.js` file and pass `'5'` and `'7'` as string arguments.

    npx run-method maths multiply 5 7


Pass the argument "Hello World!" as single string using url encoding:

    npx run-method --encoded some_module some_function 'Hello%20World!'


Print only the `info()` and `output()` messages and suppress `debug()` messages, from the following code:

    npx run-method --info maths factorial 5

Code:

    # maths.js
    const RunMethod = require('run-method');
    const maths = {
        factorial(n) {
            n = parseInt(n);
            RunMethod.debug('input', n);
            let m = 1;
            for(let i = 1; i <= n; i++) m *= i;
            RunMethod.info('output', m);
            return m;
        }
    }
    module.exports = maths;

Different levels of output functions:

    RunMethod.output(); // Level 1 = reserved to display the return value
    RunMethod.info();   // Level 2 = informational
    RunMethod.debug();  // Level 3 = debug


