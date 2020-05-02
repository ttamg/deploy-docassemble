# Development setup

This provides a simple setup for developers on a local machine.

This provides an an alternative to the `docker run` instructions provided in the full **docassemble** documentation.

Note that the `.env` file contains the full container options so that developers to play around with these features locally before deploying remotely.

## Volumes

This setup creates a backup volume that will be placed in the local `volumes` subdirectory. Backup data will persist between sessions. The backup also contains the log files which are useful for debugging.

## Getting started

From this directory, run:

    docker-compose up -d

It takes up to 10 minutes to spawn all the processes first time around. You can try the command without the `-d` tag to see the progress.

Once complete, **docassemble** app will be available on http://localhost:80 or http://127.0.0.1:80

Bring the container down using **Ctrl-C** or `docker-compose down`

## Issues

Note that it takes up to 10 minutes first time round to spawn all the processes. Make a cup of tea.

Got other issues? Try the [docassemble Docker documentation](https://docassemble.org/docs/docker.html)
