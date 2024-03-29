## :satellite: :signal_strength: NETWORK POLICY

1. 2 types of traffic:
    - Ingress - Incoming traffic
    - Egress - Outgoing traffic

2. Not all network solutions support network policies. If you are using a network solution that does not support network policies, you will still be able to create network policies without any errors however, these policies won't be enforced

3. By default, Kubernetes allows all  traffic from all pods to all destinations. To block the traffic, we use `Network Policies`

4. The `kube-dns` service is exposed on port `53`