the entire node.js platform is almost
entirely represented by node binary
executables.
 below are (2) main starting points
for node:


to view all Node command flags for node use the
executable:

node --help


in additon, we can modify the node Javascript
Runtime Engine, JRE, called V8:

node --v8-options




running javascript code just to check the
syntax of a file:

node --check app.js
node -c app.js


CODE SNIPPETS

node can 'evaluate' directly from the shell to:
(1)run small commands that use javascript
or node core
(2)checking code snippets


node --eval  $ runs javascript code
node --print $ prints the result, equivalent to
               explicit console.log
               wrapper


PRINTING RETURNS BY EVALAUTING FIRST
I.E RUNNING THE COMMAND VIA NODE
THEN, PRINTING DIRECT DIRECTLY WHAT THE
ARGUMENTS ARE, BASICALLY THESE TWO ARGUMENTS
WORK DIRECTLY WITH THE CONSOLE AND AS SUCH,
ARE EVALUATED RIGHT TO LEFT.

every Node core module can be accessed by
their namespaces through eval.
for example, fs modules

node -p "fs.readdirSync('.').filter((f)
=> /.js$/.test(f))"


another node binary operation is called
'PRELOADING' files for execution. this
essentially calls a file before another file
is called. this only works for CommonJs files.
it uses the require function. ESM modules have
a vaguely related flag called --loader
REQUIRE IS USED TO PRELOAD

node --require
node -r



STACK TRACE LIMITS

stack trace limits are part of the V8 engine
and as such are part of node --v8-options



node --stack-trace-limit=101 app.js 



the number specified equals the number of lines
shown.








