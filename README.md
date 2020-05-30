# Quick Start Digital Certificate

Create free digital (SSL/TLS) certificates from [Let’s Encrypt](https://letsencrypt.org/) using
[Certbot with Docker](https://certbot.eff.org/docs/install.html#running-with-docker).
These certificates are not self-signed and can be used in production.

A Let’s Encrypt certificate expires after 90 days, so it needs to be renewed before its expiry.

## Quick Start

   1. Run the follow command to create a free certificate using
[Certbot with Docker](https://certbot.eff.org/docs/install.html#running-with-docker).
Replace the follow variables:
        * REPLACE_ME_DOMAIN: The domain to obtain a certificate for. Use multiple -d flags for 
        multiple domains.
        * REPLACE_ME_EMAIL: The email address for important account notifications.
        * REPLACE_ME_KEY_SIZE: The size of the RSA key.

        ```bash
        docker run -it --rm -v "$PWD/etc/letsencrypt:/etc/letsencrypt" certbot/certbot certonly \
            --agree-tos \
            -d REPLACE_ME_DOMAIN \
            --email REPLACE_ME_EMAIL \
            --manual \
            --manual-public-ip-logging-ok \
            --no-eff-email \
            --preferred-challenges dns \
            --rsa-key-size REPLACE_ME_KEY_SIZE
        ```

2. Certbot will prompt to add a TXT record to your DNS provider.

    ```bash
    - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
    Please deploy a DNS TXT record under the name
    _acme-challenge.REPLACE_ME_DOMAIN with the following value:
    
    v4zLP5vWO0934Qx3KArcBN8B7jSw0j0iY7cokHuXGE
    
    Before continuing, verify the record is deployed.
    - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
    Press Enter to Continue
    ```

3. Add the TXT record and press enter to start verification.

    ```bash
    Waiting for verification...
    Cleaning up challenges
    
    IMPORTANT NOTES:
     - Congratulations! Your certificate and chain have been saved at:
       /etc/letsencrypt/live/REPLACE_ME_DOMAIN/fullchain.pem
       Your key file has been saved at:
       /etc/letsencrypt/live/REPLACE_ME_DOMAIN/privkey.pem
    ```

4. Find the certificate, chain and private key at `$PWD/etc/letsencryptlive/REPLACE_ME_DOMAIN/`.