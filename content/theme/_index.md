+++
title = "Theme"
description = "Use our beautifully designed theme, or modify it to your needs."
date = 2018-08-31T14:02:31-04:00
weight = 20
draft = false
bref = ""
toc = true
+++


## Theming 101

Every RHElement is built to automatically utilize the colors defined in the palette, which you control! Generally speaking, the only thing you will need to do is re-define the CSS variables to match your brand and you're done. 

Often components will make decisions about how to best utilize those colors, which is "baked in". For example, a standard CTA, or call-to-action component, uses the standard link color in its default state. But, if you set the `priority` attribute value to `primary`, the CTA will make use of the accent color from the palette. 


	<rh-cta priority="primary">
		<a href="#">Primary</a>
	</rh-cta>


This is because the accent color should be the brightest and boldest, and the primary call-to-action should be the most attention-grabbing item on the page. 


Additionally, each component comes equipped to adjust its colors depending on where it's placed on the page. For example, should you need to put a default CTA (which is blue) on a dark blue card, the CTA will need to adapt. You can do this by informing the component of its context (on a dark background) by giving the `on` attribute the value of `dark`. 

    <rh-card color="dark">
	    <rh-cta color="base" on="dark">
	    	<a href="#">Default</a>
	    </rh-cta>
	</rh-card>

Should you need to deviate from this color usage, and set your primary CTA to use the complement color from the palette, you may also pass a value of `complement` into the `color`  attribute, like this:

	<rh-cta priority="primary" color="complement">
		<a href="#">Primary</a>
	</rh-cta>

Please note that if you are opting to override colors of components, they will not automatically respond to the `on="dark"` attribute any longer.


