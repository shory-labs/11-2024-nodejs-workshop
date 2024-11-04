# Typescript In Action

## Run Simple JavaScript Code on Nodejs
1. Following previous samples, create a new folder named `backend-api`
2. Initiate the package.json and install the following dependencies
   `npm i express nodemon ts-node`
   `npm i @types/express typescript -D`
3. Create the following folders inside folder/files
   - src
     - index.ts
         ```
         import express, { Response } from "express";

         const app = express();

         app.get("/", (req, res: Response) => {
            res.status(200).send("hello world");
         });

         app.listen(3010, () => {
            console.log("Server is running on http://localhost:3010");
         });

         ```
   - db
     - students.jsons
         ```
         [
            {
               "id": 1,
               "name": "John Doe"
            },
            {
               "id": 2,
               "name": "Jane Doe"
            }
         ]
         ```
3. Initiate typescript config `npx tsc --init`
4. Run the server using `npx ts-node ./src/index.ts`
5. Add dev script in package json as following: 
   ```
   "scripts": {
     "dev": "npx ts-node ./src/index.ts"
   },
   ```
6. Add your first endpoint to get students `api/students`
   ```
   import fs from "node:fs";
   import path from "node:path";

   //
   // == the previous code 
   //

   app.get("/api/students", (req, res: Response) => {
      const studentsDataAsString = fs
         .readFileSync(path.resolve(__dirname, "../db/students.json"))
         .toString();

      const students = JSON.parse(studentsDataAsString);

      res.status(200).send(students);
   });

   //
   // == the remaining code
   //

   app.listen(3010, () => {
      console.log("Server is running on http://localhost:3010");
   }); 
   ```
7. Use nodemon for continue development reload. Just change the dev script as following
   ```
   "scripts": {
     "dev": "npx nodemon ./src/index.ts"
   },
   ```

 
[Back](../Readme.md)