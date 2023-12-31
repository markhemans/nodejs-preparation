/

revise the use of debugger

/

# DEBUGGING & DIAGNOSTICS

node.js processes can be put into the browser
for inspect mode.
this is done by using the
inspect flag.

inspect mode is enabled with
the --inspect flag like shown below:


node --inspect app.js


to set a breakpoint at the start of the
first executable line in the application,
before asynchronous tasks begin, use:

node --inspect-brk app.js


Otherwise, asynchronous tasks will
start to execute.


The debugger statement can be used to
explicitly pause on the line that the
statement appears when debugging:

debugger;


**it is used with the --inspect flag
only.

when not debugging, it is ignored.**


/ 

ADDITIONAL NOTES

The remote debugging protocol
uses WebSockets 
(ws://) protocol.


In order to begin debugging the process
the next step is to set a Chrome browser
tab's address bar to (chrome://inspect).

The "pause on exception" button can be
used to pause where an exception is thrown.
Ensure the pause on exception button is
unchecked. when run with the --inspect-brk
flag, the debugger will pause on the first
caugh exception. In order to add a breakpoint
at any place in Devtools, click the line number
in the column to the left of the source code.
Devtools uses a "call-stack".
In some scenarios it can be easier to set
a breakpoint directly in the code, instead
of via the Devtools UI.

/