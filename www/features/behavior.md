
## The `behavior` feature

### Syntax

```ebnf
behavior <name>(<parameter list>)
  {<hyperscript>}
end
```

```ebnf
install <name>(<named argument list>)
```

### Description

Behaviors allow you to bundle together some hyperscript code (that would normally go in the \_ attribute of an element) so that it can be "installed" on any other.

For instance, consider this disappearing div:

```html
<div
  _="
  on click remove me
"
>
  Click to get rid of me
</div>
```

This revolutionary UI technology impresses the client, and they come to you with a list of other components that they would like to be Removable™. Do you copy this code to each of those elements? That would work, but is not ideal, since

- This code is highly experimental, you'd like to be able to change it in just one place.
- Your boss is considering licensing the Removable™ tech to other companies.

To remedy this, you can define a _behavior_:

<!-- I've never actually had a job, so I'm just imitating stories from tech
     talks. This is what the industry is like, right? -->

```html
<script type="text/hyperscript">
  behavior Removable
    on click
      remove me
    end
  end
</script>
```

and then later in the document install it in your elements:

```html
<div _="install Removable">Click to get rid of me</div>
```

So far, so good! Until you come across this:

```html
<div class="banner">
  <button id="close-banner"></button>
  Click the button to close me
</div>
```

How do we implement this? We could create a new behavior, but we'd have to duplicate our highly sophisticated logic. Thankfully, behaviors can accept arguments:

```html
<script type="text/hyperscript">
  behavior Removable(removeButton)
    on click from removeButton
      remove me
    end
  end
</script>
```

```html
<div class="banner" _="install Removable(removeButton: #close-banner)">...</div>
```

This works well, but now our original div is broken. We can use an [`init` block](/features/init/) to set a default value for the parameter:

```html
<script type="text/hyperscript">
  behavior Removable(removeButton)
    init
      if no removeButton set the removeButton to me
    end

    on click from removeButton
      remove me
    end
  end
</script>
```

Success! Now let us make the behavior reusable across a project:

We will make a file called "behaviors.\_hs" where we can put the behavior.

```hyperscript
# behaviors.\_hs
behavior Removable(removeButton)
  init
    if no removeButton set the removeButton to me
  end

  on click from removeButton
    remove me
  end
end
```

We need to place the script import *before* we install the script. Let's exchange our behavior script with an import now:

```html
<script type="text/hyperscript"src="behaviors._hs"></script>
```

Now our Removable™ innovation is reusable!

For a more realistic example of a behavior, check out the Draggable behavior which creates a draggable window: [Draggable.\_hs](https://gist.github.com/dz4k/6505fb82ae7fdb0a03e6f3e360931aa9)
