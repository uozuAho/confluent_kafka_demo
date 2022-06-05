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
```
