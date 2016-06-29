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

## Buffer type convention

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