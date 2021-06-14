# Nomad Cluster Security

1. What is the nomad cluster size?
2. Deployment Strategy 
    -  Is Nomad deployed in a single region or multi-region?  
    -  How is the high availability and failover designed?
    -  In case of failover , how is the leader and follower selected?
    -  How does the brain-split strategy work ?
4. Is Nomad integrated with consul? How does the DNS resolution work to connect to the consul cluster?
5. How is Nomad to Consul connectivity? Is it over HTTP secured with TLS? And is there any consul token to encrypt the traffic?
6. Is the replication happens between the Nomad cluster in different regions?
7. Does Nomad cluster uses the ACL policies, Tokens and sentinal policies?
8. Do we have bootstrap Nomad ACL systems? it will make sure we have tokens , policies - rules and capabilities
9. Are you using vault for secret management? Is your vault has the version support?
10. How the services are isolated in Nomad cluster?
11. How the database connectivity works in Nomad cluster? How about the permission on persistent storage mounted?
12. What startegy is used for mounting the data directory for statefulsets applications?
13. Is nomand supports auto-scaling? How the resources are defined in the Nomad cluster? Is that Nomad itself defines the resource allocation for the job?
