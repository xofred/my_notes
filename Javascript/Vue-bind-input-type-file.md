**HTML**
```html
<!DOCTYPE html>
<html>
<head>
<script src="http://code.jquery.com/jquery-2.1.0.min.js"></script>
  <meta charset="utf-8">
  <title>JS Bin</title>
  <script src="http://rawgit.com/yyx990803/vue/master/dist/vue.js"></script>
</head>
<body>
  <div id="demo">
    <p><input type="text" v-model="text"> text:{{text}}</p>
    <p><input type="file" v-model="file"> file:{{file}}</p>
  </div>
</body>
</html>
```

**Javascript**
```javascript
var vue = new Vue({
    el: '#demo',
  
    // default values
    data: {
      text: '',
      file: ''
    },
    
    ready: function() {
      // watch for file input on bootstrap
      this.watchFileInput();
    },
  
    methods: {
      watchFileInput: function() {
        // will notify a file input
        $('input[type="file"]').change(this.notifyFileInput.bind(this));
      },
      
      notifyFileInput: function(event) {
        var fileName = event.target.files[0].name;
        // update file name value
        this.file = fileName;
      }
    }
});
```

Reference: [v-model doesn't support input type="file"](https://github.com/vuejs/Discussion/issues/24)