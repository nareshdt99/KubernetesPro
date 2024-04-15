## :woman_office_worker: AUTHENTICATION
### How to gain access
1. We can have basic authentication set by using static password file or static token file

2. The static password file would look something like this with a csv extention
 
           password,username,userid,group

        NOTE: group is an optional column

3. Add below flag to kube-apiserver options and then restart the service in order for it to take effect

           --basic-auth-file=user-details.csv

4. The static token file would look something like this

           token,username,userid,group

5. Then add a static token file as an option to kube-apiserver like we did for static password file above

           --token-auth-file=user-token-details.csv
