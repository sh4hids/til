# Mocking in jest

- to mock a module for all the tests, we can use `setupTests.js` file

```js
//setupTests.js
const * as calculator = require('@myorg/mylib/lib/math/calculator');

const spy = jest.spyOn(calculator, 'add');

spy.mockResolvedValue(45);
```

```js
//jest.config.js

{
  ...otherConfig,
  setupFilesAfterEnv: ['<rootDir>src/test-utils/setupTests.js']
}
```


