# instantsolutions/gitlab-ci-android-runner:1.0.0
A docker image with gitlab-ci-multi-runner, which can run android builds.

## Getting started

### Installation

Automated builds of the image are available on [Dockerhub](https://hub.docker.com/r/instantsolutions/gitlab-ci-android-runner).

```bash
docker pull instantsolutions/gitlab-ci-android-runner:1.0.0
```

Alternatively you can build the image yourself.

```bash
docker build -t instantsolutions/gitlab-ci-android-runner github.com/instant-solutions/docker-gitlab-ci-android-runner
```

### Running without persistence

```bash
docker run --name gitlab-ci-android-runner -d --restart=always \
  --env='CI_SERVER_URL=http://your.gitlab.host/ci' --env='RUNNER_TOKEN=token' \
  --env='RUNNER_DESCRIPTION=androidrunner' --env='RUNNER_EXECUTOR=shell' \
  instantsolutions/gitlab-ci-android-runner:1.0.0
```

Update the values of `CI_SERVER_URL`, `RUNNER_TOKEN` and `RUNNER_DESCRIPTION` in the above command. If these enviroment variables are not specified, you will be prompted to enter these details interactively on first run.

### Running with persistence

```bash
docker run --name gitlab-ci-android-runner -d --restart=always \
  --volume /srv/docker/gitlab-runner:/home/gitlab_ci_multi_runner/data \
  --env='CI_SERVER_URL=http://your.gitlab.host/ci' --env='RUNNER_TOKEN=token' \
  --env='RUNNER_DESCRIPTION=androidrunner' --env='RUNNER_EXECUTOR=shell' \
  instantsolutions/gitlab-ci-android-runner:1.0.0
```

Update the values of `CI_SERVER_URL`, `RUNNER_TOKEN` and `RUNNER_DESCRIPTION` in the above command. If these enviroment variables are not specified, you will be prompted to enter these details interactively on first run.


## More information

* Read about [gitlab-ci-multi-runner](https://gitlab.com/gitlab-org/gitlab-ci-multi-runner/) to learn how integration works with GitLab CI.
* This image is based on [docker-gitlab-ci-multi-runner](https://github.com/sameersbn/docker-gitlab-ci-multi-runner), which handles registration and startup.
