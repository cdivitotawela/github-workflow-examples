# Github Workflow Examples


## Multiple Jobs with Dependency

Workflow example [multi-job-dependency.yaml](.github/workflows/multi-job-dependency.yaml). This shows how typical software release workflow with dependency across jobs.


## Use Caching

Caching is useful when files need to be shared between multiple jobs/workflows. Most common usecase is the application dependency management. Example [.github/workflows/cache.yaml](.github/workflows/cache.yaml)
saves a file in `create` job and restore the file in `view` job. If fixed key is used, it will not add the save the cache as there is already cache hit which means file created in `create` job
won't be saved. So it use the `github.run_number` in key so that each run new file is saved in cache and restored on next job.


## Deploy Environments

GitHub environment helps to control the workflow run by making specific secrets available for the environment and adding 
approval gates. Configure the environment in repository Settings -> Environments with options "Required reviewers", "Wait timer", specify which branches environment applicable, specify environment secrets and variables. Example [.github/workflows/environments.yaml](.github/workflows/environments.yaml)


## Container Security Scan

Vulnerability scanning of container images using Trivy tool. Example [.github/workflows/security-scan.yaml](.github/workflows/security-scan.yaml). 
In this workflow actions are pinned to git hash instead of tags. Tags can be moved but when pinned to git hash these are static.
This improves the security as intruder cannot move the tag to a vulnerability code.


## Generate Dynamic Jobs Based on File Changes

Sometimes it is essential to run jobs based on the files changed. Example [.github/workflows/dynamic-jobs.yaml](.github/workflows/dynamic-jobs.yaml)
runs create jobs and runs dynamically based on the changes to the folders.