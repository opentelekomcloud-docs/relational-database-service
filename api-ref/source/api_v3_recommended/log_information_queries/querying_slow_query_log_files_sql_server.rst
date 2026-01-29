:original_name: rds_06_0102.html

.. _rds_06_0102:

Querying Slow Query Log Files (SQL Server)
==========================================

Function
--------

This API is used to query slow query log files.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

This API is available only for Microsoft SQL Server.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/slowlog-files?offset={offset}&limit={limit}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                      |
      +=================+=================+=================+==================================================================================================+
      | project_id      | Yes             | String          | Specifies the project ID of a tenant in a region.                                                |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
      | instance_id     | Yes             | String          | Specifies the DB instance ID.                                                                    |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
      | offset          | No              | Integer         | Index offset. The query starts from the next piece of data indexed by this parameter.            |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | The value must be a non-negative number.                                                         |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | The default value is **0**, indicating that the query starts from the first data record.         |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
      | limit           | No              | Integer         | Number of records to be queried.                                                                 |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | The value ranges from 1 (inclusive) to 100 (inclusive).                                          |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | The default value is **10**.                                                                     |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   .. table:: **Table 2** Request header parameters

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
      +=================+=================+=================+=====================================================================================================================================================+
      | X-Auth-Token    | Yes             | String          | Specifies the user token.                                                                                                                           |
      |                 |                 |                 |                                                                                                                                                     |
      |                 |                 |                 | The user token is a response to the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

-  URI example

   .. code-block:: text

      GET https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/cee5265e1e5845649e354841234567dfin01/slowlog-files

Response
--------

-  Normal response

   .. table:: **Table 3** Parameter description

      +-------------+------------------+-------------------------------------------------------------------------------------------------+
      | Name        | Type             | Description                                                                                     |
      +=============+==================+=================================================================================================+
      | list        | Array of objects | Slow log file information. For details, see :ref:`Table 4 <rds_06_0102__response_slowlogfile>`. |
      +-------------+------------------+-------------------------------------------------------------------------------------------------+
      | total_count | Integer          | Total number of files.                                                                          |
      +-------------+------------------+-------------------------------------------------------------------------------------------------+

   .. _rds_06_0102__response_slowlogfile:

   .. table:: **Table 4** SlowLogFile field data structure description

      ========= ====== ===================
      Parameter Type   Description
      ========= ====== ===================
      file_name String File name.
      file_size String File size in bytes.
      ========= ====== ===================

-  Example normal response

   .. code-block::

      {
        "total_count" : 1,
        "list" : [ {
          "file_name" : "SQLTrace.trc",
          "file_size" : "1024"
        } ]
      }

-  Abnormal Response

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
