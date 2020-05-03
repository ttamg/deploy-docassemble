# deploy-docassemble

A set of **docker-compose** template setups for deploying docassemble. Each template configuration is held in a separate directory. Choose the one most relevant for your use case.

## Why use docker-compose?

The base documentation for **docassemble** outlines how to [deploy using a docker container](https://docassemble.org/docs/docker.html). These instructions include using `docker run` on the container to deploy the application. This is great for testing and fine for deployment too.

However, we prefer to use **docker-compose** for production deployments. There are a couple of advantages to this approach:

- The **docassemble** run settings are contained in the `docker-compose.yml` file and the `.env` file. These can be easily maintained and managed using a git repo.

* For more complex setups, other containers can be orchestrated alongside the **docassemble** container using **docker-compose** For example, adding an additional **nginx** proxy to enable multiple web apps to run concurrently on the same machine.

If you like the simple `docker run` then stick with it.

But if you prefer **docker-compose** then this repo may be a helpful timesaver.

## Getting started

1.  Select the template setup that best suits your use case. Each folder is a separate setup. See the **README.md** file in each folder for more information.

1.  Tweak the `.env` and the `docker-compose.yml` files to your requirements.

1.  Spin up **docassemble** in the background using:

        docker-compose up -d

1.  Note that **docassemble** deployment is very slow for the first deployment. It can take up to 10 minutes before the app is up and running. Be patient and make a cup of tea.

1.  If you need to debug your deployment, try running `docker-compose up` without the `-d` option in order to see the console output. Or alternatively, [hop onto the container](https://docassemble.org/docs/docker.html#troubleshooting) as per the **docassemble** documentation and look at the logs.

1.  To bring down the containers cleanly and stop your app, use:

        docker-compose down

## Configuration templates

Each template configuration is held in a separate sub-directory.

- [**Development setup**](https://github.com/ttamg/deploy-docassemble/tree/master/development-setup) - this spins up a simple development server version of **docassemble** in the same way as outlined in the documentation, but using **docker-compose**.

- [**Simple production setup**](https://github.com/ttamg/deploy-docassemble/tree/master/simple-production-setup) - this creates a single server deployment setup, using LetsEncrypt for SSL. By default it stores the backup and configuration data in a persistent volume on the server itself. It also contains instructions on how to easily attach to S3 or Azure Blob storage.

- [**DigitalOcean setup**](https://github.com/ttamg/deploy-docassemble/tree/master/digitalocean-setup) - this creates a single server deployment setup on DigitalOcean using LetsEncrypt for SSL. It also uses a DigitalOcean Spaces 'bucket' for S3 storage to persist the backup and configuration.

## Contributing

Pull requests are welcomed for **improvements to configurations, documentation or bug fixes**.

If this repo is useful, we are also happy to receive **other useful template configurations**. Please follow the same structure for each setup if possible to keep things neat and easy to understand.

## Links

Check out the official documentation for this fantastic package:

- **docassemble** GitHub repo: https://github.com/jhpyle/docassemble
- **docassemble** full documentation: https://docassemble.org/

## Questions

For questions on **docassemble** please direct those to the main **docassemble** community. In particular there is a great [Slack community](https://join.slack.com/t/docassemble/shared_invite/enQtMjQ0Njc1NDk0NjU2LTUyOGIxMDcxYzg1NGZhNDY5NDI2ZTVkMDhlOGJlNTgzZTUwYzNhYTJiMTJmMDYzYjQ0YWNmNjFiOTE5NmQzMjc) providing support and answering questions.
