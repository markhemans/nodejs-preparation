//

npm client
associated manifest file

//


the npm command is a package
manager that points by default to
npmjs.com registry. this is the
default module registry.


npm help            *no hyphen at help*

this command prints out a list
of npm commands



to view the help command
for an individual command add
the flag at the end of the command

npm install -h          *no hyphen at install*


a package is a folder with some code
in it and a package.json file


a node.js application or service is also
a package.


npm init is used to initialize a package
and it can be sped up by using a -y flag
to answer yes to all the questions.


The default fields in a generated
package.json are:


name – the name of the package
version – the current version
        number of the package
description – a package description, this is 
                used for meta analysis
                in package registries
main – the entry-point file to load when
        the package is loaded
scripts – namespaced shell scripts, these
            will be discussed later
            in this section
keywords – array of keywords, improves
            discoverability
            of a published package
author – the package author
license – the package license.


a package initialized in a git
repository can read
its remote url from
git and add it to the 
package.json


once a program has a package.json
file dependencies can be
installed, such as a logger


In addition, a node_modules
folder
and a package-lock.json file
will have been added to
a package.json folder

when a dependacy is installed,
the dependencies
flag in the package.json is updated

The "dependencies" field
contains an object,
the keys of the object
contain dependency
namespaces, the values in the object contain
the Semver range version number for that dependency.


when a dependency is installed
a node_nodules and a
package-lock.json file are
created.

the package-lock.json
file contains a map of all dependencies
with their exact versions.

this is useful when a node product
is about to be released and we need
to keep the current installed versions
stable.

otherwise it is more sensible to
use the latest versions of node
packages. node uses the package-lock
to pull the dependencies

we can edit the package-lock flag in the
.npmrc file in the home directory
to not create package-lock files



then to manually create a package-lock
file we use  npm install --package-lock
to manually set this preference


if a package-lock file is present
then the user needs to manually
manage dependency updates for each
dependency.

node uses a maximally-flat tree
that places packages at the top
level of a node_modules folder
unless there are two different
versions of the same package where
its going to be placed in a
new node_modules folder

you can see packages with
npm ls


### ADDING DEPENDENCIES

the primary reason for
adding dependencies is to 
make the node_modules folder
dispoable.


to do this, run npm install
(no namespace)

node modules folder should
not be added to git.


## Development Dependencies