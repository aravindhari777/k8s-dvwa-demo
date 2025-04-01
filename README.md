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




1)Attack Vectors Demonstration
1.SQL Injection (SQLi):

-->Go to the DVWA login page.
-->Enter the following SQL injection payload into the username field: admin' --
-->Leave the password blank and click login. The application will log in without valid credentials due to the SQLi vulnerability.
-->Cross-Site Scripting (XSS):

2.Go to the XSS stored attack page.

-->Enter <script>alert('XSS!')</script> in the message box and submit.
-->Upon reloading the page, the alert will pop up, demonstrating the XSS vulnerability.
-->Cross-Site Request Forgery (CSRF):

3.Open the CSRF attack page.

-->Use an external form to send a request that changes a user's password without their consent, exploiting the CSRF vulnerability.

2)Mitigation Techniques
1.SQL Injection: Use parameterized queries to prevent SQL injection attacks.
2.Cross-Site Scripting (XSS): Sanitize user input and use Content Security Policy (CSP) to mitigate XSS risks.
3.Cross-Site Request Forgery (CSRF): Implement anti-CSRF tokens in forms to prevent unauthorized requests.

Conclusion
This setup showcases how to deploy the DVWA application on a local Kubernetes cluster using Minikube, providing a platform for security testing and demonstration of common web vulnerabilities. It’s a valuable learning tool for anyone interested in web security.
