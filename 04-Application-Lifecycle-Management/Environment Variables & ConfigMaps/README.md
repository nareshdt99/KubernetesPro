## :abcd: :1234: ENVIRONMENT VARIABLES AND CONFIGMAPS
1. Create configmap (imperative way):
  
        $ kubectl create configmap \
        <configmap_name> --from-literal=<key1>=<value1> \
        --from-literal=<key2>=<value2>

2. Create configmap and input values from a file:

       $ kubectl create configmap \
       <configmap_name> --from-file<path-to-file>

       NOTE: File name could be something like app_config.properties

3. Create configmap (declarative way):
  
       $ kubectl create -f <yaml_file_name>

4. View configmaps:
  
       $ kubectl get configmaps

5. Describe configmap:

       $ kubectl describe configmap <configmap_name>