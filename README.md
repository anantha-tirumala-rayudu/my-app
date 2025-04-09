# Simple Jenkins CI/CD Pipeline Project

This project demonstrates a basic CI/CD pipeline using Jenkins and Docker.

## How It Works

- **Jenkinsfile** defines the CI/CD pipeline.
- **Dockerfile** builds a Node.js app container.
- **app.js** is a simple HTTP server.
- **package.json** handles Node.js dependencies.

## Pipeline Stages

1. **Clone** - Clones the repo
2. **Build** - Builds Docker image
3. **Test** - Runs a basic curl test
4. **Deploy** - Deploys containerized app

## Run Locally

```bash
docker build -t simple-node-app .
docker run -p 3000:3000 simple-node-app
```

Access at: `http://localhost:3000`

## License

MIT