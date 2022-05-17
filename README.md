# Kafka Event Streaming Applications

This example and accompanying tutorial show users how to deploy an Apache Kafka® event streaming application using [ksqlDB](https://ksqldb.io?utm_source=github&utm_medium=demo&utm_campaign=ch.cp-demo_type.community_content.cp-demo) and [Kafka Streams](https://docs.confluent.io/platform/current/streams/index.html?utm_source=github&utm_medium=demo&utm_campaign=ch.cp-demo_type.community_content.cp-demo) for stream processing. All the components in the Confluent Platform have security enabled end-to-end. Run the example with the [tutorial](https://docs.confluent.io/platform/current/tutorials/cp-demo/docs/index.html?utm_source=github&utm_medium=demo&utm_campaign=ch.cp-demo_type.community_content.cp-demo).

**Table of Contents**

- [Overview](#overview)
- [Documentation](#documentation)


## Overview

The use case is a Kafka event streaming application for real-time edits to real Wikipedia pages.
Wikimedia's EventStreams publishes a continuous stream of real-time edits happening to real wiki pages.
Using Kafka Connect, a Kafka source connector `kafka-connect-sse` streams raw messages for the server sent events (SSE), and a custom Kafka Connect transform `kafka-connect-json-schema` transforms these messages and then the messages are written to a Kafka cluster.
This example uses ksqlDB and a Kafka Streams application for data processing.
Then a Kafka sink connector `kafka-connect-elasticsearch` streams the data out of Kafka and is materialized into Elasticsearch for analysis by Kibana.
Confluent Replicator  is also copying messages from a topic to another topic in the same cluster.
All data is using Confluent Schema Registry and Avro.
Confluent Control Center is managing and monitoring the deployment.

![image](docs/images/cp-demo-overview.jpg)

## nginx requirements

The example uses nginx with deferred DNS resolution to allow access to Kafka via nginx. To do this, you need to put in entries in /etc/hosts for kafak1 and kafka2

```
127.0.0.1 kafka1
127.0.0.1 kafka2
```

I did have to change the listener from SASL_PLAINTEXT to SASL_SSL so to use this you'd need to add in the right configs and credentials from the client to use it.


## Documentation

You can find the documentation for running this example and its accompanying tutorial at [https://docs.confluent.io/platform/current/tutorials/cp-demo/docs/index.html](https://docs.confluent.io/platform/current/tutorials/cp-demo/docs/index.html?utm_source=github&utm_medium=demo&utm_campaign=ch.cp-demo_type.community_content.cp-demo).

# Additional Examples

For additional examples that showcase streaming applications within an event streaming platform, please refer to the [examples GitHub repository](https://github.com/confluentinc/examples).
