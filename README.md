Installation

    Clone the project:

$ git clone https://github.com/decastpro/edumeetrebuild.git
$ cd mediasoup-demo
$ git checkout v3

    Ensure you have installed the dependencies required by mediasoup to build.

    Set up the mediasoup-demo server:

$ cd server
$ npm install

    Copy config.example.js as config.js and customize it for your scenario:

$ cp config.example.js config.js

NOTE: To be perfectly clear, "customize it for your scenario" is not something "optional". If you don't set proper values in config.js the application won't work.

    Set up the mediasoup-demo browser app:

$ cd app
$ npm install

Run it locally

    Run the Node.js server application in a terminal:

$ cd server
$ npm start

    In a different terminal build and run the browser application:

$ cd app
$ npm start

    Enjoy.

Deploy it in a server

    Globally install gulp-cli NPM module (may need sudo):

$ npm install -g gulp-cli

    Build the production ready browser application:

$ cd app
$ gulp dist

    Upload the entire server folder to your server and make your web server (Apache, Nginx, etc) expose the server/public folder.

    Edit your server/config.js with appropriate settings (listening IP/port, logging options, valid TLS certificate, etc).

    Within your server, run the Node.js application by setting the DEBUG environment variable according to your needs (more info):

$ DEBUG="*mediasoup* *ERROR* *WARN*" node server.js

    If you wish to run it as daemon/service you can use pm2 process manager. Or you can dockerize it among other options.

    The Node.js application exposes an interactive terminal. When running as daemon (in background) the host administrator can connect to it by entering into the server folder and running:

$ npm run connect

Considerations for (config.js)[server/config.example.js]

    Make sure https.listenIp is set to 0.0.0.0.
    Make sure TLS certificates reside in server/certs directory with names fullchain.pem and privkey.pem.
    The default mediasoup port range is just 2000-2020, which is not suitable for production. You should increase it, however you should then run the container in network="host" mode.
