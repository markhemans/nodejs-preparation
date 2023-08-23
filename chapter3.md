the entire node.js platform is almost
entirely represented by the node binary
executable below are (2) main starting points
for node:


to view all Node command flags for node use the
executable:

node --help


in additon, we can modify the node Javascript
Runtime Engine, JRE, called V8:

node --v8-options




running javascript code just to check the
syntax:

node --check app.js
node -c app.js




node can 'evaluate' directly from the shell to:
(1)run small commands that use javascript
or node core
(2)checking code snippets

node --print $ evaluates expression
               to print DIRECT result
               of expression DIRECTLY
node --eval  $ evaluates, does nothing

PRINTING RETURNS BY EVALAUTING FIRST
I.E RUNNING THE COMMAND VIA NODE
THEN, PRINTING DIRECT DIRECTLY WHAT THE
ARGUMENTS ARE, BASICALLY THESE TWO ARGUMENTS
WORK DIRECTLY WITH THE CONSOLE AND AS SUCH,
ARE EVALUATED RIGHT TO LEFT.

all Node core modules can be accessed by
their namespaces through code evaluation






