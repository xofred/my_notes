**Javascript**
```javascript
fetchData: function () {
    var self = this; // $vm
    $.get( apiURL + self.currentBranch, function( data ) {
        self.commits = data; // $vm.data["commits"]
    });
}
```

Reference: 

- [Fetching / persisting data using vue.js](https://laracasts.com/discuss/channels/vue/fetching-persisting-data-using-vuejs)

- [GitHub Commits Example](http://vuejs.org/examples/commits.html)

