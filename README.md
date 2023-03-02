# Checking cluster, partitions and replicas

- Start cluster
```sh
user@host:~/kraft-kafka-cluster-docker-compose> docker compose up
```

- Access `node-0` container
```sh
user@host:~/kraft-kafka-cluster-docker-compose> docker compose exec node-0 /usr/bin/env bash
```

- Create topic from `node-0`
```sh
I have no name!@node-0:/$ kafka-topics.sh --bootstrap-server node-0:9092 --create --if-not-exists --topic some_topic_name
```

- Check partitions and replicas from `node-0`
```sh
I have no name!@node-0:/$ kafka-topics.sh --bootstrap-server node-0:9092 --describe --if-exists --topic some_topic_name
```

```log
Topic: some_topic_name	TopicId: PuZuoWsYTFuko_HtJ6QmUQ	PartitionCount: 3	ReplicationFactor: 3	Configs: 
	Topic: some_topic_name	Partition: 0	Leader: 0	Replicas: 0,1,2	Isr: 0,1,2
	Topic: some_topic_name	Partition: 1	Leader: 1	Replicas: 1,2,0	Isr: 1,2,0
	Topic: some_topic_name	Partition: 2	Leader: 2	Replicas: 2,0,1	Isr: 2,0,1
```

- Access `node-1` container
```sh
user@host:~/kraft-kafka-cluster-docker-compose> docker compose exec node-1 /usr/bin/env bash
```

- Check partitions and replicas from `node-1`
```sh
I have no name!@node-1:/$ kafka-topics.sh --bootstrap-server node-1:9092 --describe --if-exists --topic some_topic_name
```

```log
Topic: some_topic_name	TopicId: PuZuoWsYTFuko_HtJ6QmUQ	PartitionCount: 3	ReplicationFactor: 3	Configs: 
	Topic: some_topic_name	Partition: 0	Leader: 0	Replicas: 0,1,2	Isr: 0,1,2
	Topic: some_topic_name	Partition: 1	Leader: 1	Replicas: 1,2,0	Isr: 1,2,0
	Topic: some_topic_name	Partition: 2	Leader: 2	Replicas: 2,0,1	Isr: 2,0,1
```

- Access `node-2` container
```sh
user@host:~/kraft-kafka-cluster-docker-compose> docker compose exec node-2 /usr/bin/env bash
```

- Check partitions and replicas from `node-2`
```sh
I have no name!@node-2:/$ kafka-topics.sh --bootstrap-server node-2:9092 --describe --if-exists --topic some_topic_name
```

```log
Topic: some_topic_name	TopicId: PuZuoWsYTFuko_HtJ6QmUQ	PartitionCount: 3	ReplicationFactor: 3	Configs: 
	Topic: some_topic_name	Partition: 0	Leader: 0	Replicas: 0,1,2	Isr: 0,1,2
	Topic: some_topic_name	Partition: 1	Leader: 1	Replicas: 1,2,0	Isr: 1,2,0
	Topic: some_topic_name	Partition: 2	Leader: 2	Replicas: 2,0,1	Isr: 2,0,1
```
