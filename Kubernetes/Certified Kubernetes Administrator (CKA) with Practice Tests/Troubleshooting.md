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

---

ImagePullBackOff -- Invalid Image / invalid tag / invalid permission

---

Image pulled but pod is pending
 resourcequota on namespace?
 requests and limits set?
node or nodes lacks resources?
also check the kube-scheduler component

kubectl describe
kubectl logs
if not imagepullbackoff

kubectl get events

---

crashloopbackoff

occurs when runtime configuration is not working

How to detect a CrashLoopBackOff in your cluster?

kubectl get pods

common reasons for crashloopbackoff

Actual Application
misconfiguration: type in config file
resource is not available: persistentvolume not mounted
wrong command line arguments: either missing or incorrect
bugs&exceptions: specific to application

network and permission

tried to bind an existing port
memory limits are too low -- out of memory killed
errors in livenessprobes are not reporting the pod as ready
read-only filesystesm or lack of permissions in general

check
 --- kubectl describe pod
     kubectl logs
     kubectl get events
     kubetcl describe deployment

---


