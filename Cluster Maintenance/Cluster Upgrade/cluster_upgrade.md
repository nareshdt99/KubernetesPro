### CLUSTER UPGRADE

1. ETCD Cluster and Core DNS can be on versions higher than other Kubernetes components

2. All the other Kubernetes components except ETCD Cluster and Core DNS also need not be on the same version. The components can be on different release versions. Since kube-apiserver is the primary component in the control plane, none of the other component should ever be at a version higher than the kube-apiserver.
   
   - The controller manager and scheduler can be at one version lower (i.e. 1.9 or 1.10) than kube-apiserver (i.e. 1.10)
   - The kubelet and kube-proxy can be 2 versions lower (i.e. 1.8 or 1.9 or 1.10) than kube-apiserver (i.e. 1.10)
   - kubectl can be one version higher (i.e. 1.11) or one version lower (i.e. 1.9) or the same version (i.e. 1.10) as the kube-apiserver (i.e. 1.10 )

:diamond_shape_with_a_dot_inside:  Steps to upgrade cluster:
Follow documentation at: https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/kubeadm-upgrade/

1. Plan the cluster upgrade and get important information about the same
 
        $ kubeadm upgrade plan

     NOTE: kubeadm does not install or upgrade kubelets

2. Upgrade kubeadm

        $ apt-get upgrade -y kubeadm=<version-00>

3. Upgrade the cluster using the command from the `kubeadm upgrade plan` output:

        $ kubeadm upgrade apply <version>

    NOTE: If you run `kubectl get nodes` command, you will see master still at an old version. This is because we have not upgraded kubelet

4. Upgrade kubelet on the master node if you have kubelet installed there

         $ apt-get upgrade -y kubelet=<version>

5. Restart the service

         $ systemctl restart kubelet
    NOTE: `kubectl get nodes` will now show master on the newer version

6. Now follow below steps on each worker node at a time

     - Drain the node
           
            $ kubectl drain <node_name>
    
    - ssh to the node
      
            $ ssh <node_name>

    - Upgrade kubeadm on the node
     
            $ apt-get upgrade -y kubeadm=<version>
    
    - Upgrade kubelet on the node

            $ apt-get upgrade -y kubelet=<version>

    - Upgrade the node configuration for the new kubelet version

            $ kubeadm upgrade node config --kubelet-version <version>

    - Restart the kubelet service

            $ systemctl restart kubelet
    
    - Uncordon the node

            $ kubectl uncordon <node_name>
    
    - To check the distribution your node is running on

            $ cat /etc/*release*