# Instructions initial setup
1. Set up Kafka CLI, by adding kafka_2.12-2.6.0/bin to PATH
2. mkdir kafka_2.12-2.6.0/data
3. mkdir kafka_2.12-2.6.0/data/zookeeper
4. mkdir kafka_2.12-2.6.0/data/kafka
5. In kafka_2.12-2.6.0/config/zookeeper.properties set dataDir=/home/$NAME/kafka_2.12-2.6.0/data/zookeeper
6. In kafka_2.12-2.6.0/config/zookeeper.properties set log.dirs=/home/$NAME/kafka_2.12-2.6.0/data/kafka


# Start zookeeper/kafka
1. Start zookeeper: zookeeper-server-start.sh config/zookeeper.properties
2. Start kafka: kafka-server-start.sh config/server.properties


# Topics
1. Create: kafka-topics.sh --bootstrap-server localhost:9092 --topic TOPIC_NAME --create --partitions 3 --replication-factor 1
2. Details of Specific Topic: kafka-topics.sh --bootstrap-server localhost:9092 --topic TOPIC_NAME --describe
3. List all topics: kafka-topics.sh --bootstrap-server localhost:9092 --list
4. Delete Topic: kafka-topics.sh --bootstrap-server localhost:9092 --topic second_topic --delete


# Producers
1. Create General Producer: kafka-console-producer.sh --bootstrap-server localhost:9092 --topic TOPIC_NAME # if topic name does not exist will create one on first stream of data
2. Create With Write confirmation: kafka-console-producer.sh --bootstrap-server localhost:9092 --topic TOPIC_NAME --producer-property acks=all # acks is write confirmation, 0, 1, all


# Consumers
1. Create: kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic TOPIC_NAME
2. Create and Read From Beginning: kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic TOPIC_NAME --from-beginning 
3. Create Consumer in Group: kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic TOPIC_NAME --group APP-NAME # one consumer in group per partition



