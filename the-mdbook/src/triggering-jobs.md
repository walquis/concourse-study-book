# Triggering Jobs

## Four ways to trigger a job
1. Click the big "+" button on the UI's job page.
1. A `fly` command: `ft tj -j <pipeline>/<jobname>`.
1. Add a trigger to a resource.
1. Make an HTTP POST to the Concourse API.

## Adding a trigger to a resource
The code sample lives in `tutorials/basic/triggers`.

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

NOTE: The UI shows non-triggering resources as a hyphenated line into the job. Triggering resources have a solid line.

## Making an API call
Every fly command accepts a `--verbose` option, which prints the request and response (except for the Authorization header).

Authorization is Bearer (aka "token authorization").  You can get the token from `~/.zshrc`.

NOTE: The HTTP response often has much more information than the normal console output.  For instance, the `ft teams --verbose` also makes an `info` API call which has no counterpart in the `fly` command list.

```
$ ft teams --verbose
ft teams --verbose     
2023/01/24 14:19:13 GET /api/v1/info HTTP/1.1
Host: 10.8.57.64:8080
User-Agent: Go-http-client/1.1
Accept-Encoding: gzip


2023/01/24 14:19:13 HTTP/1.1 200 OK
Content-Length: 297
Cache-Control: no-store, private
Content-Security-Policy: *
Content-Type: application/json
Date: Tue, 24 Jan 2023 20:19:13 GMT
Vary: Accept-Encoding
X-Concourse-Version: 7.8.3
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Frame-Options: allow
X-Xss-Protection: 1; mode=block

{"version":"7.8.3","worker_version":"2.4","feature_flags":{"across_step":false,"build_rerun":false,"cache_streamed_volumes":false,"global_resources":false,"pipeline_instances":false,"redact_secrets":false,"resource_causality":false},"external_url":"http://10.8.57.64:8080","cluster_name":"arm64"}

2023/01/24 14:19:13 GET /api/v1/teams HTTP/1.1
Host: 10.8.57.64:8080
User-Agent: Go-http-client/1.1
Accept-Encoding: gzip


2023/01/24 14:19:13 HTTP/1.1 200 OK
Content-Length: 79
Cache-Control: no-store, private
Content-Security-Policy: *
Content-Type: application/json
Date: Tue, 24 Jan 2023 20:19:13 GMT
Vary: Accept-Encoding
X-Concourse-Version: 7.8.3
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Frame-Options: allow
X-Xss-Protection: 1; mode=block

[{"id":1,"name":"main","auth":{"owner":{"groups":[],"users":["local:test"]}}}]

name
main
```
Passing the /api/v1/info JSON thru jq...
```
$ echo '{"sub":"CgR0ZXN0EgVsb2NhbA","name":"test","user_id":"test","user_name":"","email":"test","is_admin":true,"is_system":false,"teams":{"main":["owner"]},"connector":"local","display_user_id":"test"}' | jq
{
  "sub": "CgR0ZXN0EgVsb2NhbA",
  "name": "test",
  "user_id": "test",
  "user_name": "",
  "email": "test",
  "is_admin": true,
  "is_system": false,
  "teams": {
    "main": [
      "owner"
    ]
  },
  "connector": "local",
  "display_user_id": "test"
}
```
$ echo 


