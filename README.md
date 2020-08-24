![HyScale](https://www.hyscale.io/wp-content/uploads/2019/01/hyscale-logo.png)

### hspec

##### An Application centric Specification for deploying cloud native applications.

hspec (Service Specification) is used to declaratively describe the service and its related configuration. It provides abstraction on top of kubernetes deployment infrastructure. It enables users to operate on top of applications & services rather than low level infrastructure resource objects.

Additionally the hprof (Environment Profile) file is meant for environment related overrides/differences. It can override certain service related configurations like memory & cpu sizes, secrets, no.of replicas etc for specific Environments such as testing, staging, production etc.

A simple hspec looks like :

```yaml
name: myservice
image:
    registry: registry.hub.docker.com
    name: library/tomcat
    tag: 8.5.0-jre8
 
volumes:
    - name: tomcat-logs-dir
      path: /usr/local/tomcat/logs

replicas: 2
external: true
ports:
  - port: 8080/tcp
    healthCheck:
       httpPath: /docs/images/tomcat.gif
```

A sample hprof looks like below:

```yaml
environment: stage
overrides: myservice
volumes:
    - name: tomcat-logs-dir
      size: 2Gi

replicas:
    min: 1
    max: 4
    cpuThreshold: 30%
```

For full spec reference [click here](docs/hyscale-spec-reference.md). 

hspec runtime implementation is [HyScale](https://github.com/hyscale/hyscale) tool, to get started with an example of using hspec to deploy application kubernetes Applications please follow hyscale [tutorial](https://github.com/hyscale/hyscale/wiki/Tutorial).
