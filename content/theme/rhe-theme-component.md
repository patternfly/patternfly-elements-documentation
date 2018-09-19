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


When applying colors to your new component, it's important to reference CSS variables from the [RHElements palette](https://github.com/RHElements/rhelements/blob/master/elements/rh-sass/variables/_colors.scss). This way people using the components will be able to update all of them at once by changing the value of those palette variables.

It's also important for all CSS variables to have fallback values:

```css
.rh-sad-component {
    color:              var(--rh-theme--color--ui-link, #99ccff);
    background-color:   var(--rh-theme--color--ui-accent, #fe460d);
}
```

While writing CSS vars in this way is fine, the code can become difficult to read and manage. Not only must you input two colors (the variable of choice and the fallback), but you're stuck searching for the appropriate SASS color variable or, worse, looking up color hex values (which can cause inconsistencies). So we've simplified this process with the `rh-var()` function!

## rh-var function

Within rh-sass, we've added the `rh-var()` function to make it easier to apply color to components. Using this function also allows you to omit both the <code>--rh-theme--color--</code> from the theming CSS variable and the <code>$rh-color--</code> from the beginning of the color name for simplicity's sake. For example:

```css
.rh-happy-component {
    color:             #{rh-var( ui-complement )};
    background-color:  #{rh-var( surface--lightest )};
}
```

_**Note:** When you use this function, make sure you wrap it in the interpolation syntax <code>#{ }</code> so it will print the CSS variable name and a hex color fallback properly when it's compiled._

## Local component variables

In some cases, where theming a component and all its options can be complex, you may want to define local component variables. For instance, the CTA (call-to-action) component, has several background color, text color, and link colors (including hover, focus, and visited states) for each option. That's a lot of colors! Therefore, we created local variables for the CTA component, and redefined the values when different attributes come into play. Here's an example (Notice the usage of the `rh-var` function):

```css
:host {
    --rh-cta--main:           #{rh-var( ui-link )};
    --rh-cta--main--hover:    #{rh-var( ui-link--hover )};
    --rh-cta--main--focus:    #{rh-var( ui-link--focus )};
    --rh-cta--main--visited:  #{rh-var( ui-link--visited )};
    --rh-cta--aux:            transparent;
    --rh-cta--aux--hover:     transparent;
}
```

The CTA component's CSS will make use of these variables by setting the link color using `rh-cta--main` and the background color of the button using `rh-cta--aux`, like so::

```css
::slotted(a) {
    border-color: var( --rh-cta--main );
    background:   var( --rh-cta--main );
    color:        var( --rh-cta--aux );
}
```

Because the CTA component allows for palette color overrides such as `color="complement"`, it will simply reset the value of these local variables to match those of the palette variables. That way, when someone using this component adds the attribute `color="complement"` to the CTA, the complement color is applied. These properties are also marked as important so that they have higher specificity over other conditions such as `on="dark"`.

```css
:host([color="complement"]) {
    --rh-cta--main:        #{rh-var( ui-complement )} !important;
    --rh-cta--main--hover: #{rh-var( ui-complement--hover )} !important;
    --rh-cta--aux:         #{rh-var( ui-complement--text )} !important;
    --rh-cta--aux--hover:  #{rh-var( ui-complement--text--hover )} !important;
}
```

### Abstract naming of local variables

In the above examples, you may have noticed that we've named our local component variables abstractly, e.g. `--rh-cta--main` and `--rh-cta--aux`. The reason for this naming convention is that the CTA component's main color and auxiliary color often switch between text color and background color depending on the attribute options&#8212;preventing awkward redefining of colors. For instance, if we were to name our local component variables with more contextual names:

```css
:host {
    --rh-cta--link:   #{rh-var( ui-link )};
    --rh-cta--bg:     transparent;
}
```

Then, the use of these local component variables could become confusing down the road, where text colors might be assigned to background colors:

```css
:host([priority="primary"]) {
  --rh-cta--link:    #{rh-color(ui-accent)};
  --rh-cta--bg:      #{rh-color(ui-accent--text)};

  ::slotted(a) {
    border-color:    var(--rh-cta--link) !important;
    background:      var(--rh-cta--link) !important;
    color:           var(--rh-cta--bg) !important;
  }
}
```

If your component is rather simple and doesn't have instances where context-based local component variables are being assigned out-of-context, please feel free to name them appropriately!
