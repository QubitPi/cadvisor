[cAdvisor] (Container Advisor) provides Docker container users an understanding of
the resource usage and performance characteristics of their running containers. It is a running daemon that collects,
aggregates, processes, and exports information about running containers. Specifically, for each container it keeps
resource isolation parameters, historical resource usage, histograms of complete historical resource usage and network
statistics. This data is exported by container and machine-wide.

Although [cAdvisor] has some prelimilary (useful though) UI. It also offers

1. [RESTful API to query container stats](https://github.com/google/cadvisor/blob/master/docs/api.md)
2. [Export capability to common data storage, such as Elasticsearch](https://github.com/google/cadvisor/blob/master/docs/storage/README.md)

To pull the image and run it:

```bash
sudo docker run \
    --volume=/:/rootfs:ro \
    --volume=/var/run/docker.sock:/var/run/docker.sock:rw \
    --volume=/sys:/sys:ro \
    --volume=/var/lib/docker/:/var/lib/docker:ro \
    --volume=/dev/disk/:/dev/disk:ro \
    --publish=8080:8080 \
    --detach=true \
    --name=cadvisor \
    --privileged \
    --device=/dev/kmsg \
    gcr.io/cadvisor/cadvisor:v0.36.0
```

![cAdvisor Screenshot 1](img/cadvisor-1.png)
![cAdvisor Screenshot 2](img/cadvisor-2.png)

### [docker-container-stats](https://github.com/virtualzone/docker-container-stats)

[cAdvisor](https://github.com/google/cadvisor) is good for customizing container monitoring, but it's heavy. A
quick-and-lightweight option would be [docker-container-stats](https://github.com/virtualzone/docker-container-stats)

![docker-container-stats Screenshot](img/docker-container-stats.png)

[cAdvisor]: https://github.com/google/cadvisor
