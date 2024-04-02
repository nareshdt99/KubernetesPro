## <img src="https://github.com/ShivaniShah06/Kubernetes/raw/main/logos/DNS.png" width="25"> DNS

Domain Name System is basically giving a meaningful name to your IP address

- Modify the file `/etc/hosts` on the system A if it wants to refer an IP address of system B as DNS like below

       $ cat /etc/hosts
       192.168.1.11    db

- To see hostname of a system

       $ hostname

- You can use this DNS name for any commands like ssh, ping, or curl commands
- Translating host name to ip address is known as `Name Resolution`
- When we have lots of hosts in our network, managing their DNS names in a single file on each of them can become tedious. 
  - So we can have a DNS server which can manage all the DNS names for our hosts
  - We can point all hosts to look up that server if they need to resolve the hostname to  an IP address instead their own /etc/hosts files
  - Every host has a DNS resolution configuration file at `/etc/resolv.conf`. We add an entry to it with the IP address of our DNS server. It will look something like this:
       
         $ cat /etc/resolv.conf
         nameserver     192.168.1.100

    NOTE: You can have multiple nameservers configured on your host 
- A system is able to use `host name to IP mapping` from the `/etc/hosts` file locally as well as from a `remote DNS server`
   - NOTE: If we have an entry with the same DNS name in local `/etc/hosts` file and remote DNS server with different IP addresses, the system first looks at the local file and then the remote server. If it finds an entry in the local file, it never looks at the remote server entry. However, we can change this order by making changes for `hosts` field in `/etc/nsswitch.conf` file

         $ cat /etc/nsswitch.conf
         ...
         hosts:     files dns
         ...

- If you want to configure your system within the same network to refer to each other with just their name and not root and top level domains, you can add an entry in `/etc/resolv.conf`

      $ cat /etc/resolv.conf
      nameserver     192.168.1.100
      search         mycompany.com  prod.mycompany.com

  - `search` field is smart enough to ignore itself when the entire DNS name is used in the command and we can also have multiple entries for search. So if we do `ping web`, the command `ping web.mycompany.com` will be executed in the backend

- Test DNS resolution

       $ nslookup <DNS>

    NOTE: This will not consider /etc/hosts file entry. `nslookup only queries the DNS server`

- Test DNS resolution with more details stored on the server

       $ dig <DNS>

- Default port for a DNS server is `53`