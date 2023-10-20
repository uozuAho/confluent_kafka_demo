# Kafka dotnet demo, using confluent cloud

Following this tute: https://developer.confluent.io/get-started/dotnet

# Prerequisites
- [confluent cloud account](https://confluent.cloud/)
- [confluent cloud cli](https://docs.confluent.io/confluent-cli/current/install.html)

# Steps
Assuming a completely blank confluent cloud account.

- create a cluster named DotnetDemo in confluent cloud
- create a cluster API key
- create a file ./demo.properties with your values: https://developer.confluent.io/get-started/dotnet/#configuration

```sh
confluent login
confluent kafka cluster list
confluent kafka cluster use lkc-do1mzz  # replace with your cluster's id
confluent kafka topic create purchases --partitions 1

# in either order
./run_producer.sh
./run_consumer.sh
```

# Schema registry (in progress)
```sh
export SCHEMA_REGISTRY_BASIC_AUTH_USER_INFO=<SR API KEY>:<SR API SECRET>
export SCHEMA_REGISTRY_URL=<SR ENDPOINT>

curl --silent -X GET -u $SCHEMA_REGISTRY_BASIC_AUTH_USER_INFO $SCHEMA_REGISTRY_URL/subjects | jq .

# keep following https://docs.confluent.io/platform/current/schema-registry/schema_registry_ccloud_tutorial.html#using-curl-to-interact-with-schema-registry
```

## todo
- fix broken producer - move schema registry config somewhere else
- get producer consumer working. see: https://github.com/confluentinc/confluent-kafka-dotnet/blob/master/examples/AvroGeneric/Program.cs
