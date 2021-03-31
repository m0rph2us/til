# til
Today I learned :P

# 2021-03-31
## 05:31

```
FROM alpine:3.13.3

WORKDIR /jmx-exporter-agent

ENV VERSION=0.15.0

RUN wget "https://repo1.maven.org/maven2/io/prometheus/jmx/jmx_prometheus_javaagent/${VERSION}/jmx_prometheus_javaagent-${VERSION}.jar"
```

https://github.com/prometheus/jmx_exporter

```
java -javaagent:./jmx_prometheus_javaagent-0.15.0.jar=8080:config.yaml -jar yourJar.jar
```

# 2021-03-30
## 11:19

self signed certificate in certificate chain

```
yarn config set "strict-ssl" false
npm config set strict-ssl false --global
```

* https://medium.com/@jonatascastro12/understanding-self-signed-certificate-in-chain-issues-on-node-js-npm-git-and-other-applications-ad88547e7028
* https://rios.tistory.com/entry/React-npm-yarn-%EC%84%A4%EC%B9%98-%EC%98%A4%EB%A5%98-error-An-unexpected-error-occurred
