//

npm client
associated manifest file

//


the npm command is a package
manager that points by default to
npmjs.com registry. this is the
default module registry.


npm help

this command prints out a list
of npm commands



to view the help command
for an individual command add
the flag at the end of the command

npm install -h


a package is a folder with some code
in it and a package.json file

a node.js application or service is also
a package.

npm init is used to initialize a package
and it can be sped up by using a -y flag
to answer yes to all the questions.


The default fields in a generated package.json are:

name – the name of the package
version – the current version number of the package
description – a package description, this is 
                used for meta analysis in package registries
main – the entry-point file to load when
        the package is loaded
scripts – namespaced shell scripts, these
            will be discussed later in this section
keywords – array of keywords, improves discoverability
            of a published package
author – the package author
license – the package license.

a package initialized in a git repository can read
its remote url from git and add it to the 
package.json


once a program has a package.json file
dependencies can be installed, such
as a logger


In addition, a node_modules folder
and a package-lock.json file
will have been added to a package.json
folder

when a dependacy is installed, the dependencies
flag in the package.json is updated

The "dependencies" field contains an object,
the keys of the object contain dependency
namespaces, the values in the object contain
the Semver range version number for that dependency.

