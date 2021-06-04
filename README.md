# Cloud Information Security Review Checklist

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

1. Is cloud infrastructure in line with your compliance requirements?

2. Is there a multi-cloud architecture ? if yes , what other cloud provided services used ?

3. Are the underlying VMs / load-balancers / storage sufficiently protected? (e.g., via firewalls)

4. Is your application connected to any managed services? (e.g., database-as-a-service, logging-as-a-service, incident-management-as-a-service)

### Separation of testing and production

1. Do you separate testing from production cloud clusters?

2. Do you take production data into testing?

3. What is your source of test data?

4. Is your testing infrastructure sufficiently protected?

### Access Control

1. Describe your access control system?

2. Is multi-factor authentication enabled?

3. How many people have access to the production cluster?

    1. Is role based access implemented? (Read-only, Read-Write)

4. Do you have one user account per person?

5. Do you keep an audit trail on access to the production cluster?

6. Is the audit trail stored in a tamper-proof logging[^1] environment?

7. Do you regularly review access, e.g., revoking access to people leaving your organization?

### Logging

1. Do you forward nodes (journald), platform and application logs to a tamper-proof logging environment?

2. What is your retention policy? What is the minimum amount of time you keep logging entries? What is the maximum amount of time you keep logging entries?

    1. Source of retention policy? Specified in legislation or company policy?  If company policy, why that figure?

### Backups

1. Do you perform regular backups of your production clusters?

2. Do you regularly test restoring from backups?

### Change Management

1. What is the journey of code changes? (e.g., How does a new feature make it into production?)

2. What is the journey of infrastructure changes? (e.g., How do you create a new cluster? How do you update a SecurityGroup?)

3. What is the journey of data changes? (e.g., How do you add a new column to your database?)

4. Do you enforce a 2-person policy for performing system changes?

5. Do you use [semantic versioning](https://semver.org/) for container image tags?

6. How do you perform data migration?

7. In the event of a ‘bad’ deployment, can you rollback to a previous good state?

8. Is this rollback ability tested regularly?

9. Do you do Canary deployments?

### Technical Vulnerability Management

1. Do you scan containers for vulnerabilities before entering production?

2. Do you have a process in place to get alerted when a container/VM's becomes vulnerable in production?

3. Do you enforce deployment only from known-good container image registries?

4. After how much time do you fix known container image vulnerabilities?

5. Is the production cluster updated, as required to avoid vulnerabilities?

6. Is the underlying OS image updated, as required to avoid vulnerabilities?

7. Are other adjacent services (e.g., container registry, logging environment, identity provider) updated, as required to avoid vulnerabilities?

### Use of Cryptography

1. Do you encrypt traffic over open networks? Do you use HTTPS over the Internet?

2. Do you regularly rotate cryptographic keys?

3. Do you use HSTS[^2]?

### Network Segregation

1. Do you use network segregation?

### Intrusion Detection / Prevention

1. Do you have an intrusion detection system in the production cluster?

2. Do you have a web application firewall in front or within the production cluster?

3. Do you alert on blocked outbound traffic?

### Business Continuity

1. Are your systems designed with sufficient redundancy? (e.g., multiple availability zones, multiple servers, multiple application replicas)

2. Do you regularly test your redundancy? (e.g., by failing a server and killing an application replica)

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

## Cluster Security

1. Do you use Role-Based Access Control?

2. Do you use OpenPolicyAgent?

## Development Practices

1. How is a container image built?

2. How is a container image deployed into the production cluster?

3. How do you manage deployments?

4. Do you practice GitOps[^3]?

5. Do you fully separate development from production environments?

6. Is there a fully separate environment for testing/QA?

### Development Environment

#### Access control

1. How is access managed to this environment? (Role based, per user etc)

2. Describe your source control systems and process

### Testing/QA Environment

#### Access control

1. How is access managed to this Test/QA environment? (Role based, per user etc)

#### Test data

1. How is test data created/sourced?

2. Does data come from production data?

    1. If yes, is it anonymised?

### Production Environment

#### Access control

1. How is access managed to this production environment? (Role based, per user etc)

### Code/build Deployment

##### Application

1. Describe your application deployment process

2. What checks do you carry out on your application at deployment time?

##### Volume mounts/Data sources

1. Describe your deployment/update process for data sources.

2. Is your data persistence layer built using the Infrastructure as code paradigm?

3. Is your data persistence layer version controlled?

#### Permissions

##### Automated/manual system

## Operational Practices

### Health Checks

1. Do you maintain KPIs for determining if your production cluster is working well? (e.g., USE: utilization, saturation, errors)

2. Do you have relevant alerts in place?

3. Do you have alerts for “slowly filling and getting full”? (e.g., disk space)

4. Do you require Liveness, Readiness and Startup Probes?

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
     By “tamper-proof” it is understood that a person gaining (authorized or unauthorized access) to the production cluster cannot modify or delete existing log entries.

[^2]:
     https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security

[^3]:
     By “GitOps” we mean that all system changes (except in “break glass” scenarios) need to be performed via git commits.
