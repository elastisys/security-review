# Terraform Security

1. Are you storing your Terraform Code in a version control system (Git or similar)?
1. Are you using one Terraform workspace for each environment of a given infrastructure component?
1. Are you using Terraform modules to increase reusability of your infrastructure code?
1. Terraform state:
    1. Are your Terraform state files encrypted at rest?
    1. How are your Terraform state files protected against accidental disclosure?
    1. How are your Terraform state files protected against corruption?
1. How do you handle sensitive information in your Terraform scripts?
    1. How are the credentials of a Terraform service account (JSON) secured?
    1. Where are these credentials stored?
    1. Is your Terraform integrated with a secret management tool (HashiCorp’s Vault or similar)?
    1. Is your Terraform state file encrypted at rest?
1. Are the permissions of a Terraform service account restricted to minimum?
    1. What is the list of permissions given to the Terraform service account?
    1. Are there any separate roles and policies attached?
1. Are you using Terraform Cloud?
    1. How are you running it? SaaS hosted by HashiCorp or a private instance?
    1. Did you assign Terraform Cloud workspace ownership and permissions to your teams?
    1. Did you restrict the Non-Terraform access to cloud provider UIs and APIs to avoid manual infrastructure modifications?

For general advices on how to use Terraform check [Terraform Recommended Practices](https://www.terraform.io/docs/cloud/guides/recommended-practices/index.html).
