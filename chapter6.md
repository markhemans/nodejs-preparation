/

npm flags are usually not followed by dashes 

importance of package.json file


/

# PACKAGES & DEPENDENCIES


the npm points to the
npmjs.com registry by default. 

this command prints out a list
of npm commands :


npm help     *remember to include no hyphen*


to view the help command
for an individual command add
the help flag at the end of the command :

npm install -h    *no hyphen at install, but hyphen at help, just -h*


a package is a folder with some code
in it and a package.json file

a node.js application or service is also
a package.

to initialize a package:


npm init


it can be sped up to include a yes
to all the questions using a -y flag.


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



when any dependencies are installed:


In addition, a:

*node_modules*


folder and a:

*package-lock.json*


file will have been added to
already existing package.json folder

when a "dependancy" is installed,
the *dependencies*
flag in the package.json is updated

The "dependencies" field
contains an object:

the *keys* of the object
contain dependency
namespaces.

the *values* in the object contain
the Semver range version number for that dependency.

...
"DEPENDENCIES": {

        "KEYS" : "VALUES,
}

## package-lock.json file

the package-lock.json
file contains a map of all dependencies
with their exact versions.

## dependency tree

you can see all packages with:

npm ls

The tree shown is the logical dependency tree,
based on package dependencies, not the physical
layout of your node_modules folder.

Running:

npm ls --depth=999 

now reveals a much larger dependency tree.

## npm install

if you have packages in the package-lock.json
running:

npm install

would add them to the node_modules folder

## development-dependencies installations

development dependencies of installed
packages are never installed for your package.
but you can install them explicitly for yourself,

### INSTALLING A DEVELOPMENT DEPENDENCY

to install a dev-dependency:

npm install --save-dev *dev-dependency-name*

### OMITTING DEV-DEPENDENCIES FOR PRODUCTION

When deploying a service or application
for production use,
we don't want to install any dev-dependencies
that aren't needed in production.

to do this:

npm install --omit=dev


# UNDERSTANDING SEMVER

0.0.0

major changes break an api
or behavior

minor changes mean the package
was extended but is backwards
compatible

patches mean there has
been a *bug* fix



using x's in major/minor/patches
positions is the closest way to
do versioning management
it can also be replaced
with using carats (^) next
to numbers to indicate the rest
are x's

### deduped

when a subpackage has a dependency
that its enclosing package shares SEMVER
with, it is installed only higher
and the subpackage relies on that one
creating a *deduped version*.



## Package Scripts

the "scripts" feild in a package.json
allows you to define shell commands:

 "scripts": {
    "test": "echo \"error no test specified"\ && exit 1 ",


    "CREATED_SHELL_COMMAND": "BIN_COMMAND"
  }

package scripts are run by specifying


npm run *script*


# npm test and start

There are two package scripts namespaces
that have *dedicated* npm commands:
npm test and npm start.

they are aliases of *npm run test*
and *npm run start*

```
"scripts": {
    "start": "node index.js",
    "test": "echo \"Error: no test specified\" && exit 1",
    "lint": "standard"
  }
```

## creating bin feild in package.json


adding a bin feild would allow you
to use associate a namespace to a
a Node program script within
that package.


The bin field maps one or more
command name(s) to one or more
script file(s) inside the package
that can be executed in multiple ways 

"bin": {
    "command-name": "path/to/script/file.js"
  }




/

ADDITIONAL NOTES

 a package initialized in a git
repository can read
its own remote url from
git and add it to the 
package.json

### package-lock.json file

(this is useful when a node product
is about to be released and we need
to keep the current installed versions
stable.)

otherwise it is more sensible to
use the latest versions of node
packages. node uses the package-lock
to pull the dependencies

we can edit the package-lock flag in the
.npmrc file in the home directory
to *not* create package-lock files

then, to manually create a package-lock
file we use  npm install --package-lock
to manually set this preference

### dependency tree

if a package-lock file is present
then the user needs to manually
manage dependency updates for each
dependency inside.

node uses a *maximally-flat* tree
that places each package at the top
level of a node_modules folder

unless there are *two different*
*versions* of the same package where
its going to be placed in a
new node_modules folder



node modules folder should
not be added to git.

### Development Dependencies

*only top-level development dependencies*
are installed. development dependencies
of sub-dependencies are not installed.

Not all dependencies are required for
production, some are tools to support the
development process.

/