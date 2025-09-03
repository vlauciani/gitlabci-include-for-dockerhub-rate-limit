[![License](https://img.shields.io/badge/license-MIT-lightgrey.svg)](https://github.com/vlauciani/gitlabci-include-for-dockerhub-rate-limit/blob/main/LICENSE)

# DockerHub Rate Limit GitLab CI Include

A reusable GitLab CI YAML file that checks DockerHub rate limits using the `include` directive. Compatible with both free and paid DockerHub accounts.

## Usage

This snippet can be included in GitLab CI to check DockerHub rate limit.

In your `.gitlab-ci.yml` file, remember to set variables:
- `DOCKERHUB_REGISTRY_USER` - Your DockerHub username
- `DOCKERHUB_REGISTRY_PSW` - Your DockerHub password or access token

Use GitLab CI/CD variables for secure credential management ([documentation](https://docs.gitlab.com/ee/ci/variables/)).

## Output

### Free DockerHub Accounts
For free accounts, the stage displays rate limit information:
```
ratelimit-limit: 200;w=21600
ratelimit-remaining: 176;w=21600
RATELIMIT_REMAINING=176
```

### Paid DockerHub Accounts  
For paid accounts, rate limit headers are not present:
```
Rate limit headers not present (likely paid account)
RATELIMIT_REMAINING=not available (likely paid account)
```

The job will only fail if you're on a free account and have 0 remaining pulls.

## Quick Start

Add this to your `.gitlab-ci.yml`:

```yaml
# .gitlab-ci.yml
include:
  - remote: 'https://raw.githubusercontent.com/vlauciani/gitlabci-include-for-dockerhub-rate-limit/main/dockerhub-rate-limit.yml'

variables:
  # DockerHub credentials (set these in GitLab CI/CD variables)
  DOCKERHUB_REGISTRY_USER: $DOCKERHUB_USER
  DOCKERHUB_REGISTRY_PSW: $DOCKERHUB_TOKEN

stages:
  - check-limits
  - build
  - test
  - deploy

dockerhub-rate-limit:
  stage: check-limits
  variables:
    INCLUDE_DOCKERHUB_REGISTRY_USER: ${DOCKERHUB_REGISTRY_USER}
    INCLUDE_DOCKERHUB_REGISTRY_PSW: ${DOCKERHUB_REGISTRY_PSW}
```

## Features

- ✅ Works with both free and paid DockerHub accounts
- ✅ Fails build only when rate limit is exhausted (0 remaining pulls)
- ✅ Provides clear output for debugging
- ✅ Uses secure credential handling
- ✅ Minimal dependencies (curl, jq)

## Contribute
Thanks to your contributions!

Here is a list of users who already contributed to this repository: \
<a href="https://github.com/vlauciani/gitlabci-include-for-dockerhub-rate-limit/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=vlauciani/gitlabci-include-for-dockerhub-rate-limit" />
</a>

## How It Works

The script:
1. Authenticates with DockerHub using provided credentials
2. Requests a test repository manifest to check rate limits  
3. Examines response headers for rate limit information
4. Reports current limits and remaining pulls
5. Fails the job only if rate limit is exhausted (0 remaining)

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Job fails with authentication error | Check your DockerHub credentials in GitLab CI/CD variables |
| "Rate limit headers not present" | This is normal for paid accounts - job will continue |
| Job fails with rate limit 0 | Wait for rate limit reset or upgrade to paid account |

## References
- [GitLab CI includes documentation](https://docs.gitlab.com/ee/ci/yaml/includes.html)
- [DockerHub rate limiting](https://docs.docker.com/docker-hub/download-rate-limit/)
- [GitLab CI/CD variables](https://docs.gitlab.com/ee/ci/variables/)

## License
MIT License - see [LICENSE](LICENSE) file for details

## Author
(c) 2025 Valentino Lauciani vlauciani[at]gmail.com
