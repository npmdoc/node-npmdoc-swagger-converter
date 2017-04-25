# npmdoc-swagger-converter

#### basic api documentation for  [swagger-converter (v1.4.1)](https://github.com/apigee-127/swagger-converter)  [![npm package](https://img.shields.io/npm/v/npmdoc-swagger-converter.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-swagger-converter) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-swagger-converter.svg)](https://travis-ci.org/npmdoc/node-npmdoc-swagger-converter)

#### Converts Swagger documents from version 1.x to version 2.0

[![NPM](https://nodei.co/npm/swagger-converter.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/swagger-converter)

- [https://npmdoc.github.io/node-npmdoc-swagger-converter/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-swagger-converter/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-swagger-converter/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-swagger-converter/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-swagger-converter/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-swagger-converter/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Mohsen Azimi"
    },
    "bugs": {
        "url": "https://github.com/apigee-127/swagger-converter/issues"
    },
    "dependencies": {
        "common-prefix": "^1.1.0",
        "urijs": "^1.16.1"
    },
    "description": "Converts Swagger documents from version 1.x to version 2.0",
    "devDependencies": {
        "browserify": "^13.0.0",
        "chai": "^3.4.1",
        "coveralls": "^2.11.4",
        "deep-sort-object": "^1.0.1",
        "istanbul": "^0.4.0",
        "jscs": "^2.5.1",
        "mocha": "^2.3.3",
        "mocha-jscs": "^4.0.0",
        "mocha-jshint": "^2.2.5",
        "seamless-immutable": "^5.0.1",
        "sway": "^0.6.0",
        "uglify-js": "^2.6.0"
    },
    "directories": {},
    "dist": {
        "shasum": "796e430c30ba90f3ce73553d114f205856c31fca",
        "tarball": "https://registry.npmjs.org/swagger-converter/-/swagger-converter-1.4.1.tgz"
    },
    "gitHead": "007de4d9244e21f51832fa3b7ae9b2148b06034f",
    "homepage": "https://github.com/apigee-127/swagger-converter",
    "keywords": [
        "Swagger",
        "converter",
        "API"
    ],
    "license": "MIT",
    "main": "index.js",
    "maintainers": [
        {
            "name": "swagger"
        },
        {
            "name": "mohsen"
        }
    ],
    "name": "swagger-converter",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git+https://github.com/apigee-127/swagger-converter.git"
    },
    "scripts": {
        "browserify": "browserify index.js -s SwaggerConverter --outfile browser.js",
        "build": "npm run uglify",
        "coveralls": "cat ./coverage/lcov.info | coveralls",
        "istanbul": "istanbul cover --report lcovonly _mocha",
        "prepublish": "npm run build",
        "pretest": "npm run build",
        "preuglify": "npm run browserify",
        "test": "mocha",
        "uglify": "uglifyjs browser.js > browser.min.js"
    },
    "version": "1.4.1",
    "bin": {}
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
