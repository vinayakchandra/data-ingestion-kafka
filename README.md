# Data Ingestion with Kafka

This project demonstrates the use of Apache Kafka for data ingestion. The pipeline includes producing messages to a
Kafka topic from a CSV file and consuming these messages to store them in a MongoDB database.

- Apache Kafka (running locally or on a server)
- MongoDB (running locally or on a server)
- Required Python libraries:
  kafka-python
  pandas
  pymongo
  Install the dependencies using pip:

```bash
pip install kafka-python pandas pymongo
```
Project Structure
The project consists of two scripts:

Producer (producer.py): Reads data from a CSV file and sends it to a Kafka topic.
Consumer (consumer.py): Reads messages from the Kafka topic and stores them into MongoDB.

# [KafkaProducer](kafka-producer.ipynb)
![screenshot](img.png)
Purpose
The producer reads a random record from a CSV file (indexProcessed.csv) and sends it as a JSON message to a Kafka
topic (demo_test).

Code Overview
Connects to Kafka on localhost:9092.
Reads data from indexProcessed.csv.
Sends random records to the Kafka topic, one by one, in a loop (10 iterations in the example).
Usage
Ensure Kafka is running locally on port 9092.

Replace the file path in the script with the path to your CSV file.

Run the producer script:

bash
Copy code
python producer.py

# [KafkaConsumer](kafka-consumer.ipynb)

## Purpose

The consumer listens to the Kafka topic (`demo_test`) and inserts incoming JSON messages into a MongoDB collection (
customers).

Code Overview
Connects to Kafka on localhost:9092.
Connects to MongoDB on `mongodb://localhost:27017/`.
Consumes messages from the Kafka topic and inserts them into the MongoDB collection.
Usage
Ensure Kafka is running locally on port 9092.

Ensure MongoDB is running locally on port 27017.

Run the consumer script:

bash
python consumer.py
Example Workflow
Start the Kafka and Zookeeper services.
Create the demo_test topic in Kafka.
Run the producer script to send messages to the demo_test topic.
Run the consumer script to consume messages and store them into MongoDB.

# Data Flow

```plaintext
CSV File -> Kafka Producer -> Kafka Topic (demo_test) -> Kafka Consumer -> MongoDB
```

Configuration
Kafka
Default Kafka server: localhost:9092
Kafka topic: demo_test
MongoDB
Default MongoDB server: localhost:27017
Database: mydatabase
Collection: customers

# Notes

Modify the Kafka topic, MongoDB database, or collection names as per your requirements.
Ensure that the CSV file is formatted correctly and accessible by the producer script.
The consumer script currently inserts all messages into the MongoDB collection. Modify it if additional processing is
required.
