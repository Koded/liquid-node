# LiquidNode Change History

## 0.2.0

### NEW: Engine

In Liquid (Ruby) you register tags and additional filters at the Template class.
So your project only has a single possible configuration.

```diff
+ var engine = new Liquid.Engine;
- Liquid.Template.registerTag(...);
+ engine.registerTag(...);
- var output = Liquid.Template.parse(templateString).renderOrRaise({ foo: 42 });
+ var output = engine.parse(templateString).render({ foo: 42 });
```

Also note that `renderOrRaise` has been removed, since `render` has been returning a promise for some time.

### CHANGE: Tag Constructors

The signature of Tag-constructors changed to match `render()` signature where the
"context" is passed first.

```diff
- function(tagName, markup, tokens, template) { ... }
+ function(template, tagName, markup, tokens) { ... }
```

### 0.1.5

Restores compatibility with 0.1.2 after 0.1.4 introduced the engine
which was supposted to be release in a major (or at least minor) release.

- FIXED: `blank` and `empty` had odd behaviour on non-arrays
- FIXED: `[false, true] includes false` returned false
- FIXED: LiquidErrors had odd behaviour when used in `instanceof` (thanks @dotnil)
- IMPROVEMENT: Replaced `q.catch` and `q.fail` calls (they are deprecated).
- IMPROVEMENT: context.variable() is now wrapped in `Q.fcall`
- IMPROVEMENT: throw exception when somebody tries to use ranges (not implemented yet)
- IMPROVEMENT: Conditions `a < b` where a and b are async are now parallelized
- ADDITION: New operators `is` and `isnt`

### 0.1.4

(deprecated)

### 0.1.3

(deprecated)

### 0.1.2

Pseudo Public Release

### 0.1.1 and earlier

(internal development)
