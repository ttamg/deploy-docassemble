# Simple production setup on single server

This provides a simple setup for deployment on a single server, probably a cloud virtual machine.

By default, this setup will store the backups and configuation files in a persistent storage volume on the local server.

See the additional steps below if you also want to connect the backups and configuration to your AWS S3 storage.

The app is secured using LetsEncrypt SSL certificates.

## Getting started

1.  Copy across the `.env` and `docker-compose.yml` file into a new project directory.

1.  Edit the `.env` file to add the settings for for your setup. As a minimum, make sure you set

    - `DAHOSTNAME` to the **domain name**
    - `LETSENCRYPTEMAIL` to your valid email for LetsEncrypt to use.

1.  If using AWS S3 or DigitalOcean Spaces storage (_skip this step if not_) edit the `.env` file to add your S3 or Spaces configuration

    - Set `S3ENABLE=true`
    - Set the other `S3...` configuration options
    - For more information, check out the [**docassemble** S3 documentation](https://docassemble.org/docs/docker.html#persistent%20s3).

1.  Before starting up **docassemble** ensure you have a DNS record for the **domain name** pointing correctly to the **IP address** of the server. Without this, LetsEncrypt may fail to create a valid certificate for you.

1.  Run using:

        docker-compose up -d

## Notes

- In `docker-compose.yml` the **restart** option is set to `always` so that it will attempt to restart if the container goes down.

- For other settings, see the [official documentation on configuration options](https://docassemble.org/docs/docker.html#configuration%20options).
