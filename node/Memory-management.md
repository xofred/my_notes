## closure

```javascript
var foo = function () { 
  var local = "i m a local outside"; 
  (function () {
    console.log(local); // inner can access outer vars
  }());
};
```

```javascript
var foo = function () { 
  (function () {
    var local = "i m local inside"; 
  }());
  console.log(local); // but outer can't access inner vars
};
```

```javascript
var foo = function () { 
  var bar = function () {
    var local = "i m a local inside"; 
    return function () {
      return local; 
    };
  };
  var baz = bar(); 
  console.log(baz()); // inner local is accessible again cuz it's return by a function
};
```

And the technique we used in the last example is called **closure**, which allows us to access inner locals from outer.

In nomal javascript, this closure kind vars and global vars are not gonna be released soon. If there are too many of them,   the memory could be run out due to V8 memory restriction.

## heap memory
```javascript
var showMem = function () {
  var mem = process.memoryUsage(); 
  var format = function (bytes) {
    return (bytes / 1024 / 1024).toFixed(2) + ' MB'; 
  };
  console.log('Process: heapTotal ' + format(mem.heapTotal) +
              ' heapUsed ' + format(mem.heapUsed) + ' rss ' + format(mem.rss));
  console.log('-----------------------------------------------------------');
};

var useMem = function () { 
  var size = 20 * 1024 * 1024; 
  var arr = new Array(size); 
  for (var i = 0; i < size; i++) {
    arr[i] = 0;
  }
  return arr; 
};

var total = [];
for (var j = 0; j < 15; j++) { 
  showMem();
  total.push(useMem());
} 

showMem();
```

```shell
node outOfMemory.js
Process: heapTotal 9.30 MB heapUsed 3.19 MB rss 17.84 MB
-----------------------------------------------------------
Process: heapTotal 169.32 MB heapUsed 163.84 MB rss 178.46 MB
-----------------------------------------------------------
Process: heapTotal 330.32 MB heapUsed 323.27 MB rss 339.32 MB
-----------------------------------------------------------
Process: heapTotal 490.34 MB heapUsed 483.29 MB rss 499.35 MB
-----------------------------------------------------------
Process: heapTotal 650.36 MB heapUsed 643.29 MB rss 659.37 MB
-----------------------------------------------------------
Process: heapTotal 810.38 MB heapUsed 803.29 MB rss 819.39 MB
-----------------------------------------------------------
Process: heapTotal 970.40 MB heapUsed 963.30 MB rss 979.41 MB
-----------------------------------------------------------
Process: heapTotal 1130.42 MB heapUsed 1123.32 MB rss 1139.43 MB
-----------------------------------------------------------
Process: heapTotal 1290.44 MB heapUsed 1283.32 MB rss 1299.68 MB
-----------------------------------------------------------
FATAL ERROR: CALL_AND_RETRY_LAST Allocation failed - process out of memory
[1]    74327 abort      node outOfMemory.js
```

As we can see, heap memory was run out before the for loop finish.

## memory outside heap

```javascript
// almost same code, except put it in Buffer and set a bigger size
var useMem = function () { 
  var size = 200 * 1024 * 1024; 
  var arr = new Buffer(size); 
  for (var i = 0; i < size; i++) {
    arr[i] = 0;
  }
  return arr; 
};
```

```shell
node outOfHeap.js
Process: heapTotal 9.30 MB heapUsed 3.18 MB rss 17.64 MB
-----------------------------------------------------------
Process: heapTotal 10.28 MB heapUsed 3.28 MB rss 219.05 MB
-----------------------------------------------------------
Process: heapTotal 10.28 MB heapUsed 3.25 MB rss 419.20 MB
-----------------------------------------------------------
Process: heapTotal 10.28 MB heapUsed 3.25 MB rss 619.20 MB
-----------------------------------------------------------
Process: heapTotal 10.28 MB heapUsed 3.01 MB rss 819.20 MB
-----------------------------------------------------------
Process: heapTotal 10.28 MB heapUsed 2.94 MB rss 1019.20 MB
-----------------------------------------------------------
Process: heapTotal 10.28 MB heapUsed 2.93 MB rss 1219.14 MB
-----------------------------------------------------------
Process: heapTotal 10.28 MB heapUsed 2.93 MB rss 1419.14 MB
-----------------------------------------------------------
Process: heapTotal 10.28 MB heapUsed 2.93 MB rss 1619.14 MB
-----------------------------------------------------------
Process: heapTotal 10.28 MB heapUsed 2.94 MB rss 1819.14 MB
-----------------------------------------------------------
Process: heapTotal 10.28 MB heapUsed 2.94 MB rss 1998.01 MB
-----------------------------------------------------------
Process: heapTotal 10.28 MB heapUsed 2.94 MB rss 2007.94 MB
-----------------------------------------------------------
Process: heapTotal 10.28 MB heapUsed 2.94 MB rss 2107.17 MB
-----------------------------------------------------------
Process: heapTotal 10.28 MB heapUsed 2.94 MB rss 2111.38 MB
-----------------------------------------------------------
Process: heapTotal 10.28 MB heapUsed 2.94 MB rss 2111.40 MB
-----------------------------------------------------------
Process: heapTotal 10.28 MB heapUsed 2.94 MB rss 2116.29 MB
-----------------------------------------------------------
```

This time, no memory leak, for loop successfully finished.

## memory leak

Reasons:
  - cache
  - too many jobs waiting in the queue, which cannot be consumed in time
  - vars inside scope(maybe closure or global?)

### cache

Caches should always have expired time, they can't sit in the memory forever. So, if we want to use memory as cache directly, we should have sth like:
- size restriction: [limitablemap](https://www.npmjs.com/package/limitablemap)

or

- advanced restriction, higher performance: [LRU by Isaac Z. Schlueter](https://github.com/isaacs/node-lru-cache)

Or, a better option could be use cache outside our thread. Such as [Redis](https://github.com/NodeRedis/node_redis) or [Memcached](https://github.com/3rd-Eden/memcached).

### investigate leaking

[node-heapdump](https://www.npmjs.com/package/heapdump) or [node-memwatch](https://www.npmjs.com/package/memwatch) should help us find out.

## big file

```javascript
var reader, writer;

reader = fs.createReadStream('in.txt');

writer = fs.createWriteStream('out.txt');

reader.on('data', function(chunk) {
  writer.write(chunk);
});

reader.on('end', function() {
  writer.end();
});
```

or

```javascript
var reader = fs.createReadStream('in.txt'); 
var writer = fs.createWriteStream('out.txt'); 
reader.pipe(writer);
```