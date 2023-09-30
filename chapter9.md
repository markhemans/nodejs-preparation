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

const { EventEmitter } = require('events')
const myEmitter = new EventEmitter()
myEmitter.emit('an-event', some, args)

