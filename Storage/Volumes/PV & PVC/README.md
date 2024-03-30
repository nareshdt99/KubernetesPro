## <img src="https://github.com/ShivaniShah06/Kubernetes/raw/main/logos/PV.png" width="19"> PERSISTENT VOLUMES AND PERSISTENT VOLUME CLAIMS

### :package: PERSISTENT VOLUMES (PV)
 - Used to manage storage centrally
 - Cluster-wide pool of storage volumes configured by admins to be used by users deploying applications on the cluster
 - Are created by admins to configure pool of storage volumes
 - Documentation: https://kubernetes.io/docs/concepts/storage/persistent-volumes/

 ### :package: PERSISTENT VOLUME CLAIMS (PVC)
  - Users can select storage from pool of storage volumes (persistent volumes) using Persistent Volume Claims
  - Are created by users to access storage volumes
  - Documentation: https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims

:diamond_shape_with_a_dot_inside: Every PVC is bound to a single PV

:diamond_shape_with_a_dot_inside: If we want to bind our PVC to a specific PV, we can use labels (in PV) and selectors (in PVC) to do so

:diamond_shape_with_a_dot_inside: There is 1-1 relationship between PVC and PV so no other PVC can claim the remaining volume of an already claimed PV

:diamond_shape_with_a_dot_inside: To get PVC and PV

    $ kubectl get persistentvolume|persistentvolumeclaim

:diamond_shape_with_a_dot_inside: To delete the PV or PVC

    $ kubectl delete persistentvolume|persistentvolumeclaim

## :package: STORAGE CLASSES
  - In order for PV to work, we need to first manually create the gcp disk or aws bucket (as per your use case) for it to use before creating it. This is called as Static provisioning
  - With Storage Classes, we can define a provisioner such as google storage which will automatically provision storage on google cloud and attach it to your PVC
  - Storage Class provisioner will automatically create the disk or bucket as per requirement, create a PV for you and then bind your PV with the PVC which can be used in pods
