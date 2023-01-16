:original_name: rds_download_sql_auditing_log.html

.. _rds_download_sql_auditing_log:

Downloading SQL Audit Logs
==========================

If you :ref:`enable the SQL audit function <rds_sql_auditing_log>`, all SQL operations will be logged, and you can download audit logs to view details. By default, the SQL audit function is disabled. Enabling this function may affect performance.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. In the navigation pane on the left, choose **SQL Audits**.

#. On the displayed page, select a time range in the upper right corner, select SQL audit logs to be downloaded in the list, and click **Download** above the list to download SQL audit logs in batches.

   Alternatively, select an audit log and click **Download** in the **Operation** column to download an individual SQL audit log.

#. The following figure shows the SQL audit log content. For field descriptions, see :ref:`Table 1 <rds_download_sql_auditing_log__table718571813550>`.


   .. figure:: /_static/images/en-us_image_0000001470340297.png
      :alt: **Figure 1** MySQL audit logs

      **Figure 1** MySQL audit logs

   .. _rds_download_sql_auditing_log__table718571813550:

   .. table:: **Table 1** Audit log field description

      +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter         | Description                                                                                                                                       |
      +===================+===================================================================================================================================================+
      | record_id         | ID of a single audit log record.                                                                                                                  |
      +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | connection_id     | ID of the session executed by the record, which is the same as the ID in the **show processlist** command output.                                 |
      +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | connection_status | Session status, which is usually the returned error code of a statement. If a statement is successfully executed, the value **0** is returned.    |
      +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | name              | Recorded type name. Generally, DML and DDL operations are QUERY, connection and disconnection operations are CONNECT and QUIT, respectively.      |
      +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | timestamp         | Recorded UTC time.                                                                                                                                |
      +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | command_class     | SQL command type. The value is the parsed SQL type, for example, select or update. (This field does not exist if the connection is disconnected.) |
      +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | sqltext           | Executed SQL statement content. (This field does not exist if the audit connection is disconnected.)                                              |
      +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | user              | Login account.                                                                                                                                    |
      +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | host              | Login host. The value is **localhost** for local login and is empty for remote login.                                                             |
      +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | external_user     | External username.                                                                                                                                |
      +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | ip                | IP address of the remotely-connected client. The local IP address is empty.                                                                       |
      +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | default_db        | Default database on which SQL statements are executed.                                                                                            |
      +-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001470260233.png
