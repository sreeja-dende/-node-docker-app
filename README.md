# Node.js + Docker + Jenkins 🐳

My first CI/CD exercise: a Jenkins pipeline that checks out this repo, installs dependencies, builds a Docker image tagged with the build number and runs it as a container.

![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=flat-square&logo=jenkins&logoColor=white)

## Pipeline (`Jenkinsfile`)

1. Checkout from GitHub
2. `npm install`
3. `docker build`, tagged with `${BUILD_NUMBER}`
4. `docker run -d -p 3000:8080`, so the app is served on http://localhost:3000

## Run locally

```bash
npm install && npm test          # Jest unit tests
docker build -t node-docker-app .
docker run -p 3000:8080 node-docker-app
```

➡️ The extended version, with a Docker Hub push, Kubernetes deployment and GitLab CI, is in **[node-k8s-app](https://github.com/sreeja-dende/node-k8s-app)**.
