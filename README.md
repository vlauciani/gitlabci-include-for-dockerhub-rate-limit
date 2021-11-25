# `.gitlab-ci.yml` include for DockerHub rate limit
A simple yml file to include in your `.gitlab-ci` to check the DockerHub rate limit

## Usage

This snippet can be included in GitLab CI to check DockerHub rate limit.

In your `.gitlab-ci.yml` file, remeber to set 
- `INCLUDE_DOCKERHUB_REGISTRY_USER` 
- `INCLUDE_DOCKERHUB_REGISTRY_PSW`

Using GitLab CI/CD varaibles approach (https://gitlab.rm.ingv.it/help/ci/variables/index).

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

## Contribute
Thanks to your contributions!

Here is a list of users who already contributed to this repository:
<a href="https://github.com/vlauciani/gitlabci-include-for-dockerhub-rate-limit/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=vlauciani/gitlabci-include-for-dockerhub-rate-limit" />
</a>

## Author
(c) 2021 Valentino Lauciani valentino.lauciani[at]ingv.it

Istituto Nazionale di Geofisica e Vulcanologia, Italia
