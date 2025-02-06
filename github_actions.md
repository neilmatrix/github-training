github actions automates workflows in your repository.
As an ML developer, you can use it to:
- automate notebook execution
- test & lint python code and notebooks
- schedule jobs for training models
- deploy models to cloud
- ci/cd for ml projects

basics of github actions
- key concepts
1. workflows (`.github/workflows/`) - automation scripts written in YAML
2. jobs - a set of steps executed in a VM/container.
3. individual commands inside a job.
4. triggers (on: [push, pr, schedule]) - when to run a workflow
5. runners - the server executing the workflow (github hosted or self hosted)


- common commands
run python scripts
```yaml
-   name: Run Python Script
    run: python script.py
```


install dependencies
```yaml
-   name: Install dependencies
    run: pip install -r requirements.txt
```

check python version
```yaml
-   name: Check python version
    run: python --version
```

---

setting up github actions
step 1:  creating your first workflow
- create a `.github/workflows/ci.yml` file in your repository
- add this basic workflow
```yaml
name: CI for ml project

on: [push, pull_request]            # triggers on push or pr

jobs:
    test:
        runs-on: ubuntu-latest          # uses ubuntu as runner
        steps:
            -   name: checkout repo
                uses: actions/checkout@v4       # fetch repo code

            -   name: setup python
                uses: actions/setup-python@v4
                with:
                    python-version: "3.9"

            -   name: install dependencies
                run: pip install -r requirements.txt

            -   name: run tests
                run: pytest tests/
```


---
running jupyter notebooks in github actions






---
ci/cd pipelone
- commit changes
- trigger build
- build
- notify of build outcome
- run tests
- notify of test outcome
- deliver build to staging
- deploy to production

github actions
- not only ci/cd
- workflows stored as yml files
- issues created, pr created => trigger workflows
- fully integreated with github
- respond to github events
- live logs and visualised workflow execution
- built in secrets and env store

actions and SDLC
- plan - triage issues and project boards using actions
- code - automate code builds
- build - compile and build, store artifacts
- tests - automation of the unit tests, integration, tests
- release - publish release, release notes, version, and upload artifacts (zip, .exe etc) - upload to a store artifact factory(or packages on github)
- deploy - deploy to chosen env


key components
- simple ci.yaml
```yaml
name: Simple

on:
    workflow_dispatch

jobs:
    run_shell_command:
        name: actions are amazing
        runs-on: arc-test-runner
        steps:
            - name: say hello
              runs: |
                echo "hello world"
```


workflows triggers on common factors
- events => runner(where the event will be executed)
- under a runner, we create jobs
- jobs example, build, run, install packages etc.
- jobs will execute parallely by default
  - if there is dependencies, write `needs`
  - for each job, `runs-on` is required
  

```yaml
name: learn-github actions          # name of the workflow
run-name:                          # not mandatory
on: [push]                          # event to trigger this workflow
jobs:
    check-bats-version:
        runs-on: ubuntu-latest
        steps:                      # actual executable step
            - uses: actions/checkout@v4
```
steps:
  uses: actions/checkout@v4   -> uses github actions devloped action

steps:
  run: echo "hello"             -> run user defined command


---
events - 3 types
- webhook events - pr, push, issues, release
- scheduled events - 
```yaml
on:
    schedule:
        cron job
```
- manual events - 
```yaml
on:
    workflow_dispatch               # button will show up to run manually or using rest api
```



runners - 2 types
- github hosted             - windows/linux/mac         - monthly credit of action minutes
- self-hosted runner        


github hosted runners
- runners group at org/repo level
  - azure
  - mobile
  - ui-tests

self-hosted runners - ARC (Action Runner Container)



actions - 4 different
- run: hello
- public action
  - uses: actins/checkout@v4
- local action          - own created action - path tto the action
  - uses: .path/
- docker image




advaned syntax
- permission
- needs
- servies
- contianer
- env
- if
- contains
- startsWith/endswith
- tojson/fromjson
- join
- continue-on-error
- format
- concurrency
- defaults
- timeout-minutes



- jobs are parallel, steps are sequential

actions envs and secrets
- envs manage and secure deploument target like production
  - deployment protection rules
  - required reviewers
  - control deployment
  - require approvals
- secrets - variables in the system
  - handling of credentials
  - 