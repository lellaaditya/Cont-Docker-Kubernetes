# Kubernetes
 
K8s,
- is an Container Orchestration Tool  
- is an open source system for automating deployment, scaling, and management of containerized applications
- on-premises, hybrid, or public cloud infrastructure

Cluster - A cluster is a set of nodes (physical or virtual machines) running Kubernetes agents, managed by the control plane
Pod - 
Node - physical or virtual machines

<img width="918" height="595" alt="image" src="https://github.com/user-attachments/assets/6cb3f983-0751-4657-a9b7-1ee1eb667234" />

# Control plane components

kube-apiserver

etcd

kube-scheduler

kube-controller-manager

cloud-controller-manager

# Node components

kubelet

kube-proxy

Container runtime


kind lets you run Kubernetes on your local computer

minikube is a tool that lets you run Kubernetes locally. minikube runs an all-in-one or a multi-node local Kubernetes cluster on your personal computer (including Windows, macOS and Linux PCs) so that you can try out Kubernetes, or for daily development work

kubeadm tool to create and manage Kubernetes clusters. It performs the actions necessary to get a minimum viable, secure cluster up and running in a user friendly way - Production 

managed Kubernetes service 
- by Microsoft Azure which is Azure Kubernetes Service(AKS)
- by AWS which is EKS
- by Google which is GKE


kubectl is an Kubernetes command-line tool to run commands against Kubernetes clusters


A cluster is a set of nodes (physical or virtual machines) running Kubernetes agents, managed by the control plane. Kubernetes v1.33 supports clusters with up to 5,000 nodes. More specifically, Kubernetes is designed to accommodate configurations that meet all of the following criteria:

No more than 110 pods per node
No more than 5,000 nodes
No more than 150,000 total pods
No more than 300,000 total containers
You can scale your cluster by adding or removing nodes. The way you do this depends on how your cluster is deployed



# Azure Pipelines
CI/CD Process

- stage: Deploy
  displayName: Deploy stage
  dependsOn: Build
  jobs:
  - deployment: Deploy
    displayName: Deploy job
    pool:
      vmImage: $(vmImageName)
    environment: 'myenv.aksnamespace' #customize with your environment
    strategy:
      runOnce:
        deploy:
          steps:
          - task: DownloadPipelineArtifact@2
            inputs:
              artifactName: 'manifests'
              downloadPath: '$(System.ArtifactsDirectory)/manifests'

          - task: KubernetesManifest@1
            displayName: Create imagePullSecret
            inputs:
              action: 'createSecret'
              connectionType: 'kubernetesServiceConnection'
              kubernetesServiceConnection: 'myapp-default' #customize for your Kubernetes service connection
              secretType: 'dockerRegistry'
              secretName: '$(imagePullSecret)'
              dockerRegistryEndpoint: '$(dockerRegistryServiceConnection)'

          - task: KubernetesManifest@1
            displayName: Deploy to Kubernetes cluster
            inputs:
              action: 'deploy'
              connectionType: 'kubernetesServiceConnection'
              kubernetesServiceConnection: 'myapp-default' #customize for your Kubernetes service connection
              manifests: |
                $(Pipeline.Workspace)/manifests/deployment.yml
                $(Pipeline.Workspace)/manifests/service.yml
              containers: '$(containerRegistry)/$(imageRepository):$(tag)'
              imagePullSecrets: '$(imagePullSecret)'
