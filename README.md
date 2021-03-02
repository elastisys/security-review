## Kubernetes Information Security Review Checklist


## Governance, risk management, and compliance

1. What regulations / information security standards do you need to comply with?


    1. ☐ FFFS 2014:7
    2. ☐ SOC-2
    3. ☐ PCI-DSS
    4. ☐ ISO 27001
    5. ☐ HIPAA
    6. ☐ Swedish HealthCare
    7. ☐ GDPR
    8. Other


2. Who/what role in your organisation is responsible for compliance?


3. Does your organization have general information security policies outside of your compliance requirements in place? (e.g., “We need to store data in Brazil to appeal to national sentiments.”)


### Mapping of Standards to Policies

What policy statements do you have in place to show your compliance with the above standard(s)?


### Mapping of Policies to Implementation



1. How do you track implementation? 


2. What is your development/implementation methodology?


    1. How do you take high level policy requirements and create implementable units of work?



3. How do you track and plan implementation/development? 


### Evidence of Implementation fulfilling Policies


1. When a policy is implemented how is this validated?


2. Is this validation recorded?


3. Can an auditor access this record?


## High-Level General Practices


### Supply Management



1. Who supplies your Kubernetes cluster(s) infrastructure today?


2. Is the underlying cloud providers infrastructure in line with your compliance requirements?


3. Are the underlying VMs / load-balancers / storage sufficiently protected? (e.g., via firewalls)


4. Is your Kubernetes cluster connected to any managed services? (e.g., database-as-a-service, logging-as-a-service, incident-management-as-a-service)


### Separation of testing and production



1. Do you separate testing from production clusters?


2. Do you take production data into testing?


3. What is your source of test data?


4. Is your testing infrastructure sufficiently protected?


### Access Control



1. Describe your access control system for Kubernetes?


2. Is multi-factor authentication enabled?


3. How many people have access to the production Kubernetes cluster?


    1. Is role based access implemented? (Read-only, Read-Write)



4. Do you have one user account per person?


5. Do you keep an audit trail on Kubernetes API access?


6. Is the audit trail stored in a tamper-proof logging[^1] environment?


7. Do you regularly review access, e.g., revoking access to people leaving your organization?


### Logging



1. Do you forward nodes (journald), Kubernetes (API server) and application logs to a tamper-proof logging environment?


2. What is your retention policy? What is the minimum amount of time you keep logging entries? What is the maximum amount of time you keep logging entries?


    1. Source of retention policy? Specified in legislation or company policy?  If company policy, why that figure?



### Backups



1. Do you perform regular backups of your production Kubernetes clusters?


2. Do you regularly test restoring from backups?


### Change Management



1. What is the journey of code changes? (e.g., How does a new feature make it into production?)


2. What is the journey of infrastructure changes? (e.g., How do you create a new Kubernetes cluster? How do you update a SecurityGroup?)


3. What is the journey of data changes? (e.g., How do you add a new column to your database?)


4. Do you enforce a 2-person policy for performing system changes?


