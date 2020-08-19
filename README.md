![HyScale](https://www.hyscale.io/wp-content/uploads/2019/01/hyscale-logo.png)

### Hyscale Spec

##### A Simplified Specification for developing cloud native applications as well doing app level operations.

Hspec is used to declaratively describe the service and its related configuration. It provides abstraction on top of its deployment infrastructure. It enables users to operate on top of applications & services rather than low level infrastructure resource objects.

The Hprof file is meant for environment related overrides/differences, it can override certain service related configurations like memory & cpu sizes, secrets, no.of replicas etc.

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
 
external: true
ports:
  - port: 8080/tcp
    healthCheck:
       httpPath: /docs/images/tomcat.gif
```

Here is the detailed [documentation](docs/hyscale-spec-reference.md). 
