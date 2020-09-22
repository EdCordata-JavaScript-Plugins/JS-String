# js-string


### What is `js-string`?
I, personally, got very annoyed in having to write very
ugly code for merging string with variables, be it html,
logs or just strings with repeating variables.

Surely, other people, seen this and though, why is it
so ugly and there must be a better way:
```javascript
console.log('x: ' + x + '; y: ' + y);
// or
var html = '<li class="article" data-id="{' + id + '}"><a href="{' + url + '}">{' + name + '}</a><li>'
```
NO ONE WANTS THIS.!!!


### How `js-string` solves this?

```javascript
S('<li class="article" data-id="{id}"><a href="{url}">{name}</a><li>', {
  id:   1,
  name: 'ipsum',
  url:  'http://example.com/article'
});
```

You can also pass array or single variable, instead of hash,
which will result in function searching `{x}` inside the string.

Examples:

```javascript
S('{x}_{y}',     {x: 1, y: 2});     // => '1_2'
S('{x}_{y}_{x}', {x: 1, y: 2});     // => '1_2_1'
S('{x}_{x}_{x}', 1);                // => '1_1_1'
S('{x}_{x}_{x}', 'a');              // => 'a_a_a'
S('{x}_{x}_{x}', [1, 2, 'c']);      // => '1_2_c'
S('{x}_{x}_{x}', [1, 2]);           // => '1_2_2'
S('{x}_{x}_{x}', [1, 2, 'c', 'd']); // => '1_2_c'

S('{x}_{x}_{x}');                   // => '{x}_{x}_{x}'
S('{x}_{x}_{x}', null);             // => '{x}_{x}_{x}'
S('{x}_{x}_{x}', undefined);        // => '{x}_{x}_{x}'
```
