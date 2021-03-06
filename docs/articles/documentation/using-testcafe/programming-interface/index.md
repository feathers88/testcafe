---
layout: docs
title: Programming Interface
permalink: /documentation/using-testcafe/programming-interface/
checked: true
---
# Programming Interface

This section describes the API that allows you to run TestCafe tests from your Node.js modules.

Begin with creating the [TestCafe server](testcafe.md) instance using
the [createTestCafe](createtestcafe.md) factory function.

```js
const createTestCafe = require('testcafe');
const testCafe       = await createTestCafe('localhost', 1337, 1338);
```

Use this instance to create other entities required to execute tests:
[remote browser connections](browserconnection.md)
and the [test runner](runner.md).

```js
const remoteConnection = await testcafe.createBrowserConnection();
const runner           = testcafe.createRunner();
```

[Remote browser connections](browserconnection.md) allow you to run tests on remote devices.

The [test runner](runner.md) configures and launches test tasks.

The following example shows how to run tests from the `myFixture.js` fixture in two browsers:
Google Chrome installed locally and another browser (that can be any of the supported browsers) on a remote device.
The test run report will be output in the JSON format.

```js
const failedCount = await runner
    .src('tests/myFixture.js')
    .browsers([remoteConnection, 'chrome'])
    .reporter('json')
    .run();
```

For details, see the reference topics below.

----

## Reference

* [createTestCafe factory function](createtestcafe.md)
* [TestCafe Class](testcafe.md)
* [Runner Class](runner.md)
* [BrowserConnection Class](browserconnection.md)