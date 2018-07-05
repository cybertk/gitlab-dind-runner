# gitlab-dind-runner

> GitLab runner with docker support


Deploy a central docker-host with [docker:dind]()

```
docker run --privileged --name docker-host -d --restart always docker:18.05.0-dind
```

Verify dind deployment with

```
docker run --rm --link docker-host:docker docker:18.05.0 version
```

Start a GitLab Runner

```
docker run -d --name gitlab-runner --restart always -v /var/run/docker.sock:/var/run/docker.sock     gitlab/gitlab-runner:latest
```

Configure the new created Runner with

```
docker exec -it gitlab-runner gitlab-runner register
```

Add the following contents into `/etc/gitlab-runner/config.toml`


## References

- [Using Docker Images in GitLab](http://doc.gitlab.com/ci/docker/using_docker_images.html#how-to-use-other-images-as-services)
