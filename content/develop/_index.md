+++
title = "Development Overview"
description = "Build and create reusable web components."
date = 2018-08-31T14:02:31-04:00
weight = 20
draft = false
bref = ""
toc = true
+++


## The RHElements pattern library

Before getting started, it's important to note that because this is a library, each of the components within it are designed to work together. For this reason, RHElements should follow some basic guidelines:

## Guidelines for building a RHElement

1. A RHElement should be easy to understand. 
    - If it is complicated, can it be split up into simpler pieces?
2. A RHElement component can only be one of these types: `content` or `container`. 
    - If it is a `content` component, then it has typography styles.
    - If it is a `container` component, then it has surface colors and padding, no typography styles!
    - Read more on this below.
3. Context aware
    - `Content` components should be equipped with styles for the `on="dark"` attribute, so that they can be used on both light and dark backgrounds. 
4. Framework agnostic
    - A RHElement should “just work” when you drop it onto any page (provided the proper polyfills are there). It should have ALL the styles it needs, such as font-family properties.

------------

## Container RHElements

A container never imposes padding or styles on the children. It is only concerned with their horizontal or vertical alignment and spacing. For example in a card, you might apply margins to the slots, but you would not apply padding or color not to the content inside of slots.

**Example: [rh-card](https://github.com/RHElements/rhelements/blob/master/elements/rh-card/src/rh-card.scss)**

This component has background color options, and attributes to change the vertical spacing between the slots.

## Content RHElements

A component always touches all four sides of its parent container. For example, if you are creating a teaser component, it should not have padding or margins around the type. It might, however have margins between the headline and author.

**Example: [rh-cta](https://github.com/RHElements/rhelements/blob/master/elements/rh-cta/src/rh-cta.scss)**

This component has typography styles, and attributes to change the priority level of the call-to-action. It also has `on="dark"` styles built in, so that colors will automatically adjust. 