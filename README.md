# Docker - Atlassian JIRA Core

This is a Docker-Image for Atlassian JIRA Core based on Debian 9.

## Getting started
Run Atlassian JIRA Core standalone and navigate to `http://[dockerhost]:8080` to finish configuration:

```bash
docker run -ti -p 8080:8080 streacs/atlassian-jira-core:x.x.x
```

## Environment Variables
* (O) JVM_ARGUMENTS =
* (I) SYSTEM_USER = jira
* (I) SYSTEM_GROUP = jira
* (I) SYSTEM_HOME = /home/jira
* (I) APPLICATION_INST = /opt/atlassian/jira
* (I) APPLICATION_HOME = /var/opt/atlassian/application-data/jira
* (O) TOMCAT_PROXY_NAME = www.example.com
* (O) TOMCAT_PROXY_PORT = 80|443
* (O) TOMCAT_PROXY_SCHEME = http|https
* (O) TOMCAT_PROXY_SECURE = false|true
* (O) JVM_MEMORY_MIN = 1024m
* (O) JVM_MEMORY_MAX = 2048m

(M) = Mandatory / (O) = Optional / (I) Information

## Ports
* 8080 = Default HTTP Connector

## Volumes
* /var/opt/atlassian/application-data/jira

## Examples

Modify JVM memory
```bash
docker run -ti -e ORACLE_JAVA_EULA=accepted -p 8080:8080 -e JVM_MEMORY_MIN=1024m -e JVM_MEMORY_MAX=2048m streacs/atlassian-jira-core:x.x.x
```

Persist application data
```bash
docker run -ti -e ORACLE_JAVA_EULA=accepted -p 8080:8080 -v JIRA-DATA:/var/opt/atlassian/application-data/jira streacs/atlassian-jira-core:x.x.x
```

## Databases

This image doesn't include the MySQL JDBC driver.
Please use PostgreSQL.

## Source Code
[Github](https://github.com/streacs/docker_atlassian_jira_core)

## License
This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details