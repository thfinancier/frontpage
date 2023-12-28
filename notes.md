## To set up TS with Node the following steps should be applied:
1. npm init -y
2. npm install typescript --save-dev (or just -D instead of --save-dev)
3. npm install @types/node --D
4. npx tsc --init
This could be pasted to tsconfig.json (
{
  "compilerOptions": {
    "target": "es6",
    "module": "commonjs",
    "lib": ["dom", "es6", "es2017", "esnext.asynciterable"],
    "skipLibCheck": true,
    "sourceMap": true,
    "outDir": "./dist",
    "moduleResolution": "node",
    "removeComments": true,
    "noImplicitAny": true,
    "strictNullChecks": true,
    "strictFunctionTypes": true,
    "noImplicitThis": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noImplicitReturns": true,
    "noFallthroughCasesInSwitch": true,
    "allowSyntheticDefaultImports": true,
    "esModuleInterop": true,
    "emitDecoratorMetadata": true,
    "experimentalDecorators": true,
    "resolveJsonModule": true,
    "baseUrl": "."
  },
  "exclude": ["node_modules"],
  "include": ["./src/**/*.tsx", "./src/**/*.ts"]
}
)
5. Add these scripts to package.json: (
    "watch": "tsc -w", (compiles typescript to javascript)
    "dev": "nodemon dist/index.js",
    "start": "node dist/index.js"
    **Another way of doing the same thing. The difference is that the last two scripts are much slower than the previous.** 
    "start2": "ts-node src/index.ts",
    "dev2": "nodemon --exec ts-node dist/index.js"
)
6. Run "watch" in one terminal, and "dev" in another. "watch" will recompile ts after every change, and "dev" will run it (or in other words: it will reexecute the code that changes in the dist folder)