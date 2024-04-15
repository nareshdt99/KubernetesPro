## :cowboy_hat_face: KUBERNETES COMMON COMMANDS

1. To replace an existing resource with newly updated resource (with the same name):

        $ kubectl replace --force -f <yaml_file_name>

2. To run any command inside a container/pod:

        $ kubectl exec <pod_name> -- <command>

        Example:
        $ kubectl exec my-dashboard -- cat /var/run/secrets/ kubernetes.io/serviceaccount/token

3. Get pods in a particular namespace

       $ kubectl get pods --namespace kube-system

4. Create any k8s resource

       $ kubectl create -f <yaml_file_name>

5. Delete any k8s object
  
       $ kubectl delete -f <yaml_file_name>

6. Filtering pods by the value of a label

    
       $ kubectl get pods --selector env=dev,bu=finance,tier=frontend
   
7. To check nodes in the cluster
  
       $ kubectl get nodes

8. Create a taint on node01 with key of spray, value of mortein and effect of NoSchedule

        $ kubectl taint nodes node01 spray=mortein:NoSchedule

9. To check taints on a node

        $ kubectl describe node <node_name> | grep Taint

10. To display more information about a pod

        $ kubectl get pods -o wide

11. Get nodes with labels
  
        $ kubectl get node node01 --show-labels
    
12. Apply a label to a node

        $ kubectl label node node01 color=blue

13. Create a deployment

        $ kubectl create deployment blue --image=nginx --replicas=3

14. Get daemonsets

        $ kubectl get [daemonsets|ds]

15. Get all the resources in the cluster from all the namespaces

       $ kubectl get all -A

