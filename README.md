# Shadow Styles

[![Build Status](https://travis-ci.org/numtel/shadowstyles.svg?branch=master)](https://travis-ci.org/numtel/shadowstyles)

WebComponents bring Shadow DOM with isolated CSS to some browsers.
This script simulates CSS isolation for all modern browsers (IE9+, Firefox...).

## Installation
...

## How it works

1. Search for child DOM of elements to isolate.
2. Find which rules apply to those elements and add a `:not(buffer-attr*="uniqueId")`
    pseudo-class with a unique ID to each rule. Shadowed elements gain the buffer
    attribute containing the unique ID of each negated rule.

### Targeting simulated shadows

Shadowed elements are given a `shadow` attribute that must be present in the
selector:

```css
shadowed-element[shadow] p { color: blue; }
```

### Why not `::shadow`?

Originally, the plan of this project was to support styles using the native
`::shadow` pseudo-class syntax. Until the fifteenth commit, this worked, but
only if all the page's stylesheets were rewritten completely. By only
using selectors that the browser already supports, the script can skip parsing
all of your CSS itself and rely on the browser's interpretation, only making
small changes as needed.

## Todo

* observe ancestors (skip siblings) for rule match changes
