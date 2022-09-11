# App Node Pintu

This is a simple Node JS application that run on the Docker container.

# Task Explanation

This application is intended to do these requirements:
1. This is a simple application that is built using Node JS.

2. This application repository has a CI/CD pipeline for :
- build : Dockerize the Node JS application into Docker Container and store it in Docker Hub
- test : To test run the built Docker Container

3. This application also has a YAML deployment manifest to deploy it into the Kubernetes Cluster.

4. Regarding the Kubernetes deployment, since I don't have either Kubernetes Cluster, IP Public, or active domain for testing, I provide the deployment manifest instead at file `app-node-deploy.yml`.

# CI/CD Explanation

1. All needed CI variable is set on the repository CI/CD variable on settings :
- CI_REGISTRY : Variable for default container registry URL
- CI_REGISTRY_IMAGE : URL for Docker Image repository
- CI_REGISTRY_USER : Variable for container registry username
- CI_REGISTRY_PASSWORD : Variable for container registry password

2. For the Docker Hub repository URL :
https://hub.docker.com/repository/docker/barihade/app-node-pintu

3. For the Kubernetes Deployment, we just need to run these 2 commands to run the deployment service as Load Balancer :
```
kubectl apply -f app-node-deploy.yml
kubectl expose deployment node-pintu --type LoadBalancer --port 3000
```