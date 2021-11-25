# `.gitlab-ci.yml` include for DockerHub rate limit
A simple yml file to include in your `.gitlab-ci` to check the DockerHub rate limit

## Usage

This snippet can be included in GitLab CI to check DockerHub rate limit.

In your `.gitlab-ci.yml` file, remeber to set `DOCKERHUB_REGISTRY_USER` and `DOCKERHUB_REGISTRY_PSW`

### Example

```yml
# .gitlab-ci.yml
include:
  - remote: 'https://raw.githubusercontent.com/vlauciani/gitlabci-include-for-dockerhub-rate-limit/main/dockerhub-rate-limit.yml'

variables:
  # DockerHub
  INCLUDE_DOCKERHUB_REGISTRY_USER: <dockerhub_user>
  INCLUDE_DOCKERHUB_REGISTRY_PSW: <dockerhub_psw>
    
stages:
  - . . .
  - dockerhub-rate-limit_stage
  - . . .
  
dockerhub-rate-limit:
    stage: dockerhub-rate-limit_stage  
```
