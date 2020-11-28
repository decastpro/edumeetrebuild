## Installation

* Clone the project:

```bash
$ git clone https://github.com/decastpro/edumeetrebuild.git
$ cd mediasoup-demo
$ git checkout v3
```

* Ensure you have installed the [dependencies] required by mediasoup to build.
 
* Linux, OSX and any *NIX system
```bash
    node version >= v10.0.0
    python version 2 or 3
    make
    gcc and g++ >= 4.9 or clang (with C++11 support)
    cc and c++ commands (symlinks) pointing to the corresponding gcc/g++ or clang/clang++ executables.

    In Debian and Ubuntu install the build-essential DEB package. It includes both make and gcc/g++.
    In YUM based Linux (Red Hat, CentOS) use yum groupinstall "Development Tools".
   ``` 
*  If there is not python command pointing to Python 2 or 3 executable, set the PYTHON environment variable during mediasoup installation:
```bash
$ PYTHON=python3 npm install mediasoup@3 --save
```
If the MEDIASOUP_MAX_CORES environment variable is set, the build process will use that number of CPU cores. Otherwise it will auto-detect the number of cores in the machine.
Windows



* Set up the edumeet - rebuild server:

```bash
$ cd server
$ npm install
```

* Copy `config.example.js` as `config.js` and customize it for your scenario:

```bash
$ cp config.example.js config.js
```

**NOTE:** To be perfectly clear, "customize it for your scenario" is not something "optional". If you don't set proper values in `config.js` the application **won't work**.

* Set up the mediasoup-demo browser app:

```bash
$ cd app
$ npm install
```


## Run it locally

* Run the Node.js server application in a terminal:

```bash
$ cd server
$ npm start
```

* In a different terminal build and run the browser application:

```bash
$ cd app
$ npm start
```

* Enjoy.


## Deploy it in a server

* Globally install `gulp-cli` NPM module (may need `sudo`):

```bash
$ npm install -g gulp-cli
```

* Build the production ready browser application:

```bash
$ cd app
$ gulp dist
```

* Upload the entire `server` folder to your server and make your web server (Apache, Nginx, etc) expose the `server/public` folder.

* Edit your `server/config.js` with appropriate settings (listening IP/port, logging options, **valid** TLS certificate, etc).

* Within your server, run the Node.js application by setting the `DEBUG` environment variable according to your needs.

```bash
$ DEBUG="*mediasoup* *ERROR* *WARN*" node server.js
```
* If you wish to run it as daemon/service you can use [pm2](https://www.npmjs.com/package/pm2) process manager. Or you can dockerize it among other options.

* The Node.js application exposes an interactive terminal. When running as daemon (in background) the host administrator can connect to it by entering into the `server` folder and running:

```bash
$ npm run connect
