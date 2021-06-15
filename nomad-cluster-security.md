# Nomad Cluster Security

1.  What is the nomad cluster size?
2.  Deployment Strategy 
    -  Is Nomad deployed in a single region or multi-region?  
    -  How is the high availability and failover designed?
    -  In case of failover , how is the leader and follower selected?
    -  How does the brain-split strategy work ?
4.  Is Nomad integrated with consul? How does the DNS resolution work to connect to the consul cluster?
5.  How is Nomad to Consul connectivity? Is it over HTTP secured with TLS? And is there any consul token to encrypt the traffic?
6.  Is the replication between the Nomad cluster in different regions?
7.  Does Nomad cluster use the ACL policies, Tokens and sentinel policies?
8.  Do we have bootstrap Nomad ACL systems? It will make sure we have tokens , policies - rules and capabilities.
9.  Are you using a vault for secret management? Does your vault have the version support?
10. How are the services isolated in the Nomad cluster?
11. How does database connectivity work in Nomad cluster? How about the permission on persistent storage mounted?
12. Does Nomad support auto-scaling? How are the resources defined in the Nomad cluster? Nomad itself defines the resource allocation for the job?
