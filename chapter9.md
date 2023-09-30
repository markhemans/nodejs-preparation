/

create events
consume events

http , tcp use events

/


# NODE EVENT SYSTEM



## creating events emitter


const {EventEmitter} = require('events') *cjs node*
const EventEmitter = require('events') *ESM VERSION*

const myEmitter = new EventEmitter();


## using emit method

to emit an event, call the emit method
on an instantiation:'

myEmitter.emit('an-event', some, args)

## listening to events (on)

To add a listener to an event emitter
the addListener method or it's alias *on* method
 is used:

const { EventEmitter } = require('events')

const ee = new EventEmitter()
ee.on('close', () => { console.log('close event fired!') })
ee.emit('close')


*An event can also be emitted more than once:*

unless:

## once

The once method will immediately remove
its listener after it has been called:



## removeListener

removeListener can be used to
remove an event from a 
listener.

## removeAllListeners

remove all listeners from
an event




## the 'error' event

the error event will cause the
listener to throw an exception

ee.on('error', )




/
ADDITIONAL NOTES

The prependListener method can be
used to inject listeners into the top position:
/