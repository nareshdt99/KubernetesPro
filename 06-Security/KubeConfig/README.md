## :gear: KUBECONFIG
Specifies Clusters, Contexts, and Users. The default location is $HOME/.kube/config

1. List clusters, users, contexts, and current context (default from `$HOME/.kube/config` file)
  
        $ kubectl config view

2. List clusters, users, contexts, and current context from a specified file

        $ kubectl config view --kubeconfig=my-custom-config

3. Change context (also reflects in yaml file after running this)
         
         $ kubectl config use-context <context_name>

4. Make other changes to the config file using other commands

         $ kubectl config -h