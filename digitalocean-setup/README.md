# DigitalOcean single server setup

[DigitalOcean](https://www.digitalocean.com/) is a popular web hosting alternative to AWS and Azure. It is a cost-effective solution for hosting docassemble apps.

For deployment, DigitalOcean [virtual machines (called 'Droplets') with docker pre-installed](https://marketplace.digitalocean.com/apps/docker) can be spun up quickly and docassemble installed there.

[DigitalOcean Spaces](https://www.digitalocean.com/products/spaces/) are available to store the backups and configuration files. These are S3 compatible and therefore the setup is very similar to the AWS S3 instructions.

This setup uses both a new Droplet and Spaces.

The app is secured using LetsEncrypt SSL certificates.

## Getting started

1.  This assumes you have already set up:

    - a new DigitalOcean Droplet with docker running - can be done with [one click](https://marketplace.digitalocean.com/apps/docker). A USD 10 per month droplet will usually be sufficient to get started with docassemble.

    - a new DigitalOcean Space (i.e. 'S3 bucket') to store the data and an access token - [step-by-step instructions](https://www.digitalocean.com/community/tutorials/how-to-create-a-digitalocean-space-and-api-key)

1.  Log into your Droplet and copy across the `.env` and `docker-compose.yml` file into a new project directory.

1.  Edit the `.env` file to add the settings for for your setup. As a minimum, make sure you set

    - `DAHOSTNAME` to the **domain name**
    - `LETSENCRYPTEMAIL` to your valid email for LetsEncrypt to use.

1.  Edit the `.env` file to add the configuration for the S3 compatible DigitalOcean Space:

    - `S3ENABLE=true`
    - `S3ENDPOINTURL=https://fra1.digitaloceanspaces.com` - or similar for other regions than `fra1`
    - `S3BUCKET=spaces_name` - putting in the name of your Space
    - `S3ACCESSKEY=yourkey` - from the access token
    - `S3SECRETACCESSKEY=yoursecret` - from the access token

1.  Before starting up **docassemble** ensure you have a DNS record for the **domain name** pointing correctly to the **IP address** of the server. Without this, LetsEncrypt may fail to create a valid certificate for you.

1.  Run using:

        docker-compose up -d

## Notes

- In `docker-compose.yml` the **restart** option is set to `always` so that it will attempt to restart if the container goes down.

- For other settings, see the [official documentation on configuration options](https://docassemble.org/docs/docker.html#configuration%20options).
