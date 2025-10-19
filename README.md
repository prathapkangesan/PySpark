# PySpark
This is for PySpark knowledge Sharing Purpose only

Spark Architecture

<img width="664" height="274" alt="image" src="https://github.com/user-attachments/assets/57d6fef2-3a84-4b5f-8967-ce44b36d614d" />

PySpark's architecture is built upon the core Apache Spark architecture, which operates on a master-worker paradigm for distributed processing. The key components and their interactions are as follows:
1. Driver Program:
This is the main program where your PySpark code resides.
It orchestrates the entire Spark application, translating your code into a series of Spark operations (jobs, stages, tasks).
It creates the SparkSession (or SparkContext in older versions), which serves as the entry point to Spark functionality and interacts with the cluster manager.
The driver schedules tasks to be executed on worker nodes and collects the results.
2. Cluster Manager:
The cluster manager (e.g., YARN, Mesos, Kubernetes, or Spark Standalone) is responsible for managing resources across the cluster.
It allocates resources (CPU, memory) to Spark applications and ensures tasks are assigned to available worker nodes.
It acts as an intermediary between the driver program and the worker nodes.
3. Worker Nodes:
These are the physical or virtual machines in the cluster that perform the actual computations.
Each worker node hosts one or more Executors.
4. Executors:
Executors are processes launched on worker nodes.
They are responsible for executing the tasks assigned by the driver program. 
Each executor runs tasks in parallel on multiple threads and stores intermediate results in memory (or disk if memory is insufficient).
They report task status and results back to the driver.
5. SparkSession (or SparkContext):
SparkSession (introduced in Spark 2.0) is the unified entry point for all Spark functionality, including SQL, DataFrames, and Datasets.
It works with the cluster manager to monitor and manage the execution of jobs in the cluster. 
It provides access to various Spark APIs.
6. Jobs, Stages, and Tasks:
A Job is initiated by a Spark action (e.g., collect(), write()).
A job is divided into Stages, which are sequences of tasks that can be executed together without shuffling data.
Each stage consists of multiple Tasks, which are the smallest units of work executed by executors on partitions of data.
How PySpark Integrates:
PySpark leverages the Python interpreter to interact with the Java Virtual Machine (JVM) where the core Spark engine runs. When you write PySpark code:
The Python driver program communicates with the JVM-based Spark driver through a Py4J bridge.
The Spark driver then interacts with the cluster manager and executors as described above.
Data is efficiently transferred between the Python and Java processes, often using optimized serialization methods, allowing Python users to harness the power of distributed Spark processing.

This architecture enables PySpark to process large datasets efficiently by distributing computations across a cluster of machines.


