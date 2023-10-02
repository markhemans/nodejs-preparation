/




/


# CHILD PROCESSES


the child_process 'library'


The child_process module has the following methods,
all of which
spawn a process some way or another:

exec & execSync
spawn & spawnSync
execFile & execFileSync
fork

# Fork

The fork method is a specialization
of the spawn method. By default,
it will spawn a new Node process
of the currently executing JavaScript
file (although a different JavaScript
file to execute can be supplied).
It also sets up Interprocess
Communication (IPC) with the
subprocess by default. 

