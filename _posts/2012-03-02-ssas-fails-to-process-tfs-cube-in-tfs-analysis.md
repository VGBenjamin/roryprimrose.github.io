---
title: SSAS fails to process TFS cube in Tfs_Analysis
tags : TFS
date: 2012-03-02 10:43:47 +10:00
---



{% highlight text linenos %}
[Full Analysis Database Sync]: 
AnalysisDatabaseProcessingType=Full, needCubeSchemaUpdate=True. 
Microsoft.TeamFoundation.Server.WarehouseException: TF221122: An error occurred running job Full Analysis Database Sync for team project collection or Team Foundation server TEAM FOUNDATION. 
Microsoft.TeamFoundation.Server.WarehouseException: Failed to Process Analysis Database 'Tfs_Analysis'. 
Microsoft.TeamFoundation.Server.WarehouseException: Internal error: The operation terminated unsuccessfully.
OLE DB error: OLE DB or ODBC error: A network-related or instance-specific error has occurred while establishing a connection to SQL Server. Server is not found or not accessible. Check if instance name is correct and if SQL Server is configured to allow remote connections. For more information see SQL Server Books Online.; 08001; Client unable to establish connection; 08001; Encryption not supported on the client.; 08001.
Errors in the high-level relational engine. A connection could not be made to the data source with the DataSourceID of 'Tfs_AnalysisDataSource', Name of 'Tfs_AnalysisDataSource'.
Errors in the OLAP storage engine: An error occurred while the dimension, with the ID of 'Today', Name of 'Today' was being processed.
Errors in the OLAP storage engine: An error occurred while the 'Day Of Year' attribute of the 'Today' dimension from the 'Tfs_Analysis' database was being processed.
Server: The operation has been cancelled.
OLE DB error: OLE DB or ODBC error: A network-related or instance-specific error has occurred while establishing a connection to SQL Server. Server is not found or not accessible. Check if instance name is correct and if SQL Server is configured to allow remote connections. For more information see SQL Server Books Online.; 08001; Client unable to establish connection; 08001; Encryption not supported on the client.; 08001.
Errors in the high-level relational engine. A connection could not be made to the data source with the DataSourceID of 'Tfs_AnalysisDataSource', Name of 'Tfs_AnalysisDataSource'.
Errors in the OLAP storage engine: An error occurred while the dimension, with the ID of 'Today', Name of 'Today' was being processed.
Errors in the OLAP storage engine: An error occurred while the 'Day Of Month' attribute of the 'Today' dimension from the 'Tfs_Analysis' database was being processed.
OLE DB error: OLE DB or ODBC error: A network-related or instance-specific error has occurred while establishing a connection to SQL Server. Server is not found or not accessible. Check if instance name is correct and if SQL Server is configured to allow remote connections. For more information see SQL Server Books Online.; 08001; Client unable to establish connection; 08001; Encryption not supported on the client.; 08001.
Errors in the high-level relational engine. A connection could not be made to the data source with the DataSourceID of 'Tfs_AnalysisDataSource', Name of 'Tfs_AnalysisDataSource'.
Errors in the OLAP storage engine: An error occurred while the dimension, with the ID of 'Today', Name of 'Today' was being processed.
Errors in the OLAP storage engine: An error occurred while the 'Year' attribute of the 'Today' dimension from the 'Tfs_Analysis' database was being processed.
OLE DB error: OLE DB or ODBC error: A network-related or instance-specific error has occurred while establishing a connection to SQL Server. Server is not found or not accessible. Check if instance name is correct and if SQL Server is configured to allow remote connections. For more information see SQL Server Books Online.; 08001; Client unable to establish connection; 08001; Encryption not supported on the client.; 08001.
Errors in the high-level relational engine. A connection could not be made to the data source with the DataSourceID of 'Tfs_AnalysisDataSource', Name of 'Tfs_AnalysisDataSource'.
Errors in the OLAP storage engine: An error occurred while the dimension, with the ID of 'Today', Name of 'Today' was being processed.
Errors in the OLAP storage engine: An error occurred while the 'Month Of Year' attribute of the 'Today' dimension from the 'Tfs_Analysis' database was being processed.
OLE DB error: OLE DB or ODBC error: A network-related or instance-specific error has occurred while establishing a connection to SQL Server. Server is not found or not accessible. Check if instance name is correct and if SQL Server is configured to allow remote connections. For more information see SQL Server Books Online.; 08001; Client unable to establish connection; 08001; Encryption not supported on the client.; 08001.
Errors in the high-level relational engine. A connection could not be made to the data source with the DataSourceID of 'Tfs_AnalysisDataSource', Name of 'Tfs_AnalysisDataSource'.
Errors in the OLAP storage engine: An error occurred while the dimension, with the ID of 'Today', Name of 'Today' was being processed.
Errors in the OLAP storage engine: An error occurred while the 'Week Of Year' attribute of the 'Today' dimension from the 'Tfs_Analysis' database was being processed.
OLE DB error: OLE DB or ODBC error: A network-related or instance-specific error has occurred while establishing a connection to SQL Server. Server is not found or not accessible. Check if instance name is correct and if SQL Server is configured to allow remote connections. For more information see SQL Server Books Online.; 08001; Client unable to establish connection; 08001; Encryption not supported on the client.; 08001.
Errors in the high-level relational engine. A connection could not be made to the data source with the DataSourceID of 'Tfs_AnalysisDataSource', Name of 'Tfs_AnalysisDataSource'.
Errors in the OLAP storage engine: An error occurred while the dimension, with the ID of 'Today', Name of 'Today' was being processed.
Errors in the OLAP storage engine: An error occurred while the 'Month' attribute of the 'Today' dimension from the 'Tfs_Analysis' database was being processed.
OLE DB error: OLE DB or ODBC error: A network-related or instance-specific error has occurred while establishing a connection to SQL Server. Server is not found or not accessible. Check if instance name is correct and if SQL Server is configured to allow remote connections. For more information see SQL Server Books Online.; 08001; Client unable to establish connection; 08001; Encryption not supported on the client.; 08001.
Errors in the high-level relational engine. A connection could not be made to the data source with the DataSourceID of 'Tfs_AnalysisDataSource', Name of 'Tfs_AnalysisDataSource'.
Errors in the OLAP storage engine: An error occurred while the dimension, with the ID of 'Today', Name of 'Today' was being processed.
Errors in the OLAP storage engine: An error occurred while the 'Week' attribute of the 'Today' dimension from the 'Tfs_Analysis' database was being processed.
OLE DB error: OLE DB or ODBC error: A network-related or instance-specific error has occurred while establishing a connection to SQL Server. Server is not found or not accessible. Check if instance name is correct and if SQL Server is configured to allow remote connections. For more information see SQL Server Books Online.; 08001; Client unable to establish connection; 08001; Encryption not supported on the client.; 08001.
Errors in the high-level relational engine. A connection could not be made to the data source with the DataSourceID of 'Tfs_AnalysisDataSource', Name of 'Tfs_AnalysisDataSource'.
Errors in the OLAP storage engine: An error occurred while the dimension, with the ID of 'Today', Name of 'Today' was being processed.
Errors in the OLAP storage engine: An error occurred while the 'Date' attribute of the 'Today' dimension from the 'Tfs_Analysis' database was being processed.
{% endhighlight %}



