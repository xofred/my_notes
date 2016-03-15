```javascript
ownerIndex = $('th:contains("Owner")').index() + 1;
$('table tr td:nth-child('+ownerIndex+')');
```

Reference: [JQuery select table column](http://stackoverflow.com/questions/8375625/jquery-select-table-column)