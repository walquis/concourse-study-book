# Overview and Setup

[The Stark & Wayne Tutorial](https://concoursetutorial.com/) - since 2015

[My fork of the corresponding git repo](https://github.com/walquis/concourse-tutorial-stark-and-wayne)

[The Concourse System - concourse-ci.org](https://concourse-ci.org)

# Getting Started
1. Install Docker, and Docker Compose
1. Deploy Concourse using Docker Compose
1. Install the `fly` CLI, with `brew install --cask fly`


You will need to set CONCOURSE_EXTERNAL_URL to your mac's IP address, so that you can login to the concourse web UI.
```
      - CONCOURSE_EXTERNAL_URL=http://10.8.57.64
```

If you have an M1 Mac, use this docker-compose.yaml instead of the one obtained with `wget` below...
```
---
version: "3"

services:
  concourse-db:
    image: postgres
    environment:
      - POSTGRES_DB=concourse
      - POSTGRES_PASSWORD=concourse_pass
      - POSTGRES_USER=concourse_user
      - PGDATA=/database

  concourse:
    image: rdclda/concourse:7.8.3
    command: quickstart
    privileged: true
    depends_on: [concourse-db]
    ports: ["8080:8080"]
    environment:
      - CONCOURSE_POSTGRES_HOST=concourse-db
      - CONCOURSE_POSTGRES_USER=concourse_user
      - CONCOURSE_POSTGRES_PASSWORD=concourse_pass
      - CONCOURSE_POSTGRES_DATABASE=concourse
      # replace this with your external IP address
      - CONCOURSE_EXTERNAL_URL=http://10.8.57.64:8080
      - CONCOURSE_ADD_LOCAL_USER=test:test
      - CONCOURSE_MAIN_TEAM_LOCAL_USER=test
      # instead of relying on the default "detect"
      - CONCOURSE_WORKER_BAGGAGECLAIM_DRIVER=overlay
      - CONCOURSE_CLIENT_SECRET=Y29uY291cnNlLXdlYgo=
      - CONCOURSE_TSA_CLIENT_SECRET=Y29uY291cnNlLXdvcmtlcgo=
      - CONCOURSE_X_FRAME_OPTIONS=allow
      - CONCOURSE_CONTENT_SECURITY_POLICY=*
      - CONCOURSE_CLUSTER_NAME=arm64
      - CONCOURSE_WORKER_CONTAINERD_DNS_SERVER=8.8.8.8
      - CONCOURSE_WORKER_RUNTIME=houdini
```

Example of starting up with the above docker-compose-m1.yml:
```
wget https://raw.githubusercontent.com/starkandwayne/concourse-tutorial/master/docker-compose.yml
# Or, use the docker-compose-m1.yml above...
docker-compose -f docker-compose-m1.yml up -d
```
## Login with `fly`
```
fly --target=tutorial login --concourse-url=http://10.8.57.64:8080 --username=test --password=test
fly --target=tutorial sync
cat ~/.flyrc
```
You have to specify the `target` with every command.  I added this alias to my `.zshrc`...
```
alias ft="fly -t tutorial"
```