{% highlight text linenos %}
[Full Analysis Database Sync]: 
---> AnalysisDatabaseProcessingType=Full, needCubeSchemaUpdate=False. ---> Microsoft.TeamFoundation.Server.WarehouseException: TF221122: An error occurred running job Full Analysis Database Sync for team project collection or Team Foundation server TEAM FOUNDATION. 
---> Microsoft.TeamFoundation.Server.WarehouseException: Failed to Process Analysis Database 'Tfs_Analysis'. 
---> Microsoft.TeamFoundation.Server.WarehouseException: Internal error: The operation terminated unsuccessfully. 
OLE DB error: OLE DB or ODBC error: Login timeout expired; HYT00; A network-related or instance-specific error has occurred while establishing a connection to SQL Server. Server is not found or not accessible. Check if instance name is correct and if SQL Server is configured to allow remote connections. For more information see SQL Server Books Online.; 08001; SQL Server Network Interfaces: Error getting enabled protocols list from registry [xFFFFFFFF]. ; 08001. 
Errors in the high-level relational engine. A connection could not be made to the data source with the DataSourceID of 'Tfs_AnalysisDataSource', Name of 'Tfs_AnalysisDataSource'. 
Errors in the OLAP storage engine: An error occurred while the dimension, with the ID of 'Dim Build Platform', Name of 'Build Platform' was being processed. 
Errors in the OLAP storage engine: An error occurred while the 'Build Platform' attribute of the 'Build Platform' dimension from the 'Tfs_Analysis' database was being processed. Server: The operation has been cancelled. 
OLE DB error: OLE DB or ODBC error: Login timeout expired; HYT00; A network-related or instance-specific error has occurred while establishing a connection to SQL Server. Server is not found or not accessible. Check if instance name is correct and if SQL Server is configured to allow remote connections. For more information see SQL Server Books Online.; 08001; SQL Server Network Interfaces: Error getting enabled protocols list from registry [xFFFFFFFF]. ; 08001. 
Errors in the high-level relational engine. A connection could not be made to the data source with the DataSourceID of 'Tfs_AnalysisDataSource', Name of 'Tfs_AnalysisDataSource'. 
Errors in the OLAP storage engine: An error occurred while the dimension, with the ID of 'Dim WorkItem Link Type', Name of 'Work Item Link Type' was being processed. 
Errors in the OLAP storage engine: An error occurred while the 'TeamProjectCollectionSK' attribute of the 'Work Item Link Type' dimension from the 'Tfs_Analysis' database was being processed. 
OLE DB error: OLE DB or ODBC error: Login timeout expired; HYT00; A network-related or instance-specific error has occurred while establishing a connection to SQL Server. Server is not found or not accessible. Check if instance name is correct and if SQL Server is configured to allow remote connections. For more information see SQL Server Books Online.; 08001; SQL Server Network Interfaces: Error getting enabled protocols list from registry [xFFFFFFFF]. ; 08001. 
Errors in the high-level relational engine. A connection could not be made to the data source with the DataSourceID of 'Tfs_AnalysisDataSource', Name of 'Tfs_AnalysisDataSource'. 
Errors in the OLAP storage engine: An error occurred while the dimension, with the ID of 'Dim WorkItem Link Type', Name of 'Work Item Link Type' was being processed. 
Errors in the OLAP storage engine: An error occurred while the 'Link ID' attribute of the 'Work Item Link Type' dimension from the 'Tfs_Analysis' database was being processed. 
OLE DB error: OLE DB or ODBC error: Login timeout expired; HYT00; A network-related or instance-specific error has occurred while establishing a connection to SQL Server. Server is not found or not accessible. Check if instance name is correct and if SQL Server is configured to allow remote connections. For more information see SQL Server Books Online.; 08001; SQL Server Network Interfaces: Error getting enabled protocols list from registry [xFFFFFFFF]. ; 08001. 
Errors in the high-level relational engine. A connection could not be made to the data source with the DataSourceID of 'Tfs_AnalysisDataSource', Name of 'Tfs_AnalysisDataSource'. 
Errors in the OLAP storage engine: An error occurred while the dimension, with the ID of 'Dim WorkItem Link Type', Name of 'Work Item Link Type' was being processed. 
Errors in the OLAP storage engine: An error occurred while the 'WorkItemLinkTypeBK' attribute of the 'Work Item Link Type' dimension from the 'Tfs_Analysis' database was being processed. 
OLE DB error: OLE DB or ODBC error: Login timeout expired; HYT00; A network-related or instance-specific error has occurred while establishing a connection to SQL Server. Server is not found or not accessible. Check if instance name is correct and if SQL Server is configured to allow remote connections. For more information see SQL Server Books Online.; 08001; SQL Server Network Interfaces: Error getting enabled protocols list from registry [xFFFFFFFF]. ; 08001. 
Errors in the high-level relational engine. A connection could not be made to the data source with the DataSourceID of 'Tfs_AnalysisDataSource', Name of 'Tfs_AnalysisDataSource'. 
Errors in the OLAP storage engine: An error occurred while the dimension, with the ID of 'Dim WorkItem Link Type', Name of 'Work Item Link Type' was being processed. 
Errors in the OLAP storage engine: An error occurred while the 'Reference Name' attribute of the 'Work Item Link Type' dimension from the 'Tfs_Analysis' database was being processed. 
OLE DB error: OLE DB or ODBC error: Login timeout expired; HYT00; A network-related or instance-specific error has occurred while establishing a connection to SQL Server. Server is not found or not accessible. Check if instance name is correct and if SQL Server is configured to allow remote connections. For more information see SQL Server Books Online.; 08001; SQL Server Network Interfaces: Error getting enabled protocols list from registry [xFFFFFFFF]. ; 08001. 
Errors in the high-level relational engine. A connection could not be made to the data source with the DataSourceID of 'Tfs_AnalysisDataSource', Name of 'Tfs_AnalysisDataSource'. 
Errors in the OLAP storage engine: An error occurred while the dimension, with the ID of 'Dim WorkItem Link Type', Name of 'Work Item Link Type' was being processed. 
Errors in the OLAP storage engine: An error occurred while the 'Link Name' attribute of the 'Work Item Link Type' dimension from the 'Tfs_Analysis' database was being processed. 
OLE DB error: OLE DB or ODBC error: Login timeout expired; HYT00; A network-related or instance-specific error has occurred while establishing a connection to SQL Server. Server is not found or not accessible. Check if instance name is correct and if SQL Server is configured to allow remote connections. For more information see SQL Server Books Online.; 08001; SQL Server Network Interfaces: Error getting enabled protocols list from registry [xFFFFFFFF]. ; 08001. 
Errors in the high-level relational engine. A connection could not be made to the data source with the DataSourceID of 'Tfs_AnalysisDataSource', Name of 'Tfs_AnalysisDataSource'. 
Errors in the OLAP storage engine: An error occurred while the dimension, with the ID of 'Dim WorkItem Link Type', Name of 'Work Item Link Type' was being processed. 
Errors in the OLAP storage engine: An error occurred while the 'Rules' attribute of the 'Work Item Link Type' dimension from the 'Tfs_Analysis' database was being processed. 
OLE DB error: OLE DB or ODBC error: Login timeout expired; HYT00; A network-related or instance-specific error has occurred while establishing a connection to SQL Server. Server is not found or not accessible. Check if instance name is correct and if SQL Server is configured to allow remote connections. For more information see SQL Server Books Online.; 08001; SQL Server Network Interfaces: Error getting enabled protocols list from registry [xFFFFFFFF]. ; 0800
{% endhighlight %}

