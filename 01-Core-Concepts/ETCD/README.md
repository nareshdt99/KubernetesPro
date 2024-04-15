## <img src="https://github.com/ShivaniShah06/Kubernetes/raw/main/logos/ETCD.png" width="40">  ETCD

- ETCD is a distributed reliable key-value store that is simple, secure & fast
- When you start **`ETCD`** it will by default listen on port **`2379`**
      
    - The default client that comes with **`ETCD`** is the [**`etcdctl`**](https://github.com/etcd-io/etcd/tree/main/etcdctl) client. You can use it to store and retrieve key-value pairs.
        - To Store a Key-Value pair
        
              $ ./etcdctl put key1 value1
        - To retrieve the stored data
         
              $ ./etcdctl get key1
        
        - To view more commands. Run etcdctl without any arguments
        
              $ ./etcdctl

- The ETCD Datastore stores information regarding the cluster such as Nodes, PODS, Configs, Secrets, Accounts, Roles, Bindings and Others
- Every information you see when you run the kubectl get command is from the ETCD Server

## Explore ETCD
- To list all keys stored by kubernetes, run the below command
  ```
  $ kubectl exec etcd-master -n kube-system -- sh -c "ETCDCTL_API=3 etcdctl --cert=/etc/kubernetes/pki/etcd/server.crt --key=/etc/kubernetes/pki/etcd/server.key --cacert=/etc/kubernetes/pki/etcd/ca.crt get / --prefix --keys-only"
  ```
- Kubernetes Stores data in a specific directory structure, the root directory is the **`registry`** and under that you have various kubernetes constructs such as **`minions`**, **`nodes`**, **`pods`**, **`replicasets`**, **`deployments`**, **`roles`**, **`secrets`** and **`Others`**

## ETCD in HA Environment
   - In a high availability environment, you will have multiple master nodes in your cluster that will have multiple ETCD Instances spread across the master nodes
   - Make sure etcd instances know each other by setting the right parameter in the **`etcd.service`** configuration. The **`--initial-cluster`** option where you need to specify the different instances of the etcd service



