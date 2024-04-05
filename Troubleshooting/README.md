## :interrobang: :nerd_face: TROUBLESHOOTING


  ### :diamond_shape_with_a_dot_inside: APPLICATION FAILURE
  Assume that we have a database and a web server. They both have their own pods and services
  - Check accessibility to the web service
     
         $ curl http://web-service-ip:node-port
    
  - Check service and see if it has discovered the endpoints for the web port. If not, then make changes to it accordingly
  - Compare the labels on pod and selectors on service. They should match
  - Check if web pod is running. Its status and restarts can give some idea if there is an issue from the application end
       - Check events on the pod
       - Check logs of the application
             
              # To check the logs of the previous pod
              $ kubectl logs <pod-name> -f --previous
  - Check the status of the database service just like we checked web service
  - Check database pod just like web pod
  
  ### :diamond_shape_with_a_dot_inside: CONTROLPLANE FAILURE
  - Check nodes
  - Check pods
  - Check pods in kube-system namespace
  - If controlplane components are deployed as services, then check the service status

        $ service <service-name> status
  
    - kube-apiserver, kube-scheduler, and kube-controller-manager on the master node
    - kubelet and kube-proxy on the worker node/s
  - Check service logs

     - In case of controlplane components that are deployed as pods:

           $ kubectl logs <pod-name> -n kube-system
    - In case of controlplane components that are deployed as services:

           $ sudo journalctl -u <service-name>

  ### :diamond_shape_with_a_dot_inside: WORKER NODE FAILURE
  - Check node status
  - If any of the nodes is "NotReady", then check the `Conditions` field of that node through `kubectl describe` command
  - If the status under `Conditions` of node are `Unknown`, then this indicates a possible loss of the node
  - Check the `last heartbeat time` field to find out the time when the node might have crashed
  - Check for possible CPU or memory and disk space on the node
 
         $ top
         $ df -h
  - Check kubelet status
   
         $ service kubelet status
-  Check kubelet logs

         $ sudo journalctl -u kubelet
- Check the kubelet certificates to make sure that they have not expired, they are part of the right group, and that the certificates are issued by the right Certificate Authority

         $ openssl x509 -in <cert-location> -text
- kubelet config files can be found at `/etc/kubernetes/kubelet.conf` and `/var/lib/kubelet/` folder

### :diamond_shape_with_a_dot_inside: NETWORKING TROUBLESHOOTING
 - Find details about the network plugins in this documentation: https://kubernetes.io/docs/concepts/cluster-administration/addons/#networking-and-network-policy
 - Debug Service issues: https://kubernetes.io/docs/tasks/debug-application-cluster/debug-service/
 - DNS Troubleshooting: https://kubernetes.io/docs/tasks/administer-cluster/dns-debugging-resolution/
   
  

