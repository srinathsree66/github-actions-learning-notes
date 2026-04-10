# GITHUB ACTIONS

## What GitHub Actions is? why it's used?

A service introduced by GitHub. A service used by Devops Engineers to run the CI/CD pipelines.

      BUILD ---> DEPLOY ----> TEST

It doesn't required scripting/programming languages.

### CI/CD

#### CI (Continuous Integration)

CI is a devops practise where developers regularly integrate their code, Each integration automatically verified by automated builds, tests.

#### CD (Continuous Delivery/Deployment)

Both practices automate the process of preparing the code for production releases.

**Continuous Delivery** -> Required manual intervantion(approval)
**Continuous Deployment** -> Not required manual approval.

## Evaluation of GitHub and GitHub Actions

- GitHub was launched in 2008
- Microsoft acquired GitHub in 2018
- They introduced new things such as:-

                      1) GitHub Actions.
                      2) GitHub Advanced Security.
                      3) GitHub Container Registry.
                      4) GitHub Copilot.

### GitHub Workflow Structure

In github repository workflow can be created inside **.github** folder with **workflows** folder.

Workflow can have different components like when to trigger ex when we push or PR creation.

We have jobs those have to run on specific compute software. GitHub Actions support wide range of Runners.

Job can have multiple steps. A step is ntg but a piece of activity like Run a command.

All jobs run in parallel(by default)

Let's create a **Hello world** workflow.

### Running multiple shell commands in single step

<!-- markdownlint-disable MD046 -->

```yml
name: Hello World

on: workflow_dispatch

jobs:
  hello-world:
    runs-on: ubuntu-latest
    steps:
      - name: Hello step
        run: echo "Welcome to Github Actions"
```

we can use pipe symbol to run multiple commands (**|**)
ex:-

<!-- markdownlint-disable MD046 -->

```yml
name: Hello World

on: workflow_dispatch

jobs:
  hello-world:
    runs-on: ubuntu-latest
    steps:
      - name: Hello step
        run: |
          echo "This is line one"
          echo "This is line two"
```
