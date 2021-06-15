# Nomad Cluster Security

1. What is the Nomad cluster size?
1. Deployment Strategy
    - Is Nomad deployed in a single region or in multiple regions?
    - How is the high availability and failover designed?
    - In case of failover, how is the leader and follower selected?
    - How does the brain-split strategy work?
1. Nomad-Consul connectivity
    - Is Nomad integrated with consul? If yes, how does the DNS resolution work to connect to the Consul cluster?
    - Is it over HTTP secured with TLS?
    - Is there any Consul token to encrypt the traffic?
1. Is there a replication between the Nomad cluster in different regions?
1. Do you have bootstrap Nomad ACL systems?
1. Do you have different tokens generated for authentication to Nomad API's?
1. Do you have policies defined as per user specific to schedule the job to Nomad Cluster?
1. Do you have sentinel policies defined in Nomad clusters?
1. Are you using a vault for secret management? Does your vault have the version support?
1. How are the services isolated in the Nomad cluster?
1. How does database connectivity work in Nomad cluster?
1. How stateful workloads are managed inside the Nomad cluster? How about the permission on persistent storage mounted?
1. Does your Nomad deployment support auto-scaling?
    - How are the resources defined in the Nomad cluster?
    - Does Nomad itself define the resource allocation for the job?
