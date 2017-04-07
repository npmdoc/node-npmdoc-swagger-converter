# api documentation for  [swagger-converter (v1.4.1)](https://github.com/apigee-127/swagger-converter)  [![npm package](https://img.shields.io/npm/v/npmdoc-swagger-converter.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-swagger-converter) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-swagger-converter.svg)](https://travis-ci.org/npmdoc/node-npmdoc-swagger-converter)
#### Converts Swagger documents from version 1.x to version 2.0

[![NPM](https://nodei.co/npm/swagger-converter.png?downloads=true)](https://www.npmjs.com/package/swagger-converter)

[![apidoc](https://npmdoc.github.io/node-npmdoc-swagger-converter/build/screenCapture.buildNpmdoc.browser.%2Fhome%2Ftravis%2Fbuild%2Fnpmdoc%2Fnode-npmdoc-swagger-converter%2Ftmp%2Fbuild%2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-swagger-converter/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-swagger-converter/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-swagger-converter/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Mohsen Azimi",
        "email": "me@azimi.me"
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
            "name": "swagger",
            "email": "mazimi+swagger@apigee.com"
        },
        {
            "name": "mohsen",
            "email": "me@azimi.me"
        }
    ],
    "name": "swagger-converter",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
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
    "version": "1.4.1"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module swagger-converter](#apidoc.module.swagger-converter)
1.  [function <span class="apidocSignatureSpan">swagger-converter.</span>convert (resourceListing, apiDeclarations, options)](#apidoc.element.swagger-converter.convert)
1.  [function <span class="apidocSignatureSpan">swagger-converter.</span>listApiDeclarations (sourceUrl, resourceListing)](#apidoc.element.swagger-converter.listApiDeclarations)
1.  object <span class="apidocSignatureSpan">swagger-converter.</span>browser

#### [module swagger-converter.browser](#apidoc.module.swagger-converter.browser)
1.  [function <span class="apidocSignatureSpan">swagger-converter.browser.</span>convert (resourceListing, apiDeclarations, options)](#apidoc.element.swagger-converter.browser.convert)
1.  [function <span class="apidocSignatureSpan">swagger-converter.browser.</span>listApiDeclarations (sourceUrl, resourceListing)](#apidoc.element.swagger-converter.browser.listApiDeclarations)



# <a name="apidoc.module.swagger-converter"></a>[module swagger-converter](#apidoc.module.swagger-converter)

#### <a name="apidoc.element.swagger-converter.convert"></a>[function <span class="apidocSignatureSpan">swagger-converter.</span>convert (resourceListing, apiDeclarations, options)](#apidoc.element.swagger-converter.convert)
- description and source-code
```javascript
convert = function (resourceListing, apiDeclarations, options) {
  if (Array.isArray(apiDeclarations)) {
    throw new SwaggerConverterError(
      'Second argument(apiDeclarations) should be plain object, ' +
      'see release notes.');
  }

  var converter = new Converter();
  converter.options = options || {};
  return converter.convert(resourceListing, apiDeclarations);
}
```
- example usage
```shell
...

var apiDeclarations = {
  '/pet': require('/path/to/petstore/pet.json'),
  '/user': require('/path/to/petstore/user.json'),
  '/store': require('/path/to/petstore/store.json')
};

var swagger2Document = swaggerConverter.convert(resourceListing, apiDeclarations);

console.log(JSON.stringify(swagger2Document, null, 2));
'''

##### listApiDeclarations function
'listApiDeclarations' function accept following arguments:
...
```

#### <a name="apidoc.element.swagger-converter.listApiDeclarations"></a>[function <span class="apidocSignatureSpan">swagger-converter.</span>listApiDeclarations (sourceUrl, resourceListing)](#apidoc.element.swagger-converter.listApiDeclarations)
- description and source-code
```javascript
listApiDeclarations = function (sourceUrl, resourceListing) {
<span class="apidocCodeCommentSpan">  /*
   * Warning: This code is intended to cover us much as possible real-life
   * cases and was tested using hundreds of public Swagger documents. If you
   * change code please do not introduce any breaking changes.
   * Possible workaround: you can alter algorithm by add/change 'basePath'
   * before passing it into this function.
  */
</span>  sourceUrl = URI(sourceUrl || '').query('');

  var baseUrl = URI(resourceListing.basePath || '');
  if (baseUrl.is('relative')) {
    baseUrl = baseUrl.absoluteTo(sourceUrl);
  }

  if (resourceListing.swaggerVersion === '1.0' && baseUrl.suffix() === 'json') {
    baseUrl.filename('');
  }

  var result = {};
  resourceListing.apis.forEach(function(api) {
    // skip embedded documents
    if (!isValue(api.path) || isValue(api.operations)) {
      return;
    }

    var resourceUrl = URI(api.path.replace('{format}', 'json'));
    if (resourceUrl.is('relative')) {
      resourceUrl = URI(baseUrl.href() + resourceUrl.href());
    }
    result[api.path] = resourceUrl.normalize().href();
  });

  return result;
}
```
- example usage
```shell
...
* 'resourceListing'(required) - root Swagger 1.x document

'''javascript
var swaggerConverter = require('swagger-converter');

var resourceListing = require('/path/to/petstore/index.json');

var apiDeclarations = swaggerConverter.listApiDeclarations('http://test.com/api-docs', resourceListing);

console.log(JSON.stringify(apiDeclarations, null, 2));
/*
{
"/pet": "http://test.com/api-docs/pet",
"/user": "http://test.com/api-docs/user",
"/store": "http://test.com/api-docs/store"
...
```



# <a name="apidoc.module.swagger-converter.browser"></a>[module swagger-converter.browser](#apidoc.module.swagger-converter.browser)

#### <a name="apidoc.element.swagger-converter.browser.convert"></a>[function <span class="apidocSignatureSpan">swagger-converter.browser.</span>convert (resourceListing, apiDeclarations, options)](#apidoc.element.swagger-converter.browser.convert)
- description and source-code
```javascript
convert = function (resourceListing, apiDeclarations, options) {
  if (Array.isArray(apiDeclarations)) {
    throw new SwaggerConverterError(
      'Second argument(apiDeclarations) should be plain object, ' +
      'see release notes.');
  }

  var converter = new Converter();
  converter.options = options || {};
  return converter.convert(resourceListing, apiDeclarations);
}
```
- example usage
```shell
...

var apiDeclarations = {
  '/pet': require('/path/to/petstore/pet.json'),
  '/user': require('/path/to/petstore/user.json'),
  '/store': require('/path/to/petstore/store.json')
};

var swagger2Document = swaggerConverter.convert(resourceListing, apiDeclarations);

console.log(JSON.stringify(swagger2Document, null, 2));
'''

##### listApiDeclarations function
'listApiDeclarations' function accept following arguments:
...
```

#### <a name="apidoc.element.swagger-converter.browser.listApiDeclarations"></a>[function <span class="apidocSignatureSpan">swagger-converter.browser.</span>listApiDeclarations (sourceUrl, resourceListing)](#apidoc.element.swagger-converter.browser.listApiDeclarations)
- description and source-code
```javascript
listApiDeclarations = function (sourceUrl, resourceListing) {
<span class="apidocCodeCommentSpan">  /*
   * Warning: This code is intended to cover us much as possible real-life
   * cases and was tested using hundreds of public Swagger documents. If you
   * change code please do not introduce any breaking changes.
   * Possible workaround: you can alter algorithm by add/change 'basePath'
   * before passing it into this function.
  */
</span>  sourceUrl = URI(sourceUrl || '').query('');

  var baseUrl = URI(resourceListing.basePath || '');
  if (baseUrl.is('relative')) {
    baseUrl = baseUrl.absoluteTo(sourceUrl);
  }

  if (resourceListing.swaggerVersion === '1.0' && baseUrl.suffix() === 'json') {
    baseUrl.filename('');
  }

  var result = {};
  resourceListing.apis.forEach(function(api) {
    // skip embedded documents
    if (!isValue(api.path) || isValue(api.operations)) {
      return;
    }

    var resourceUrl = URI(api.path.replace('{format}', 'json'));
    if (resourceUrl.is('relative')) {
      resourceUrl = URI(baseUrl.href() + resourceUrl.href());
    }
    result[api.path] = resourceUrl.normalize().href();
  });

  return result;
}
```
- example usage
```shell
...
* 'resourceListing'(required) - root Swagger 1.x document

'''javascript
var swaggerConverter = require('swagger-converter');

var resourceListing = require('/path/to/petstore/index.json');

var apiDeclarations = swaggerConverter.listApiDeclarations('http://test.com/api-docs', resourceListing);

console.log(JSON.stringify(apiDeclarations, null, 2));
/*
{
"/pet": "http://test.com/api-docs/pet",
"/user": "http://test.com/api-docs/user",
"/store": "http://test.com/api-docs/store"
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
