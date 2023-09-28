## events emitter

the events module exports
an EventEmitter object:

const {EventEmitter} = require('events') *cjs node*
const EventEmitter = require('events') *ECMA node*

to use it, call it with new


const myEmitter = new EventEmitter();


## emitting

const { EventEmitter } = require('events')
const myEmitter = new EventEmitter()
myEmitter.emit('an-event', some, args)

