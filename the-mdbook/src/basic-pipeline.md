# Basic Pipeline

```
$ cd tutorials/basic/basic-pipeline

# This updates the entire pipeline
$ ft set-pipeline -c pipeline.yml -p hello-world
$ ft unpause-pipeline -p hello-world
$ ft unpause-job -j hello-world/job-hello-world
```
This first pipeline is unimpressive - a single job job-hello-world with no inputs from the left and no outputs to its right, no jobs feeding into it, nor jobs feeding from it. It is the most basic pipeline. The job is gray colour because it has never been run before.

A blue bar across top of a pipeline means it's paused.

The job is gray 'cause it's never been run (it didn't kick off when it was un-paused, because there are not yet any trigger resources in play).

To run the job: Click the job, then click the big "+" at top right.  Or, from cmd line...
```
$ ft trigger-job -j hello-world/job-hello-world
# or ft tj       -j hello-world/job-hello-world
```

To destroy the pipeline:
```
$ ft dp -p hello-world
```
