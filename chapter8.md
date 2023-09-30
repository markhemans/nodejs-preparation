/



/

# ASYNCHRONOUS CONTROL FLOW

tasks can be scheduled and another
task can be completed before the
task is selected

setTimeout() calls a function
after a specified amount
of time passes

# callbacks

__filename *holds the path to the current*
*file being executed in node*


const print = (err, contents) => {
  if (err) {
    console.error(err)
    return
  }
  console.log(contents.toString())
}

readFile() *is an asynchronous operation*

const { readFile } = require('fs')
readFile(__filename, *operation*)

### printing asynchronously

readFile(bigFile, print)
readFile(mediumFile, print)
readFile(smallFile, print)

### printing serially

readFile(bigFile, (err, contents) => {
  print(err, contents)
  readFile(mediumFile, (err, contents) => {
    print(err, contents)
    readFile(smallFile, (err, contents) => {
      print(err, contents)
    })
  })
})

## promises

promises can be returned from functions

const promise = myAsyncOperation()
promise
  .then((value) => { console.log(value) })
  .catch((err) => { console.error(err) })

## promises contd.

const { readFile } = require('fs').promises

const print = (contents) => {
  console.log(contents.toString())
}
readFile(bigFile)
  .then((contents) => {
    print(contents)
return readFile(mediumFile)
})
.then((contents) => {
print(contents)
return readFile(smallFile) 
})
.then(print)
.catch(console.error)


Once bigFile has been read,
the first .then handler returns a promise
for reading mediumFile. The second
.then handler receives the contents of
mediumFile and returns a promise for
reading smallFile. The third .then handler
is the prints the contents of the
smallFile and returns itself. The catch
handler will handle errors from any of
the intermediate promises.

## Promise.all(arrayOfPromises)

Promise.all(readers)
  .then(print)
  .catch(console.error)

The Promise.all function takes an array of promises and returns a promise that resolves when all promises have been resolved. That returned promise resolves to an array of the values for each of the promises. This will give the same result of asynchronously reading all the files and concatenating them in a prescribed order, but the promises will run in parallel. For this case that's even better.

However if one of the promises was to fail, Promise.all will reject, and any successfully resolved promises are ignored. If we want more tolerance of individual errors, Promise.allSettled can be used:

## Promise.allSettled(arrayOfPromises)

returns an array of objects representing the settled status of each promise. Each object has a status property, which may be rejected or fulfilled (which means resolved). Objects with a rejected status will contain a reason property containing the error associated with the rejection. Objects with a fulfilled status will have a value property containing the resolved value. 

Promise.allSettled(readers)
  .then(print)
  .catch(console.error)

## ASYNC


async function run () {
  print(await readFile(bigFile))
  print(await readFile(mediumFile))
  print(await readFile(smallFile))
}

run().catch(console.error)

To determine the order in which we want operations to resolve in async/await we simply await those operations in that order.

### concatenated approach


async function run () {
  const data = [
    await readFile(bigFile),
    await readFile(mediumFile),
    await readFile(smallFile)
  ]
  print(Buffer.concat(data))
}

run().catch(console.error)

### chronological async/await/using promises

const { readFile } = require('fs').promises

const print = (contents) => {
console.log(contents.toString())
}

async function run () {
const big = readFile(bigFile)
const medium = readFile(mediumFile)
const small = readFile(smallFile)

big.then(print)
medium.then(print)
small.then(print)

await small
await medium
await big

}

run().catch(console.error)

This will ensure the contents are printed out
chronologically, according to the time
it took each of them to load. 


## aborting operations

const timeout = setTimeout(() => { 
  console.log('will not be logged') 
}, 1000)

setImmediate(() => { clearTimeout(timeout) })


or (ESM):

import { setTimeout } from 'timers/promises'


const timeout = setTimeout(1000, 'will be logged'

setImmediate(() => { 
  clearTimeout(timeout) // do not do this, it won't work 
})
console.log(await timeout)




