+++
title = "Theming Slots"
description = ""
weight = 5
draft = false
bref = ""
toc = true
menu = "theme"
tags = [ "theme" ]
+++


There seem to be lots of tricky gotchas related to web components, and a *lot* of [documentation](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_templates_and_slots). Here’s a simplified guide with some basic code examples.


## Slots

**Vocab tip: Elements that can be inserted into slots are known as _slotable_; when an element has been inserted in a slot, it is said to be _slotted_.**

* Slots are places to pass content or markup into specific regions within your web component template.

```
// my-component.html:
<div class="whatev">
    <slot name="header"></slot>
    <slot></slot>
    <slot name="footer"></slot>
</div>
```

* If you put something into a web component tag without a slot name, it will put that markup into the unnamed slot. 

    * If there is no unnamed slot, it will not render that content. 

    * For this reason, it’s perhaps a good idea to leave one unnamed slot if general markup is allowed.

* Whenever you add slot="something", you are telling the webcomponent where to put this information in the inner template

```
// my-web-page.html:

<my-component>
    <div slot="header"></div>
</my-component>
```

* You can’t have nested slots *with the same name *(but when you use different names, the WC will pick up the content and put it where it belongs in the WC template)

```
// my-web-page.html:
<my-component>
   <div slot="header">
     <h1 slot="header">Nope</h1>
   </div>
 </my-component>
 	
 // But...
 <my-component>
   <div slot="header">
     <h1 slot="header__content">Yep</h1>
   </div>
 </my-component>
 ```

* The reason that we are able to style links within the CTA component is because the `<a>` tag is being passed into the only unnamed slot in the CTA component. The link tag doesn’t need an explicit attribute like `slot="link"` because if a web component has one unnamed `<slot></slot>` then anything you put inside that custom component tag will be in that slot by default. 

```
<rh-cta priority="primary">
    <a href="#">Primary</a>   <!-- this element is slotted by default -->
</rh-cta>
```

* Child elements within a custom tag don’t have to be the first child to be styled, they only have to be direct descendants of the component. Meaning, once you nest something inside another tag, it can no longer receive styles targeted with the `::slotted` pseudo selector.

If we assume the component has some basic styles on all slots like this:   `::slotted()  { color: red; }`

Then both the div and link tag would be styled:

```
 <rh-cta priority="primary">
   <div>styled!</div>
   <a href="#">styled!</a>
 </rh-cta>
```

However if the link tag is nested inside the div, then it would not receive styles because it’s not a direct child of the rh-cta component.

```
 <rh-cta priority="primary">
   <div>
     <a href="#">cannot receive styles, because it’s nested</a>
   </div>
 </rh-cta>
```

## Styling Slots

The lines blur between shadow DOM & light DOM when slots are involved. Basically if you add `slot=" "` to a regular HTML element inside a web component, you are opening a window to allow styles from the web component to style that thing. It only applies directly to the item with the slot name on it though, nothing nested inside it. 

The examples below would be inside the my-component.scss file:


* Style any slot. Probably way too general.
    * `::slotted() { color: red; }` 
* Style any iframe in any slot. Still too general.
    * `::slotted(iframe) { color: red; }` 

* Style any HTML element with attribute **slot="video"**, but not anything *inside* the slot.
    * `[name="video"]::slotted(*)  { color: red; }` will style some of the markup inside the web component:

    * ```
	<my-component>
       <h1 slot="video">I will be red!</h1>
	    <div slot="video">
	        <h2>I will not be red.</h2>
	    </div>
    </my-component>
	```

* Add further specificity, styling only iframes with the slot="video"
    * `[name="video"]::slotted(iframe)  { color: red; }`

* Just for the record, here are some examples that *won’t* work:

    * ` ::slotted() iframe[name="video"] {}`
    * ` ::slotted() h2 {}`
    * ` ::slotted() anything_here… {}`

## Document styles vs. web component styles

* Note that anything in the light DOM can be styled by regular classes loaded on the page (in the document head or inline) and they will *win* the specificity battle. For example, this style:

```
<head>
<style>
  iframe {
    border: 2px solid wheat;
  }
</style>
</head>
```

Will trump any slotted styles coming from the web component CSS, like:

`[name="video"]::slotted(iframe)  {}`

However, you can move an element into the Shadow DOM, where document styles will not apply. 

```
connectedCallback() {
  super.connectedCallback();
  const iframe = this.querySelector("iframe");
  this.shadowRoot.appendChild(iframe);
}
```
