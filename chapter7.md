
/

strict mode

language specific ESM modules
CJS module system

/


# NODE MODULE SYSTEM


## USING OLD CJS

module has been loaded using *require*

the require function takes a *namespace*,
looks for it in the node_modules directory
and returns the main file.


const VARIABLE = require('node_modules_folder')

you can also require a local module using
the filepath in the require function

const variable = require(./files/index.js)

## MODULE.EXPORTS

the CJS WAY must be exporting the variable
using module.exports

<module.exports = ANYTHING(object, function, variable..)>


### using a file as both entry point and program file

we can set a file to have two operational
modes by accessing the require function's
main property to see if theres a module there


by checking if require.main === module


if (require.main === module) {
  const pino = require('module_name')
}
else
{
    module.exports = some-variable
}

## ESM modules

they allow the browser to
pre-parse imports and collect scripts

















/ 
ADDITIONAL NOTES

in strict mode,
undeclared-variables throw
an error

cjs loads synchrously
esm loads asynchrously

/