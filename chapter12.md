/

Streams facilitate high volume data
processing without requiring exorbitant compute resources. 


/

# STREAMS


The Node core stream module exposes six constructors for creating streams:

Stream
Readable
Writable
Duplex
Transform
PassThrough


The only thing the Stream constructor
implements is the *pipe* method, which
we will cover later in this section.

The main events emitted by various Stream implementations that one may commonly encounter in application-level code are:

data
end
finish
close
error


there are four events that could signify the end of a stream,
which emits the *close* event

## Stream modes

There are two stream modes:

Binary streams
Object streams

### default stream mode

The mode of a stream is determined by its
objectMode option passed when the stream is
instantiated. The default objectMode is false,
which means the default mode is binary.
Binary-mode-streams only read or write
Buffer instances (Buffers were covered in Chapter 11).


## readable

The Readable constructor creates readable streams. A readable stream could be used to read a file, read data from an incoming HTTP request, or read user input from a command prompt to name a few examples. The Readable constructor inherits from the Stream constructor which inherits from the EventEmitter constructor, so readable streams are event emitters. As data becomes available, a readable stream emits a data event.

The following is an example demonstrating the consuming of a readable stream:

'use strict'
const fs = require('fs')
const readable = fs.createReadStream(__filename)
readable.on('data', (data) => { console.log(' got data', data) })
readable.on('end', () => { console.log(' finished reading') })