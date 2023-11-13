# RDD

RDD (Resilient Distributed Dataset) is a fundamental building block of PySpark which is fault-tolerant, immutable distributed collections of objects. Immutable meaning once you create an RDD you cannot change it. Each record in RDD is divided into logical partitions, which can be computed on different nodes of the cluster.

RDDs are a collection of objects similar to list in Python, with the difference being RDD is computed on several processes scattered across multiple physical servers also called nodes in a cluster

RDDs provide data abstraction of partitioning and distribution of the data designed to run computations in parallel on several nodes, while doing transformations on RDD we don’t have to worry about the parallelism as PySpark by default provides.

This Apache PySpark RDD tutorial describes the basic operations available on RDDs, such as map(), filter(), and persist() and many more. In addition, this tutorial also explains Pair RDD functions that operate on RDDs of key-value pairs such as groupByKey() and join() etc.



###  Benefits
- In-Memory Processing    
PySpark loads the data from disk and process in memory and keeps the data in memory, this is the main difference between PySpark and Mapreduce (I/O intensive). In between the transformations, we can also cache/persists the RDD in memory to reuse the previous computations.

- Immutability   
PySpark RDD’s are immutable in nature meaning, once RDDs are created you cannot modify. When we apply transformations on RDD, PySpark creates a new RDD and maintains the RDD Lineage.

- Fault Tolerance    
PySpark operates on fault-tolerant data stores on HDFS, S3 e.t.c hence any RDD operation fails, it automatically reloads the data from other partitions. Also, When PySpark applications running on a cluster, PySpark task failures are automatically recovered for a certain number of times (as per the configuration) and finish the application seamlessly.

- Lazy Evolution    
PySpark does not evaluate the RDD transformations as they appear/encountered by Driver instead it keeps the all transformations as it encounters(DAG) and evaluates the all transformation when it sees the first RDD action.

- Partitioning     
When you create RDD from a data, It by default partitions the elements in a RDD. By default it partitions to the number of cores available.

### Fault tolerance

Fault tolerance in Apache Spark's Resilient Distributed Datasets (RDDs) is achieved primarily through two mechanisms: lineage information and data replication. These ensure that the system can recover data lost due to node failures without needing to checkpoint or replicate the entire data across the cluster, thus making it efficient and scalable.

1. Lineage Information    
   What is Lineage?: Lineage refers to the sequence of transformations applied to the base RDD to obtain the current RDD. Essentially, it's the RDD's transformation history or recipe.
   How it Works for Fault Tolerance: In case of a failure (like a node crash), Spark can use this lineage information to rebuild only the lost partitions of the RDD. For example, if an RDD B is created by applying a transformation on RDD A, and a partition of RDD B is lost, Spark can recompute that partition of RDD B by reapplying the transformation on the corresponding partition of RDD A.
   Advantages: This approach is often more efficient than traditional replication methods, especially for large datasets, as it avoids the need to replicate and store multiple copies of the data across the cluster.
2. Data Replication (For Certain RDDs)    
   Replication of Data: While lineage is the primary mechanism, Spark also uses data replication for fault tolerance, but selectively. For example, Spark may replicate the data stored in memory or even on disk for storage levels that request replication.
   RDD Persistence: When an RDD is persisted (or cached) with a replication storage level, its partitions may be replicated across multiple nodes. If a partition is lost due to a node failure, Spark can retrieve the data from a replica on a different node.
   Use Case Specific: The use of replication is more common with RDDs that are expensive to compute (like those involving shuffles) or are used very frequently. This helps in reducing the recomputation cost.
3. Combining Lineage and Replication
   Balanced Approach: Spark's approach to fault tolerance is balanced. It primarily relies on lineage for efficient recovery while using data replication in scenarios where recomputation costs are high or quick recovery is crucial.
   Minimal Overhead: This method ensures minimal overhead in normal operations while providing robust fault tolerance. It also allows Spark to handle very large datasets efficiently, as the entire dataset does not need to be replicated across the cluster.
