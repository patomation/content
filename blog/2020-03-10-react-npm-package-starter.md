---
templateKey: blog-post
title: Making a React npm package starter
date: 2020-03-10T15:04:10.000Z
featuredpost: false
featuredimage: /img/flavor_wheel.jpg
description: 
tags:
  - React
  - Rollup
  - npm
---

As I've been creating projects with react over the years I have created many components.
When I remember I need a component I would look back into the project a that used it.
This can be a time sink.

Recently I created a UI library for shairing my components. But I've found that some of the compoents counld be stand alone.
When I cloned my library to create the one off component I noticed that I was having to delete a lot of stuff that pertained to the UI library. And next time I created again onother component I would probably clone that single component.

I decided It was in my best interest to create a starter repo where I can put my component code and tests it while keeping in updated when the latest best practices.

I would like to walk through the features of this stater.

### Typescript

First its using React but also typescript. I find that haveing strict type checking is helpfull to keep the code more in line with best practices. I accomplish this by linking my ts configs to eslint. My ide, vscode, picks up on these rules and automatically highlights syntax errors and can even auto fix some on save. Which is nice.

### Prop Type Generation
I didn't want to have to maintain both react prop-types and TypScript types each time I make a component. SO I sought out a way to generate the prop-types from the types.
One solution I found is a babel plugin that is called ```babel-plugin-typescript-to-proptypes```. 
This nessesity made it challenging to use everything together with Rollup.

### Rollup
I don't think I needed to use rollup or even babel for that mater to transpile the code. I could have gotten away with simply running ```tsc``` and call it done. But I wanted two things one to be able to create a common js module and an esm module. Second I wanted prop types generation.
since I didn't find another proptype gen plugin I was stuck having to use a babel plugin for rollup and then in the babel config add a typescript transpiler plugin. This was a little messy since all the configs are now pointing all over the place. But the rollup config was keeping things a little orderly.

### Types file generation
Another thing I also wanted was the types ```.d.ts``` file to be generated only. So i had to run a separate tsconfig that extended the first one that used ```"declaration": true``` and ```"emitDeclarationOnly": true```. This config gets used in a separate npm script. 

What I get is a publishable module that makes a commonjs, esm, and types files.

If you want to see this project [check out it out here](https://github.com/patomation/react-npm-package-starter)

Going forward I would like to look into creating a script that can clone the repo and replace template varaible names like the package.json name and other name refferences in other places for example the readme and so on. 


