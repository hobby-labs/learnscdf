# Learn SCDF

# Install SCDF environment on your machine

```
$ wget -O docker-compose.yml https://raw.githubusercontent.com/spring-cloud/spring-cloud-dataflow/v2.6.1/spring-cloud-dataflow-server/docker-compose.yml
$ DATAFLOW_VERSION=2.6.1 SKIPPER_VERSION=2.5.1 docker-compose up
```

The command specified environment variables `DATAFLOW_VERSION`, `SKIPPER_VERSION`.
You can also specify other variables.
Variables you can specify are in the link below.

https://dataflow.spring.io/docs/installation/local/docker/#starting-docker-compose

Ports that will be used by default are like below.

| Port        | Condition |
| ----------- | --------- |
| 9393        | Data flow server. You can see the dashboard at http://localhost:9393/dashboard |
| 7577        | Skipper server. You can see the Skipper REAST api at http://localhost:7577/api |
| 20000-20105 | Skipper and Local Deployer. These range of port will be used by stream applications |

# Spring Cloud Data Flow Shell

```
$ docker exec -ti dataflow-server java -jar shell.jar
```

## Host file system

By default docker-compose.yml mounts the local host folter to a `/root/scdf` that mounted on the containers `dataflow-server` and `skipper` containers.
The mount point can be changed by settings the environment variables like below.

```
exoprt HOST_MOUNT_PATH=/tmp/myapps
```

## Register applications

```
$ app register --type source --name my-app --uri file://root/scdf/my-app-1.0.0.RELEASE.jar
```




# References
[Getting Started with Stream Processing](https://dataflow.spring.io/docs/stream-developer-guides/getting-started/stream/)
