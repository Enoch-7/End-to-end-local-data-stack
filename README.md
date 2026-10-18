End-to-end Data Engineering stack on a local machine. From source systems to Machine Learning applications, 


 this simple process aims at transforming raw data into valuable assets for a business. 

System design : Python environment running on Github platform
Consuming large files through a local data system requires specific configurations that enable fast upstream reads and writes as well as reproducible downstream data transformations. In this architecture we present a three stages pipeline through which data flows 


Data is consumed through public APIs and the pipeline transformation runs on a free open-source Python environment. 

Tennis Betting Engine
We use tennis data to illustrate how our local data system works. We have historical results, players statistics, advanced analytics from tennis experts and in some cases pre-match odds. 

Data Collection 
The first step of the pipeline consists of data ingestion from various sources  


The first step of the pipeline is to scrap and store all this data in a way that facilitates further reads and downstream transformations. And we should run this process on a regular basis given the fact that players’statistics and players’rankings change so frequently. More importantly when training a ML model or doing some analytics we need to capture the exact context surrounding each matchup which for a large part is time-dependent (recent performances). 

Storage
We need a flexible storage system 





Definitions : 

We speak of a single node system when the whole data engineering stack runs locally on your machine with zero cloud configuration or database servers. While in a distributed system, computational resources are distributed across the network. Although their architecture and complexity are fundamentally different, we generally apply the same metrics to measure their performances.  One important variable is response time for a given request. We also pay attention to the amount of data our system can process per second. These are essential parameters that define how our system behaves according to its design and purpose. When the data workloads fit into memory, we expect the system to render the desired output at a reasonable time. However when the amount of data increases more than the available resources can handle, our system starts to slow down and any additional request may never deliver its outcome. Solutions vary from simply adding more resources to better latency management. And for a given task some algorithms may deliver faster results than others so we should constantly work on optimization at every step of data transformations. These are some of the basic requirements of an efficient local data system, the security aspect which goes along with performances is the subject of another project. 




Technical stack

From a software development point of view, our data system represents the back-end of an ML-based application. As such it is designed to support overall data management as well as client-server relationship. The system is designed to work as a pipeline architecture (Ingestion ---> Storage ---> Analytics/ML), where raw data flows from external sources to a local database where it’s served for analytics and Machine Learning purposes. 

First the ingestion process transforms raw data to Parquet files. Then a relational warehouse is implemented for more efficient storage and fast querying. 

 The whole environment runs in-process inside Python. 




The following pipeline explains the logic behind these transformations : 
.  

Sources can be Public API, Raw CSV, Web scrapping etc. and data can be of any type : structured or unstructured. The only requirement is we have to standardize the ingestion procedure within a Python code in order to keep the resulting asset inside the pipeline. 
