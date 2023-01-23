# Resources

Concourse offers no services for storing/retrieving your data. No git repositories. No blobstores. No build numbers. Every input and output must be provided externally. Concourse calls them ["Resources"](https://resource-types.concourse-ci.org/). For example, `git`, `s3`, and `semver` provide git repos, blobstore, and build versions, respectively.

Your pipelines will mostly use a `git` resource to pull in the task files.

Let's modify the basic-pipeline to get its task as a file from a git repo.  Instead of embedding the task in job plan...
1. Define a git resource where the task file lives, and
1. In the job plan, get the resource and run the task file.

NOTE: The git resource may need some git config options defined, namely:
```
      git_config:
      - name: safe.directory
        value: "*"
```
This global setting squelched a "fatal: detected dubious ownership in repository at '/tmp/build/get'" error.

Interesting also to note that the git resource is completely self-contained, with its own image; if you SSH into the Concourse worker, you'll not find a `git` executable in the PATH.

The job can be triggered from the cmd line, and also watched via `--watch` ...
```
$ ft tj -j hellow-world-with-git/job-hello-world --watch
```

Note that the git-resource clones the repo into a directory corresponding to the name you've given the resource.  Now the git-resource can be used as an input to any subsequent tasks in the job's build plan.

Also, since this pipeline now depends on a git repo, `pipeline.yml` no longer completely determines the pipeline state; the repo state has now become a component of the pipeline state.

You can also watch a build without triggering it...
```
# Watch latest build...
$ ft watch -j hello-world-with-git/job-hello-world
# See output of given build...
$ ft watch -j hello-world-with-git/job-hello-world -b 14
```
...and see summary of builds...
```
$ ft builds
$ ft builds --help  # Show options for 'builds' command
```
