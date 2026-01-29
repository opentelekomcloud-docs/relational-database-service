:original_name: rds_20_0001.html

.. _rds_20_0001:

Adding a SQL Throttling Rule for a Database
===========================================

Function
--------

This API is used to add a SQL throttling rule for a database.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  SQL statements executed by built-in users (**rdsAdmin**, **rdsMetric**, **rdsRepl**, and **rdsBackup**) are not affected by SQL throttling rules.

-  To use SQL throttling, the self-developed extension rds_pg_sql_ccl must be installed. For details, see :ref:`Creating an Extension <rds_11_0012>`.

-  Before enabling SQL throttling, you must set the RDS for PostgreSQL kernel parameter **rds_pg_sql_ccl.enable_ccl** to **ON**. For details, see :ref:`Modifying a Parameter Template <rds_09_0303>`.

   By default, the kernel parameter **rds_pg_sql_ccl.enable_ccl** is set to **OFF**.

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/sql-limit

-  Parameter description

   .. table:: **Table 1** Parameters

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Instance ID.                                                                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================+
   | Content-Type    | Yes             | String          | The content type.                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | The default value is **application/json**.                                                                                                          |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token    | Yes             | String          | Specifies the user token.                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | The user token is a response to the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Parameters

   +-----------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type    | Description                                                                                                                                                                                          |
   +=================+===========+=========+======================================================================================================================================================================================================+
   | db_name         | Yes       | String  | Database name. For example: "**postgres**".                                                                                                                                                          |
   +-----------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | query_id        | No        | Long    | Internal hash code calculated by the SQL parse tree. The default value is **0**. The value range is from -9223372036854775808 to 9223372036854775807.                                                |
   +-----------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | query_string    | No        | String  | Text format of an SQL statement. Only either **query_id** or **query_string** can be specified.                                                                                                      |
   +-----------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | max_concurrency | Yes       | Integer | Number of SQL statements that can be executed at the same time. If the value is less than or equal to 0, the number is not limited. The default value is **0**. The value range is from -1 to 50000. |
   +-----------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | max_waiting     | Yes       | Integer | Maximum waiting time, in seconds.                                                                                                                                                                    |
   +-----------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | search_path     | No        | String  | Schema search order set for names that are not schema-qualified. The default value is **public**.                                                                                                    |
   +-----------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Add a SQL throttling rule for a database.

.. code-block:: text

   POST https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/49b9dd1d6f464ba4bc91df5cbd2e52ebin03/sql-limit
   {
      "db_name" : "postgres",
      "query_id" : 1,
      "max_concurrency" : 10,
      "max_waiting" : 10,
      "search_path" : "public"
    }

Response
--------

-  Normal response

   .. table:: **Table 4** Parameters

      ========= ====== ====================================================
      Parameter Type   Description
      ========= ====== ====================================================
      resp      String Returns **successful** if the calling is successful.
      ========= ====== ====================================================

-  Example normal response

   .. code-block::

      {
         "resp" : "successful"
       }

-  Abnormal response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

-  Normal

   200

-  Abnormal

   For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
