
<div id="intro-to-hyperscript">

# hyperscript is an easy & approachable language designed for modern front-end web development

<div id="sample" class="basicgrid" style="align-items: stretch" _="
  on mouseenter queue none
    repeat until event mouseleave
      transition #sample-tip's transform to 'translateX(-2ch)' using 'all 500ms ease-out'
      transition #sample-tip's transform to initial            using 'all 500ms ease-in'">

<div class="box">
<pre><code id="snippet" class="lang-hyperscript">writeText(the #snippet's innerText)
  into the navigator's clipboard
put 'copied!' into me
wait 1s
put 'copy' into me</code></pre>
</div>

<div class="box center">
<span id="sample-tip">see it in action &rarr;</span>
<button class="btn primary" _="on click
writeText(the #snippet's innerText) into the navigator's clipboard
put 'copied!' into me
wait 1s
put 'copy' into me">
copy
</button>
</div>
</div>
</div>

hyperscript makes writing event handlers and highly
responsive user interfaces easy with a clear, DOM-oriented syntax and by transparently
 handling asynchronous behavior for you &mdash; easier than callbacks, promises, even async/await.


<div>

 <span id='install'>Install: <input type=text style=display:inline;width:auto readonly value='<script src="https://unpkg.com/hyperscript.org@0.9.5"></script>'>
<button
  _="on click
  writeText(my previousElementSibling's value) on navigator.clipboard
  put 'copied!' into me
  wait 1s
  put 'copy' into me">copy</button>
</span>

</div>

## features

<div id="features-list" class="textcolumns">

**Events as first class citizens in the language**&mdash;clean syntax for
[receiving](/features/on) and [sending](/commands/send) events, as well as
[event-driven control flow](docs/#event-control-flow)

**DOM-oriented syntax**&mdash;seamless integrated [CSS id, CSS class and CSS
query literals](https://hyperscript.org/expressions/#css)

**First-class [web workers](/docs#workers)**

**[Async-transparent](/docs#async) runtime**&mdash;highly responsive user
experiences without callback hell

**[Pluggable & extendable](/docs/#extending)** parser & grammar

**[Debugger](/docs#debugging)** to step through hyperscript code

**An [xTalk](https://en.wikipedia.org/wiki/XTalk) syntax, inspired by [HyperTalk](https://hypercard.org/HyperTalk%20Reference%202.4.pdf)**

See the [**Comparison** with VanillaJS & jQuery](/comparison)

Read the [**docs**](/docs)

Try it on the [**playground**](/playground)

Community news: [This Week in HTMX](https://thisweek.htmx.org)

</div>

<div id="links">

[Companion of **htmx**](https://htmx.org) |
[**Comparison** with VanillaJS & jQuery](/comparison) |
[Read the **docs**](/docs) |
[Try it on the **playground**](/playground) |
[Check out the **cheatsheet**](https://denizaksimsek.com/wiki/en/HS%20Cheatsheet)

<aside class="box warn crowded color" style="font-size: .9em; --rhythm: 1em;">

hyperscript is in active development, working towards 1.0. The syntax and core
feature set are reasonably complete. We're focusing on more test cases and
docs. Please join us at the
<a style="font-weight: bold" href="https://htmx.org/discord">#hyperscript discord channel</a>
&mdash; thank you!

NB: because hyperscript relies on
[promises](https://caniuse.com/?search=Promise) it cannot offer IE11
compatibility

</aside>

## examples

{% example %}
<button _="on click toggle .big-text">
  Toggle the "big-text" class on me on click
</button>
{% endexample %}

<style>
button.big-text {
  font-size: 2em;
}
</style>

{% example %}
<div _="on mouseenter toggle .visible on #help until mouseleave">
  Mouse Over Me!
</div>
<div id="help"> I'm a helpful message!</div>
{% endexample %}

<style>
#help {
  opacity: 0;
}
#help.visible {
  opacity: 1;
  transition: opacity 200ms ease-in;
}
</style>

{% example %}
<button _="on click
             call alert('OK, Going to put the current date into the output!')
             make a Date then put it into the next <output/>">
  Show An Alert
</button>
<output>--</output>
{% endexample %}
