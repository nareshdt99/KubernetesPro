# <img src="https://github.com/ShivaniShah06/Kubernetes/raw/main/logos/Kubernetes.png" width="28"> KUBERNETES


## This repository contains different configuration files for Kubernetes components as well as important commands to work with Kubernetes.

## SECTIONS & SEQUENCE TO FOLLOW

- [01-Core-Concepts](01-Core-Concepts/README.md)
   - [ETCD](01-Core-Concepts/ETCD/README.md)
   - [Kube API Server](01-Core-Concepts/Kube-API-Server/README.md)
   - [Kube Controller Manager](01-Core-Concepts/Kube-Controller-Manager/README.md)
   - [Kube Scheduler](01-Core-Concepts/Kube-Scheduler/README.md)
   - [Kubelet](01-Core-Concepts/Kubelet/README.md)
   - [Kube Proxy](01-Core-Concepts/Kube-Proxy/README.md)
   - [Pods](01-Core-Concepts/Pods/README.md)
   - [ReplicaSets](01-Core-Concepts/ReplicaSets/README.md)
   - [Deployments](01-Core-Concepts/Deployment/README.md)
   - [Namespaces](01-Core-Concepts/Namespaces/README.md)
   - [Services](01-Core-Concepts/Services/README.md)

- [02-Scheduling](02-Scheduling/README.md)
  - [Manual Scheduling](02-Scheduling/Manual%20Scheduling/README.md)
  - [Labels and Selectors](02-Scheduling/Labels%20and%20Selectors/README.md)
  - [Taints and Tolerations](02-Scheduling/Taints%20and%20Tolerations/README.md)
  - [Node Selectors](02-Scheduling/Node%20Selectors/README.md)
  - [Node Affinity](02-Scheduling/Node%20Affinity/README.md)
  - [Taints and Tolerations vs Node Affinity](02-Scheduling/Taints%20and%20Tolerations%20vs%20Node%20Affinity/README.md)
  - [Resource Limits](02-Scheduling/Resource%20Limits/README.md)
  - [DaemonSets](02-Scheduling/Daemonsets/README.md)
  - [StaticPods](02-Scheduling/Static%20pods/README.md)
  - [Multiple Schedulers](02-Scheduling/Multiple%20Schedulers/README.md)

- [03-Logging and Monitoring](03-Logging%20and%20Monitoring/README.md)
   - [Monitor Cluster Components](03-Logging%20and%20Monitoring/Monitor%20Cluster%20Components/README.md)
   - [Managing Application Logs](03-Logging%20and%20Monitoring/Managing%20Application%20Logs/README.md) 

- [04-Application Lifecycle Management](04-Application-Lifecycle-Management/README.md)
   - [Rolling Updates and Rollbacks](04-Application-Lifecycle-Management/Rolling%20Updates%20and%20Rollbacks/README.md)
   - [Commands and Arguments](04-Application-Lifecycle-Management/pod-with-command-and-argument.yaml)
   - [Environment Variables and ConfigMaps](04-Application-Lifecycle-Management/Environment%20Variables%20&%20ConfigMaps/README.md)
   - [Secrets](04-Application-Lifecycle-Management/Secrets/README.md)
   - [Init Containers](04-Application-Lifecycle-Management/InitContainers.yaml)

- [05-Cluster Maintenance](05-Cluster%20Maintenance/README.md)
  - [OS Upgrades](05-Cluster%20Maintenance/OS%20Upgrades/README.md)
  - [Cluster Upgrades](05-Cluster%20Maintenance/Cluster%20Upgrade/README.md)
  - [ETCD Backup & Restore](05-Cluster%20Maintenance/Backup%20and%20Restore%20Clusters/README.md)

- [06-Security](06-Security/README.md)
   - [Authentication](06-Security/Authentication/README.md)
   - [TLS Certificates](06-Security/TLS%20Certificates/README.md)
   - [Certificate Authority (CA)](06-Security/Certificate%20Authority%20(CA)/README.md)
   - [Certificates API](06-Security/Certificates%20API/README.md)
    - [KubeConfig](06-Security/KubeConfig/README.md)
    - [API Groups](06-Security/API%20Groups/README.md)
    - [Authorization](06-Security/Authorization/README.md)
        - [Role Based Access Control](06-Security/Authorization/Role%20Based%20Access%20Control/README.md)
    - [Service Accounts](06-Security/Service%20Accounts/README.md)
    - [Image Security](06-Security/Image%20Security/README.md)
    - [Security Context](06-Security/Security%20Context/README.md)
    - [Network Policy](06-Security/Network%20Policy/README.md)
* [07-Storage](07-Storage/README.md)
   - [Persistent Volumes & Persistent Volume Claims](07-Storage/Volumes/PV%20&%20PVC/README.md)
   * [Storage Classes](07-Storage/Volumes/PV%20&%20PVC/README.md#STORAGE%20CLASSES)
* [08-Networking](08-Networking/README.md)
   - [Prerequisite Concepts](08-Networking/01-Prerequisite%20Concepts/)
   - [Cluster Networking](08-Networking/02-Cluster%20Networking/README.md)
   - [Pod Networking](08-Networking/03-Pod%20Networking/README.md)
   - [CNI in Kubernetes](08-Networking/04-CNI%20in%20Kubernetes/README.md)
   - [DNS in Kubernetes](08-Networking/05-DNS%20in%20Kubernetes/README.md)
   - [Service Networking](08-Networking/06-Service%20Networking/README.md)
   - [Ingress](08-Networking/07-Ingress/README.md)

- [09-Deployment with Kubeadm](09-Deployment%20with%20Kubeadm/README.md)
- [10-Troubleshooting](10-Troubleshooting/README.md)
- [11-Kubectl with JSON queries](11-Kubectl%20with%20JSON%20path%20queries/README.md)
   - [JSONPATH basics](11-Kubectl%20with%20JSON%20path%20queries/JSONPATH%20basics/README.md)


## HELPFUL RESOURCES TO PREPARE FOR KUBERNETES ADMINISTRATION EXAM (HANDS-ON)
- [CKA course on Udemy](https://www.udemy.com/course/certified-kubernetes-administrator-with-practice-tests)
- [Killercoda](https://killercoda.com/cka)
- [Killer Shell CKA Simulator](https://killer.sh/cka)

#### References:

- https://github.com/kodekloudhub/certified-kubernetes-administrator-course/tree/master

- https://kubernetes.io/docs
