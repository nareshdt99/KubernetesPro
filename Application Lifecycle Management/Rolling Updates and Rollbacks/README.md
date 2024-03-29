## :arrows_counterclockwise: :leftwards_arrow_with_hook: ROLLING UPDATES AND ROLLBACKS
1. Check rollout status


       $ kubectl rollout status deployment <deployment_name>

2. Check rollout history

       $ kubectl rollout history deployment <deployment_name>

3. 2 strategies for deployment:
   
        1. Recreate 
        2. RollingUpdate --> default

4. Trigger a rollout

        $ kubectl apply -f <yaml_file_name>

5. Trigger a rollout by changing image from command

        $ kubectl set image deployment <deployment_name> <container_name>=<image_name>

        NOTE: This command will make direct changes to cluster. The yaml file will not get updated

6. Roll back a deployment

        $ kubectl rollout undo deployment <deployment_name>