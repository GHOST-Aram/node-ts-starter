# Setting Up an Initial Project Directory for TypeScript and Node.js

Are you new to Typescript? Do you need help creating and configuring a project directory for Typescript and Node? This article will guide you on how to create a project directory for Node and Typescript.

This article will guide you through 5 key steps as follows:

 1. Intialize project directory and install dev dependencies
 2. Generate and edit Typescript configuration file
 3. Test your Typescript configuration
 4. Customize npm scripts
 5. Test npm script commands

After completing this guide, you will have created a project directory in which you can:

 - run the Typescript code without manual compilation step
 - compile Typescript source code to JS build code
 - run the Typescript code without manual compilation step
 - compile Typescript source code to JS build code
 - run JS build code and
 - run your code automatically on every change

using custom npm commands.

## 1.Intialize Project Directory and Install Dev Dependencies
First and foremost, we re going to create a project directory, generate `package.json` file and install preliminary dependencies in the following sequence. 

1. Create a folder with a name of your choice and open it in your favorite IDE.
2. Generate package.json file using the command `npm init -y`
3. Install development dependencies using the command

`npm install -D typescript ts-node @types/node nodemon`

By executing the above command, we have installed

- typescipt for Typescript language.
- ts-node to run Typescript code without manual compiling
- @types/node Typescript types for node
- nodemon for server auto-restart on code change

## 2.Generate and edit Typescript configuration file
After step one, we can successfully create and execute Typescript code but it would not be convenient enough. In order to take better advantage of Typescript, we need to adopt some of the settings it provides. We will generate `tsconfig.json` file and make a few changes in the following sequence:

 1. Run the command `tsc --init` to generate tsconfig.json file.
 2. Replace your `tsconfig.json` file with the following configs
```
{
  "compilerOptions": {
    "target": "ESNext",                                  
    "module": "CommonJS",                               
    "rootDir": "./src",                                  
    "declaration": true,
    "sourceMap": true,
    "outDir": "./build",                                   
    "esModuleInterop": true,                             
    "forceConsistentCasingInFileNames": true,            
    "strict": true,                                      
    "skipLibCheck": true                                 
  }
}
```
These are not the only Typescript configurations that you can use. This is what you need to get started. Visit [Typescript Documentation](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html#:~:text=The%20tsconfig.json%20file%20specifies,compiler%20flags%20enabled%20by%20default.) to learn more about Typescript configuration.

## 3.Test your Typescript configuration
We have configure Typescript, let us see if we have done everything correctly up to this point. Below is a sequence of actions we need to perform to test the configuration.

 i). Create `src` directory in your project directory and `index.ts` file inside it.
 ii). Write a simple piece of Typescript code in `index.ts` that prints a string on console. For example:

```
const projectName: string = 'Project creater'
console.log(projectName)
```
iii). Run Typescript code before compilation
run `ts-node src/index.ts`
iv). Compile Typescript code and run compiled code.
- run `tsc` command to generate `./build` directory
- run `node ./build/index.js` to test compiled code.

Assuming you successfully followed the above procedure, your code did run without errors and produced the expected output, you can have successfully configured Typescript in this project directory.

## 4. Customize npm scripts
After successfully testing the configuration, we need to add executable actions to package.json file. This will enable you to compile and run your code with little effort using `npm run <action>` commands.
 
Replace the scripts in package.json with the following settings
```
"scripts": {
    "build": "tsc",
    "dev": "ts-node src/index",
    "start": "node ./build/index",
    "nodemon":"nodemon src/index"
  },
```
- `build`: Executed as `npm run build`. Compiles your Typescript code and writes it in the `outDir` directory as configured in `tsconfig.json`.
- `dev`: Executed as `npm run dev`. Runs Typescript files in development mode without emitting compiled code.
- `start``: Executed as `npm start`. Runs code that has been compile into JavaScript.
- `nodemon`: Executed as `npm run nodemon`. Continuously runs Typescript code and restarts automatically on every change.


## 5.Test npm script commands
Run the commands below to confirm that they work as described in step 4.

- run in dev mode:  `npm run dev`
- compile Typescript into JavaScript: `npm run build`
- run compiled JavaScript: `npm run start`
- run with auto-restart on change: `npm run nodemon`


Finally, if you are interested in cloning this project starter, feel free to do so from [my github repository](https://github.com/GHOST-Aram/node-ts-starter/tree/main).
