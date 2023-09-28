/

understand this. keyword
understand call
understand ... spread operator
when a function is created an invisible
object is created
learn the use of super in name construction

/

# KEY JAVASCRIPT CONCEPTS

DATA TYPES

null : absence of an object
undefined : absence of a defined
            value (i.e an
            number object that hasnt
            been assigned a value)
Number: limited numbers
BigInt: no limits on integers,
        numbers are limited
String: "strings" , 'strings' or
        `string ${strings}`
Boolean: true, false
Symbol: can be used as unique identifier keys
        in objects 
        Symbol('description')
        & Symbol.for('description')


STRINGS


Strings can be created with single
or double quotes, or
backticks. Strings created with
backticks are template
strings, these can be multiline
and support interpolation

normal strings can only
be concatenated together using the
plus (+) operator.


SYMBOLS

Symbols are used as unique identifying
keys for objects.

Symbols are immutable and unique. 

They can be used in
many ways and can have flags.

Symbol.for method creates/gets a global symbol.

You can add symbols as a key in an
object using square brackets []: 



let id = Symbol("id");
let person = { name: "Jack",
*adding symbol as a key*
[id]: 123 // not "id": 123 };
console.log(person); // {name: "Jack",
Symbol(id): 123}


Symbols are not included in for...in Loop

The for...in loop does not iterate
over Symbol properties. For example,

let id = Symbol("id");

let person = {
    name: "Jack",
    age: 25,
    [id]: 12
};

// using for...in
for (let key in person) {
    console.log(key); }

*output*

name
age




everything else in JavaScript is an object.


All objects in javascript have prototypes.

Javascript is a prototypal language.

if a property is not found in an object,
it would be looked for in its prototype.



OBJECTS

an object is any key, value pair in javascript
with the value being any primitive data
type or an object, or even a function as they
are first class citizens.

an objects key is called a property

If an object doesn't have a particular
property, the object's prototype
is checked for that property. -inheritance




FUNCTIONS

Functions are first class citizens
in JavaScript.
A function is an object, and therefore
a value that can be used like any
other value.


Functions can be returned from functions

function createGreeting(A)
{
    function greet(example)
    {
        console.log(greeting)
    }

   return greet;
}

Functions can even be passed as arguments
to other functions.

setTimeout(
    function () {
        console.log('hello from the future')
        }, 100)


THIS. pt.1


"this" keyword refers to the function
on which it was CALLED, not the 
function on which it was assigned to.

PRIME EXAMPLE:


const obj = { id: 999, fn: function ()
            { console.log(this.id) } }
const obj2 = { id: 2, fn: obj.fn }
obj2.fn() // prints 2
obj.fn() // prints 999

here obj2 is passed the function obj.fn
but when it is called, it is called
on obj2, so it prints 2.


Both obj and obj2 reference the same
function but on each invocation the
this context changes to the object
on which that function was called.




THIS

When a function is assigned to an object
when the implicit *this* keyword
is accessed within that function
it will refer to the object on 
which the function was called. if this is
used in a regular function, it will
reference the global object.

This is extra explanation on when
it is called on an object, 
it will refer to the exact object on which
it is called and not reference the function
on which it was defined. This is normally set
on function invocation, but can be set
explicitly using the call method.

In an object method, this refers to the object.
Alone, this refers to the global object.
In a function, this refers to the global object.
In a function, in strict mode, this is undefined.
In an event, this refers to the element
that received the event.
Methods like call(), apply(),
and bind() can refer this to any object.





CALL

.call 

Functions have a "call" method that
can be used
to set their this context, i.e 
the object on which they are called.:


function fn()
{
    console.log(this.id)
}

const obj = {
    id: 999 }

const obj2 = {
    id: 2 }

fn.call(obj2)         // prints 2
fn.call(obj)          // prints 999
fn.call({id: ':)'})   // prints :)


In this case the fn function wasn't assigned
to any of the objects, this was set dynamically
via the call function.



FAT ARROW FUNCTIONS

Fat arrow functions are a new syntax
for defining functions in ES6.

They are anonymous functions
that can be assigned to variables
or passed as arguments to other functions.

They are called fat arrow functions
because they use the => operator.

They are also called lambda functions
in other languages.

They are useful because they
don't have their own this context,
they inherit the this context
from the parent scope.

This means that they can be used
as methods on objects without
losing the this context.

They also don't have their own new.target
object, so they can't be used
with the new keyword.

They also don't have their own prototype
object, so they can't be used
as constructors.

They also don't have their own arguments
object, so they can be used
to create functions with a variable
number of arguments.





PROTOTYPAL INHERITANCE


There are many approaches and variations
to creating a prototype chain in JavaScript
but we will explore three common approaches: 

~functional
~constructor functions
~class-syntax constructors.
~closure scope


functional approach:

The functional approach to creating
prototype chains is to use Object.create:


