DEBUGGING

node.js processes can be put into
inspect mode. this exposes a debugger
port that can be connected to
using chrome dev tools. 
this is done by using the
--inspect flag.

we can also run other diagnostic checks.

inspect mode is enabled with
the --inspect flag like shown below:


node --inspect app.js


this will output a url that can be
used to connect to the debugger.

to set a breakpoint at the start of the
file we can do so,
otherwise, the application will have fully
initialized and may be performing
asynchronous tasks.

node --inspect-brk app.js


The remote debugging protocol
uses WebSockets 
(ws://) protocol  


In order to begin debugging the process
the next step is to set a Chrome browser
tab's address bar to (chrome://inspect).




