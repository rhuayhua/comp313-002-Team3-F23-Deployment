# JPAS Deployment

Deployment setup for the JPAS app. It runs two Docker containers, a backend and a frontend, using Docker Compose. A Jenkins pipeline is included to automate the deployment.

## Services

| Service         | Image                           | Port   |
|-----------------|---------------------------------|--------|
| `jpas-backend`  | `rhuayhua/jpas-backend:latest`  | `8910` |
| `jpas-frontend` | `rhuayhua/jpas-frontend:latest` | `8501` |

The frontend reaches the backend through the `BACKEND_HOST` environment variable, which is set to `jpas-backend`.

## Requirements

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Jenkins](https://www.jenkins.io/) (optional, only for the pipeline)

## Run locally

```bash
# Pull the latest images
docker pull rhuayhua/jpas-backend
docker pull rhuayhua/jpas-frontend

# Start both services in the background
docker-compose up -d
```

Then open:

- Frontend: http://localhost:8501
- Backend: http://localhost:8910

To stop the services:

```bash
docker-compose down
```

## Deploy with Jenkins

The `Jenkinsfile` defines a pipeline that:

1. Pulls the backend image from Docker Hub.
2. Pulls the frontend image from Docker Hub.
3. Starts the app with `docker-compose up -d`.

To use it, create a Pipeline job in Jenkins that points to this repository. The Jenkins agent needs Docker and Docker Compose installed.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
