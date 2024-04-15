## :lock_with_ink_pen: IMAGE SECURITY

Refer to this documentation to create and add secret to your pod yaml file: https://kubernetes.io/docs/concepts/containers/images/#creating-a-secret-with-a-docker-config

### IMAGE SECURITY

1. Login to private repository

        $ docker login private-registry.io

        Use login credentials

2. Run the image from the private registry

        $ docker run private-registry.io/apps/internal-app

3. Command to create secrets to be passed to the worker nodes

        $ kubectl create secret docker-registry <secret_name> \
        --docker-server= <registry_server_name> \
        -- docker-username= <docker_user_name> \
        -- docker-password= <user_password> \
        -- docker-email= <user_email_address>

### DOCKER SECURITY
1. Run a command with added privileges

        $ docker run --cap-add MAC_ADMIN ubuntu

2. Run a command with dropped privileges

        $ docker run --cap-drop KILL ubuntu

3. Run a command with all the privileges

        $ docker run --privileged

-> Get a list of namespaced resources

        $ kubectl api-resources --namespaced=true

-> Get a list of non-namespaced resources

        $ kubectl api-resources --namespaced=false

-> Get a list of all the resources regardless of namespaced or not

         $ kubectl api-resources
