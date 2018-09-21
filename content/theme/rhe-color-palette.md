+++
title = "RHElements color palette"
description = ""
date = 2018-09-15T14:02:31-04:00
weight = 5
draft = false
bref = ""
toc = true
menu = "theme"
+++

Looking for values fast? We have a [list of all the system colors](https://github.com/RHElements/rhelements/blob/master/elements/rh-sass/variables/_colors.scss) available.

In general, a user interface uses color to convey:

 - Feedback: Error and success states
 - Information: Charts, graphs, and way-finding elements
 - Hierarchy: Showing structured order through color and typography


## UI Colors

UI colors are used throughout RHElements, and are intended to provide basic colors for ubiquitous page elements like body text and basic links in addition to hierarchical page elements, like buttons and CTA (call-to-action) links.

We've exposed 3 color variants for this design system to represent your brand:

 - Base
 - Complement
 - Accent &#8212; _the color which should stand out the most_

### Using UI colors in your theme

Let's say your brand colors are navy, orange, and medium gray, you'll want to set orange as the accent color&#8212;since it's the most noticeable. This way, you'll see it appear on primary level CTA (call-to-action) links and other elements that need to have more weight in the visual hierarchy of the page.

To override the default RHElements' colors, simply redefine the CSS variables in your theme stylesheet, like this:

```css
:root {
  --rh-theme--color--ui-base:                     #030070;
  --rh-theme--color--ui-base--hover:              #010047;
  --rh-theme--color--ui-base--text:               #ffffff;
  --rh-theme--color--ui-base--text--hover:        #eeeeee;
  --rh-theme--color--ui-complement:               #646464;
  --rh-theme--color--ui-complement--hover:        #464646;
  --rh-theme--color--ui-complement--text:         #ffffff;
  --rh-theme--color--ui-complement--text--hover:  #eeeeee;
  --rh-theme--color--ui-accent:                   #d62e00;
  --rh-theme--color--ui-accent--hover:            #a92500;
  --rh-theme--color--ui-accent--text:             #ffffff;
  --rh-theme--color--ui-accent--text--hover:      #eeeeee;
}
```

_**Note:** Though it is not required, you may choose to set the value of a link color to something in your brand. However, it is highly recommended that you choose colors that provide a good user experience, e.g. color contrast._


## Surface Colors

It's also a good idea to choose some neutral colors for general UI backgrounds and borders—usually grays. Surface color encompass any "surface" that are typically part of container-type elements, like cards or bands. These colors should be harmonious with your corporate style guide (if you have one), but they may not necessarily be your company’s primary brand colors.

```css
:root {
    --rh-color--surface--base:                      #ccc;
    --rh-color--surface--base--text:                #000;
    --rh-color--surface--base--link:                #00538c;
    --rh-color--surface--base--link--visited:       #7551a6 !default;
    --rh-color--surface--base--link--hover:         #00305b !default;
    --rh-color--surface--base--link--focus:         #00305b !default;
}
```


## Feedback Colors

And finally, you’ll have colors for states such as error, warning, and success. Group these colors to see how well they work together and refine as needed.

```css
:root {
    --rh-color--feedback--critical:                 $rh-color--red-600 !default;
    --rh-color--feedback--critical--lightest:       $rh-color--red-50 !default;
    --rh-color--feedback--critical--darkest:        $rh-color--red-800 !default;
}
```
