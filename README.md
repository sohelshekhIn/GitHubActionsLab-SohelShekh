# GitHub Actions Lab

## Overview

This repository demonstrates automated workflows using GitHub Actions. The lab includes two workflows:

1. Dependent Jobs Workflow
2. Multi-Platform Testing Workflow

## Workflow 1: Dependent Jobs Workflow

The first workflow is defined in:

```
.github/workflows/dependent-jobs.yml
```
This workflow runs when code is pushed to the main branch.

It contains three jobs:
```text
build
test
deploy
```
The jobs run in this order:
```txt
build → test → deploy
```
This order is controlled using the needs keyword.

For example:
```txt
needs: build
```
means that the test job will only run after the build job completes successfully.

Workflow 2: Multi-Platform Testing Workflow

The second workflow is defined in:
```
.github/workflows/multi-platform.yml
```
This workflow runs when a pull request is created against the main branch.

It contains three independent jobs:
```
ubuntu-job
windows-job
macos-job
```
Each job runs on a different operating system using the runs-on keyword.

Examples:

runs-on: ubuntu-latest
runs-on: windows-latest
runs-on: macos-latest

Because these jobs do not use the needs keyword, they run in parallel.


## Key Concepts Demonstrated
```
needs
```
The needs keyword creates job dependencies. It controls the order in which jobs run.
Example:
needs: build
runs-on


The runs-on keyword defines the operating system used by a job.
Example:
runs-on: ubuntu-latest
env


The env keyword is used to define environment variables. Environment variables can be defined at the workflow, job, or step level.
Example:
```
env:
  APP_ENV: test
```

## Challenges Faced
One challenge was understanding the difference between dependent jobs and independent jobs.

In the first workflow, the needs keyword was required because the jobs had to run in order.
In the second workflow, the needs keyword was not used because all three operating system jobs had to run at the same time.
Another challenge was making sure the YAML indentation was correct, because GitHub Actions workflows are sensitive to spacing.

## Conclusion
This lab demonstrates how GitHub Actions can automate build, test, and deployment steps, as well as how to run jobs across multiple operating systems.
