# `.gitlab-ci.yml` include for DockerHub rate limit
A simple yml file to include in your `.gitlab-ci` to check the DockerHub rate limit

## Usage

This snippet can be included in GitLab CI to che DockerHub rate limit.

### Example

```yml
# .gitlab-ci.yml
include:
  - remote: 'https://raw.githubusercontent.com/italia/publiccode-parser-gitlab-ci/main/publiccode-validation.yml'
  
stages:
  - . . .
  - publiccode-parser-gitlab-ci_stage
  - . . .
  
publiccode-parser:
    stage: publiccode-parser-gitlab-ci_stage  
```
