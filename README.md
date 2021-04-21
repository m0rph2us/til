# til

Today I learned :P

# 2021-04-21
## 09:50

* AWS DMS Components : https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Introduction.Components.html
* Choosing the right DMS replication instance : https://docs.aws.amazon.com/dms/latest/userguide/CHAP_ReplicationInstance.Types.html 
  * At least C4 is a good choice
* AWS DMS support for AWS CloudFormation : https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Introduction.AWS.html
* Getting started : https://docs.aws.amazon.com/dms/latest/userguide/CHAP_GettingStarted.html
* AWS Schema Conversion Tool (AWS SCT) : If source and target engines are different 
* Using SSL with DMS : https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Security.html#CHAP_Security.SSL

In case of Oracle, You should enable the `supplemental_log_data_min` attribute.

>Last Error Failed in resolving configuration. Task error notification received from subtask 0, thread 0 [reptask/replicationtask.c:2859] [1020418] CDC cannot be provided because supplemental_log_data_min in v$database is set to NO; Minimal database supplemental logging level is not enabled; Failed while preparing stream component 'st_0_GMFJZ4YM6I64WI2BSNP2CP2LTHDMMHDHAAGL3WI'.; Cannot initialize subtask; Stream component 'st_0_GMFJZ4YM6I64WI2BSNP2CP2LTHDMMHDHAAGL3WI' terminated [reptask/replicationtask.c:2866] [1020418] Stop Reason FATAL_ERROR Error Level FATAL

> Last Error ARCHIVELOG mode is not configured in the Oracle instance Task error notification received from subtask 0, thread 0 [reptask/replicationtask.c:2859] [1022313] To use CDC, the Oracle database must be configured to archived Redo logs; Failed while preparing stream component 'st_0_GMFJZ4YM6I64WI2BSNP2CP2LTHDMMHDHAAGL3WI'.; Cannot initialize subtask; Stream component 'st_0_GMFJZ4YM6I64WI2BSNP2CP2LTHDMMHDHAAGL3WI' terminated [reptask/replicationtask.c:2866] [1022313] Stop Reason FATAL_ERROR Error Level FATAL

* Using Oracle as a source : https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Source.Oracle.html



# 2021-04-12
## 17:32

https bypass with haproxy.

* https://tossolution.com/2019/04/haproxy-ssl-bypass/
* https://www.haproxy.com/blog/how-to-get-ssl-with-haproxy-getting-rid-of-stunnel-stud-nginx-or-pound/
* https://www.haproxy.com/blog/haproxy-ssl-termination/

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
