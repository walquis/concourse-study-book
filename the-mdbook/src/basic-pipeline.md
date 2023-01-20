# Basic Pipeline

```
$ cd basic-pipeline
$ ft set-pipeline -c pipeline.yml -p hello-world
$ ft unpause-pipeline -p hello-world
$ ft unpause-job -j hello-world/job-hello-world
```
This first pipeline is unimpressive - a single job job-hello-world with no inputs from the left and no outputs to its right, no jobs feeding into it, nor jobs feeding from it. It is the most basic pipeline. The job is gray colour because it has never been run before.

A blue bar across top of a pipeline means it's paused.
