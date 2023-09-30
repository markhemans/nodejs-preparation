/



/

# BUFFERS

The correct way to allocate a
buffer of a certain amount of bytes is to use Buffer.alloc:

const buffer = Buffer.alloc(10)

the number of bytes
added to the buffer is the number in
the function

### Buffer.AllocUnsafe(10)

Every time Buffer.allocUnsafe is used it
will return a different buffer of garbage bytes:


## Buffer from a string

const buffer = Buffer.from('hello world')

When the first argument passed to Buffer.from is a string, a second argument can be supplied to set the encoding. There are two types of encodings in this context: character encodings and binary-to-text encodings.

UTF8 is one character encoding, another is UTF16LE.

## Buffer to string

To convert a buffer to a string, call the toString method on a Buffer instance:

const buffer = Buffer.from('👀')
console.log(buffer) // prints <Buffer f0 9f 91 80>
console.log(buffer.toString()) // prints 👀
console.log(buffer + '') // prints 👀
 

 The toString method can also be passed an encoding as an argument:

 .toString('hex')


 ## JSON Stringify & Parse

 JSON.stringify()
 JSON.parse()

