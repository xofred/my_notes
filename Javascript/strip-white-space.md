Use the replace function in js:
```javascript
var emailAdd = $(this).text().replace(/ /g,'');
```
That will remove all the spaces

If you want to remove the leading and trailing whitespace only, use the jQuery $.trim method :
```javascript
var emailAdd = $.trim($(this).text());
```

Reference: [how do I strip white space when grabbing text with jQuery?](http://stackoverflow.com/questions/360491/how-do-i-strip-white-space-when-grabbing-text-with-jquery)