# YouTube Tutorial
https://www.youtube.com/watch?v=n_IQq3pze0s

# Blog Tutorial

# Create Docker Network
```
docker network create kafka
```

# Zookeeper
```
docker pull confluentinc/cp-zookeeper
```
```
docker run -d --network=kafka --name=zookeeper -e ZOOKEEPER_CLIENT_PORT=2181 -e ZOOKEEPER_TICK_TIME=2000 -p 2181:2181  confluentinc/cp-zookeeper
```

# Kafka
```
docker pull confluentinc/cp-kafka
```
```
docker run -d --network=kafka --name=kafka -e KAFKA_ZOOKEEPER_CONNECT=zookeeper:2181 -e KAFKA_ADVERTISED_LISTENERS=PLAINTEXT://localhost:9092 -p 9092:9092  confluentinc/cp-kafka
```

# Topic

Create a topic called "demo".

```
docker exec -ti kafka kafka-topics --create --if-not-exists --zookeeper zookeeper:2181 --partitions 1 --replication-factor 1 --topic demo
```

List topics.

```
docker exec -ti kafka kafka-topics --list --zookeeper zookeeper:2181
```