/

come back to propagation

/


# HANDLING ERRORS


Typically, an input error is dealt
with by using the throw keyword on the line:


if (typeof amount !== 'number') throw new Error('amount must be a number')



you can throw a native new Error(' ') object,
or throw anything at all directly


you can do console.error

you can do

const ee = new Error()
ee.code = "SYSTEM_ERR_CODE_1"
throw ee

# FOR ASYNCHRONOUS FUNCTIONS

we use reject()

to throw an error in the failed block

and 

resolve()

to do an operation in a successful block