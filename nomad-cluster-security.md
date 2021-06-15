# Nomad Cluster Security

1.  What is the nomad cluster size?
2.  Deployment Strategy 
    -  Is Nomad deployed in a single region or multi-region?  
    -  How is the high availability and failover designed?
    -  In case of failover , how is the leader and follower selected?
    -  How does the brain-split strategy work ?
3.  Is Nomad integrated with consul? How does the DNS resolution work to connect to the consul cluster?
4.  Nomad-Consul connectivity 
    -  Is Nomad integrated with consul?If yes,How does the DNS resolution work to connect to the consul cluster?
    -  Is it over HTTP secured with TLS? 
    -  Is there any consul token to encrypt the traffic?
5.  Is the replication between the Nomad cluster in different regions?
6.  Does Nomad cluster use the ACL policies, tokens and sentinel policies?
7.  Do we have bootstrap Nomad ACL systems? It will make sure we have tokens , policies - rules and capabilities.
8.  Are you using a vault for secret management? Does your vault have the version support?
9.  How are the services isolated in the Nomad cluster?
10. How does database connectivity work in Nomad cluster? 
11. How stateful workloads are managed inside the nomad cluster ? How about the permission on persistent storage mounted?
12. Does Nomad support auto-scaling? How are the resources defined in the Nomad cluster? Does Nomad itself define the resource allocation for the job?
