### letter or number only

To match anything other than letter or number you could try this:
```javascript
[^a-zA-Z0-9]
```
And to replace:
```javascript
var str = 'dfj,dsf7lfsd .sdklfj';
str = str.replace(/[^A-Za-z0-9]/g, ' ');
```

### letter, number, or underscore

This regular expression match not letters, digits, and underscores chars.

```javascript
\W
```
For example in javascript:

```javascript
"(,,@,£,() asdf 345345".replace(/\W/g, ' ');
```

Reference: [Regular Expression: Any character that is NOT a letter or number](http://stackoverflow.com/questions/2991901/regular-expression-any-character-that-is-not-a-letter-or-number)

