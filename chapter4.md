DEBUGGING

node.js processes can be put into inspect mode. it
exposes a debugger port that can be connected to
using chrome dev tools. this is done by using the
--inspect flag.

we can also run other diagnostic checks.



inspect mode can be enabled with the --inspect flag

node --inspect app.js

this will output a url that can be used to connect
to the debugger.


node --inspect-brk app.js

this will output a url that can be used to connect
to the debugger. the difference is that the
debugger will stop at the first line of code.
otherwise, the application will have fully initialized and may be performing asynchronous tasks


The remote debugging protocol uses WebSockets which is why a ws:// protocol address is printed. 

In order to begin debugging the process, the next step is to set a Chrome browser tab's address bar to chrome://inspect.


Note that execution is paused is at the first line of executable code, in this case line 5, which is the first function call.

The "Pause on exceptions" feature can be used to automatically set a breakpoint at the line where an error is thrown.

To activate this behavior, start app.js in Inspect Break mode (--inspect-brk), connect Chrome Devtools. Make sure the pause on exc

