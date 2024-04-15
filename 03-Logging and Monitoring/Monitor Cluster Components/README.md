## Monitor Cluster Components

#### How do you monitor resource consumption in kubernetes? or more importantly, what would you like to monitor?
  ![alt text](lom1.png)
 
## Heapster vs Metrics Server
- Heapster is now deprecated and a slimmed down version was formed known as the **`metrics server`**.

  ![alt text](lom2.png)
  
## Metrics Server

  ![alt text](lom3.png)

#### How are the metrics generated for the PODs on these nodes?

  ![alt text](lom4.png)
  
## Metrics Server - Getting Started

  ![alt text](lom5.png)
  
- Clone the metric server from github repo
  ```
  $ git clone https://github.com/kubernetes-incubator/metrics-server.git
  ```
- Deploy the metric server
  ```
  $ kubectl create -f metric-server/deploy/1.8+/
  ```
  
- View the cluster performance
  ```
  $ kubectl top node
  ```
- View performance metrics of pod
  ```
  $ kubectl top pod
  ```
  
  ![alt text](lom6.png)

- There are other options available to list the CPU and memory usage of pods and nodes. Use below command to view options

      $ kubectl top [pods|nodes] -h