# Cassandra-Kafka-PySpark

## Objective
The objective of this project is to create a scalable data processing pipeline that utilizes Apache Cassandra for storage, Apache Kafka for message brokering, and PySpark for data processing and analytics. This setup demonstrates how to handle real-time data ingestion and processing efficiently.

## Introduction
This project integrates three powerful technologies:
- **Apache Cassandra**: A distributed NoSQL database designed to handle large amounts of data across many commodity servers, providing high availability with no single point of failure.
- **Apache Kafka**: A distributed streaming platform that can publish, subscribe to, store, and process streams of records in real-time.
- **PySpark**: The Python API for Apache Spark, enabling large-scale data processing and analytics.

Together, these technologies create a robust framework for building real-time data pipelines, allowing for efficient data storage, retrieval, and processing.

## Features
- **Real-time Data Processing**: Stream data from Kafka and process it in real-time using PySpark.
- **Scalability**: Utilize Cassandra for storing large volumes of data with high write and read throughput.
- **Integration**: Seamless integration between Kafka and PySpark for efficient data ingestion and processing.
- **Fault Tolerance**: Reliable data handling with no single point of failure, ensuring data integrity.

## Architecture Diagram
![Architecture Diagram](https://user-images.githubusercontent.com/115451707/219657272-0b190c35-b148-43d3-a30f-7611705f3a6f.png) <!-- Replace this with the actual link to your architecture diagram -->

## Installation
To set up the project, follow these steps:

### Prerequisites
- Apache Cassandra
- Apache Kafka
- Apache Spark with PySpark
- Python 3.x

### Steps
1. Clone the repository:
    ```bash
    git clone https://github.com/Satyam20091998/Cassandra-Kafka-Pyspark.git
    cd Cassandra-Kafka-Pyspark
    ```
2. Set up Docker containers for Cassandra and Kafka or install them locally.
3. Create the necessary keyspace and tables in Cassandra.
4. Configure Kafka topics for data streaming.
5. Run the PySpark application to start processing data.

## Usage
After setting up the project, you can start the PySpark application to begin processing data from Kafka:

```bash
# Example command to run the PySpark application
spark-submit pyspark_app.py
```

## Contributing
Contributions are welcome! Please fork the repository and submit a pull request with your improvements or bug fixes.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments
- [Apache Cassandra](https://cassandra.apache.org/) for distributed database management.
- [Apache Kafka](https://kafka.apache.org/) for message brokering.
- [Apache Spark](https://spark.apache.org/) for large-scale data processing.
- Any additional resources or libraries that contributed to this project.

### Notes
- Make sure to replace `link-to-your-diagram` with the actual link to your architecture diagram if you have one.
- Feel free to customize any sections to better fit your project's specifics or add more details as necessary.


## Steps to setup projects

To start the setup
```
docker-compose up -d
```

To stop the setup
```
docker-compose down
```

Install few extension in vscode to work with cassandra db
1. Cassandra Workbench

Create a keysapce with name "ineuron"
```
CREATE KEYSPACE ineuron
	WITH REPLICATION = {
		'class': 'org.apache.cassandra.locator.SimpleStrategy',
		'replication_factor': '3'
	}
	AND DURABLE_WRITES = true;
```

Create a table Employee
```
 CREATE TABLE ineuron.EMPLOYEE(
     EMP_ID INT,
     EMP_NAME text,
     CITY text,
     STATE text,
     primary key (EMP_ID)
 );
```

> To insert records into Employee table refer CQL_SCRIPT.cql

Once above steps is completed execute below command

To launch producer script
```
spark-submit --packages org.apache.spark:spark-sql-kafka-0-10_2.12:3.0.1,com.datastax.spark:spark-cassandra-connector_2.12:3.0.0  producer.py 
```

To launch consumer script
```
spark-submit --packages org.apache.spark:spark-sql-kafka-0-10_2.12:3.0.1 consumer.py 
```
