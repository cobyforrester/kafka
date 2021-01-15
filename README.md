# Instructions initial setup
1. Pull repo in ~
2. Set up Kafka CLI, by adding /home/$NAME/kafka/bin to PATH
3. In kafka/config/zookeeper.properties set dataDir=/home/$NAME/kafka/data/zookeeper
4. In kafka/config/server.properties set log.dirs=/home/$NAME/kafka/data/kafka

<!-- # FOR FRESH KAFKA SETUP
1. Set up Kafka CLI, by adding /home/$NAME/kafka/bin to PATH
2. mkdir kafka/data
3. mkdir kafka/data/zookeeper
4. mkdir kafka/data/kafka
5. In kafka/config/zookeeper.properties set dataDir=/home/$NAME/kafka/data/zookeeper
6. In kafka/config/server.properties set log.dirs=/home/$NAME/kafka/data/kafka -->


# Start zookeeper/kafka, run in kafka directory
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

# Consumer Groups
1. List Current Consumers: kafka-consumer-groups.sh --bootstrap-server localhost:9092 --list
2. Information on Consumer Group: kafka-consumer-groups.sh --bootstrap-server localhost:9092 --describe --group GROUP_NAME
3. List Lagged Messages/Catch Up: kafka-consumer-groups.sh --bootstrap-server localhost:9092 --topic TOPIC_NAME --describe --group GROUP_NAME
4. kafka-consumer-groups.sh --bootstrap-server localhost:9092 --group GROUP_NAME --reset-offsets --to-earliest --execute --topic TOPIC_NAME # possible to use --all-topics












