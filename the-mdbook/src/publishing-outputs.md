# Publishing Outputs
The sample code lives in `tutorials/basic/publishing-outputs`.

Notes:
- The instructions specify 'master' for a gist branch, but the default branch is now 'main'.
- Have to update/add/commit/push the `bump-timestamp-file.sh` to set `safe.directory`.
- `bump-timestamp-file.sh` uses a neat trick to clone a local repo into another local repo:
```
$ git clone localRepo anotherLocalRepo
```
- It's far from great that the private key lives in `pipeline.yml`.  This issue will be addressed in [Managing Secrets](./managing-secrets.md). 
- The `bump-timestamp-file.sh` script relies on `git` being installed in the image resource that is used to run it--that is, the image of type [`registry-image`](https://github.com/concourse/registry-image-resource).
- `registry-image` is much smaller and more focused on simply pushing and pulling, as opposed to the `docker-image` type that it replaced, which had too large an interface (i.e., many ways of building/publishing Docker images) for effective support.

