---
title: "Data processing pipeline in Apache Beam"
categories:
  - Tutorials
tags:
  - Apache Beam
  - Machine Learning
  - Data preprocessing
  - Pipeline
---

<p align="center">
  <img src="https://i.imgur.com/Oger284.png">
</p>


If you are into the field of data science and machine learning you might have heard about the Apache Beam. If not this technology is vastly being used into the field of parallel processing of data in deployment phase mostly. Since we that there is large amount of data increasing day by day, if we see a IOT device which is used to collect pollution level after every 5 min of interval it can became a large amount of data in a day to week. In this tutrial we will learn about the Apache Beam its origin and its benefits than we will see apache beam in practical. 

## What is Apache Beam? 

Apache Beam is an open source, unified model for defining and executing both batch and streaming data-parallel processing pipelines. It also a set of language SDK like java, python and Go for constructing pipelines and few runtime-specific Runners  such as Apache Spark, Apache Flink and Google Cloud DataFlow for executing them.

The history of beam behind contains number of internal Google Data processing projects including, MapReduce, FlumeJava, Milwheel. Beam was originally known as "DataFlow Model" and first implemented as Google Cloud Dataflow - including a Java SDK on GitHub for writing pipelines and fully managed service for executing them on Google Cloud Platform. Others in the community began writing extensions, including a Spark Runner, Flink Runner, and Scala SDK. In January 2016, Google and a number of partners submitted the Dataflow Programming Model and SDKs portion as an Apache Incubator Proposal, under the name Apache Beam (unified Batch + strEAM processing). Apache Beam graduated from incubation in December 2016.

So, in summarised form we can say, Apache Beam is a Batch and Stream Processing Model with set of API. It was open sourced by Google (with Cloudera and PayPal) in 2016 via an Apache incubator project.

## Why we need Apache Beam when we have Spark/Flink/Hadoop? 

Well there are many models such as Spark, Flink, MillWheel etc cameout which were sufficiently scalabel, fault tolerant and low latency, but all lack high level programming API that binds these models and data sources and provide an abstraction to the application logic fromm big data ecosystem. Apache Beam provides the abstraction between your application logic and the big data ecosystem. 

## Apache Beam Model: 

<p align="center">
  <img src="https://i.imgur.com/xuTr2Uk.png">
</p>

### 1. DataSource:
Data source can be in batches or in the streaming format. If we take interms of GCP data can be stored in Big query format can be fetched in batches or data can be taken from PubSub in a streaming format. 

### 2. SDK:
Apache beam supports three language SDK java, python and Go. You can choose your SDK based upon your requirement. 

### 3. Runner: 
Beam supports executing programs on multiple distributed processing backends through PipelineRunners. Currently, the following PipelineRunners are available:

* The `DirectRunner` runs the pipeline on your local machine. 
* The  `ApexRunner` runs the pipeline on an Apache Hadoop YARN cluster (or in embedded mode)
* The `DataflowRunner` submits the pipeline to the Google Cloud Dataflow.
* The `FlinkRunner` runs the pipeline on an Apache Flink cluster. 
* The `SparkRunner` runs the pipeline on an Apache Spark cluster.
* The `JetRunner` runs the pipeline on a Hazelcast Jet cluster.

You can see the runner capability matrix for more details [here.](https://beam.apache.org/documentation/runners/capability-matrix/)

While creating a beam pipeline, one can have the following processing tasks in terms of abstractions –

### Pipeline:
A pipeline consists of the entire data processing tasks from start to end. The stages which are involved in this are reading the input data, transforming that data, and after that, writing the output. When we create a pipeline, we must give the execution option, which tells the pipeline where to run and how to run.

### PCollection: 
As the name suggests, it represents a distributed data set on which the beam pipeline has to operate. The data set can be bounded or unbounded i.e., it can come from a fixed source or can come from a continuously updating source with the help of subscription or any other mechanism.

### PTransform: 
It represents a data processing transform or an operation. The input for every PTransform is a PCollection object, performs the processing functions that we provide, and gives zero or more PCollection objects as an output.

### ParDo: 
A ParDo transform considers each element in the input PCollection, performs some processing function (your user code) on that element, and emits zero, one, or multiple elements to an output PCollection.

### DoFn: 
A DoFn applies your logic in each element in the input PCollection and lets you populate the elements of an output PCollection. To be included in your pipeline, it’s wrapped in a ParDo PTransform.

## Implementing Apache Beam Pipeline

In this I will show to use Apache Beam in Direct runner and in next part i will show you to run in GCP Dataflow. 

For running in local, you need to install python as I will be using python SDK. To install apache beam in python run `pip install apache-beam`

#### 1. Simple Pipeline to strip: 

Tip: You can run apache beam locally in [Google Colab](https://colab.research.google.com) also. 

<script src="https://gist.github.com/AtriSaxena/faf26672653ba6d12a5ade66958c0606.js"></script>

In this we have created the data using the beam.Create() function. Using the Beam.Map() functions we can use python lambda function for small operations like in above code `beam.Map(lambda text: text.strip('# \n'))`

### 2. Count word in the Text document: 

In this problem we will use Shakespeare’s Romeo & Juliet text data and count the words. You can download the file from [gutenberg](http://www.gutenberg.org/cache/epub/1777/pg1777.txt) and rename as `romeojuliet.txt`

<script src="https://gist.github.com/AtriSaxena/d185b2e67e4186c317bd48c22813b439.js"></script>

Here you can see text file is passed which can be read using the beam `ReadFromText` function. After that `beam.FlatMap` is used to findall the words in the text and set the word count with 1 than using the words as the key words are combine using the `beam.CombinePerKey(sum)` which gives the sum group by key. At last we format the output or can write to text file using the `beam.WriteToText()`.

### Learn More about Apache Beam

1. Github Repo (https://github.com/apache/beam)
2. Documentation (https://beam.apache.org/documentation/programming-guide/)

### References

1. https://stackoverflow.com/questions/43581127/what-are-the-benefits-of-apache-beam-over-spark-flink-for-batch-processing
2. https://www.slideshare.net/HadoopSummit/apache-beam-a-unified-model-for-batch-and-stream-processing-data
3. The [VLDB 2015 paper](http://www.vldb.org/pvldb/vol8/p1792-Akidau.pdf) (using the original naming Dataflow model).
