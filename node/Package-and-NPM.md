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

### Priority

**Always load from cache first, then:**

- core modules, such as 'http'、'fs'、'path' (fastest)
- relative directories start with '.' or '..' (fast)
- absolute directories start with '/' (fast)
- connect modules which are not provided as path (slow)

### extension

Since Node wiil try in this follow order: **.js、.json、.node**. 

So if we have module like .node or .json, we should specify it in require()'s path

### package

Node will try locating path of **main** property under **package.json**

## package and NPM

### package(.zip or tar.gz)

A unzipped package should include:

- **package.json** package description
- **bin/** executable binaries
- **lib/** js source codes
- **doc/** documents
- **test/** unit test codes

### NPM

#### dependencies install

For example, when run `npm install express`, will create node_modules/ under current directory, then create express/ under node_modules/, then unzip the package in express/

Then inn our code, `require('express');` 

##### 'global install'

`npm install express –g` 

It doesn't mean we can require it from anywhere, it just link it based on package.json:

```json
"bin": {
  "express": "./bin/express"
},
```

Let's say our Node in `/usr/local/bin/node`, so it will be linked under `/usr/local/lib/node_ modules`

##### local install

We have serval options:

```shell
npm install <tarball file>
npm install <tarball url>
npm install <folder>
```

##### install from unofficial source

```shell
npm install underscore --registry=http://registry.url
```

Or we can use it always:

```shell
npm config set registry http://registry.url
```
---
Reference: 《深入浅出Node.js》朴灵