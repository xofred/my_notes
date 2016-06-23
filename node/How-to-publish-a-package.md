- **Our module**

```javascript
// hello.js
exports.sayHello = function () { 
  return 'Hello, world.';
};
```

- **Initialize `package.json`**

```shell
➜ npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help json` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg> --save` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
name: (hellojs) hello_test_xo
version: (1.0.0) 0.0.1
description: A helloworld package
entry point: (hello.js) ./hello.js
test command:
git repository:
keywords: helloworld
author: xo
license: (ISC) MIT
About to write to /Users/MD212/projects/hellojs/package.json:

{
  "name": "hello_test_xo",
  "version": "0.0.1",
  "description": "A helloworld package",
  "main": "./hello.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [
    "helloworld"
  ],
  "author": "xo",
  "license": "MIT"
}


Is this ok? (yes) yes
```

- **Register a repository**

```shell
➜ npm adduser
Username: fwin3000
Password:
Email: (this IS public) fwin3000@gmail.com
Logged in as fwin3000 on https://registry.npmjs.org/.
```

- **Upload package**

under directory where our `package.json` sits

```shell
➜  npm publish .
+ hello_test_xo@0.0.1
```

That's it, then we can eat our dog food by 

```shell
➜  npm install hello_test_xo
hello_test_xo@0.0.1 node_modules/hello_test_xo
```

- **Ownership**

```shell
➜ npm owner ls hello_test_xo
fwin3000 <fwin3000@gmail.com>
```

```shell
npm owner ls <package name>
npm owner add <user> <package name>
npm owner rm <user> <package name>
```

- **See if requireable**

```shell
➜ npm ls
/Users/MD212/projects
└── hello_test_xo@0.0.1
```
