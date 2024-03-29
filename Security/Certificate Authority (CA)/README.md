## <img src="https://github.com/ShivaniShah06/Kubernetes/raw/main/logos/Certificate.png" width="19"> CERTIFICATE AUTHORITY (CA)

1. CAs are well-known organizations that can sign and validate your certificates for you. Some of the popular ones are Symantec, Digicert, GlobalSign, etcetera
 
2. CAs also use public and private keys to sign the certificates sent by server. All users have CA public key to validate the authenticity of the certificate

3. The admin generates a keypair for securing SSH access to the server, the web server generates a keypair for securing the website with https, the certificate authority generates its own set of keypair to sign the certificates, and the end user only generates a single symmetric key. Once he/she establishes trust with the website, he/she uses his/her password to authenticate to the website

4. Usually certificates with public keys are named with .crt or .pem extensions and private keys are named with .key or server-key.pem extensions

5. 3 types of certificates

     - Server Certificates: Configured on servers
     - Client Certificares: Configured on clients
     - Root Certificates: Configured on the CA servers

6. Clients and servers in Kubernetes

         ![alt text](CA.png)

### Generating Root Certificates

7. Generate keys

       $ openssl genrsa -out ca.key 2048

8. Generate Certificate Signing Request (CSR)
 
        $ openssl req -new -key ca.key -subj "/CN=KUBERNETES-CA" -out ca.csr

9. Sign certificates


        $ openssl x509 -req -in ca.csr -signkey \
        ca.key -out ca.crt

### GENERATING CLIENT CERTIFICATES

#### ADMIN USER CERTIFICATES
10. Generate Keys

          $ openssl genrsa -out admin.key 2048

11. Generate Certificate Signing Request (CSR)
  
          $ openssl req -new -key admin.key -subj "/CN=kube-admin/O=system:masters" -out admin.csr

     NOTE: 
       - Kube Scheduler, Kube Controller Manager, and Kube Proxy are system components so their CN must be prefixed with the keyword SYSTEM. Eg: `SYSTEM:KUBE-SCHEDULER`
       - Nodes are also system components so we need to name them as `system:node:<node_name>` while creating csr. Also, the nodes should be added to a group named `system:node` to ensure that it gets right privileges 

          

12. Sign certificates
  
          $ openssl x509 -req -in admin.csr -CA ca.crt -CAkey ca.key -out admin.crt
* Can add a `--config` flag for kube-apiserver certs as it needs more alternative names. config flag should point to a yaml file which has details about the alternate names - check this for more info: https://github.com/kodekloudhub/certified-kubernetes-administrator-course/blob/master/docs/07-Security/07-TLS-in-Kubernetes-Certificate-Creation.md#kube-apiserver-certificate

13. Alternative names for kube-apiserver

     - kubernetes
     - kubernetes.default
     - kubernetes.default.svc
     - kubernetes.default.svc.cluster.local

### Viewing the certificates

NOTE:
   - If the cluster was setup manually, the components will be created as services and can be found at: `/etc/systemd/system/` location
   - If the cluster was setup using kubeadm, the components will be created as pods and their yaml files can be found at `/etc/kubernetes/manifests/`

14. Get details in the certificate

          $ openssl x509 -in <location_of_the_cert> -text -noout

15. Inspect service logs

      - If the cluster was set manually:

            $ journalctl -u <service_name>.service -l
     
     - If cluster was set using kubeadm:
         
            $ kubectl logs <pod_nam-e>


