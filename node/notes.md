# 深入浅出Node.js读书笔记

## CommonJS's  module strategy

Let's say we have a module called 'math.js'

```javascript
// math.js
exports.add = function () {
  var sum=0, i=0, args = arguments, l = args.length;

  while(i < l) {
    sum += args[i++]; 
  }

  return sum; 
};
```

And we want to use its 'add' function in our main program

```javascript
// program.js
var math = require('math');

exports.increment = function (val) {
  return math.add(val, 1);
};
```

## Node's  module strategy

### always load from cache first

### path analyzing and file locating

#### analyzing

- core modules, such as 'http'、'fs'、'path' (fastest)
- relative directories start with '.' or '..' (fast)
- absolute directories start with '/' (fast)
- connect modules which are not provided as path (slow)

#### locating

##### extension

Since Node wiil try in this follow order: **.js、.json、.node**. 

So if we have module like .node or .json, we should specify it in require()'s path

##### package

Node will try locating path of **main** property under **package.json**

## package and NPM

### package(.zip or tar.gz)

A unzipped package should include:

- **package.json** package description
- **bin/** executable binaries
- **lib/** js source codes
- **doc/** documents
- **test/** unit test codes

### NPM frequent usage

#### dependencies install

For example, when run `npm install express`, will create node_modules/ under current directory, then create express/ under node_modules/, then unzip the package in express/

Then inn our code, `require('express');` 

##### 'global install'

`npm install express –g` 

---
Reference: 《深入浅出Node.js》朴灵