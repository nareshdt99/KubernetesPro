## <img src="https://github.com/ShivaniShah06/Kubernetes/raw/main/logos/docker.png" width="38"> DOCKER NETWORKING

- 3 types of docker networking:
   - None: 
       - Not attached to any network
       - No container can reach each other
       - Outside world cannot reach the container and vice-versa
   - Host:
      - No network isolation between the host and the container
      - If your app runs on port x on the container, it will be available on the same port on the host but if we try to run another application from another container on the same host, it will not work  
   - Bridge:
      -  This uses concept similar to what has been explained in Network Namespace
      - An internal private network called `Bridge` will be created on the host to which the docker containers attach to
      - List networks:
           
            $ docker network ls

- To forward traffic from one port to another on a host
 
         $ iptables \
                 -t nat \
                 -A PREROUTING \
                 -j DNAT \
                 --dport <host-port>> \
                 --to-destination <container-port>

- List rules in iptables

         $ iptables -nvL -t nat
