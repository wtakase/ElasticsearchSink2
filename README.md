# ElasticsearchSink2

This is Flume-NG Sink for Elasticsearch >= 2.0 and SearchGuard.
I developed this because the official version does not support Elasticsearch >= 2.0 due to API changes.
Hope Flume dev team will fix this soon.


# Requirements

- Flume-NG >= 1.6
- Elasticsearch >= 2.0
- SearchGuard SSL

# Build

Build standard jar by the following command

```bash
$ ./gradlew build
```

Build fat jar which contains elasticsearch and search-guard-ssl dependencies
```bash
$ ./gradlew assembly
```

Jar will be generated in `build/libs`


# Usage

1. Append the built jar to Flume's classpath
2. remove `guava-*.jar` and `jackson-core-*.jar` in flume's default libs dir. They are outdated and newer version are included in Elasticsearch.
3. set sink type to `com.frontier45.flume.sink.elasticsearch2.ElasticSearchSink` in flume.conf
4. start flume agent

# SSL Usage

```
agent.sinks.exampleSink.ssl = true
agent.sinks.exampleSink.sslCertVerify = true
agent.sinks.exampleSink.truststore = /path/to/truststore.jks
agent.sinks.exampleSink.truststorePassword = changeit
agent.sinks.exampleSink.keystore = /path/to/keystore.jks
agent.sinks.exampleSink.keystorePassword = changeit
agent.sinks.exampleSink.keystoreAlias = some_alias
```
