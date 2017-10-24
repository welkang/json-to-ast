# JSON AST parser

[npm-icon]:           https://img.shields.io/npm/v/json-to-ast.svg
[npm-downloads-icon]: https://img.shields.io/npm/dm/json-to-ast.svg
[npm-url]:            https://www.npmjs.com/package/json-to-ast

[node-versions-icon]: https://img.shields.io/node/v/json-to-ast.svg
[node-url]:           https://nodejs.org

[test-icon]:          https://travis-ci.org/vtrushin/json-to-ast.svg?branch=master
[test-url]:           https://travis-ci.org/vtrushin/json-to-ast

[coverage-icon]:      https://coveralls.io/repos/github/vtrushin/json-to-ast/badge.svg?branch=master
[coverage-url]:       https://coveralls.io/github/vtrushin/json-to-ast?branch=master

[![NPM][npm-icon]][npm-url]
[![NPM downloads][npm-downloads-icon]][npm-url]
[![Requirements][node-versions-icon]][node-url]
[![Travis-CI][test-icon]][test-url]

## Install
```
> npm install json-to-ast
```

## Usage

```js
const parse = require('json-to-ast');

const settings = {
  loc: true, // Appends location information. Default is <true>
  source: 'data.json' // Appends source information to node’s location. Default is <null>
};

parse('{"a": 1}', settings);
```

Output
```js
{
  type: 'Object',
  children: [
    {
      type: 'Property',
      key: {
        type: 'Identifier',
        value: 'a',
        raw: '"a"',
        loc: {
          start: { line: 1, column: 2, offset: 1 },
          end: { line: 1, column: 5, offset: 4 },
          source: 'data.json'
        }
      },
      value: {
        type: 'Literal',
        value: 1,
        raw: '1',
        loc: {
          start: { line: 1, column: 7, offset: 6 },
          end: { line: 1, column: 8, offset: 7 },
          source: 'data.json'
        }
      },
      loc: {
        start: { line: 1, column: 2, offset: 1 },
        end: { line: 1, column: 8, offset: 7 },
        source: 'data.json'
      }
    }
  ],
  loc: {
    start: { line: 1, column: 1, offset: 0 },
    end: { line: 1, column: 9, offset: 8 },
    source: 'data.json'
  }
}
```

## Node types

Object:
```js
{
  type: 'Object',
  children: <Property[]>,
  loc: Object | null
}
```

Property:
```js
{
  type: 'Property',
  key: <Identifier>,
  value: any,
  loc: Object | null
}
```

Identifier:
```js
{
  type: 'Identifier',
  value: String,
  raw: String,
  loc: Object | null
}
```

Array:
```js
{
  type: 'Array',
  children: <any[]>,
  loc: Object | null
}
```

Literal:
```js
{
  type: 'Literal',
  value: String | Number | Boolean | null,
  raw: String,
  loc: Object | null
}
```

## AST explorer
[Try it online](https://astexplorer.net/#/gist/6e328cf76a27ca85e552c9cb583cdd74/1077c8842337972509a29bc9063d17bf90a1a492) on [astexplorer.net](https://astexplorer.net/)

## License
MIT
