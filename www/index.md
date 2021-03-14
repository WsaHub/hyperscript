---
layout: layout.njk
title: ///_hyperscript
---

<div style="background-color: lightgoldenrodyellow; margin: 16px; border-radius: 8px;
            color: darkgoldenrod; border: gold 1px solid; font-size: 20px">
  <p>
    <b>NOTE:</b> hyperscript is still in very early development and may change
    dramatically between releases.  Please bear this in mind, and jump on the
    <a style="color: darkgoldenrod;font-weight: bold" href="https://htmx.org/discord">#hyperscript discord channel</a> to work with us as we develop the language.  Thank you!
  </p> 
</div>

<div class="hero" style="margin: 0; font-size: 1.6em; color: #16f;
	line-height: 1.4; margin-bottom: 2em;">

hyperscript is an experimental scripting language designed for the web, inspired by 
 [HyperTalk](https://hypercard.org/HyperTalk%20Reference%202.4.pdf)

</div>

hyperscript features include:

<div style="padding: 16px">

* inline embedding on HTML elements
* tools for working with DOM events, including event-driven control flow
* a DOM-oriented syntax, such as element id and class literals
* first class [web workers](/docs#workers)
* [async-transparancy](/docs#async)
* A pluggable, extendable parser & grammar

</div>

hyperscript is a companion project of [htmx](https://htmx.org).  Because Promises are not available in IE, unlike htmx, 
hyperscript does not strive for IE11 compatibility.

## examples

```html
<script src="https://unpkg.com/hyperscript.org@0.0.5"></script>

<button _="on click toggle .big-text">
  Toggle the "big-text" class on me on click
</button>

<div _="on mouseenter toggle .visible on #help until mouseleave">
  Mouse Over Me!
</div>
<div id="help"> I'm a helpful message!</div>

<button _="on click log me then call alert('yep, it\’s an alert')">
    Show An Alert
</button>
```

## demos

Here are the examples above in demo form:

<div class="row">
    <div class="4 col">
        <style>
        button {
          transition: all 300ms ease-in;
        }
        button.big-text {
          font-size: 2em;
        }
        </style>
        <button class="btn primary" _="on click toggle .big-text">
          Toggle .clicked
        </button>
        </div>
    <div class="4 col">
        <style>
        #help {
          opacity: 0;
        }
        #help.visible {
          opacity: 1;
          transition: opacity 200ms ease-in;
        }
        </style>
        <div _="on mouseenter toggle .visible on #help until mouseleave">
          Mouse Over Me!
        </div>
        <div id="help"> I'm a helpful message!</div>
    </div>
    <div class="4 col">
        <button class="btn primary" _="on click log me then call alert('yep, it\'s an alert - check the console...')">
            Show An Alert
        </button>
    </div>
</div>


## haiku

*the unknown button<br/>
so often inscrutable<br/>
now says what it does*
