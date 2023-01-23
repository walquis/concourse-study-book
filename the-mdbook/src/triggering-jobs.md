# Triggering Jobs

## Four ways to trigger a job
1. Click "+" button on job page of UI
1. Cmd-line, e.g., `ft trigger-job -j <pipeline>/<jobname>`
1. Add a trigger to a resource
1. HTTP POST to Concourse API

## Adding a trigger to a resource

In the plan's `get` of the resource, add `trigger: true`...
```
jobs:
- name: some-job
  plan:
  - get: some-resource
    trigger: true
```

### The `time` resource - specifically for timed triggering of jobs
```
resources:
- name: my-timer
  type: time
  source:
    interval: 2m
...
jobs:
  plan:
    - get: my-timer
      trigger: true
...
```


