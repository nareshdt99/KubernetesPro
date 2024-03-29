## :cowboy_hat_face: KUBERNETES COMMON COMMANDS

1. To replace an existing resource with newly updated resource (with the same name):

        $ kubectl replace --force -f <yaml_file_name>

2. To run any command inside a container/pod:

        $ kubectl exec -it <pod_name> <command>

        Example:
        $ kubectl exec -it my-dashboard cat /var/run/secrets/ kubernetes.io/serviceaccount/token
