## <img src="https://github.com/ShivaniShah06/Kubernetes/raw/main/logos/Kubeadm.png" width="40"> DEPLOYMENT WITH KUBEADM

- Refer to the documentation here: https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/

  `Disclaimer: Below instructions are based on documentation available on April 02, 2024`  

  Follow these on master node as well as worker nodes:
    - Go to Container Runtime page and install and configure prerequisites
    - Select the Container Runtime of choice. We go with containerd
    - Go to `getting started with containerd` page and click on the option to install it using `apt-get` command
    - Then setup the repository for containerd documentation from apt-get page
    - Check the status of containerd service
         
           $ systemctl status containerd
    - Go to cgroup driver section on containerd documentation
    - Set up appropriate ccgroup driver (cgroupfs is default for containerd. Kubelet and container runtime must always have same cgroup driver). Verify the init system used by your host (grep process with process ID of 1)
        
          $ ps -p 1
    -  If above command outputs systemd, then follow the steps to change cgroup driver for container runtime from documentation
    - Go back to the main documentation and follow instructions to install kubeadm, kubelet, and kubectl


    On master node:
    - Go to `Creating a cluster with kubeadm` documentation: https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/ and start from `Initializing your control-plane node`
    - Follow commands from the output of the first step on the master node to create kubeconfig file and put it in .kube folder
    - Run `kubectl join` command from the output of the first command on each worker node to join the cluster
