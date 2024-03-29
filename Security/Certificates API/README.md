## <img src="https://github.com/ShivaniShah06/Kubernetes/raw/main/Security/API%20Groups/API.png" width="19"> CERTIFICATES API

1. Get certificate signing requests

       $ kubectl get csr

2. Approve certificate signing request

       $ kubectl certificate approve <name_of_certificate>

3. View certificate in yaml format
 
       $ kubectl get csr <name_of_certificate> -o yaml

4. Delete certificate
    
       $ kubectl delete csr <name_of_certificate>

5. Reject certificate
  
       $ kubectl certificate deny <name_of_certificate>