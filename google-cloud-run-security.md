# Google Cloud Run Security

## Cloud Run Container Security

1.Container Base Image 
   - What is the source of your base image? 
   - Is the docker image signed one? Do you use Docker Content Trust feature ?
   - Do you have a lean base image? 
2. How are vulnerabilities found at Non-OS level (Python, npm, ruby gems, etc.)?
3. Does your container follow [CIS benchmark](https://github.com/docker/docker-bench-security)?
4. Are there any extra packages in containers that can be security vulnerabilities?
5. Are containers running as a non-root user?
6. How image ensures to avoid privilege escalation and how it deals with Linux capabilities.


## Cloud Run Authentication

1. Do you have Identity provider access control in place? Is it both for the user and other service?
1. Do you have the service account for cloud run service? If so, what permissions are provided?
1. How access tokens are used to authenticate when calling Google Cloud APIs?
1. How are the secrets manage in Cloud Run? Are secrets managed by the Secret Manager?
1. Do you have customer managed encrytion keys?
1. Is Cloud Run integrated with Binarization autherization? Or is code binarized and then deployed?
