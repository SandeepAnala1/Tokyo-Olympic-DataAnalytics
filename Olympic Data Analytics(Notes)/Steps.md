1) Create Azure Data Lake Storage and create resource group on the go
		Key things to learn [[Hierarchical Namespace]]
		i) In containers, we have created two directories for raw data and transformed data
2) Create Azure Data Factory 
3) Upload the data into github and copy the source data raw github link, it will become source
4) Create a pipeline in ADF with Copy Data Activity
5) While creating new dataset, use HTTP as we are getting the data from github.
6) Now created Linked Service on the go [[4) Linked Service]] for the source, here we have provided the base URL
7) And also for the sink, [[4) Linked Service]] is needed and as we store that to ADLS, we need to select ath and file format. Debug and check if Azure is able to get the data from github raw data and store it in Azure DLS
8) 5 copy data activities are added, and I feel this is not the best industry practice
9) As we have collected the data and loaded into raw data container, we now need to access it from databricks and do transformations
10) Here we need to mount the data from adls to adf to adb
11) And also here we need App registration for client, tenant and secret keys
12) to access it from adb, further we need to create IAM (Access Control), under this we need to do the role assignment, for Storage blob explorer(to perform read and write operations)
------------------------------
13) After performing Azure Databricks, we create synapse analytics
14) 