5. Do you use [semantic versioning](https://semver.org/) for container image tags?


6. How do you perform data migration?


7. In the event of a ‘bad’ deployment, can you rollback to a previous good state?


8. Is this rollback ability tested regularly?


9. Do you do Canary deployments?


### Technical Vulnerability Management



1. Do you scan containers for vulnerabilities before entering production?


2. Do you have a process in place to get alerted when a container becomes vulnerable in production?


3. Do you enforce deployment only from known-good container image registries?


4. After how much time do you fix known container image vulnerabilities?


5. Is the production Kubernetes cluster updated, as required to avoid vulnerabilities?


6. Is the underlying OS image updated, as required to avoid vulnerabilities?


7. Are other adjacent services (e.g., container registry, logging environment, identity provider) updated, as required to avoid vulnerabilities?


### Use of Cryptography



1. Do you encrypt traffic over open networks? Do you use HTTPS over the Internet?


2. Do you regularly rotate cryptographic keys?


3. Do you use HSTS[^2]?


### Network Segregation



1. Do you have NetworkPolicies in place?


### Intrusion Detection / Prevention



1. Do you have an intrusion detection system in the Kubernetes cluster?


2. Do you have a web application firewall in front or within the Kubernetes cluster?


3. Do you alert on blocked outbound traffic?


### Business Continuity



1. Are your systems designed with sufficient redundancy? (e.g., multiple availability zones, multiple Kubernetes nodes, multiple Pod replicas)


2. Do you regularly test your redundancy? (e.g., by failing a Kubernetes node and killing a Pod replica)


3. Do at least two team members have access to each system?


### Incident Management



1. Are your systems sufficiently documented for incident management?


2. Do you have a clear definition of what is an incident?


3. Does your team have clear procedures for who handles incidents and how to handle incidents?


4. Are there situations where you need to fix data in a production environment?


    1. If yes, what is your process?



#### Incident reporting: Internal



1. How do internal users report incidents?


2. Is there an escalation process in place if an incident is not responded to in time?


#### Incident reporting: External



1. How do external users report incidents?


2. Is there an escalation process in place if an incident is not responded to in time?


## Kubernetes Cluster Security



1. Does your cluster pass the [CIS Kubernetes security benchmark](https://github.com/aquasecurity/kube-bench)?


2. Do you have RBAC enabled?


3. Do you use PodSecurityPolicy?


4. Do you use OpenPolicyAgent?


## Kubernetes Workload Security



1. Do you enforce appropriate Pod SecurityContext?


    1. Do you enforce no privileged Pods?
    2. Do you enforce minimum Pod capabilities?
    3. Do you enforce no Pods running as root?
    4. Do you enforce no Pod sysctls?
    5. Do you enforce no hostPath-s?
    6. Do you enforce no nodePort / host network?



2. Do you enforce no [automountServiceAccountToken](https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/)?


3. Do you enforce Pod resource limits?


4. Do you enforce minimum Pod replication?


5. Do you enforce a read-only Pod file system?


6. Are all Pods properly labeled?


7. Are Pod container images pinned to a specific version (i.e., no “latest”)?


8. Do you use Secrets appropriately?


9. Do you restrict access to Secrets?


10. Do you enforce Ingress TLS?


11. Do you have sufficient and tested NetworkPolicies in place?


12. Did you run through other [Kubernetes Best Practices](https://learnk8s.io/production-best-practices)?


## Kubernetes Development Practices



1. How is a container image built?


2. How is a container image deployed into the Kubernetes cluster?


3. How do you manage Kubernetes resources? (e.g., Helm)


4. Do you practice GitOps[^3]?


5. Do you fully separate development from production environments?


6. Is there a fully separate environment for testing/QA?


### Development Environment


#### Access control



1. How is access managed to this environment? (Role based, per user etc)


2. Describe your source control systems and process


### Testing/QA Environment


#### Access control



1. How is access managed to this environment? (Role based, per user etc)


#### Test data



1. How is test data created/sourced?


2. Does data come from production data?


    1. If yes, is it anonymised?



### Production Environment


#### Access control



1. How is access managed to this environment? (Role based, per user etc)


### Code/build Deployment


##### Kubernetes



1. Describe your pod deployment process


2. What checks do you carry out on pods at deployment time?


##### Volume mounts/Data sources



1. Describe your deployment/update process for data sources.


2. Is your data persistence layer built using the Infrastructure as code paradigm?


3. Is your data persistence layer version controlled?


#### Permissions


##### Automated/manual system


## Kubernetes Operational Practices


### Health Checks



1. Do you maintain KPIs for determining if your Kubernetes cluster is working well? (e.g., USE: utilization, saturation, errors)


2. Do you have relevant alerts in place?


3. Do you have alerts for “slowly filling and getting full”? (e.g., disk space)


4. Do you require [Liveness, Readiness and Startup Probes](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/)?


### Operational Logging and Alerts



1. Do you have relevant alerts in place?


2. Do you have a defined process for handling alerts?


3. What is the retention period for these logs?


#### SLA’s/SLO’s management



1. Do you maintain KPIs for determining if your users are served well? (e.g., daily active users, log-ins per day, registrations per day)


2. Do you maintain KPIs for determining if your application is working well? (e.g., RED: request rate, error rate, duration)


#### Path to resolution

Describe the chain of events from an alert/issue raised to resolution


### Security Logging and Alerts



1. Do you have relevant alerts in place?


2. Do you have a defined process for handling alerts?


3. What is the retention period for these logs?


#### Triage



1. Do you have processes and systems in place for evaluating security incidents? (Info, Low, Medium, High, Critical)


2. Do you have processes and systems in place for informing/alerting external shareholders of relevant incidents? (Data leaks, System availability etc)


#### Path to resolution

Describe the chain of events from an alert/issue raised to resolution


<!-- Footnotes themselves at the bottom. -->
## Notes

[^1]:
     By “tamper-proof” it is understood that a person gaining (authorized or unauthorized access) to the production Kubernetes cluster cannot modify or delete existing log entries.

[^2]:
     https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security

[^3]:
     By “GitOps” we mean that all system changes (except in “break glass” scenarios) need to be performed via git commits.