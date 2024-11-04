# Typescript In Action

## Run Simple JavaScript Code on Nodejs
1. Starting with the nodejs project structure created in previous step
2. In `add-numbers.js` file, try the following modification to accept array of numbers
   ```
   function add_numbers(values) {
   const result = values.reduce((partialSum, a) => partialSum + a, 0);

   return result;
   }

   const sum = add_numbers([1, 2, 5, 6]);
   console.log("The result=", sum);

   ```
3. Now let's try the following code, note that we send the array by mistake without brackets as following
   ```
   const sum2 = add_numbers(1, 2);
   console.log("The result=", sum);
   ```
4. Install typescript dependency `npm i typescript -D`
5. Change the `add-numbers.js` file name to `add-numbers.ts`
6. Modify the file to include types as following
   ```
   function add_numbers(values: number[]) {
      const result = values.reduce((partialSum, a) => partialSum + a, 0);
      return result;
   }

   const sum = add_numbers([1, 2, 5, 6]);
   console.log("The result=", sum);

   const sum2 = add_numbers([2, 4]);
   console.log("The result=", sum);

   ```
7. Run `npx tsc add_numbers.ts` or `npx tsc add_numbers.ts --outDir dist` to generate the js file
8. Run `node add_numbers.js`
 
[Back](../Readme.md)