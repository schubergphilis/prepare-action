[![Release Status](https://github.com/schubergphilis/prepare-action/actions/workflows/pipeline.yml/badge.svg)](https://github.com/schubergphilis/prepare-action/actions/workflows/pipeline.yml)

# Prepare

Prepare is a GitHub action used to setup the dependencies needed by specific project types and their pipeline jobs. The
currently supported project types and jobs are:

| Project Type | Jobs               | OS    |
| ------------ | ------------------ | ----- |
| container    | cd, ci, lint, scan | linux |
| python       |                    | linux |

# Inputs

| Input            | Description                         | Required | Default |
| ---------------- | ----------------------------------- | -------- | ------- |
| job              | Job we are preparing for            | No       | unknown |
| type             | Project type we are preparing for   | Yes      |         |
| version_checkov  | Version of checkov to be installed  | No       | 3.2.125 |
| version_hadolint | Version of hadolint to be installed | No       | 2.12.0  |
| version_poetry   | Version of poetry to be installed   | No       | 1.8.3   |
| version_python   | Version of python to be installed   | No       | 3.10    |

# Outputs

None.

# Example Usage

Setting up the `cd` job of a `container` project type:

```yaml
- name: Prepare
  uses: schubergphilis/action-prepare@v1
  with:
    type: container
    job: cd
```

Setting up the `lint` job of a `python` project type with a specific version of `poetry`:

```yaml
- name: Prepare
  uses: schubergphilis/action-prepare@v1
  with:
    type: python
    job: lint
    version_poetry: 1.8.0
```
