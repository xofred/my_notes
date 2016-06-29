Javascript is easy to manipulate string, char length always consider as 1
```javascript
console.log("0123456789".length); // 10 
console.log("感觉还没到服务就跪了".length); //10 
console.log("\u00bd".length); // 1
```
But in Node, we have so many other things -- net protocol, db manipulation, pic process, recv upload file, and binary data in net/file stream -- which are not suitable for string. That's why we need Buffer object.

## Buffer object

The Buffer el is between 0 and 255.
```javascript
var str = "深入浅出node.js";
var buf = new Buffer(str, 'utf-8');
console.log(buf); // <Buffer e6 b7 b1 e5 85 a5 e6 b5 85 e5 87 ba 6e 6f 64 65 2e 6a 73>
```

Like Array, we can get its length and el.
```javascript
var buf = new Buffer(100); 
console.log(buf.length); // => 100
console.log(buf[10]); // some random int between 0 and 255
```

And set el's value.
```javascript
buf[10] = 100; 
console.log(buf[10]); // => 100

buf[20] = -100; 
console.log(buf[20]); // 156 

buf[21] = 300; 
console.log(buf[21]); // 44 

buf[22] = 3.1415; 
console.log(buf[22]); // 3
```

## Type convention

  - ASCII
  - UTF-8
  - UTF-16LE/UCS-2
  - Base64
  - Binary
  - Hex

### String to Buffer

Through new Buffer, 1 encoding only:
```javascript
new Buffer(str, [encoding]); // [encoding] default is UTF-8
```

Or through write() method:
```javascript
// can write several times with different encoding
buf.write(string, [offset], [length], [encoding])
```

### Buffer to String
```javascript
// if buf is written by different encoding, it should be converted at exact point by exact encoding
buf.toString([encoding], [start], [end]) // also [encoding] default is UTF-8
```

### Unsupported encoding
```javascript
Buffer.isEncoding(encoding) // true or false
``` 

But! We can use third-party library such as: 

[iconv-lite](https://www.npmjs.com/package/iconv-lite)
```javascript
var iconv = require('iconv-lite');
// Buffer to String 
var str = iconv.decode(buf, 'win1251');
// String to Buffer
var buf = iconv.encode("Sample input string", 'win1251');
```

or [iconv](https://www.npmjs.com/package/iconv)
```javascript
var iconv = new Iconv('UTF-8', 'ASCII'); 
iconv.convert('ça va'); // throws EILSEQ

var iconv = new Iconv('UTF-8', 'ASCII//IGNORE'); 
iconv.convert('ça va'); // returns "a va"

var iconv = new Iconv('UTF-8', 'ASCII//TRANSLIT'); 
iconv.convert('ça va'); // "ca va"

var iconv = new Iconv('UTF-8', 'ASCII//TRANSLIT//IGNORE'); 
iconv.convert('ça va  '); // "ca va "
```

## Unicode chars in Buffer concat
```shell
cat test.md
床前明月光，疑是地上霜，举头望明月，低头思故乡。
```

```javascript
var data, fs, rs;

data = '';
fs = require('fs');
rs = fs.createReadStream('test.md');

rs.on("data", function (chunk){
  data += chunk; 
});

rs.on("end", function () { 
  console.log(data);
});
```

```shell
node luanma.js
床前明月光，疑是地上霜，举头望明月，低头思故乡。
```