## Deploying docassemble to DigitalOcean

[DigitalOcean](https://www.digitalocean.com/) is a popular web hosting alternative to AWS and Azure. It is a cost-effective solution for hosting docassemble apps.

For deployment, DigitalOcean [virtual machines with docker pre-installed](https://marketplace.digitalocean.com/apps/docker) can be spun up quickly and docassemble installed there.

[DigitalOcean Spaces](https://www.digitalocean.com/products/spaces/) are available to store the backups and configuration files. These are S3 compatible and therefore the setup is very similar to the AWS S3 instructions.

This setup uses both a new Droplet and Spaces.

### Deploy a DigitalOcean Droplet (VM) with docker installed

From your DigitalOcean account dashboard, click to set up a new Droplet (this is the DigitalOcean name for a 'virtual machine').

In the options, go to the Marketplace tab and search for the [docker image](https://marketplace.digitalocean.com/apps/docker). This will spin up a new virtual machine with docker already installed.

A USD 10 per month droplet will usually be sufficient to get started on docassemble.

### Set up a new DigitalOcean Space (S3 compatible)

From the DigitalOcean account dashboard, create a new 'Space' and an access token. DigitalOcean provides a [step-by-step guide](https://www.digitalocean.com/community/tutorials/how-to-create-a-digitalocean-space-and-api-key) for these steps.

Note the URL for this new Space, and the access token as you will need for configuration later.

### Configure docassemble

When deploying docassemble on this new droplet, point the S3 configuration to the DigitalOcean Space you set up.

The URL from your new DigitalOcean Space (e.g. https://spacename.fra1.digitaloceanspaces.com) maps to the `S3` configuration options as follows:

- `S3ENDPOINTURL=https://fra1.digitaloceanspaces.com`
- `S3REGION=` (leave this blank)
- `S3BUCKET=spacename`

Set the `S3ACCESSKEY` and `S3SECRETACCESSKEY` parameters to the access token values, and set `S3ENABLED=true`.

Your S3 configuration should now be complete.
