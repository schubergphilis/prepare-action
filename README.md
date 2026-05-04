[![Release Status](https://github.com/schubergphilis/prepare-action/actions/workflows/pipeline.yml/badge.svg)](https://github.com/schubergphilis/prepare-action/actions/workflows/pipeline.yml)

# Prepare

Prepare is a GitHub action used to setup the dependencies needed by specific project types and their pipeline jobs. The
currently supported project types and jobs are:

| Project Type | Jobs               | OS    |
| ------------ | ------------------ | ----- |
| container    | cd, ci, lint, scan | linux |

# Inputs

| Input            | Description                         | Required | Default |
| ---------------- | ----------------------------------- | -------- | ------- |
| job              | Job we are preparing for            | Yes      |         |
| type             | Project type we are preparing for   | Yes      |         |
| version_checkov  | Version of checkov to be installed  | No       | 3.2.521 |
| version_hadolint | Version of hadolint to be installed | No       | 2.14.0  |
| version_task     | Version of task to be installed     | No       | 3.50.0  |

# Outputs

None.

# Example Usage

Setting up the `cd` job of a `container` project type:

```yaml
- name: Prepare
  uses: schubergphilis/action-prepare@v1.0.0
  with:
    type: container
    job: cd
```
