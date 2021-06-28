# Ansible Security Review Checklists

1. Ansible control node:
    1. Where is your Ansible control node located?
    1. Who has access to it?
    1. How do you minimize the access to the Ansible control node to a limited number of users.
1. Ansible Vault:
    1. Do you use Vault to encrypt sensitive data in Ansible playbooks?
    1. Where is the Ansible Vault password stored?
1. Secrets:
    1. How secrets are stored?
    1. How often they are rotated?
1. What network-level security solution is in place for safeguarding access to the Ansible control node (e.g., SSH, VPN)?
