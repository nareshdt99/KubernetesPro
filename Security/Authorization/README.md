## :clipboard: AUTHORIZATION

#### Once access has been gained, what can a user or a machine do with that access is defined by authorization

1. Different types of Authorization Mechanisms:

      - Node:
          - Node Authorizer for Kubelet to provide required privileges to read from and write to kube-apiserver
      - Attribute Based Access Control (ABAC)
          - You associate a user or a group of users with a set of permissions
          - You do this by creating a policy file with a set of policies defined in a json format and pass this file into the apiserver
          - Everytime you want to make changes in the security, you must edit this policy file manually, and restart the kube-apiserver and so these are difficult to manage
      - Role Based Access Control (RBAC)
          - We define a role with required permissions for a role and then associate respective users to this role
          - If we need to make changes to the permissions, we only need to modify the role
      - Webhook
          - Used to manage authorization externally and not by using built-in mechanisms
2. Authorization Modes:

    - AlwaysAllow (set by default) - allows all requests without performing any authorization checks  
    - AlwaysDeny - denies all requests
    - Node
    - ABAC
    - RBAC

    NOTE: 
    - Authorization Modes are set using `--authorization-mode` option on kube-apiserver
    - Example:
        - `--authorization-mode=Node,RBAC,Webhook` will apply modes in order they are specified
        
        


       
