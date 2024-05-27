# Try Kafka
check list
- [apache kafka quickstart](https://kafka.apache.org/quickstart)


## 1. Run Kafka with Docker Container

__docker-compose.yaml file__  
```yaml
services:
  kafka:
    image: apache/kafka:3.7.0
    ports:
      - "9092:9092"
    container_name: kafka_container
```

__Connect to the container__  
```sh
docker exec -it <kafka container name> /bin/sh
```
In the terminal, all the command-line tools are in `/opt/kafka/bin`.

## 2. Use kafka with Command-line Tools
All the command-line tools used below are in `/opt/kafka/bin` from kafka container.  
__1. Create topic__  
```sh
./kafka-topics.sh --create --topic quickstart-events --bootstrap-server localhost:9092
```
  
__2. Check the topic__  
```sh
./kafka-topics.sh --describe --topic quickstart-events --bootstrap-server localhost:9092
```  
  
__3. Write some events into the topic__  
Firstly, run below command, and it receives user's message interactively.  
```sh
./kafka-console-producer.sh --topic quickstart-events --bootstrap-server localhost:9092
```
Below is an example of events I wrote with the interactive UI.  
```sh
> This is first event
> This is second event
```
  
__4. Read the events__  
Run below command.
```sh
./kafka-console-consumer.sh --topic quickstart-events --from-beginning --bootstrap-server localhost:9092
```
Then, you will see below text.  
```
This is first event
This is second event
```  
  
## 3. Python API

