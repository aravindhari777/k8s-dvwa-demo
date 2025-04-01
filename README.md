# Kubernetes DVWA Demo

This is a demo for deploying **DVWA (Damn Vulnerable Web Application)** on a **Minikube** Kubernetes cluster.

## Prerequisites
- **Minikube** installed on your local machine.
- **kubectl** installed to interact with Kubernetes.

## Setup and Run

1. Start Minikube:
    ```cmd
    minikube start --driver=docker
    ```

2. Create the Kubernetes namespace:
    ```cmd
    kubectl create namespace dvwa
    ```

3. Apply the MySQL deployment:
    ```cmd
    kubectl apply -f mysql-deployment.yaml -n dvwa
    ```

4. Apply the DVWA deployment:
    ```bash
    kubectl apply -f dvwa-deployment.yaml -n dvwa
    ```

5. Apply the DVWA service:
    ```cmd
    kubectl apply -f dvwa-service.yaml -n dvwa
    ```

6. Access the DVWA application via Minikube service:
    ```cmd
    minikube service dvwa-service -n dvwa --url
    ```

## Attack Vectors

1. **SQL Injection**: Demonstrates SQL injection vulnerability.
2. **Cross-Site Scripting (XSS)**: Demonstrates XSS vulnerability.
3. **Cross-Site Request Forgery (CSRF)**: Demonstrates CSRF vulnerability.
