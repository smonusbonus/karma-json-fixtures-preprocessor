karma-json-fixtures-preprocessor
================================

##### Preprocessor for converting .json files into .js files and making them accessible from karma test environment

## Installation
```json
{
    "devDependencies": {
        "karma": "~0.12.1",
        "karma-json-fixtures-preprocessor": "0.0.0"
    }
}
```

## Configuration
```js
// karma.conf.js
module.exports = function(config) {
  config.set({
    preprocessors: {
      './fixtures/**/*.json': ['json_fixtures']
    },

    files: [
      './fixtures/**/*.json'
    ]
  });
};
```

## How it works

Preprocessor requires .json files and converts them into .js files by storing json data as javascript objects under `__fixtures__` namespace.

the following file:
```json
// ./fixtures/test.json
{
    "a": "test"
}
```
will be accessible in your test environment:
```js
var fixture = window.__fixtures__['fixtures/test'];
fixture["a"] // => 'test'
```