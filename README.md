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
bin/kafka-topics.sh --create --zookeeper localhost:2181 --topic demo
```