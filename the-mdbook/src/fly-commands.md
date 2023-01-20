# Fly commands, by category
`fly help` shows this same list; here, they're organized by category.

The letters in parens are aliases.

## Builds
  - `builds` -                     List builds data (**bs**)
  - `abort-build` -                Abort a build (**ab**)
  - `rerun-build` -                Rerun a build (**rb**)
  - `execute` -                    Execute a one-off build using local bits (**e**)
  - `watch` -                      Stream a build's output (**w**)

## Resources
  - `resources` -                  List the resources in the pipeline (**rs**)
  - `pin-resource` -               Pin a version to a resource (**pr**)
  - `resource-versions` -          List the versions of a resource (**rvs**)
  - `unpin-resource` -             Unpin a resource (**ur**)
  - `check-resource` -             Check a resource (**cr**)
  - `check-resource-type` -        Check a resource-type (**crt**)
  - `clear-resource-cache` -       Clear cache of a resource (**crc**)
  - `clear-versions` -             Clear versions of a resource or resource type (**cv**)
  - `disable-resource-version` -   Disable a version of a resource (**drv**)
  - `enable-resource-version` -    Enable a version of a resource (**erv**)

## Targets
  - `targets` -                    List saved targets (**ts**)
  - `delete-target` -              Delete target (**dtg**)
  - `edit-target` -                Edit a target (**etg**)
  - `status` -                     Login status
  - `login` -                      Authenticate with the target (**l**)
  - `logout` -                     Release authentication with the target (**o**)
  - `sync` -                       Download and replace the current fly from the target (**s**)

## Pipelines
  - `pipelines` -                  List the configured pipelines (**ps**)
  - `set-pipeline` -               Create or update a pipeline's configuration (**sp**)
  - `unpause-pipeline` -           Un-pause a pipeline (**up**)
  - `expose-pipeline` -            Make a pipeline publicly viewable (**ep**)
  - `format-pipeline` -            Format a pipeline config (**fp**)
  - `get-pipeline` -               Get a pipeline's current configuration (**gp**)
  - `checklist` -                  Print a Checkfile of the given pipeline (**cl**)
  - `hide-pipeline` -              Hide a pipeline from the public (**hp**)
  - `pause-pipeline` -             Pause a pipeline (**pp**)
  - `paused-pipelines` -           List the configured paused pipelines (**pps**)
  - `order-instanced-pipelines` -  Orders instanced pipelines w/in an instance group (**oip**)
  - `order-pipelines` -            Orders pipelines (**op**)
  - `rename-pipeline` -            Rename a pipeline (**rp**)
  - `validate-pipeline` -          Validate a pipeline config (**vp**)
  - `archive-pipeline` -           Archive a pipeline (**ap**)
  - `destroy-pipeline` -           Destroy a pipeline (**dp**)

## Jobs
  - `jobs` -                       List the jobs in the pipelines (**js**)
  - `pause-job` -                  Pause a job (**pj**)
  - `paused-jobs` -                List the paused jobs in the pipelines (**pjs**)
  - `schedule-job` -               Request the scheduler to run for a job. Introduced as a recovery command for the v6.0 scheduler. (**sj**)
  - `trigger-job` -                Start a job in a pipeline (**tj**)
  - `unpause-job` -                Unpause a job (**uj**)

## Teams and Users
  - `userinfo` -                   User information
  - `active-users` -               List the active users since a date or for the past 2 months (**au**)
  - `teams` -                      List the configured teams (**t**)
  - `rename-team` -                Rename a team (**rt**)
  - `get-team` -                   Show team configuration (**gt**)
  - `set-team` -                   Create or modify a team to have the given credentials (**st**)
  - `destroy-team` -               Destroy a team and delete all of its data (**dt**)

## Containers
  - `containers` -                 Print the active containers (**cs**)
  - `hijack` -                     Execute a command in a container (**intercept, i**)
  - `clear-task-cache` -           Clears cache from a task container (**ctc**)

## Workers
  - `workers` -                    List the registered workers (**ws**)
  - `prune-worker` -               Prune a stalled, landing, landed, or retiring worker (**pw**)
  - `land-worker` -                Land a worker (**lw**)

## Misc
  - `curl` -                       curl the api (**c**)
  - `help` -                       Print this help message
  - `volumes` -                    List the active volumes (**vs**)
  - `completion` -                 generate shell completion code

