## CONTAINER NETWORKING INTERFACE (CNI)

- CNI is a set of standards that define how programs should be developed to solve networking challenges in a container runtime environment. The programs are referred to as plugins

- CNI defines how the plugins should be developed and how container runtimes should invoke them

- CNI defines a set of responsibilites for container runtimes and plugins. As long as the container runtimes and plugins adhere to these standards, they can all move together in harmony

- Docker does not implement CNI. It has its own set of standards known as Container Network Model (CNM). If we want to use network solutions that implements CNI on docker, then follow below:
         
        # Create a docker container with none network
        $ docker run --network=none nginx
  
        # Manually invoke the bridge plugin (that follows CNI)
        $ bridge add <container-id> <network-namespace-location>



