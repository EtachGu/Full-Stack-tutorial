

# Big Data platform overview

https://www.predictiveanalyticstoday.com/bigdata-platforms-bigdata-analytics-software/

https://docs.microsoft.com/en-us/azure/architecture/guide/architecture-styles/big-data

# Data Ingestion, data management, ETL and warehouse

The process of importing, transferring, loading and processing data for later use or storage in a database is called Data ingestion and this involves loading data from a variety of sources, altering and modification of individual files and formatting them to fit into a larger document.

Data ingestion can be continuous, asynchronous, real-time or batched and the source and the destination may also have different format or protocol, which will require some type of transformation or conversion.


数据采集、管理、清洗

# Data Integration 数据集成

任意数据源的数据集成

[Otter 阿里巴巴分布式数据库同步系统(解决中美异地机房)](https://github.com/alibaba/otter), 其基于[Canal](http://github.com/alibaba/canal)，Canal是otter之前开源的一个子项目

[Kettle （Pentaho Data Integration ETL）](https://github.com/pentaho/pentaho-kettle)

[Apache NiFi was built to automate the flow of data between systems.](https://nifi.apache.org/docs.html)

[StreamSets](https://streamsets.com/)

Singer https://www.singer.io/


https://hevodata.com/blog/best-etl-tools-data-warehouse/


# Storage 存储

Kudu
[A new addition to the open source Apache Hadoop ecosystem, Apache Kudu completes Hadoop's storage layer to enable fast analytics on fast data.](https://kudu.apache.org/)

# Analytics/Machine Learning 分析/机器学习




# Data Governance

[Apache Atlas, a scalable and extensible set of core foundational governance services – enabling enterprises to effectively and efficiently meet their compliance requirements within Hadoop and allows integration with the whole enterprise data ecosystem](http://atlas.apache.org/index.html)

[Netflix Metacat,a unified metadata exploration API service. You can explore Hive, RDS, Teradata, Redshift, S3 and Cassandra](https://github.com/Netflix/metacat)


# IDE Integrated Development Environment

[Hue, Hadoop User Expeirence. Hue is an open source SQL Workbench for browsing, querying and visualizing data in cloud/on-prem Data Warehouses: gethue.com](https://github.com/cloudera/hue)


# Designing Data-Intensive Applications

[Designing Data-Intensive Applications](https://github.com/ept/ddia-references)

# Data lake

[Databricks Data lake, is an open-source storage layer that brings ACID transactions to Apache Spark™ and big data workloads.](https://delta.io/)