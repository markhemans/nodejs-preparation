//

understand this. keyword

//

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
Symbol: Symbol('description')
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

Symbols are immutable and unique. 
They can be used in
many ways and can have flags.

You can add symbols as a key in an
object using square brackets []


let id = Symbol("id");

let person = { name: "Jack",

*adding symbol as a key*

[id]: 123 // not "id": 123 };

console.log(person); // {name: "Jack",
Symbol(id): 123}


Symbols are not included in for...in Loop

The for...in loop does not iterate
over Symbolic properties. For example,

let id = Symbol("id");

let person = {
    name: "Jack",
    age: 25,
    [id]: 12
};

// using for...in
for (let key in person) {
    console.log(key);
}

Output

name
age






everything else in JavaScript is an object.















FUNCTIONS

Functions are first class citizens
in JavaScript.
A function is an object, and therefore
a value that can be used like any
other value.


Functions can be returned from functions

function createGreeter(greeting)
{
    function greet(name)
    {
        console.log(greeting, 

    return greet;
}

Functions can be passed as arguments
to functions.


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


Functions have a "call" method that
can be used
to set their this context:

function fn() { console.log(this.id) }
const obj = { id: 999 }
const obj2 = { id: 2 }
fn.call(obj2) // prints 2
fn.call(obj) // prints 999
fn.call({id: ':)'}) // prints :)

