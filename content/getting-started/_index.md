+++
title = "Getting Started"
description = "Create your own bulletproof web component."
date = 2018-08-31T14:02:31-04:00
weight = 20
draft = false
bref = ""
toc = true
+++

## Prerequisites

Clone the [RHElements/rhelements](https://github.com/RHElements/rhelements) and run the install command from the root of the repository.

```
npm install
```

## Generate a RHElement

Using the [generator-rhelement](https://github.com/RHElements/generator-rhelement), which installed as a dev dependency, the generator will ask you a few questions that will help with the scaffolding. Make sure you are in the root directory of the RHElements repository.

```
npm run new
```

## Scaffolding Structure

The generator will scaffold out a new RHElement that will include a ES6 module version of your element as well as a version compiled to ES5 code. These two files will live at the root of your new element. **DO NOT EDIT THESE TWO FILES**. These two files are the files that will be used when your element is distributed and they'll be overwritten during development and your build.

Instead, do your development in the `/src` directory of your element. In the `/src` directory you'll find a Javascript file that extends the RHElement class that takes care of setting up a shadow root and ShadyCSS. The HTML file is where you'll add the HTML that will be cloned into the shadow root. And the CSS or SCSS file (depending on if you're using Sass) is where you'll add your styles. During the development and build tasks, a Gulp task will merge these three files together into the root of your element and will update the ES6 and ES5 versions.

## Develop

Run the dev script in the package.json file at the root of the element you just created and Gulp will start watching the files in your `/src` directory and will run a build each time you edit one of those files.

```
npm run dev
```

## Preview Your Changes

From the root of the RHElements repository, run the start command which will open a browser to the `/doc` directory.

```
npm start
```

From there you can change the URL to the demo page of the element you're working on. For example, if I ran `npm run dev` in the `/elements/rh-card` directory, I'd navigate in the browser to `http://localhost:1234/elements/rh-card/demo`.

## Test

From the directory of the element you're working on, run the test script in the package.json file and Web Component Tester will use Mocha and Chai to execute your tests in the browser.

```
npm test
```

## Build

Prepare your element for distribution by running the build script in the package.json file located at the root of the element you're working on. If you've been running `npm run dev`, the dev script runs the build script every time you save a file in the `/src` directory so running the build script might be redundant, but better safe than sorry.

```
npm run build
```

The build script will merge the files in the `/src` directory and update the ES6 and ES5 versions of your element in the root of the element. These two files are the files that your applications will either require or import for use.

## Publish

We've been publishing our RHElements to npm under the [RHElements organization](https://www.npmjs.com/org/rhelements).

## Create a Rhelement

Now that we have everything set up, let's create a RHElement together.

[Create a RHElement](/docs/create-a-rhelement/step-1.html)
