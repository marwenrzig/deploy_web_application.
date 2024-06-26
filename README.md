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
6. Using Helm for Packaging:
Install Helm: If you haven't already, install Helm on your local machine.

Create Helm Chart: Create a Helm chart for your application. Helm charts are directories containing Kubernetes YAML files and a values.yaml file for configuration.

Structure the Helm Chart: Organize your Helm chart with directories like templates for Kubernetes manifests, charts for dependencies, and values.yaml for default configuration values.

Template Kubernetes Manifests: Use Helm's templating language to parameterize your Kubernetes manifests. You can use placeholders in your YAML files and reference values from the values.yaml file.

## Testing
- Test the application by accessing its URL in a web browser or using tools like curl or Postman.
- Test the scalability by monitoring the number of pods and CPU usage.
- Test the self-healing mechanism by manually deleting a pod and observing Kubernetes recreating it.
- Test the network policy by attempting to access the application from allowed and disallowed sources.
