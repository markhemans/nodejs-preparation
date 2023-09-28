/

remember stack trace limits

/


# THE NODE BINARY

the entire node.js platform is almost
entirely filled with node binary
executables.

below are (2) main starting points
for node:


to view all Node command flags:

node --help


modify node engine called (V8):

node --v8-options


## checking syntax

to check the syntax of a file,
if the code parsed without errors :

node --check app.js
node -c app.js


## dynamic evaluation

we can either print or eval :

node --eval  $ runs javascript code as is
node --print $ print evals, i.e runs
               then prints everything again
    

## requiring


another name for this operation is called
'PRELOADING' files for execution. we do
this to call a file before another file : 

node --require
node -r



## STACK TRACE LIMITS

stack trace limits happen to be
part of the V8 engine used to run files
(they are part of node --v8-options) :


node --stack-trace-limit=101 app.js 



the number specified equals the number of
lines shown.








