# Initialized Project Directory for TypeScript and Node.js

Are you new to Typescript? Do you need help creating and configuring a project directory for Typescript and Node? This article sequentially describes steps on how to create an initial project directory for Node and Typescript.

This article will guide you through 5 key steps as follows:

1. Create a project directory and install dev dependencies
2. Generate and edit the Typescript configuration file
3. Test Typescript configuration
4. Customize `npm` scripts
5. Test `npm` script commands

After completing this guide, you will have created a project directory in which you can do the following:

 - Run Typescript code without the manual compilation step.

 - Compile Typescript source code to JavaScript build code.

 - Run JavaScript build code.

 - Run Typescript code automatically on every change.

Now with the knowledge of what to expect from this article, let us go ahead and start by creating a new project directory.

## 1. Create a Project Directory and Install Dev Dependencies.
First and foremost, we need to create a new folder, generate a `package.json` file, and install dev dependencies in the following sequence. 

i). Create a folder with a name of your choice and open it in your favorite IDE.

ii). Generate a `package.json` file using the command `npm init -y`

iii). Install development dependencies using the command

`npm install -D typescript ts-node @types/node nodemon`

By executing the above command, we have installed

- `typescript` for Typescript language.
- `ts-node` to run Typescript code without manual compilation step
- `@types/node` Typescript types for node
- `nodemon` to restart code execution automatically on saving changes change

## 2. Generate and edit the Typescript configuration file.
After step 1, we can successfully create and execute Typescript code but it would not be convenient enough. To take better advantage of Typescript, we need to adopt some of the settings it provides. To achieve the objective of this step we will generate a `tsconfig.json` file and make a few changes in the following sequence:

 i). Run the command `tsc --init` to generate the `tsconfig.json` file.

 ii). Replace your `tsconfig.json` file with the following configs
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
These settings are not the only Typescript configurations that you can use. This is just what you need to get started. Visit [Typescript Documentation](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html#:~:text=The%20tsconfig.json%20file%20specifies,compiler%20flags%20enabled%20by%20default.) to learn more about Typescript configuration.

## 3. Test your Typescript configuration.
Now that we have configured Typescript, let us see if we have done everything correctly up to this point. Below is a sequence of actions we need to perform to test the configuration.

i). Create a `src` directory in your project directory.

ii). Navigate into the `src` directory and create an `index.ts` file inside it.

iii). Write a simple Typescript code snippet in `index.ts` that prints a string on the console. For example:

```
const projectName: string = 'Project creator'
console.log(projectName)
```

ii). Run Typescript code before compilation: Run `ts-node src/index.ts`
```
//expected output
Project creator
```

v). Compile Typescript code into JavaScript. Run the `tsc` command to compile Typescript and generate the `./build` directory. This step should create a `build` directory in the root directory of your project.

v). Run compiled JavaScript code. Run `node ./build/index.js` to test compiled code.

```
//expected output
Project creator
```

By following the above procedure, your code should execute without errors and produce the expected output. Typescript configuration is successful, let us go ahead and add some custom `npm` scripts in the next step.

## 4. Customize `npm` scripts.
After successfully testing the configuration, we need to add executable actions to the `package.json` scripts object. This will enable us to compile and run our code with little effort using `npm run <script>` commands.
 
Replace the scripts object in package.json with the following settings
```
"scripts": {
    "build": "tsc",
    "dev": "ts-node src/index",
    "start": "node ./build/index",
    "nodemon":"nodemon src/index"
  },
```

The new scripts we have added will enable us to do the following:

- Compile Typescript code and generate JavaScript. The script `build`, executed as `npm run build`, generates a `build` folder.

- Run Typescript files in development mode without emitting compiled code. The script `dev`, executed as `npm run dev`, runs Typescript code without creating the `build` folder.

- Run compiled JavaScript. The script `start`, executed as `npm start`, runs the `index.js` file in the `build` directory. 

Let us go ahead and test the scripts in the next step.

## 5. Test `npm` script commands.
Run the commands below to verify that they work as described in step 4.

- Run Typescript code:  `npm run dev`.
- Compile Typescript into JavaScript: `npm run build`.
- Run compiled JavaScript: `npm run start`.
- Run with auto-restart on change: `npm run nodemon`.


Finally, That's all you need to create an initial project directory for Node and Typescript. If you are interested in cloning this project starter, feel free to do so from [my GitHub repository](https://github.com/GHOST-Aram/node-ts-starter/tree/main).
