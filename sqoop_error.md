postgres-xl-9.5r1.1\src\backend\pgxc\pool\execRemote.c

line 2783
<pre>/* Start transaction on connections where it is not started */
	if (pgxc_node_begin(conn_count, connections, gxid, need_tran_block, false, PGXC_NODE_DATANODE))
	{
		ereport(ERROR,
				(errcode(ERRCODE_INTERNAL_ERROR),
				 errmsg("Could not begin transaction on data nodes.")));
	}
</pre>




err_msg:
<pre>16/06/14 15:40:17 INFO manager.SqlManager: Using default fetchSize of 1000
16/06/14 15:40:18 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM "pgbench_accounts" AS t LIMIT 1
16/06/14 15:40:18 ERROR manager.SqlManager: Error executing statement: org.postgresql.util.PSQLException: ERROR: Could not begin transaction on data node.
org.postgresql.util.PSQLException: ERROR: Could not begin transaction on data node.
        at org.postgresql.core.v3.QueryExecutorImpl.receiveErrorResponse(QueryExecutorImpl.java:2284)
        at org.postgresql.core.v3.QueryExecutorImpl.processResults(QueryExecutorImpl.java:2003)
        at org.postgresql.core.v3.QueryExecutorImpl.execute(QueryExecutorImpl.java:200)
        at org.postgresql.jdbc.PgStatement.execute(PgStatement.java:424)
        at org.postgresql.jdbc.PgPreparedStatement.executeWithFlags(PgPreparedStatement.java:161)
        at org.postgresql.jdbc.PgPreparedStatement.executeQuery(PgPreparedStatement.java:114)
        at org.apache.sqoop.manager.SqlManager.execute(SqlManager.java:753)
        at org.apache.sqoop.manager.SqlManager.execute(SqlManager.java:762)
        at org.apache.sqoop.manager.SqlManager.getColumnInfoForRawQuery(SqlManager.java:270)
        at org.apache.sqoop.manager.SqlManager.getColumnTypesForRawQuery(SqlManager.java:241)
        at org.apache.sqoop.manager.SqlManager.getColumnTypes(SqlManager.java:227)
        at org.apache.sqoop.hive.TableDefWriter.getCreateTableStmt(TableDefWriter.java:126)
        at org.apache.sqoop.hive.HiveImport.importTable(HiveImport.java:189)
        at org.apache.sqoop.tool.CreateHiveTableTool.run(CreateHiveTableTool.java:58)
        at org.apache.sqoop.Sqoop.run(Sqoop.java:143)
        at org.apache.hadoop.util.ToolRunner.run(ToolRunner.java:70)
        at org.apache.sqoop.Sqoop.runSqoop(Sqoop.java:179)
        at org.apache.sqoop.Sqoop.runTool(Sqoop.java:218)
        at org.apache.sqoop.Sqoop.runTool(Sqoop.java:227)
        at org.apache.sqoop.Sqoop.main(Sqoop.java:236)
</pre>



