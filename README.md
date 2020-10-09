PHPUnit Polyfills
=====================================================

[![Latest Stable Version](https://poser.pugx.org/yoast/phpunit-polyfills/v/stable)](https://packagist.org/packages/yoast/phpunit-polyfills)
[![Travis Build Status](https://travis-ci.com/Yoast/PHPUnit-Polyfills.svg?branch=master)](https://travis-ci.com/Yoast/PHPUnit-Polyfills/branches)
[![Minimum PHP Version](https://img.shields.io/packagist/php-v/yoast/phpunit-polyfills.svg?maxAge=3600)](https://packagist.org/packages/yoast/phpunit-polyfills)
[![License: BSD3](https://poser.pugx.org/yoast/phpunit-polyfills/license)](https://github.com/Yoast/PHPUnit-Polyfills/blob/master/LICENSE)


Set of polyfills for changed PHPUnit functionality to allow for creating PHPUnit cross-version compatible tests.

* [Requirements](#requirements)
* [Installation](#installation)
* [Features](#features)
* [Contributing](#contributing)
* [License](#license)


Requirements
-------------------------------------------

* PHP 5.6 or higher.
* PHPUnit 5.7 - 9.x (automatically required via Composer).


Installation
-------------------------------------------

To install this package, run:
```bash
composer require --dev yoast/phpunit-polyfills
```

To update this package, run:
```bash
composer update --dev yoast/phpunit-polyfills --with-dependencies
```

This package can also be used when running tests via a PHPUnit Phar file.
In that case, make sure that the `phpunitpolyfills-autoload.php` file is explicitly `require`d in the test bootstrap file.
(Not necessary when the Composer `vendor/autoload.php` file is used as, or `require`d in, the test bootstrap.)


Features
-------------------------------------------

This library is set up to allow for creating PHPUnit cross-version compatible tests.

This library offers a number of polyfills for functionality which was introduced, split up or renamed in PHPUnit.

### Write your tests for PHPUnit 9.x and run them on PHPUnit 5.7 - 9.x

The polyfills have been setup to allow tests to be _forward_-compatible. What that means is, that your tests can use the assertions supported by the _latest_ PHPUnit version, even when running on older PHPUnit versions.

This puts the burden of upgrading to use the syntax of newer PHPUnit versions at the point when you want to start running your tests on a newer version.
By doing so, dropping support for an older PHPUnit version becomes as simple as removing it from the version constraint in your `composer.json` file.

### Supported ways of calling the assertions

By default, PHPUnit supports four ways of calling assertions:
1. As a method in the `TestCase` class - `$this->assertSomething()`.
2. Statically as a method in the `TestCase` class - `self/static/parent::assertSomething()`.
3. Statically as a method of the `Assert` class - `Assert::assertSomething()`.
4. As a global function - `assertSomething()`.

The polyfills in this library support the first two ways of calling the assertions as those are the most commonly used type of assertion calls.

For the polyfills to work, a test class is **required** to be a (grand-)child of the PHPUnit native `TestCase` class.


Contributing
-------
Contributions to this project are welcome. Clone the repo, branch off from `develop`, make your changes, commit them and send in a pull request.

If you are unsure whether the changes you are proposing would be welcome, please open an issue first to discuss your proposal.


License
-------
This code is released under the [BSD-3-Clause License](https://opensource.org/licenses/BSD-3-Clause).