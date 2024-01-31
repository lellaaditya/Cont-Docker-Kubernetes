Kubernetes Scenarios

Check Access Issue --follows


if it is web application web server is accessible on the IP of the node port using Curl 

check the service to pod discovery -- running kubectl describe service web-service

endpoints and selectors in kubectl describe and also yaml file make sure they match

check pod
kubectl describe pod web
kubectl logs web -f or kubectl logs web -f --previous
check dependent service
check dependent application
