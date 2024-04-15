## <img src="https://github.com/ShivaniShah06/Kubernetes/raw/main/logos/Networking.png" width="40"> NETWORKING

### NETWORKING COMMANDS CHEAT SHEET

      $ ip link

      $ ip addr

      $ ip addr add <ip-address-with-cidr> dev <interface-name>

      $ ip route

      $ ip route add <ip-we-need-access-to-cidr> via <gateway-ip>

      $ cat /proc/sys/net/ipv4/ip_forward
      1

      $ arp

      $ netstat -plnt # To list what process is listening on what port

      $ route

      $ ip address show type bridge # To list the bridge on host