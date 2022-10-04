# Introduction

This is a sample application showing how to use Testcontainers and Redpanda for writing integration tests in a Spring Boot Kafka application. 

It uses [Redpanda Testcontainers module](https://www.testcontainers.org/modules/redpanda/) which enables straightforward integration and provides additional developer experience enhancements for better integration tests.
For more information please check out the [article about this sample application](https://www.atomicjar.com/2022/10/simplify-development-of-kafka-applications-with-redpanda-and-testcontainers/). 

# Run the tests

Clone the project and run Maven tests: 

```
./mvnw test
```

# A bit more details 

The environment for the integration tests is created by Testcontainers, and to create a Redpanda instance for your application to work with all you need is to instantiate and start a Testcontainers Redpanda class:
```
RedpandaContainer kafka = new RedpandaContainer("docker.redpanda.com/vectorized/redpanda:v22.2.1");
kafka.start();
```

You can see how it's implemented and how the configuration about Redpanda location (host/port) is passed to the Spring Boot app in [the code](https://github.com/shelajev/testcontainers-redpanda/blob/oleg-demo/src/test/java/com/example/demo/com/example/demo/support/AbstractIntegrationTest.java#L50).

