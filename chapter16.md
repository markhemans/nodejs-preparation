/


/

# UNIT TESTING


## assertions

the 'assert' library

const assert = require('assert')

An assertion checks a value for
a given condition and throws
if that condition is not met. 

example

assert.equal(val1, val2)  *coercive equal, val1 == *val2*

5 main assertion types:

Truthiness (assert and assert.ok)
Equality (strict and loose) and Pattern Matching (match)
Deep equality (strict and loose)
Errors (ifError plus throws, rejects and their antitheses)
Unreachability (fail)


const assert = require('assert')
const add = require('./get-add-from-somewhere.js')
assert.equal(add(2, 2), 4)


when one assertion fails,
the process stops running.

It would be great if we could group assertions together so that if one in a group fails, the failure is output to the terminal but the remaining groups of assertions still run. so:

## TEST HARNESS

PURE LIBRARIES
FRAMEWORK

Test Harnesses

Close Pure Library
Pure library test harnesses provide a module, which is loaded into a file and then used to group tests together. As we will see, pure libraries can be executed directly with Node like any other code. This has the benefit of easier debuggability and a shallower learning curve. We'll be looking at tap.

Alternative test libraries include tape and brittle.

Close Framework Environment
A test framework environment may provide a module or modules, but it will also introduce implicit globals into the environment and requires another CLI tool to execute tests so that these implicit globals can be injected. For an example of a test framework environment we'll be looking at jest.

Alternative test frameworks include jasmine and mocha.


## configuring the json file

{
  "name": "my-project",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "tap"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}