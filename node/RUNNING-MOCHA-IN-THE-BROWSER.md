```html
<html>
<head>
  <meta charset="utf-8">
  <title>Mocha Tests</title>
  <link href="https://cdn.rawgit.com/mochajs/mocha/2.2.5/mocha.css" rel="stylesheet" />
</head>
<body>
  <div id="mocha"></div>

  <script src="https://cdn.rawgit.com/jquery/jquery/2.1.4/dist/jquery.min.js"></script>
  <script src="https://cdn.rawgit.com/Automattic/expect.js/0.3.1/index.js"></script>
  <script src="https://cdn.rawgit.com/mochajs/mocha/2.2.5/mocha.js"></script>

  <script>mocha.setup('bdd')</script>
  <script src="test.array.js"></script>
  <script src="test.object.js"></script>
  <script src="test.xhr.js"></script>
  <script>
    mocha.checkLeaks();
    mocha.globals(['jQuery']);
    mocha.run();
  </script>
</body>
</html>
```

Reference: [RUNNING MOCHA IN THE BROWSER](http://mochajs.org/#running-mocha-in-the-browser)