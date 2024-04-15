## SERVICE NETWORKING

1. You rarely configure your pods to directly communicate with each other. Ideally, they do that by using services
2. Types of services:
    1. ClusterIP:
         
         - Service created on a pod can be accessed by any pod in the cluster because services are hosted across the cluster. But this service is only accessible from within the cluster
    2. NodePort:

          - It works similar to ClusterIP i.e. all the other pods in the cluster can access it using the IP assigned to it but it also exposes the application on a port on all nodes in the cluster. So, external users will have access of the service 
          - Is managed by kube-proxy. There are 3 modes in which kube-proxy can be managed: userspace, ipvs, and iptables. It defaults to iptables. You can set it while configuring the kube-proxy:

                $ kube-proxy --proxy-mode [userspace | ipvs | iptables] ...
- To see the rules created by kube-proxy

      $ iptables -L -t nat | grep <service-name>
- Find kube-proxy logs (the location may vary based on the installation and so you must check  verbosity level of the process)

      $ cat /var/log/kube-proxy.log

- Find ip range for pods in the cluster

      $ kubectl logs -n kube-system <weave-pod> weave

      Look for `ipalloc` in the logs

- Find ip address range for the services in the cluster

      $ cat /etc/kubernetes/manifest/kube-apiserver

      Look for `service-cluster-ip-range`

- To check what type of proxy is being used by kube-proxy

      $ kubectl logs -n kube-system <kube-proxy-pod> 

      