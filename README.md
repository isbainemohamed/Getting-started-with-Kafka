# Getting-started-with-Kafka
This repository contains a small project to get started with Kafka
## Objectives
After completing this lab we will be able to:

- Download and install Kafka
- Start the Zookeeper server for Kafka metadata management
- Start the Kafka message broker service
- Create a topic
- Start a producer
- Start a consumer

### Download and install Kafka:

Open a new terminal in your linux machine
Run the commands below on the newly opened terminal. (You can copy the code by clicking on the little copy button on the bottom right of the codeblock below and then paste it, wherever you wish.)

Download Kafka, by running the command below:

```bash
wget https://archive.apache.org/dist/kafka/2.8.0/kafka_2.12-2.8.0.tgz
```
![alt text](https://github.com/isbainemohamed/Getting-started-with-Kafka/blob/bb2edf4be72ee8e5ec7ce9110eb36973b487c2ce/images/1-downloading_kafka.png)

Extract kafka from the zip file by running the command below.

```bash
tar -xzf kafka_2.12-2.8.0.tgz
```

![alt text](https://github.com/isbainemohamed/Getting-started-with-Kafka/blob/bb2edf4be72ee8e5ec7ce9110eb36973b487c2ce/images/2-unziping.png)

This creates a new directory 'kafka_2.12-2.8.0' in the current directory.

### Run the ZooKeeper and the Broker:

Move to the created directory and run the Zookeper

```bash
cd kafka_2.12-2.8.0 
bin/zookeeper-server-start.sh config/zookeeper.properties
```
![alt text](https://github.com/isbainemohamed/Getting-started-with-Kafka/blob/bb2edf4be72ee8e5ec7ce9110eb36973b487c2ce/images/3-start-the-zoo-keeper.png)

ZooKeeper, as of this version, is required for Kafka to work. ZooKeeper is responsible for the overall management of Kafka cluster. It monitors the Kafka brokers and notifies Kafka if any broker or partition goes down, or if a new broker or partition goes up.

Start a new terminal.
Run the commands below. This will start the Kafka message broker service.

```bash
cd kafka_2.12-2.8.0
bin/kafka-server-start.sh config/server.properties
```

![alt text](https://github.com/isbainemohamed/Getting-started-with-Kafka/blob/bb2edf4be72ee8e5ec7ce9110eb36973b487c2ce/images/4-starting-broker-server.png)


### Create new Topic , producer and consumer:
Now we need to create a topic before you can start to post messages.

To create a topic named news, start a new terminal and run the command below.

```bash
cd kafka_2.12-2.8.0
bin/kafka-topics.sh --create --topic news --bootstrap-server localhost:9092
```
You will see the message: 'Created topic news.'
![alt text](https://github.com/isbainemohamed/Getting-started-with-Kafka/blob/bb2edf4be72ee8e5ec7ce9110eb36973b487c2ce/images/5-create-topic.png)

Now we need a producer to send messages to Kafka. Run the command below to start a producer.

```bash
bin/kafka-console-producer.sh --topic news --bootstrap-server localhost:9092
```

Once the producer starts, and you get the '>' prompt, type any text message and press enter. Or you can copy the text below and paste. The below text sends three messages to kafka.

```
Good morning
Good day
Enjoy the Kafka lab
```

![alt text](https://github.com/isbainemohamed/Getting-started-with-Kafka/blob/3d897697cd0cf1af9ca054fe4f1084b0c7f0f312/images/6-%20creating%20produceer%20and%20send%20messages.png)

Now we need a consumer to read messages from kafka.

we open a new terminal. And we run the command below to listen to the messages in the topic news:

```bash
cd kafka_2.12-2.8.0
bin/kafka-console-consumer.sh --topic news --from-beginning --bootstrap-server localhost:9092
```

You should see all the messages you sent from the producer appear here.
![alt text](https://github.com/isbainemohamed/Getting-started-with-Kafka/blob/fb5092a4373c27877ec3cba43cdb2f8086d7ba84/images/7-cearting%20producer.png)

You can go back to the producer terminal and type some more messages, one message per line, and you will see them appear here.

### Clean up:

Delete the kafka installation file.
```bash
rm kafka_2.12-2.8.0.tgz
```


##


