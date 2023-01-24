# Inputs and Outputs: Using Resources in Job Tasks

## Using resource outputs for task inputs
The sample code lives in `tutorials/basic/job-inputs`.

Add the pipeline and unpause it.

- An app is retrieved via `get` of the `resource-app` git resource.
- Test scripts are retrieved via `get` of the `resource-tutorial` git resource.
- The `web-app-tests` script is run from the previously retrieved resource directory. 

Notice that when the pipeline is unpaused, the job automatically starts.

(Notice also how `task_run_test.yml` uses the `path` attribute to copy the `resource-app` output to an alternate path to use for its input, so as to make Go testing happy).

## Using task outputs for subsequent task inputs
The sample code lives in `tutorials/basic/task-outputs-to-inputs`.

The git resources in the previous example auto-created output that were used by subsequent tasks as input.

What about tasks that create output?  Let's see how to pass that output to a later task as input.

A task can declare `outputs:`.  **The name of the output corresponds to the name of the directory in which the next task will find those outputs.**

The first task (whose source code is retrieved via the git resource) creates some files.  (Note the `mkdir some-files` is unnecessary; Concourse goes ahead and does this).

The second task specifies `some-files` as its input, and runs a script that lists them.

