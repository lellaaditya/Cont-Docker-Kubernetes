# Kubernetes

K8s is developed by Google

Google open-sourced the Kubernetes project in 2014

Maintain by CNCF

In a production environment, you need to manage the containers that run the applications and ensure that there is no downtime. For example, if a container goes down, another container needs to start

Reasons to choose K8S
1.Container platform scope to single host
2.Auto Healing -> without manual intervention container should start itself
3.Auto Scaling -> scale a workload depending on the current demand of resources . Horizontal scaling means that the response to increased load is to deploy more Pods. This is different from vertical scaling, which for Kubernetes would mean assigning more resources (for example: memory or CPU) to the Pods that are already running for the workload
4.Enterprise level support -> Load Balancer,Firewall,Autoscale,Auto healing and API Gateway

kube-controller-manager

Node controller: Responsible for noticing and responding when nodes go down.
Job controller: Watches for Job objects that represent one-off tasks, then creates Pods to run those tasks to completion.
EndpointSlice controller: Populates EndpointSlice objects (to provide a link between Services and Pods).
ServiceAccount controller: Create default ServiceAccounts for new namespaces.
