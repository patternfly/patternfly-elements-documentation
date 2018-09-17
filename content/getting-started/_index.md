+++
title = "Getting Started"
description = "Use a RHElement in your web site or web app."
date = 2018-08-31T14:02:31-04:00
weight = 20
draft = false
bref = ""
toc = true
+++


## 1. Install RHElements


Use [NPM](https://www.npmjs.com/) (Node Package Manager) to install the whole RHElements library or a handful of individual RHElements.

```bash
npm install --save @rhelements/rh-card
```

Or, utilize the Red Hat asset library! When it exists! 



## 2. Include RHElements on a page

You have some options:

1. Load JavaScript modules via script tag: `script type="module"`
	1.  Downloads all of the dependencies on its own
	2.  [Only supported in modern browsers](https://caniuse.com/#search=module)
2. Include the RHElement and its dependencies on the page(s) or within the app.

	```html
	import '@rhelements/rh-card/rh-card.js';
	import '@rhelements/rh-cta/rh-cta.js';
	```

3. Use [require.js](https://requirejs.org/) JavaScript file and module loader
	- Learn more about [Polyfills](/getting-started/polyfills)
3. Load individual RHElement scripts, but bundle the polyfills with the base `rhelement.js` file
	1.  All elements are based off of rhelement.js so including the polyfills with this one file would mean you only need to include the rhelement.js file before you include anything else
4. Bundle all of the scripts together into one
5. TBD Idea: polyfill.io > webservice (build something similar internal to RH - component service)
	1.  pipe needed polyfills for website, checks headers, runtime
	2.  delivers dynamic JS
	3.  If I want rh-card - it gets the rh-card.js + required other files (serves up js bundle)



## 3. Use RHElements markup

You can use RHElements with other standard HTML markup in your app or page:

```html
import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';
import '@rhelements/rh-card/rh-card.js';
import '@rhelements/rh-cta/rh-cta.js';

class App extends Component {
  render() {
    return (
      <div className="App">
        <header className="App-header">
          <img src={logo} className="App-logo" alt="logo" />
          <h1 className="App-title">Welcome to React</h1>
        </header>
        <p className="App-intro">
          To get started, edit <code>src/App.js</code> and save to reload.
        </p>
        <div className="body">
          <rh-card>
            <h2 slot="header">Default card</h2>
            <p>This is the default rh-card and <a href="#">a link</a>.</p>
            <p>Leverage agile frameworks to provide a robust synopsis for high level overviews. Iterative approaches to corporate strategy foster collaborative thinking to further the overall value proposition.</p>
            <p>Organically grow the holistic world view of disruptive innovation via workplace diversity and empowerment.</p>
            <div slot="footer">
            	<rh-cta priority="secondary"><a href="#">Learn more</a></rh-cta>
            </div>
          </rh-card>
        </div>
      </div>
    );
  }
}

```


## 4. Add attributes 

You may choose to add attributes such as `priority` or `color` as needed to adjust usage of palette color, context, or priority.

```html
  <rh-card color="darkest">
    <h2 slot="header">Dark card</h2>
    <p>Lorem ipsum.</p>
    <rh-cta color="complement" priority="primary" on="dark" slot="footer">
        <a href="#">Important call-to-action</a>
    </rh-cta>
  </rh-card>
```



