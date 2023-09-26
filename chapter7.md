//

learn how to manage modules

//


~~~
npm install
~~~

As long as Pino is installed, the module that the Pino package exports can be loaded.

~~~
const pino = require('pino')
~~~

The *require* function is passed a package's namespace,
looks for a directory with that name in the node_modules folder
and returns the exported value from the main file of that package.



