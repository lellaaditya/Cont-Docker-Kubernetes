# Kubernetes Scenarios
---
Check Access Issue --follows

if it is web application web server is accessible on the IP of the node port using Curl 

check the service to pod discovery -- running kubectl describe service web-service

endpoints and selectors in kubectl describe and also yaml file make sure they match

check pod

kubectl describe pod web

kubectl logs web -f or kubectl logs web -f --previous

check dependent service

check dependent application

---

worker node failure

check node status -- ready/not ready

kubectl describe node worke --- OutofDisk , MemoryPressure , DiskPressure ,
PIDPressure , Ready

check Memory disk space -- top df -h

check service kubelet status

sudo journalctl -u kubelet

check certificates

openssl x509 -in /var/lib/kubelet/workr.crt -text

---

