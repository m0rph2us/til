# til
Today I learned :P

# 2021-04-12
## 17:32

https bypass with haproxy.

* https://tossolution.com/2019/04/haproxy-ssl-bypass/
* https://www.haproxy.com/blog/how-to-get-ssl-with-haproxy-getting-rid-of-stunnel-stud-nginx-or-pound/

## 15:33

structure of `NLS_LANG`.

```
Determine the NLS_LANG value.
In the data warehouse database, run the command
SELECT * FROM V$NLS_PARAMETERS

Make a note of the NLS_LANG value, which is in the format [NLS_LANGUAGE]_[NLS_TERRITORY].[NLS_CHARACTERSET].
For example: American_America.UTF8
```

# 2021-04-01
## 17:07

use `.` instead of `source`.

https://stackoverflow.com/questions/13702425/source-command-not-found-in-sh-shell

## 12:45

sincedb tracks input files. logstash sincedb default is `<path.data>/plugins/inputs/file`(hidden file). It is clean after if no more file change has detected. see `sincedb_clean_after`(default is 2 weeks) at below link.

https://www.elastic.co/guide/en/logstash/current/plugins-inputs-file.html#plugins-inputs-file-start_position

# 2021-03-31
## 17:31

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
