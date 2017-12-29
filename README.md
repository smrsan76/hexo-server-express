# hexo-server-express
It's similar to "hexo-server" package, but it uses express instead of connect.

[![NPM](https://nodei.co/npm/hexo-server-express.png)](https://nodei.co/npm/hexo-server-express/)

## Guides
These are some useful guides.

### How to install ?
Enter it in a command line:
```sh
npm i hexo-server-express --save
```

### How to start it ?
Enter it in command line:
```sh
hexo server-express
```

### How to start it from node.js codes ?
Enter this codes in the start of your app:
```javascript
const Hexo = require('hexo');
let hexo = new Hexo(process.cwd() /*The base dir*/, { /*Hexo options*/ });

hexo.init()
    .then(function(){

        hexo.call("server-express", { /*server options*/ })
            .then(() => {

                // do some stuff ...

            })
            .catch(err => {

                hexo.log.fatal("SERVER-EXPRESS START FAILED!!!");
                console.error(err);

            });

    });
```
and it should be start.
As you can see, everything is similar to [hexo-server](https://npmjs.com/package/hexo-server)
, but I just changed the command name `server` to `server-express`.

### How to use my app in a hexo server/server-express ?
Simply, make this `server_middleware` like codes below:
```javascript
// ...
// After starting hexo from your node.js codes

// Make your app
const express = require("express");
let yourApp = express();

// Register a server_middleware
hexo.extend.filter.register('server_middleware', hexoApp => {

    hexoApp.use("/admin", yourApp);
    // or do whatever you want with hexoApp ...

});

```

### Related Packages
* [hexo-app-connect](https://npmjs.com/package/hexo-app-connect):
  It lets you use hexo as a route in your main express/connect app

for getting more info, visit

[hexo-server package on github](https://github.com/hexojs/hexo-server)

[hexo-server package on npm](https://npmjs.com/package/hexo-server)


#### Made with ❤️ for [hexo](https://npmjs.com/package/hexo)