# node-ts-starter
This an Initialized project directory for Node and Typescript


## 1.Intialize Project Directory
I. Create a folder with a name of your choice and open it in your favorite IDE.
I. Generate package.json file using the command `npm init`
I. Install dev dependencies 
`npm install -D typescript ts-node @types/node nodemon`

-typescipt for Typescript language.
-ts-node to run TS code without manual compiling
-@types/node Typescript types for node
-nodemon for server auto-restart on change

## 2.Generate Typescript configuration file
 I. Run the command `tsc --init` to generate tsconfig.json file.
 II. Replace your `tsconfig.json` file with the following configs
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

## 4. Configure npm scripts
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
