# Deploying My Node.js App on Kubernetes

This guide explains how to deploy a simple Node.js web application on Kubernetes.

## Prerequisites
- Kubernetes cluster up and running
- kubectl CLI installed and configured
- Docker installed

## Steps

1. Clone this repository.
2. Build the Docker image:
    ```
    docker build -t my-node-app .
    ```
3. Push the Docker image to a container registry:
    ```
    docker tag node-app marwenrzig/node-app
    docker push marwenrzig/node-app
    ```
4. Apply the Kubernetes resources:
    ```
    kubectl apply -f deployment.yaml
    kubectl apply -f service.yaml
    kubectl apply -f ingress.yaml
    kubectl apply -f autoscalling.yaml
    kubectl apply -f networkpolicy.yaml
    ```
5. Access the application using the external IP provided by the LoadBalancer service or through the defined hostname in the Ingress resource.

## Testing
- Test the application by accessing its URL in a web browser or using tools like curl or Postman.
- Test the scalability by monitoring the number of pods and CPU usage.
- Test the self-healing mechanism by manually deleting a pod and observing Kubernetes recreating it.
- Test the network policy by attempting to access the application from allowed and disallowed sources.
