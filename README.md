# postfix-sendgrid

Simple SMTP Relay to Sendgrid


# RUN

    docker run --rm -d --name postfix \
    -e SENDGRID_USER=postmaster@domain \
    -e SENDGRID_PASS=xxxxxxxxx \
    fametec/postfix-sendgrid 

# DOCKER-COMPOSER

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
         SENDGRID_USER: postmaster@XXXXXXXXXXXXXXXX
         SENDGRID_PASS: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
