# `.gitlab-ci.yml` include for DockerHub rate limit
A simple yml file to include in your `.gitlab-ci` to check the DockerHub rate limit

## Usage

This snippet can be included in GitLab CI to che DockerHub rate limit.

### Example

```yml
# .gitlab-ci.yml
include:
  - remote: 'https://raw.githubusercontent.com/vlauciani/gitlabci-include-for-dockerhub-rate-limit/main/dockerhub-rate-limit.yml'
  
stages:
  - . . .
  - dockerhub-rate-limit_stage
  - . . .
  
dockerhub-rate-limit:
    stage: dockerhub-rate-limit_stage  
```
