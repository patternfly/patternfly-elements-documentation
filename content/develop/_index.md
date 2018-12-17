+++
title = "Development Overview"
description = "Build and create reusable web components."
weight = 1
draft = false
bref = ""
toc = true
menu = "theme"
tags = [ "theme" ]
+++


## The Elements pattern library

Before getting started, it's important to note that because this is a library, each of the components within it are designed to work together. For this reason, Elements should follow some basic guidelines:

## Guidelines for building a PatternFly Element

1. It should should be easy to understand. 
    - If it is complicated, can it be split up into simpler pieces?
2. A component can only be one of these types: `content`, `container` or `combo`. 
    - If it is a `content` component, then it has typography styles.
    - If it is a `container` component, then it has surface colors and padding, no typography styles!
    - Read more on this below.
3. Context aware
    - `Content` components should be equipped with styles for the `on="dark"` attribute, so that they can be used on both light and dark backgrounds. 
4. Framework agnostic
    - A PatternFly Element should "just work" when you drop it onto any page (provided the proper polyfills are there). It should have ALL the styles it needs, such as font-family properties.

## Container Elements

A container never directly styles the children inside the contain. It is only concerned with their horizontal or vertical alignment and spacing. For example in a card, you might apply margins to the slots, but you would not apply padding or color not to the content inside of slots.

**Example: [Card](https://github.com/patternfly/patternfly-elements/blob/master/elements/pfe-card/src/pfe-card)**

This component has background color options, and attributes to change the vertical spacing between the slots.

## Content Elements

A component always touches all four sides of its parent container. For example, if you are creating a teaser component, it should not have padding or margins around the type. It might, however have margins between the headline and author.

**Example: [Call-to-action](https://github.com/patternfly/patternfly-elements/blob/master/elements/pfe-cta/src/pfe-cta)**

This component has typography styles, and attributes to change the priority level of the call-to-action. It also has `on="dark"` styles built in, so that colors will automatically adjust. 

## Combo Elements

These elements are designed to create easy-to-use combinations of other smaller components. Ideally they also bundle up attributes into a few configurations.

**Example: [Hide-show](https://github.com/patternfly/patternfly-elements/blob/master/elements/pfe-hide-show)**


## @todo should features be opt-in or opt-out?
- If it's both, that’s confusing
- If they are opt-in, it ensures that components don't change themselves on people's sites who are asking for all minor versions of components.




# Attribute naming 

## General
- Attribute names should be specific so they are easy to read and understand. 
- Use standard [HTML global attributes](https://www.w3schools.com/tags/ref_standardattributes.asp) and / or proper [ARIA attributes](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA) when appropriate
    - Example: `<pfe-pagination hidden>` `<pfe-cta title="RHEL features">`

## Prefixing attributes

- To avoid collisions with other libraries, known and unknown as well as new HTML tags and attributes
- To ensure folks who have no prefixing on their existing sites can use PF Elements without worry of collisiding CSS or JavaScript
- To  have a single-source-of-truth, i.e. one class or attribute for styling vs. chaining attributes

## Optional component features should be activated with a unique attribute instead of values within a generic attribute
- The pagination component has opt-in features like enbaling the previous and next buttons. Ideally items are treated like booleans and can be toggled on if the attribute name is present on the tag. However if a feature requires a specific value to be passed in, such as a a number of results shown per page, it is fine to look for a value.
- Example: 
    - YES: `<pfe-pagination pfe-prev-next pfe-jump-nav pfe-results="10">`
    - NO: `<pfe-pagination pfe-features="prev next caret">`


## Example attributes with values
Some attributes are standardized. 

- `pfe-type="content"`
    - Intended to provide context about parent child relationships and separation of concerns
    - Other values: `container combo`
- `pfe-orientation="vertical"`
    - To change alignment of a container component 
    - Other values: `horizontal`
- `pfe-state="expanded"`
    - To reflect the desired state of a component on render. It may be toggled.
    - Other values: `collapsed`
- `pfe-variant="earth"`
    - The purpose is to group various styles together into one batch of settings, and to be abstract enough to allow for the evolution of the design system. The values are arbirtary and do not convey information about the styles.
    - Other values: earth, wind, fire, water
- `pfe-surface-color="complement"`
    - Purpose: Invoke palette color overrides
    - Example values: `base accent`
    - @todo Can this mean background color and/or background color?
