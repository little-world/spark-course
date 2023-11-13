# Hadoop

Apache Hadoop is a framework that allows for the distributed processing of large data sets across clusters of computers using simple programming models. It's designed to scale up from single servers to thousands of machines, each offering local computation and storage. Here's a brief introduction to its key components and features:

#### Distributed Storage
Hadoop Distributed File System (HDFS): HDFS is the primary storage system used by Hadoop applications. It's a distributed file system that stores data on commodity machines, providing very high aggregate bandwidth across the cluster. HDFS is designed to be highly fault-tolerant by replicating each piece of data across multiple nodes.
#### Distributed Computation 
MapReduce: MapReduce is a programming model and processing technique for distributed computing. It divides the task into small parts, each of which can be processed in parallel across the Hadoop cluster. MapReduce consists of two steps: the Map step, which processes and converts input data into a format suitable for analysis; and the Reduce step, which aggregates the results to produce a final output.
#### Scalability and Reliability
Hadoop is highly scalable. You can start with a single machine and scale up to thousands, adding machines to the cluster as needed without needing to change the data formats, how data is loaded, the way jobs are written, or the applications on top. Its distributed nature ensures that data is safely stored even in the case of hardware failure.
#### Ecosystem and Flexibility
Hadoop is more than just a storage and processing system. Its ecosystem includes various other Apache projects that can complement and extend its basic capabilities. These include Hive (data warehousing), Pig (scripting), HBase (NoSQL database), and others. This ecosystem makes Hadoop flexible for a variety of data processing and analysis tasks.
#### Cost-Effective
Since Hadoop uses commodity hardware for storage and computation, it's a cost-effective solution for storing and processing huge volumes of data as compared to traditional relational database management systems.
#### Community and Development
As an open-source project, Hadoop has a large community of contributors from across the globe who continually work on improving the system and adding new features. This active development ensures that Hadoop stays relevant in the fast-evolving field of big data.
#### Use Cases
Hadoop is suitable for a range of use cases, particularly those involving large volumes of unstructured or semi-structured data. It's widely used for data mining, log processing, data warehousing, machine learning, and large-scale analytics.


### Hadoop History

#### Early 2000s - Google's Influence: 
The foundation for Hadoop was laid by two research papers published by Google. The first, in 2003, introduced the Google File System (GFS), a scalable distributed file system for large distributed data-intensive applications. The second paper, published in 2004, presented MapReduce, a programming model for processing and generating large datasets with a parallel, distributed algorithm on a cluster.
#### 2004 - Development at Nutch:
Hadoop started as a project to support distribution for the Nutch search engine project. Doug Cutting and Mike Cafarella, who were working on Nutch, a part of the Apache Lucene project, needed a scalable system for processing and storing large amounts of data, and they started creating Hadoop as a subproject of Lucene.
#### 2006 - Birth of Hadoop: 
Cutting, who was working at Yahoo! at the time, was heavily influenced by Google's papers. He named the project "Hadoop" after his son's toy elephant. In 2006, Hadoop was spun off from Nutch and became a separate Apache project, with Cutting leading the way.
#### 2008 - Hadoop Breaks a World Record: 
In 2008, Hadoop broke the world record for the fastest system to sort a terabyte of data, completing the task in just 209 seconds. This achievement highlighted Hadoop's potential for large-scale data processing.
#### 2011 - Foundation of the Apache Hadoop Project: 
Hadoop had evolved significantly with contributions from a wider community. Recognizing its potential and growing popularity, the Apache Software Foundation established Hadoop as a top-level project, independent of Lucene.
#### Expansion and Ecosystem Growth: 
Alongside the development of Hadoop itself, an ecosystem of related projects began to grow. This includes systems like Apache Pig (a high-level platform for creating MapReduce programs), Apache Hive (data warehousing infrastructure), Apache HBase (a non-relational, distributed database), and others.
#### Continued Evolution: 
Over the years, Hadoop continued to evolve, improving in scalability, efficiency, and usability. The introduction of YARN (Yet Another Resource Negotiator) in Hadoop 2.0 was a significant milestone, transforming it from a simple MapReduce engine into a multi-application data processing platform.
#### Present and Future: 
Today, Hadoop is widely used across industries for big data analytics. It's considered a standard for distributed data processing and storage. The future of Hadoop includes continuous improvements, addressing challenges like real-time data processing and integration with other emerging big data technologies.


### Hadoop vs Spark

#### Processing Method:

- Hadoop: Hadoop MapReduce works by reading data from a disk, processing it, and writing the results back to the disk. This approach can be slower due to extensive disk I/O operations.
- Spark: Spark processes data in-memory and keeps intermediate data in memory rather than writing to disk, which leads to faster processing speeds. This is particularly beneficial for applications involving iterative processing and machine learning.

#### Performance:

- Hadoop: Generally slower due to its reliance on disk-based data processing. It's more suited for simple, large-scale data processing tasks that do not require fast iterative processing.
- Spark: Known for its high performance, especially for complex applications, Spark can be significantly faster than Hadoop MapReduce for certain applications, particularly those requiring iterative processing.

#### Ease of Use:

- Hadoop: The MapReduce programming model can be more complex and harder to master. It often requires longer and more complex codes.
- Spark: Offers high-level APIs in Java, Scala, Python, and R, and includes several built-in functions, making it easier to use and program. Spark's DataFrame and Dataset APIs simplify development.

#### Fault Tolerance:

- Hadoop: Provides fault tolerance through data replication in HDFS. It's highly reliable.
- Spark: Achieves fault tolerance through a concept called Resilient Distributed Datasets (RDDs). It can also recover lost data through lineage.

#### Cost:
- Hadoop: More cost-effective for larger datasets that do not require fast processing, as it relies on disk storage which is cheaper than memory.
- Spark: While faster, it may require more expensive memory resources to fully utilize its in-memory processing capabilities, especially for large datasets.

#### Real-Time Processing:

- Hadoop: Not designed for real-time data processing; it's primarily batch-oriented.
- Spark: Offers Spark Streaming (micro-batch processing) and Structured Streaming for real-time data processing.

#### Scalability:
Both Hadoop and Spark are highly scalable, but Spark's performance advantages can diminish with very large datasets due to its in-memory processing model.

#### Ecosystem and Integration:

- Hadoop: Has a rich ecosystem with various tools like HBase, Hive, Pig, etc., for different data processing needs.
- Spark: Also has a strong ecosystem and can integrate with many of the same Hadoop ecosystem components and other data sources.

#### Use Cases:
- Hadoop: Ideal for large-scale data processing tasks, especially where data size exceeds memory capabilities and fast processing is not critical.
- Spark: Better for machine learning, real-time analytics, and graph processing where speed and iterative processing are key.

#### Map Reduce
- Hadoop: This is a two-step process of Map and Reduce. The Map function processes and transforms the input data into intermediate key-value pairs, which are then shuffled across the network to the Reduce nodes. The Reduce function aggregates these key-value pairs to produce the final output. Hadoop MapReduce reads from and writes to a disk, which makes it suitable for large-scale data processing but slower for iterative and interactive workloads.
- Spark: Spark also uses a concept similar to MapReduce, but it is not limited to two steps. It allows data to be loaded into a cluster's memory and processed in parallel across the cluster. Spark's in-memory processing can be significantly faster than Hadoop's disk-based processing, especially for complex algorithms and iterative processes, such as machine learning and graph algorithms.

