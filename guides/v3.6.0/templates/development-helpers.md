## Development Helpers

Handlebars and Ember come with a few helpers that can make developing your
templates a bit easier. These helpers make it simple to output variables into
your browser's console, or activate the debugger from your templates.

### Logging

The [`{{log}}`](https://api.emberjs.com/ember/3.6/classes/Ember.Templates.helpers/methods/if?anchor=log) helper makes it easy to output variables or expressions in
 the
current rendering context into your browser's console:

```handlebars
{{log 'Name is:' this.name}}
```

The `{{log}}` helper also accepts primitive types such as strings or numbers.

### Adding a breakpoint

The [``{{debugger}}``](https://api.emberjs.com/ember/3.6/classes/Ember.Templates.helpers/methods/if?anchor=debugger) helper provides a handlebars equivalent to JavaScript's
`debugger` keyword.  It will halt execution inside the debugger helper and give
you the ability to inspect the current rendering context:


```handlebars
{{debugger}}
```

When using the debugger helper you will have access to a `get` function. This
function retrieves values available in the context of the template.
For example, if you're wondering why a value `{{foo}}` isn't rendering as
expected within a template, you could place a `{{debugger}}` statement and,
when the `debugger;` breakpoint is hit, you can attempt to retrieve this value:

```javascript
> get('foo')
```

`get` is also aware of keywords. So in this situation:

```handlebars
{{#each this.items as |item|}}
  {{debugger}}
{{/each}}
```

You'll be able to get values from the current item:

```javascript
> get('this.item.name')
```

You can also access the context of the view to make sure it is the object that
you expect:

```javascript
> context
```
