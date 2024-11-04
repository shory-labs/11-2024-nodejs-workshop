# Nodejs Project Structure

## Run Simple JavaScript Code on Nodejs
1. Create empty folder `nodejs-project`
2. Open the newly created folder in VS Code.
3. Create a file `add-numbers.js` 
4. Add the following content inside that folder
   ```
    function add_numbers(num1, num2) {
        return num1 + num2;
    }

    const sum = add_numbers(1, 2);
    console.log("The result=", sum);
   ```
4. Run `node add_numbers`
   
## Use npm Third-Party package

1. Run `npm init`
2. Install a dependency in action `npm i add-numbers`
3. Create a `add-numbers2.js` file to add two numbers
4. Add the following content inside that folder
   ```
    const add_numbers = require("add-numbers");

    const sum = add_numbers(1, 2);

    console.log("The result=", sum);
   ```
5. Run `node add_numbers2`
6. Add start script in the `package.json`


[Back](../Readme.md)