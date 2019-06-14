# Our Stack

Most of our code is in Scala and most engineers use the IntelliJ IDE. We use a handful of [akka modules](https://akka.io/docs/) including HTTP, Streams, and Aplakka.

We run our production environment on AWS, with a bit of [redislabs](https://redislabs.com/), [CloudAMQP](https://www.cloudamqp.com/), and [Heroku](https://www.heroku.com/) as well. Most of our stack is deployed straight to EC2, but we're increasingly moving to [Docker](https://www.docker.com/) and [kubernetes](https://kubernetes.io/). We have a few hundred terabytes of [Elasticsearch](https://elastic.co/) running in self-managed clusters on EC2.

We move a lot of data around in messaging systems. Today that is largely RabbitMQ and Kafka, but we are experimenting with [Apache Pulsar](https://pulsar.apache.org/) which we hope will replace both of these systems. Pulsar promises better performance and uptime than RabbitMQ, while allowing many more independent data streams than Kafka.
