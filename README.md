# GITHUB ACTIONS

## Workflow Status

[![Hello World](https://github.com/srinathsree66/github-actions-learning-notes/actions/workflows/hello-world.yml/badge.svg)](https://github.com/srinathsree66/github-actions-learning-notes/actions/workflows/hello-world.yml)

## What GitHub Actions is? why it's used?

GitHub Actions is a CI/CD automation service provided by GitHub.  
It allows developers and DevOps engineers to automate tasks such as building, testing, and deploying applications.

      BUILD ---> DEPLOY ----> TEST

It does not require complex scripting or programming to get started.

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

### Creating multiple jobs in single workflow

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
  build:
    runs-on: ubuntun-latest
    steps:
      - name: Build Step
        run: echo "A demo build"
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Test Phase
        run: echo "Running test cases"
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Deploy the App
        run: echo "Deploying the app"
```

If you observe by default multiple jobs running in parallel this is default. To run in sequential manner
we can use **needs:{jobName}**
ex:-

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
  build:
    runs-on: ubuntun-latest
    needs: hello-world
    steps:
      - name: Build Step
        run: echo "A demo build"
  test:
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Test Phase
        run: echo "Running test cases"
  deploy:
    runs-on: ubuntu-latest
    needs: test
    steps:
      - name: Deploy the App
        run: echo "Deploying the app"
```

### GitHub Actions Workflow Triggers & Types

In GitHub actions triggers are defined by keyword **on**

#### Types of Triggers

      1) Event based trigger
      2) Manual triggers
      3) Scheduled triggers
      4) Workflow triggers

### Push & Pull Request Triggers (workflow triggers)

```yml
name: Hello World

on: push

jobs:
  hello-world:
    runs-on: ubuntu-latest
    steps:
      - name: Hello step
        run: |
          echo "This is line one"
          echo "This is line two"
  build:
    runs-on: ubuntun-latest
    needs: hello-world
    steps:
      - name: Build Step
        run: echo "A demo build"
  test:
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Test Phase
        run: echo "Running test cases"
  deploy:
    runs-on: ubuntu-latest
    needs: test
    steps:
      - name: Deploy the App
        run: echo "Deploying the app"
```
