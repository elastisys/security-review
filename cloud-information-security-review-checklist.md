# Cloud Information Security Review Checklist

This document is a general, technology-neutral Cloud Information Security Review Checklist.

In this repository you can also find technology specific checklists.

## Governance, risk management, and compliance

1. What regulations / information security standards do you need to comply with?

    1. FFFS 2014:7
    1. SOC-2
    1. PCI-DSS
    1. ISO 27001
    1. HIPAA
    1. Swedish HealthCare
    1. GDPR
    1. Other

1. Who/what role in your organisation is responsible for compliance?

1. Does your organization have general information security policies outside of your compliance requirements in place? (e.g., “We need to store data in Brazil to appeal to national sentiments.”)

### Mapping of Standards to Policies

What policy statements do you have in place to show your compliance with the above standard(s)?

### Mapping of Policies to Implementation

1. How do you track implementation?

1. What is your development/implementation methodology?

    1. How do you take high level policy requirements and create implementable units of work?

1. How do you track and plan implementation/development?

### Evidence of Implementation fulfilling Policies

1. When a policy is implemented how is this validated?

1. Is this validation recorded?

1. Can an auditor access this record?

## High-Level General Practices

### Supply Management

1. Who supplies your cloud infrastructure today?

1. Is the underlying cloud providers infrastructure in line with your compliance requirements?

1. Are the underlying VMs / load-balancers / storage sufficiently protected? (e.g., via firewalls)

1. Is your application connected to any managed services? (e.g., database-as-a-service, logging-as-a-service, incident-management-as-a-service)

### Separation of testing and production

1. Do you separate testing from production clusters?

1. Do you take production data into testing?

1. What is your source of test data?

1. Is your testing infrastructure sufficiently protected?

### Access Control

Consider access control to all components of your system: infrastructure, platforms, third party services or applications, as well as, your own application.

1. Do you have a clear policy regarding who gets what access?

1. Do you use an Identity Provider (IdP) and single sign-on (SSO)?

1. Is multi-factor authentication mandatory?

1. Do you have one user account per person?

1. Do you regularly review access, e.g., revoking access to people leaving your organization?

### Logging

1. Do you forward nodes (journald), cloud platform and application logs to a tamper-proof logging environment?

1. What is your retention policy? What is the minimum amount of time you keep logging entries? What is the maximum amount of time you keep logging entries?

    1. Source of retention policy? Specified in legislation or company policy?  If company policy, why that figure?

### Backups

1. Do you perform regular backups of your production clusters?

1. Do you regularly test restoring from backups?

### Change Management

1. What is the journey of code changes? (e.g., How does a new feature make it into production?)

1. What is the journey of infrastructure changes? (e.g., How do you create a new cluster? How do you update a SecurityGroup?)

1. What is the journey of data changes? (e.g., How do you add a new column to your database?)

1. Do you enforce a 2-person policy for performing system changes?

