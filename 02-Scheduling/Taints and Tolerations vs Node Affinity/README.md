## Taints and Tolerations vs Node Affinity

- Taints and Tolerations do not guarantee that the pods will only prefer these nodes; in this case, the red pods may end up on one of the other nodes that do not have a taint or toleration set.

  ![alt text](tnna1.png)

- As such, a combination of taints and tolerations and node affinity rules can be used together to completely dedicate nodes for specific parts.

  ![alt text](tnna2.png)
  
#### K8s Reference Docs:
- https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration/
- https://kubernetes.io/docs/tasks/configure-pod-container/assign-pods-nodes-using-node-affinity/
