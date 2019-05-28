## This is a simple hello world app

----

Dockerfile and required application files are available in the base path. 

Kubernetes YAMLs are availale in the manifests folder and can be deployed using kubectl apply -f manifests/ (Make sure ingress is configured with the right domain name and if https needs to be enabled configure the secret with the certificate and key. Also change the image name to the image that you created using the given Dockerfile). 

Basic helm chart is available in the hello-world-chart folder and can be deployed using "helm install --name hello-world hello-world-chart"

----

### Points Considered
  
 -  Multi Stage dockerfile has been used to reduce the image size.
 -  Deployment has been used in order to do rolling update as the downtime should be 0
 -  Readyness probe has added for kuberentes to check when the app is ready
 -  CPU and memory has been configured to same in order to have a Guaranteed QOS Class
 -  Ingress can be confugured and the sample yaml file is provided  
  
### Further Action Points Recommended
 
 -  Use https(can be configured at the ingress controller level, Let's Encrypt is an option for this)
 -  Add liveness probe to the app, so that kubernetes will keep monitoring the app and will restart it if the check fails
 -  Create and use a separate namespace for this app.
