# Lab 3 submission

## Task 1

1. [Link](https://github.com/sarrtr/DevOps-Intro/actions/runs/22032997595) to successful run.

2. **Key concepts of GitHub Actions:**

- Job is a set of steps that execute on the same runner. It can have dependencies on other jobs, executes in parallel by default.
- Steps are individual tasks that run commands or actions in a job. In my script (basic one suggested by GitHub) there are 7 steps of 3 types: `run` (executes shell commands), `uses` (executes pre-built GitHub Actions) and `name` (labels the step for better readability).
- Runners are servers that execute the workflows (in my script `runs-on: ubuntu-latest`).
- Triggers are events that cause the workflow to run.

3. **Workflow process analysis:**

- Trigger Phase: workflow was triggered by a push event to the repository (in my script: `on: [push]`).
- Setup Phase: Ubuntu runner prepared.
- Execution Phase:
    - Displays runner OS info
    - Shows branch and repository details
    - Clones the code
    - Lists repository files
    - Reports final job status

## Task 2

1. **Changes in workflow file:**

- add manual trigger 

![3.1](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab3.1.png?raw=true)

- add system info collection

![3.2](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab3.2.png?raw=true)

![3.3](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab3.3.png?raw=true)

2. **Gathered information:**

![3.4](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab3.4.png?raw=true)

![3.5](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab3.5.png?raw=true)

3. **Comparison of manual vs automatic workflow triggers:**
Automatic triggers are initiated immediately when code is pushed to the repository. They are useful for CI and automated testing. Manual triggers through `workflow_dispatch` require explicit user action, they allow to pass custom input parameters at runtime. You can choose which branch to run against at execution time. This can be useful for performing controlled deployments when needed.

4. **Runner environment & capabilities:**

Runner (`ubuntu-latest`):

- OS: Ubuntu Linux (latest version)
- Hardware: 4-core CPU, 15GB RAM, 145GB SSD storage
- IP Range: GitHub-hosted runners use ephemeral IPs

Key Capabilities:

- Isolation (clean state every run)
- Files shared between steps within a job
- Full access to github, runner, job contexts