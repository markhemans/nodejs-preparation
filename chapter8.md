/



/

# ASYNCHRONOUS CONTROL FLOW


tasks can be scheduled and another
task can be completed before the
task is selected


after the process called in
a setTimeout() function is called
the function in the declaration
is called

it waits for the amount of
time specified in the setTimeout

# callbacks

__filename *holds the path to the current file being executed in node*

readFile(__filename, (err, contents) =>
{
 if (err)
    console.log(err)
 else
})

once the file is read, the function
calls the next param

errback

if there is an error, we use
err to print the error of the function

The simplest way to read a file in Node.js
is to use the fs.readFile() method,
passing it the file path, encoding and a callback function
that will be called with the file data (and the error):
it uses memory meaning asynchrously it would
pull smaller files first concurently

What if we wanted to use serial execution,
let's say we want bigFile to print first,
then mediumFile even though they take longer
to load than smallFile. Well now the
callbacks have to be placed inside each other:


const { readFile } = require('fs')
const [ bigFile, mediumFile, smallFile ] = Array.from(Array(3)).fill(__filename)
const print = (err, contents) => {
  if (err) {
    console.error(err)
    return
  }
  console.log(contents.toString())
}


readFile(bigFile, (err, contents) => {
  print(err, contents)
  readFile(mediumFile, (err, contents) => {
    print(err, contents)
    readFile(smallFile, print)
  })
})
