
### Cloud Run Security - ( Google Managed service for running container ) 

1. What is the source of base image ? Is is signed one ? Do we have a lean base image 
2. How vulnerabilities found at Non-OS level (Python, npm, ruby gems, etc)
3. Is your container follows CIS benchmark ?
4. Is there any extra packages in container that can be security vulnerabilities ?
5. Is your container running as a user ?
6. Do we have Identity provider access control in place ? Is it both for the user and other service ?
7. Do we have the service account for cloud run service ? If so , what permissions are provided ?
8. How access tokens used to authenticate when calling Google Cloud APIs ?
9. How is the secrets manages in cloud run ? Is secret managed by secret manager ?
10. Do we have customer managed encrytion keys ?
11. Is cloud run integrated with Binarization autherization ? Or code is binarized and then deployed ?




