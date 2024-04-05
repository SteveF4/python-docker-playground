# python-docker-sandbox

A simple Python app for [Docker's Python Language Guide](https://docs.docker.com/language/python).

Includes docker containers:
- py-svc (Python)
- postgres (database)

Start with `docker compose up --build`


## Docker

This project contains a `Dockerfile` to build the Docker container, and a `compose.yaml` for Docker Compose.

### Dockerfile

This is used to build a local Docker container for local use. 

You can leave the Dockerfile in your project. OpenShift does not use the Dockerfile directly when deploying applications. Instead, it uses a concept called Source-to-Image (S2I) to build container images from your source code.

However, OpenShift can also build images directly from a Dockerfile if you want it to. This is done by creating a BuildConfig that references the Dockerfile. If you don't create such a BuildConfig, OpenShift will ignore the Dockerfile.

So, you can continue to use the Dockerfile for local development and testing, while OpenShift uses its S2I process (or a Dockerfile-based BuildConfig if you create one) for deployments.

### compose.yaml

This is for Docker Compose to create multiple containers locally to run different products.

OpenShift does not natively support Docker Compose files. If you want to deploy your application to OpenShift, you will need to convert your docker-compose.yaml file to Kubernetes manifests (such as Deployment, Service, and PersistentVolumeClaim resources).

You can use a tool like Kompose to automate this conversion. Kompose can take a Docker Compose file and convert it into Kubernetes or OpenShift artifacts.

However, you can certainly leave the docker-compose.yaml file in your repository. It will not interfere with OpenShift, and you can continue to use it for local development and testing. Just remember that it won't be used when you deploy your application to OpenShift, unless you manually convert it to the appropriate format.