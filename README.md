# api documentation for  [path-is-absolute (v1.0.1)](https://github.com/sindresorhus/path-is-absolute#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-path-is-absolute.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-path-is-absolute) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-path-is-absolute.svg)](https://travis-ci.org/npmdoc/node-npmdoc-path-is-absolute)
#### Node.js 0.12 path.isAbsolute() ponyfill

[![NPM](https://nodei.co/npm/path-is-absolute.png?downloads=true)](https://www.npmjs.com/package/path-is-absolute)

[![apidoc](https://npmdoc.github.io/node-npmdoc-path-is-absolute/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-path-is-absolute_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-path-is-absolute/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-path-is-absolute/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-path-is-absolute/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Sindre Sorhus",
        "email": "sindresorhus@gmail.com",
        "url": "sindresorhus.com"
    },
    "bugs": {
        "url": "https://github.com/sindresorhus/path-is-absolute/issues"
    },
    "dependencies": {},
    "description": "Node.js 0.12 path.isAbsolute() ponyfill",
    "devDependencies": {
        "xo": "^0.16.0"
    },
    "directories": {},
    "dist": {
        "shasum": "174b9268735534ffbc7ace6bf53a5a9e1b5c5f5f",
        "tarball": "https://registry.npmjs.org/path-is-absolute/-/path-is-absolute-1.0.1.tgz"
    },
    "engines": {
        "node": ">=0.10.0"
    },
    "files": [
        "index.js"
    ],
    "gitHead": "edc91d348b21dac2ab65ea2fbec2868e2eff5eb6",
    "homepage": "https://github.com/sindresorhus/path-is-absolute#readme",
    "keywords": [
        "path",
        "paths",
        "file",
        "dir",
        "absolute",
        "isabsolute",
        "is-absolute",
        "built-in",
        "util",
        "utils",
        "core",
        "ponyfill",
        "polyfill",
        "shim",
        "is",
        "detect",
        "check"
    ],
    "license": "MIT",
    "maintainers": [
        {
            "name": "sindresorhus",
            "email": "sindresorhus@gmail.com"
        }
    ],
    "name": "path-is-absolute",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/sindresorhus/path-is-absolute.git"
    },
    "scripts": {
        "test": "xo && node test.js"
    },
    "version": "1.0.1"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module path-is-absolute](#apidoc.module.path-is-absolute)
1.  [function <span class="apidocSignatureSpan">path-is-absolute.</span>posix (path)](#apidoc.element.path-is-absolute.posix)
1.  [function <span class="apidocSignatureSpan">path-is-absolute.</span>win32 (path)](#apidoc.element.path-is-absolute.win32)



# <a name="apidoc.module.path-is-absolute"></a>[module path-is-absolute](#apidoc.module.path-is-absolute)

#### <a name="apidoc.element.path-is-absolute.posix"></a>[function <span class="apidocSignatureSpan">path-is-absolute.</span>posix (path)](#apidoc.element.path-is-absolute.posix)
- description and source-code
```javascript
function posix(path) {
	return path.charAt(0) === '/';
}
```
- example usage
```shell
...
// Running on Windows
pathIsAbsolute('C:/Users/foo');
//=> true
pathIsAbsolute('/home/foo');
//=> false

// Running on any OS
pathIsAbsolute.posix('/home/foo');
//=> true
pathIsAbsolute.posix('C:/Users/foo');
//=> false
pathIsAbsolute.win32('C:/Users/foo');
//=> true
pathIsAbsolute.win32('/home/foo');
//=> false
...
```

#### <a name="apidoc.element.path-is-absolute.win32"></a>[function <span class="apidocSignatureSpan">path-is-absolute.</span>win32 (path)](#apidoc.element.path-is-absolute.win32)
- description and source-code
```javascript
function win32(path) {
	// https://github.com/nodejs/node/blob/b3fcc245fb25539909ef1d5eaa01dbf92e168633/lib/path.js#L56
	var splitDeviceRe = /^([a-zA-Z]:|[\\\/]{2}[^\\\/]+[\\\/]+[^\\\/]+)?([\\\/])?([\s\S]*?)$/;
	var result = splitDeviceRe.exec(path);
	var device = result[1] || '';
	var isUnc = Boolean(device && device.charAt(1) !== ':');

	// UNC paths are always absolute
	return Boolean(result[2] || isUnc);
}
```
- example usage
```shell
...
//=> false

// Running on any OS
pathIsAbsolute.posix('/home/foo');
//=> true
pathIsAbsolute.posix('C:/Users/foo');
//=> false
pathIsAbsolute.win32('C:/Users/foo');
//=> true
pathIsAbsolute.win32('/home/foo');
//=> false
'''


## API
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
