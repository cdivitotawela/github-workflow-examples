# Github Workflow Examples


## Multiple Jobs with Dependency

Workflow example [multi-job-dependency.yaml](.github/workflows/multi-job-dependency.yaml). This shows how typical software release workflow with dependency across jobs.


## Use Caching

Caching is useful when files need to be shared between multiple jobs/workflows. Most common usecase is the application dependency management. Example [.github/workflows/cache.yaml](.github/workflows/cache.yaml)
saves a file in `create` job and restore the file in `view` job. If fixed key is used, it will not add the save the cache as there is already cache hit which means file created in `create` job
won't be saved. So it use the `github.run_number` in key so that each run new file is saved in cache and restored on next job.