PROPERTIES DESCRIPTOR

Object properties, besides a value,
have three special attributes
( so-called “flags”):

writable – if true, the value can be changed,
otherwise it’s read-only.
enumerable – if true, then listed in loops,
otherwise not listed.
configurable – if true, the property can be
deleted and these attributes can be modified,
otherwise not.

FUNCTIONAL APPROACH (using Object.create)


<<OBECT.CREATE()>>

The second argument of Object.create
is the Properties Descriptor object.

A Properties Descriptor object contains keys
that will become the key name on the object
being created. The values of these keys
are Property Descriptor objects.


When the dog prototype object is created,
the property descriptor is an object with
a woof key. The woof key references an
object with the value property set to
a function. This will result in the
creation of an object with a woof method.

So when rufus.woof() is called,
the rufus object does not have a woof
property itself. The runtime will then
check if the prototype object of rufus
has a woof property. The prototype of
rufus is dog and it does have a woof
property. The dog.woof function contains
a reference to this. Typically, the this
keyword refers to the object on which the
method was called. Since woof was called
on rufus and rufus has the name property
which is "Rufus the dog", the this.name
property in the woof method has the
value "Rufus the dog" so console.log
is passed the string: "Rufus the
dog: woof".


object.create (uses property descriptors)::

const wolf = { 
  howl: function ()
        {
    console.log(this.name + ': awoooooooo')
        }
             }

const dog = Object.create(wolf, { 
  woof: {                               *property descriptor key*
    value: function()                    *property descriptor*
            {
        console.log(this.name + ': woof')
            }
        }
                                })

const rufus = Object.create(dog, {
  name: {                               *property descriptor key*
    value: 'Rufus the dog'               *property descriptor*
        }
                                 })

rufus.woof() // prints "Rufus the dog: woof"
rufus.howl() // prints "Rufus the dog: awoooooooo"



CONSTRUCTOR FUNCTIONS (using functions & prototypes)

All functions have a prototype property.
This property is an object that
contains a constructor property
that references the function itself.

When a function is used as a constructor
with the new keyword, the prototype
property of the function is used
as the prototype of the new object.

The Constructor approach to creating a prototype
chain is to define properties on a function's prototype
object and then call that function with "new":



function Wolf (name) {
  this.name = name
}

Wolf.prototype.howl = function () {
  console.log(this.name + ': awoooooooo')
}

function Dog (name) {
  Wolf.call(this, name + ' the dog')
}

function inherit (proto) {
  function ChainLink(){}
  ChainLink.prototype = proto
  return new ChainLink()
}

Dog.prototype = inherit(Wolf.prototype)

Dog.prototype.woof = function () {
  console.log(this.name + ': woof')
}

const rufus = new Dog('Rufus')

rufus.woof() // prints "Rufus the dog: woof"
rufus.howl() // prints "Rufus the dog: awoooooooo"





CLASS SYNTAX CONSTRUCTORS (using constructor (name) & extends)

knowing javascript does not have classes,
the class syntax is just syntactic sugar
to create a function that can be called
with new.


class Wolf {
  constructor (name) {
    this.name = name
  }

  howl () { console.log(this.name + ': awoooooooo') }
  barf() {console.log('barfed')}

}

class Dog extends Wolf {
  constructor(name) {
    super(name + ' the dog')
  }

  woof () { console.log(this.name + ': woof') }

}

const rufus = new Dog('Rufus')





CLOSURE SCOPE

When a function is created,
an invisible object is also created
this is known as closure scope.

When a function is inside
another function, it can access both
its closure scope and outer closure scope.

if there is a naming collision,
the inner function will use its own
variable and not the outer one.



Closure scope cannot be accessed outside of
a function:


if a function returns a function, the
returned function can provide controlled
access to the parent closure scope:

function init (type) {
  var id = 0
  return (name) => {
    id += 1
    return { id: id, type: type, name: name }
  }
}
const createUser = init('user')
const createBook = init('book')
const dave = createUser('Dave')
const annie = createUser('Annie')
const ncb = createBook('Node Cookbook')
console.log(dave) //prints {id: 1, type: 'user', name: 'Dave'}
console.log(annie) //prints {id: 2, type: 'user', name: 'Annie'}
console.log(ncb) //prints {id: 1, type: 'book', name: 'Node Cookbook'}

The advantage of using closure scope to compose
objects is it eliminates the complexity of prototypes,
context (this) and the need to call a function with "new" 

Closure scope can also be used as an alternative to
prototypal inheritance. The following example
provides equivalent functionality and the same
level of composability as the three prototypal
inheritance examples but it doesn't use a
prototype chain, nor does it rely the
implicit this keyword:


theres the fccc


functional
constructor
class-syntax
closurescope



Context is always the value 
of the this keyword which is a
reference to the object that “owns” the
currently executing code or the function
where it’s looked at.

