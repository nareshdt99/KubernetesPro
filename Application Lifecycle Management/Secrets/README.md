## SECRETS
1. Create secrets (imperative way):
  
        $ kubectl create secret generic \
        <secret_name > --from-literal=<key1>=<value1> \
        --from-literal=<key2>=<value2>
    
2. Create secret and input values from a file:

       $ kubectl create secret generic \
       <secret_name> --from-file<path-to-file>

       NOTE: File name could be something like app_secret.properties

3. Create secret (declarative way):
  
       $ kubectl create -f <yaml_file_name>

       NOTE: The secrets in yaml file name should be encoded before adding there

4. Encode secrets to be added to yaml file:
 
       $ echo -n 'password' | base64

       This will give you encoded value for "password" and then you can copy it and paste into yaml file for generating generic secret

5. View secrets:
 
       $ kubectl get secrets

6. Get more information on a secret:

       $ kubectl describe secret <secret_name>

       NOTE: This will show the attributes but will hide values

7. To view encoded values in a secret:
 
       $ kubectl get secret <secret_name> -o yaml

8. Decode encoded values in secret:
 
       $ echo -n '<encoded_value>' | base64 --decode

### NOTES ABOUT SECRETS:
1. If we mount secret as a volume, each attribute in the secret is created as a file with the value of the secret as its content

2.  Secrets are NOT encrypted. They are only encoded. So anyone can lookup the file we created for secret and decode it. Hence we should NEVER push secret objects to source control management tools with other code.

3. Secrets are not encrypted in ETCD.

4. Anyone who is able to create pods/deployments in the same namespace can access the secrets. Hence it is recommended to use role based access control (RBAC) or third-party secret store providers