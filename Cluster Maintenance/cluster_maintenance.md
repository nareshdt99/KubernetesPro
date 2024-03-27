## :recycle: CLUSTER MAINTANENCE
:diamond_shape_with_a_dot_inside: The time for which the replicaset waits for a pod that is down to come back up is called as "pod-eviction-timeout". It is set on the controller manager with a default value of 5m0s. If the node comes back up after 5 minutes, it comes back blank as pods are considered dead by controller manager after 5 minutes.


