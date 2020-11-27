# edumeet - rebuild
 custom update with vimeo feed
 Run it in few easy step

    
        $ openssl req -x509 -newkey rsa:4096 -keyout privkey.pem -out cert.pem -days 365 -nodes

    Recomended: set TURN server and credential in configs/server/config.js
        In case you are using coturn, you can generate a user and key with

        $ turnadmin -k -u <username> -p <password>

Placeholder looks like

    turnServers     : [
        {
            urls : [
                'turn:example.com:443?transport=tcp'
            ],
            username   : 'example',
            credential : 'example'
        }
  ]

You would need to replace example.com by your IP or domain, add the username previously used <username> and credential is the code generated by the above mentioned command.

    Optional: Change other stuff in config:
        Optional: replace logo/logo.svg with your company logo svg.
        Optional: sort audio/video codecs according to preference.

Run

Run with docker-compose / install docker compose /

  $ sudo docker-compose up --detach

Rebuild

If you change .env then you have to rebuild the image.

  $ sudo docker-compose up --build --detach
