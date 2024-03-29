## <img src="https://github.com/ShivaniShah06/Kubernetes/raw/main/logos/rbac.png" width="19"> ROLE BASED ACCESS CONTROL

### ROLE AND ROLE BINDINGS
1. Get roles

        $ kubectl get roles

2. Get rolebindings
 
        $ kubectl get rolebindings

3. Describe a role
 
        $ kubectl describe role <role_name>

4. Describe rolebinding

        $ kubectl describe rolebinding <rolebinding_name>

5. Check your own access

        $ kubectl auth can-i create deployments

        $ kubectl auth can-i delete nodes

6. Admin can impersonate other user to validate permissions given using below command option

        $ kubectl auth can-i create deployments --as <user_name>

        $ kubectl auth can-i create deployments --as <user_name> --namespace <namespace_name>

7. Imperative command to create role
  
        $ kubctl create role --help

### CLUSTERROLES
1. To see a full list of namespaced and non-namespaced resources

        $ kubectl api-resources --namespaced=true

        $ kubectl api-resources --namespaced=false

NOTE: We can also create cluster role and cluster role bindings for namespaces. They will have access across all namespaces   