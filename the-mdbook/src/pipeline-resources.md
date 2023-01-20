# Resources

Concourse offers no services for storing/retrieving your data. No git repositories. No blobstores. No build numbers. Every input and output must be provided externally. Concourse calls them ["Resources"](https://resource-types.concourse-ci.org/). For example, `git`, `s3`, and `semver` provide git repos, blobstore, and build versions, respectively.

Your pipelines will mostly use a `git` resource to pull in the task files.

