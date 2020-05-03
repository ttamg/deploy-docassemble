# Development setup

A simple **docassemble** set up on your local development machine for trial and development processes.

The app runs on http://localhost or http://127.0.0.1 on port 80.

This setup is _not suitable for deployment_ as it does not use SSL.

## Volumes

This setup creates a backup volume that will be placed in the local `volumes` subdirectory. Backup data will persist between sessions.

## Getting started

1.  Copy across the `.env` and `docker-compose.yml` file into a new project directory.

2.  Run using:

        docker-compose up

    Add the `-d` option to this command if you want **docassamble** to run in the background.

3.  After around 10 mins of initial setup time, the app will be available on http://localhost or http://127.0.0.1 port 80.

4.  Bring the container down using:

        docker-compose down

## Notes

- This setup achieves the same outcome as the simple `docker run` instructions provided in the [official documentation](https://docassemble.org/docs/docker.html#starting), but does so using `docker-compose` instead.

- The `.env` file in this setup contains many more container options than are needed for development. They are included here so that developers can play around with these features locally before deploying remotely.
