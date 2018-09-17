+++
title = "Create a themed RHElement"
description = ""
date = 2018-09-15T14:02:31-04:00
weight = 2
draft = false
bref = ""
toc = true
menu = "theme"
+++


When applying colors to your new component, it's important to reference CSS variables from the <a href="https://github.com/RHElements/rhelements/blob/master/elements/rh-sass/variables/_colors.scss" target="_blank">RHElements palette</a>. This way people using the components will be able to update all of them at once by changing the value of those palette variables.

It's also important for all CSS variables to have fallback values, but then the code can become difficult to read and manage, since you now must input two colors (the variable of choice and the fallback):

```css
.rh-sad-component {
    color:              var(--rh-theme--color--ui-link, #99ccff);
    backgground-color:  var(--rh-theme--color--ui-accent, #fe460d);
}
```

## rh-var function

To remedy this, there is a special function within rh-sass that makes it easier to apply color to components! When you make use of it, be sure to wrap it in the interpolation syntax `#{ }` so that when the Sass is compiled, it will print the CSS variable name and a hex color fallback. You can also omit the `rh-color--` from the beginning of the color for simplicity's sake:

```css
.rh-happy-component {
    color:             #{rh-var( ui-complement )};
    backgground-color: #{rh-var( surface--lightest )};
}
```

## Local component variables

In some cases, like the CTA (call-to-action) component, you might need to define a background color and a text color, as well as hover, focus, and visited states. That's a lot of colors! For this reason, it might be useful to create local variables for that particular component, and then redefine the values when different attributes come into play. Let's see an example, noticing the usage of the `rh-var` function:


```css
:host {
    --rh-cta--main:                     #{rh-var( ui-link )};
    --rh-cta--main--hover:              #{rh-var( ui-link--hover )};
    --rh-cta--main--focus:              #{rh-var( ui-link--focus )};
    --rh-cta--main--visited:            #{rh-var( ui-link--visited )};
    --rh-cta--aux:                      transparent;
    --rh-cta--aux--hover:               transparent;
}

```

The CTA component CSS will make use of these variables by setting the link color using `rh-cta--main` and the background color of the button using `rh-cta--aux`, like so:

```css
::slotted(a) {
    border-color: var( --rh-cta--main );
    background:   var( --rh-cta--main );
    color:        var( --rh-cta--aux );
}
```

Because the CTA component allows for palette color overrides such as `color="completement"`, it will simply reset the value of these local variables to match those of the palette variables. That way when someone using this component adds the attribute `color="complement"`to the CTA, the completement color is applied. These properties are also marked as important so that they always win over other condidions such as `on="dark"`.

```css
:host([color="complement"]) {
    --rh-cta--main:        #{rh-var( ui-complement )} !important;
    --rh-cta--main--hover: #{rh-var( ui-complement--hover )} !important;
    --rh-cta--aux:         #{rh-var( ui-complement--text )} !important;
    --rh-cta--aux--hover:  #{rh-var( ui-complement--text--hover )} !important;
}
```


