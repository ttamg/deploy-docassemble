# Simple production setup on single server

This provides a simple setup for deployment on a single server, probably a cloud virtual machine.

This setup stores all the backups on server itself in persistent storage. See other setups if you want to use AWS or Azure instead.

The app is secured using LetsEncrypt certificates for SSL.

## Getting started

1.  Copy across the `.env` and `docker-compose.yml` file into a new project directory.

1.  Edit the `.env` file to add the settings for for your setup. As a minimum, make sure you set the particular make sure you set the `DAHOSTNAME` to the **domain name**, and `LETSENCRYPTEMAIL` to a valid email for LetsEncrypt to use.

1.  Before starting up **docassemble** ensure you have a DNS record for the **domain name** pointing correctly to the **IP address** of the server. Without this, LetsEncrypt may fail to create a valid certificate for you.

1.  Run using:

        docker-compose up -d

## Notes

- For other settings, see the [official documentation on configuration options](https://docassemble.org/docs/docker.html#configuration%20options).
