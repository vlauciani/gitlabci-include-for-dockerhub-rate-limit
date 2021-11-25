[![License](https://img.shields.io/badge/license-MIT-lightgrey.svg)](https://github.com/vlauciani/gitlabci-include-for-dockerhub-rate-limit/blob/main/LICENSE)

# DockerHub rate limit 'include', for `.gitlab-ci.yml`
A simple yml file to use `include` directive in your `.gitlab-ci` to check the DockerHub rate limit

## Usage

This snippet can be included in GitLab CI to check DockerHub rate limit.

In your `.gitlab-ci.yml` file, remeber to set variables:
- `DOCKERHUB_REGISTRY_USER` 
- `DOCKERHUB_REGISTRY_PSW`

Using GitLab CI/CD varaibles approach (https://gitlab.rm.ingv.it/help/ci/variables/index).

This `stage` returns:
```
ratelimit-limit: 200;w=21600
ratelimit-remaining: 176;w=21600
```

### Example

```yml
# .gitlab-ci.yml
include:
  - remote: 'https://raw.githubusercontent.com/vlauciani/gitlabci-include-for-dockerhub-rate-limit/main/dockerhub-rate-limit.yml'

variables:
  # DockerHub
  DOCKERHUB_REGISTRY_USER: <dockerhub_user>
  DOCKERHUB_REGISTRY_PSW: <dockerhub_psw>
    
stages:
  - . . .
  - dockerhub-rate-limit_stage
  - . . .
  
dockerhub-rate-limit:
    stage: dockerhub-rate-limit_stage  
    variables:
      INCLUDE_DOCKERHUB_REGISTRY_USER: ${DOCKERHUB_REGISTRY_USER}
      INCLUDE_DOCKERHUB_REGISTRY_PSW: ${DOCKERHUB_REGISTRY_PSW}    
```

## Contribute
Thanks to your contributions!

Here is a list of users who already contributed to this repository:
<a href="https://github.com/vlauciani/gitlabci-include-for-dockerhub-rate-limit/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=vlauciani/gitlabci-include-for-dockerhub-rate-limit" />
</a>

## References
- https://medium.com/@imalik8088/tired-of-repeated-gitlab-ci-files-includes-to-the-rescue-17225532812a
- https://gitlab.com/imalik8088/gitlab-ci-include-test/-/blob/master/.gitlab-ci.yml

## Author
(c) 2021 Valentino Lauciani vlauciani[at]gmail.com
