### OS UPGRADES

1. To drain the node
 
       $ kubectl drain <node_name>

       NOTE: This will delete the pods from the current node and recreate them on other available nodes in the cluster. The current node will also be marked UNSCHEDULABLE.

2. To mark a node schedulable

        $ kubectl uncordon <node_name>

3. To mark a node unschedulable

        $ kubectl cordon <node_name>