# til

Today I learned :P

# 2021-04-22
## 10:00

>깃헙 dev, stg pr 시 이미 main 으로 머지했던 내용인데 왜 또 diff 에 나올까 궁금해서 찾아봤습니다.
>
>https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/about-comparing-branches-in-pull-requests#three-dot-and-two-dot-git-diff-comparisons

>요약하면 …(뜨리닷) 비교냐 ..(투닷) 비교냐에 따라 다른데, 깃헙은 뜨리닷이라 부모 기점을 기준으로 비교를 해서 그렇다고 합니다. 반면 투닷은 두 브랜치의 끝지점을 가지고 비교하구요. 깃헙은 뜨리닷이 기본이구요. 깃헙에서 투닷을 시뮬레이션 하려면 base -> topic 으로 merge 하면 된다고 합니다. 예를들면 feature-1 을 작업후 develop 으로 pr 할때 develop 을 feature-1 으로 merge 하면 된다고 합니다.

## 10:30

대량 이메일 발송 관련

* https://medium.com/sjk5766/aws-ses-smtp%EB%A5%BC-%ED%99%9C%EC%9A%A9%ED%95%9C-%EB%8C%80%EB%9F%89-%EB%A9%94%EC%9D%BC-%EC%A0%84%EC%86%A1-%EC%8B%9C%EC%8A%A4%ED%85%9C-%EC%A0%95%EB%A6%AC-e32863abbe4c


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

If ARCHIVELOG mode is disabled.

>Last Error ARCHIVELOG mode is not configured in the Oracle instance Task error notification received from subtask 0, thread 0 [reptask/replicationtask.c:2859] [1022313] To use CDC, the Oracle database must be configured to archived Redo logs; Failed while preparing stream component 'st_0_GMFJZ4YM6I64WI2BSNP2CP2LTHDMMHDHAAGL3WI'.; Cannot initialize subtask; Stream component 'st_0_GMFJZ4YM6I64WI2BSNP2CP2LTHDMMHDHAAGL3WI' terminated [reptask/replicationtask.c:2866] [1022313] Stop Reason FATAL_ERROR Error Level FATAL

`supplemental_log_data_min` is enabled. But i got following error.

>Last Error Endpoint initialization failed. Task error notification received from subtask 0, thread 0 [reptask/replicationtask.c:2859] [1020401] Cannot retrieve Oracle archived Redo log destination ids; Failed to set stream position on context '(null)'; Error executing command; Stream component failed at subtask 0, component st_0_GMFJZ4YM6I64WI2BSNP2CP2LTHDMMHDHAAGL3WI; Stream component 'st_0_GMFJZ4YM6I64WI2BSNP2CP2LTHDMMHDHAAGL3WI' terminated [reptask/replicationtask.c:2866] [1020401] Stop Reason FATAL_ERROR Error Level FATAL

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
