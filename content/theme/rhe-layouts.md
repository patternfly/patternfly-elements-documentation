+++
title = "RH Layouts"
description = ""
date = 2018-08-31T14:02:31-04:00
weight = 11
draft = false
bref = ""
toc = true
menu = "theme"
+++

<link rel="stylesheet" type="text/css" href="//overpass-30e2.kxcdn.com/overpass.css">
<link rel="stylesheet" type="text/css" href="../rhe-layouts.css">
<link rel="stylesheet" type="text/css" href="https://cdnjs.cloudflare.com/ajax/libs/prism/1.14.0/themes/prism.min.css">
<link rel="stylesheet" type="text/css" href="../../cp-themeset/cp-themeset.css">

<style>

.rhe-l-grid > * {
  background: #e0d7ee;
  padding: 8px;
}
</style>

<article>
  <section>
    <h2>Grid</h2>

    <section>
      <h3>Pure Grid</h3>
      <div class="rhe-l-grid rhe-m-gutters rhe-m-all-6-col rhe-m-all-4-col-on-md rhe-m-all-3-col-on-lg">
        <div>Item</div>
        <div>Item</div>
        <div>Item</div>
        <div>Item</div>
        <div>Item</div>
      </div>

      <h4>Code</h4>
      <pre><code class="lang-markup">&lt;div class="rhe-l-grid rhe-m-gutters rhe-m-all-6-col rhe-m-all-4-col-on-md rhe-m-all-3-col-on-lg"&gt;
&lt;div&gt;Item&lt;/div&gt;
&lt;div&gt;Item&lt;/div&gt;
&lt;div&gt;Item&lt;/div&gt;
&lt;div&gt;Item&lt;/div&gt;
&lt;div&gt;Item&lt;/div&gt;
&lt;/div&gt;</code></pre>
    </section>

    <section>
      <h3>Bootstrap-style Columns</h3>
      <div class="rhe-l-grid rhe-m-gutters">
        <div class="rhe-l-grid__item">Default Item</div>
        <div class="rhe-l-grid__item rhe-m-2-col"><code>rhe-m-2-col</code></div>
        <div class="rhe-l-grid__item rhe-m-10-col"><code>rhe-m-10-col</code></div>
        <div class="rhe-l-grid__item rhe-m-4-col"><code>rhe-m-4-col</code></div>
        <div class="rhe-l-grid__item rhe-m-4-col"><code>rhe-m-4-col</code></div>
        <div class="rhe-l-grid__item rhe-m-4-col"><code>rhe-m-4-col</code></div>
        <div class="rhe-l-grid__item rhe-m-6-col rhe-m-3-col-on-md"><code>rhe-m-6-col rhe-m-3-col-on-md</code></div>
        <div class="rhe-l-grid__item rhe-m-6-col rhe-m-3-col-on-md rhe-m-startat-7-col-on-md"><code>rhe-m-6-col rhe-m-3-col-on-md rhe-m-startat-7-col-on-md</code></div>
        <div class="rhe-l-grid__item rhe-m-6-col rhe-m-3-col-on-md"><code>rhe-m-6-col rhe-m-3-col-on-md</code></div>
      </div>

      <h4>Code</h4>
      <pre><code class="lang-markup">&lt;div class="rhe-l-grid rhe-m-gutters"&gt;
&lt;div class="rhe-l-grid__item"&gt;Default Item&lt;/div&gt;
&lt;div class="rhe-l-grid__item rhe-m-2-col"&gt;&lt;code&gt;rhe-m-2-col&lt;/code&gt;&lt;/div&gt;
&lt;div class="rhe-l-grid__item rhe-m-10-col"&gt;&lt;code&gt;rhe-m-10-col&lt;/code&gt;&lt;/div&gt;
&lt;div class="rhe-l-grid__item rhe-m-4-col"&gt;&lt;code&gt;rhe-m-4-col&lt;/code&gt;&lt;/div&gt;
&lt;div class="rhe-l-grid__item rhe-m-4-col"&gt;&lt;code&gt;rhe-m-4-col&lt;/code&gt;&lt;/div&gt;
&lt;div class="rhe-l-grid__item rhe-m-4-col"&gt;&lt;code&gt;rhe-m-4-col&lt;/code&gt;&lt;/div&gt;
&lt;div class="rhe-l-grid__item rhe-m-6-col rhe-m-3-col-on-md"&gt;&lt;code&gt;rhe-m-6-col rhe-m-3-col-on-md&lt;/code&gt;&lt;/div&gt;
&lt;div class="rhe-l-grid__item rhe-m-6-col rhe-m-3-col-on-md rhe-m-startat-7-col-on-md"&gt;&lt;code&gt;rhe-m-6-col rhe-m-3-col-on-md rhe-m-startat-7-col-on-md&lt;/code&gt;&lt;/div&gt;
&lt;div class="rhe-l-grid__item rhe-m-6-col rhe-m-3-col-on-md"&gt;&lt;code&gt;rhe-m-6-col rhe-m-3-col-on-md&lt;/code&gt;&lt;/div&gt;
&lt;/div&gt;</code></pre>

    </section>

  </section>
</article>
