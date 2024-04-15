### :cloud: :arrows_clockwise: BACKUP & RESTORE

1. To take the backup of all the resource configuration files querying kube-apiserver

            $ kubectl get all --all-namespaces -o yaml\
             > all_config_files.yaml

2. To take the backup of the etcd cluster, follow below steps:
    
    - Save the snapshot of the etcd
    
    
          $ ETCDCTL_API=3 etcdctl \
            snapshot save <name_of_the_snapshot> \
            -- endpoints=https://127.0.0.1:2379 \
            -- cacert=<location of ca.crt file> \
            -- cert=<location of server.crt file> \
            -- key=<location of server.key file>
    
    - Check the status of the snapshot

          $ ETCDCTL_API=3 etcdctl \ 
          snapshot status <name_of_the_snapshot> \
          -- endpoints=https://127.0.0.1:2379 \
          -- cacert=<location of ca.crt file> \
          -- cert=<location of server.crt file> \
          -- key=<location of server.key file>

3. To restore the backup from the backup taken in 2nd point, follow below steps:

    - Stop the kube-apiserver service
        
          $ service kube-apiserver stop
    
    - Restore the backup from the snapshot

          $ ETCDCTL_API=3 etcdctl\
          snapshot restore <name_of_the_snapshot>\
          --data-dir /var/lib/etcd-from-backup

          NOTE: This will create a new directory named etcd-from-backup at /var/lib location

    - Configure the etcd configuration file (located at /etc/kubernetes/manifests) to use the new data directory

        - Example etcd.yaml:

              apiVersion: v1
              kind: Pod
              metadata:
                ...
              spec:
                containers:
                - command:
                  - etcd
                  - --data-dir=/var/lib/etcd
                  - ...
                  - ...
                  volumeMounts:
                  - mountPath: /var/lib/etcd
                    name: etcd-data
                  - mountPath: /etc/kubernetes/pki/etcd
                    name: etcd-certs
                volumes:
                - hostPath:
                    path: /etc/kubernetes/pki/etcd
                    type: DirectoryOrCreate
                  name: etcd-certs
                - hostPath:
                    path: /var/lib/etcd
                    type: DirectoryOrCreate
                  name: etcd-data
        - The value for --data-dir and etcd-data named volumeMount should always be same
        - We need to change the value for the path of etcd-data named volume. So, in our case, we change it from:
                
                volumes:
                - ...
                - hostPath:
                    path: /var/lib/etcd
                    type: DirectoryOrCreate
                  name: etcd-data
        to:
         
                volumes:
                - ...
                - hostPath:
                    path: /var/lib/etcd-from-backup
                    type: DirectoryOrCreate
                  name: etcd-data

    - Reload the service daemon

           $ systemctl daemon-reload

    -  Restart etcd service

           $ service etcd restart

    - Start the kube-apiserver service

           $ service kube-apiserver start

4. To check available clusters in current node

        $ kubectl config view

5. To switch the cluster context

        $ kubectl config use-context <cluster_name>

## When external etcd is attached to the cluster

6. You can use below command after doing ssh to the external etcd to see etcd configs

        $ ps -aux | grep etcd

7. You run the same command as mentioned in step 3 after doing ssh to the IP address found in `--etcd-servers` option on kube-apiserver to restore the backup

8. After restoring the backup, go to `/etc/systemd/system/etcd.service` and change the value for `--data-dir` to the new directory created while restoring the backup

9. Update the permissions on the new directory to etcd user recursively

       $ sudo chown -R etcd:etcd <directory-name>

10. Reload the daemon and restart the etcd service

        $ systemctl daemon-reload
        $ service etcd restart