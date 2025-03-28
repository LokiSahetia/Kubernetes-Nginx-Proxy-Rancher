# Kubernetes-Nginx-Proxy-Rancher
This project demonstrates how to configure Nginx as a reverse proxy for internal services running on a Kubernetes cluster. It sets up a simple Python web server using a Kubernetes deployment and uses Nginx to route external traffic to this internal service.

**Project Structure**:

**Namespace Creation**

A separate namespace prox is created to isolate the application components.

**Python Web Server Deployment**

Deploys a basic Python HTTP server using the http.server module.

Exposes the server on port 8000 using a Kubernetes Service.

**Nginx Configuration with ConfigMap**

ConfigMap stores the Nginx configuration, enabling reverse proxying to the Python server.

Routes all incoming traffic to the internal service endpoint using proxy_pass.

**Nginx Deployment and Service**

Nginx is deployed using a Deployment resource.

ConfigMap is mounted to /etc/nginx/nginx.conf inside the container.

A **NodePort** service exposes Nginx on port **30077**, making it accessible externally.

**Prerequisites**

Kubernetes Cluster

kubectl configured to access the cluster

Steps:
(Terminal)

mkdir gitnginxprox

cd gitnginxprox

git clone https://github.com/LokiSahetia/Kubernetes-Nginx-Proxy-Rancher.git

cd Kubernetes-Nginx-Proxy-Rancher 

kubectl create ns prox

kubectl apply -f nginx-confi.yaml

kubectl apply -f pyweb.yaml

kubectl apply -f nginey.yaml

On your browser, go to localhost:30077
