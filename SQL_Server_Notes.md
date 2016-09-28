# SQL SERVER 2012 Filtered Index

## Filtered Index

* statistics updated if 20% of a column’s data has been modified

CREATE NONCLUSTERED INDEX <index name>
ON <table> (<columns>)
WHERE <criteria>;
GO

--add nonclustered filtered index to UnitPrice column
CREATE NONCLUSTERED INDEX fIX_SalesOrderDetail_UnitPrice
ON AdventureWorks2012.Sales.SalesOrderDetail(UnitPrice)
WHERE UnitPrice > 1000
GO

--re-add filtered index to UnitPrice column, include UnitPriceDiscount column
CREATE NONCLUSTERED INDEX fIX_SalesOrderDetail_UnitPrice
ON AdventureWorks2012.Sales.SalesOrderDetail(UnitPrice)
INCLUDE (UnitPriceDiscount)
WHERE UnitPrice > 1000
GO
 
CREATE NONCLUSTERED INDEX fIX_SalesOrderDetail_ModifiedDate
ON AdventureWorks2012.Sales.SalesOrderDetail(ModifiedDate)
WHERE ModifiedDate >= '2008-01-01'  <= '2008-01-07'
GO


* The query optimizer won’t consider filtered indexes if you’re using local variables or parameterized SQL for the predicate that matches the filter.

SELECT ind.index_id, ind.name, ind.type_desc, par.reserved_page_count, par.used_page_count, 
par.row_count, ind.filter_definition FROM sys.dm_db_partition_stats par
INNER JOIN sys.indexes ind ON par.object_id = ind.object_id AND par.index_id = ind.index_id
WHERE par.object_id = OBJECT_ID('Employee')


## Update Statistics
UPDATE STATISTICS -- on one table/index only

UPDATE STATISTICS table_or_indexed_view_name
sp_updatestats	- All
sp_helpindex	- view all indexes for a table or view

* IndexOptimize is the SQL Server Maintenance Solution’s stored procedure for rebuilding and reorganizing indexes and updating statistics. 
https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html

> To look up

1. DBCC SHOW_STATISTICS
2. AUTO_CREATE_STATISTICS
3. AUTO_UPDATE_STATISTICS Option
4. AUTO_UPDATE_STATISTICS_ASYNC
 	* application frequently executes the same query, similar queries, or similar cached query plans.

* Certain query implementations, such as local variables and complex expressions in the query predicate, can lead to suboptimal query plans. Following query design guidelines for using statistics effectively can help to avoid this. For more information about query predicates, see Search Condition (Transact-SQL).
https://msdn.microsoft.com/en-us/library/ms173545.aspx

