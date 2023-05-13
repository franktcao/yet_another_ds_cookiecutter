# {{cookiecutter.project_name}}

## Getting Started (DEV)
To setup and install dependencies, run the following command in the project root directory:
```bash
make setup
```
This will install a virtual environment to develop and/or run the app.

### Docker
Use the Docker image as your environment. Check to see if the the `Dockerfile` has all that is needed for development.
To develop, build the `dev` image by running:

```bash
docker compose build dev
```

Now that the image has been built, use

```bash
docker compose up
```

to run the `dev` container
