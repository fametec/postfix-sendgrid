# postfix-sendgrid

Simple SMTP Relay to Sendgrid


# run

    docker run --rm -d --name postfix \
    -e SENDGRID_USER=postmaster@domain \
    -e SENDGRID_PASS=xxxxxxxxx \
    fametec/postfix-sendgrid 

# docker-compose

    version: '3.2'
    #
    ### Services
    #
    services:
    #
    # SENDGRID
    #
      relay:
        build: .
        image: fametec/postfix-sendgrid:latest
        restart: unless-stopped
        container_name: relay
        ports:
         - "30025:25"
        environment:
         SENDGRID_USER: apikey
         SENDGRID_PASS: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
        volumes:
         - spool:/var/spool/postfix
    volumes:
      spool:

 # testing

    echo "Email Test" | mail -s "This is a simple test" contato@fametec.com.br
 
 
