Are you new to Typescript? Do you need help creating and configuring a project directory for Typescript and Node? This article will guide you on how to create a project directory for Node and Typescript.
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

a) Create a folder with a name of your choice and open it in your favorite IDE.
b) Generate package.json file using the command `npm init -y`
c) Install development dependencies using the command

`npm install -D typescript ts-node @types/node nodemon`

By executing the above command, we have installed

- typescipt for Typescript language.
- ts-node to run Typescript code without manual compiling
- @types/node Typescript types for node
- nodemon for server auto-restart on code change

## 2.Generate and edit Typescript configuration file
After step one, we can successfully create and execute Typescript code but it would not be convenient enough. In order to take better advantage of Typescript, we need to adopt some of the settings it provides. We will generate `tsconfig.json` file and make a few changes in the following sequence:

 a) Run the command `tsc --init` to generate tsconfig.json file.
 b) Replace your `tsconfig.json` file with the following configs
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
 I. Create `src` directory in your project directory and create `index.ts` file inside it.
 II. Write a simple piece of Typescript code in `index.ts` that prints a string on console.

```
const projectName: string = 'Project creater'
console.log(projectName)
```
III. Run Typescript code before compilation
run `ts-node src/index.ts`
IV. Compile Typescript code and run compiled code
run `tsc` command to generate `./build` directory
run `node ./build/index.js` to test compiled code

## 4. Customize npm scripts
  -Replace the scripts in package.json with the following settings
```
"scripts": {
    "build": "tsc",
    "dev": "ts-node src/index",
    "start": "node ./build/index"
  },
```


## 5.Test npm script commands
`npm run dev`
`npm run build`
`npm run start`
