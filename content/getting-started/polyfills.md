+++
title = "Polyfills"
description = "Add polyfills to support all of the major browsers."
date = 2018-08-31T14:02:31-04:00
weight = 3
draft = false
bref = ""
toc = true
menu = "start"
+++

Some browsers do not support ES6 modules, custom elements, shadow DOM, and
custom CSS variables yet. We'll need to add some polyfills to make everything
work in our supported browsers.

The easiest way to get everything working is to add the following polyfills to
the head of your document.

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>RHElements</title>

    <!-- polyfills -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/webcomponentsjs/1.0.10/custom-elements-es5-adapter.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/webcomponentsjs/1.0.10/webcomponents-lite.js"></script>
  </head>
  <body></body>
</html
```

## custom-elements-es5-adapter
This polyfill is needed if your custom elements have been compiled from ES6 to ES5.
It's not necessary to include this polyfill for IE 11 and it will throw a syntax
error in IE 11 because the adapter was written in ES6. However, you can ignore
this error because it will not cause issues with your elements.
