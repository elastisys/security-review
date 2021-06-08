# Nomad Cluster Security

1. What is the noamd cluster size?
1. Is Nomad deployed single region or multi-region? What is the deployment strategy? How is the high availability and failover designed? How is leader and follower selected?
1. Is Nomad integrated with consul? How the DNS resolutions works to connect to the consul cluster?
1. How is Nomad to Consul connectivity? Is it over HTTP secured with TLS? And is there any consul token to encrypt the traffic?
1. Is the replication happens between the Nomad cluster in different regions?
1. Does Nomad cluster uses the ACL policies, Tokens and sentinal policies?
1. Do we have bootstrap Nomad ACL systems? it will make sure we have tokens , policies - rules and capabilities
1. Are you using vault for secret management? Is your vault has the version support?
1. How the services are isolated in Nomad cluster?
1. How the database connectivity works in Nomad cluster? How about the permission on persistent storage mounted?
1. What startegy is used for mounting the data directory for statefulsets applications?
1. Is nomand supports auto-scaling? How the resources are defined in the Nomad cluster? Is that Nomad itself defines the resource allocation for the job?