1. Do you use [semantic versioning](https://semver.org/) for container image tags?

1. How do you perform data migration?

1. In the event of a ‘bad’ deployment, can you rollback to a previous good state?

1. Is this rollback ability tested regularly?

1. Do you do Canary deployments?

### Technical Vulnerability Management

1. Do you scan containers for vulnerabilities before entering production?

1. Do you have a process in place to get alerted when a container becomes vulnerable in production?

1. Do you enforce deployment only from known-good container image registries?

1. After how much time do you fix known container image vulnerabilities?

1. Is the production cluster updated, as required to avoid vulnerabilities?

1. Is the underlying OS image updated, as required to avoid vulnerabilities?

1. Are other adjacent services (e.g., container registry, logging environment, identity provider) updated, as required to avoid vulnerabilities?

### Use of Cryptography

1. Do you encrypt traffic over open networks? Do you use HTTPS over the Internet?

1. Do you regularly rotate cryptographic keys?

1. Do you use HSTS<sup>[2](#footnote1)</sup>?

### Network Segregation

1. Do you use network segregation?

### Intrusion Detection / Prevention

1. Do you have an intrusion detection system in the production cluster?

1. Do you have a web application firewall in front or within the production cluster?

1. Do you alert on blocked outbound traffic?

### Business Continuity

1. Are your systems designed with sufficient redundancy? (e.g., multiple availability zones, multiple servers, multiple application replicas)

1. Do you regularly test your redundancy? (e.g., by failing a server and killing an application replica)

1. Do at least two team members have access to each system?

### Incident Management

1. Are your systems sufficiently documented for incident management?

1. Do you have a clear definition of what is an incident?

1. Does your team have clear procedures for who handles incidents and how to handle incidents?

1. Are there situations where you need to fix data in a production environment?

    1. If yes, what is your process?

#### Incident reporting: Internal

1. How do internal users report incidents?

1. Is there an escalation process in place if an incident is not responded to in time?

#### Incident reporting: External

1. How do external users report incidents?

1. Is there an escalation process in place if an incident is not responded to in time?

## Cluster Security

1. Do you use Role-Based Access Control?

1. Do you use OpenPolicyAgent?

## Development Practices

1. How is a container image built?

1. How is a container image deployed into the production cluster?

1. How do you manage deployments?

1. Do you practice GitOps<sup>[3](#footnote1)</sup>?

1. Do you fully separate development from production environments?

1. Is there a fully separate environment for testing/QA?

### Development Environment

#### Access control

1. How is access managed to your development environment? (Role based, per user, read-only, read-write, etc.)

1. Which source code control system are you using?

1. Which flow (branching model) are you using?

### Testing/QA Environment

#### Access control

1. How is access managed to your testing/QA environment? (Role based, per user, read-only, read-write, etc.)

#### Test data

1. How is test data created/sourced?

1. Does data come from production data?

    1. If yes, is it anonymised?

### Production Environment

#### Access control

1. How is access managed to this environment? (Role based, per user, read-only, read-write, etc.)

1. How many people have access to the production cluster?

1. Do you keep an audit trail on access to the production cluster?

1. Is the audit trail stored in a tamper-proof logging<sup>[1](#footnote1)</sup> environment?

### Code/build Deployment

##### Application

1. Do you have an automated pipeline in place to build container images?

1. What checks do you carry out on your application at deployment time?

##### Volume mounts/Data sources

1. What are the requirements of your application regarding the data persistence layer?

1. What cloud storage services is your application using?

1. Is your data persistence layer built using the Infrastructure as code paradigm?

1. Is your data persistence layer version controlled?

#### Permissions

##### Automated/manual system

## Operational Practices

### Health Checks

1. Do you maintain KPIs for determining if your production cluster is working well? (e.g., USE: utilization, saturation, errors)

1. Do you have relevant alerts in place?

1. Do you have alerts for “slowly filling and getting full”? (e.g., disk space)

1. Do you require Liveness, Readiness and Startup Probes?

### Operational Logging and Alerts

1. Do you have relevant alerts in place?

1. Do you have a defined process for handling alerts?

1. What is the retention period for these logs?

#### SLA’s/SLO’s management

1. Do you maintain KPIs for determining if your users are served well? (e.g., daily active users, log-ins per day, registrations per day)

1. Do you maintain KPIs for determining if your application is working well? (e.g., RED: request rate, error rate, duration)

#### Path to resolution

1. Do you have an incident management strategy in place?

1. Who is reponsible for responding to an incident? Do you have defined roles for incident response, e.g., Incident Commander (IC), Communications Lead (CL), and Operations Lead (OL)?

1. Do you categorize issues and differentiate the way how you handle them depending on their severity? (e.g., is the outage visible to customers? does it require an immediate response or resolution can be postponed until office hours?)

1. Do you maintain up-to-date runbooks with scripts or procedures to apply in case of a typical issue? Do you have a procedure to update the runbooks before new software versions are released?

1. Do you have a procedure in place defining the way how issues should be escalated if the person/team involved at the time is unable to mitigate the issue?

1. Do you perform a regular practice of your incident management strategy?

1. Do you perform a Postmortem Analysis?

1. Who decides about the incident closure and what conditions have to be fulfilled before that happens?

### Security Logging and Alerts

1. Do you have relevant alerts in place?

1. Do you have a defined process for handling alerts?

1. What is the retention period for these logs?

#### Triage

1. Do you have processes and systems in place for evaluating security incidents? (Info, Low, Medium, High, Critical)

1. Do you have processes and systems in place for informing/alerting external shareholders of relevant incidents? (Data leaks, System availability etc)

#### Path to resolution

1. Who is responsible for applying security patches to each software layer of your system (operating system, platform, libraries, application)?

1. What is the expected time frame for security patches to be applied?

1. How do you verify that the security patches were deployed succesfully?

## Billing

1. Do you have a method in place to assign actual resourse/service usage costs to each project?
1. Do you have billing alerts set at organization and/or project levels? Who is receiving these alerts? Is there a process in place how to deal with the alerts?
1. Do you regularly review historical billing records and forcasts for future costs?

<!-- Footnotes themselves at the bottom. -->
## Notes

<a name="footnote1">[1]</a>:
     By “tamper-proof” it is understood that a person gaining (authorized or unauthorized access) to the production cluster cannot modify or delete existing log entries.

<a name="footnote1">[2]</a>:
     https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security

<a name="footnote1">[3]</a>:
     By “GitOps” we mean that all system changes (except in “break glass” scenarios) need to be performed via git commits.
