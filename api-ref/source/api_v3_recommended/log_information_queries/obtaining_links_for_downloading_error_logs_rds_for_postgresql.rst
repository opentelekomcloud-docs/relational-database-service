:original_name: rds_05_0040.html

.. _rds_05_0040:

Obtaining Links for Downloading Error Logs (RDS for PostgreSQL)
===============================================================

Function
--------

This API is used to obtain links for downloading error logs of a DB instance.

You need to call this API repeatedly until **FINISH** is returned for **status**.

Or, you can use the **workflow_id** value returned by the first API call to query the task status. After the task is successfully executed, call the API again to obtain the download link.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

This API can only be used to obtain links for downloading error logs of an instance that is working properly.

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/errorlog-download

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the ID of the DB instance to be queried.                                               |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Request header parameters

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
      +=================+=================+=================+=====================================================================================================================================================+
      | X-Auth-Token    | Yes             | String          | Specifies the user token.                                                                                                                           |
      |                 |                 |                 |                                                                                                                                                     |
      |                 |                 |                 | The user token is a response to the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example

   .. code-block:: text

      POST https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/3d39c18788b54a919bab633874c159dfin03/errorlog-download

Response
--------

-  Normal response

   .. table:: **Table 3** Parameter description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                        |
      +=======================+=======================+====================================================================================================================================+
      | list                  | Array of objects      | List of links for downloading error logs. For details, see :ref:`Table 4 <rds_05_0040__en-us_topic_0245436507_table222815913918>`. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Status of the error log download link.                                                                                             |
      |                       |                       |                                                                                                                                    |
      |                       |                       | -  **FINISH**: The download link has been generated.                                                                               |
      |                       |                       | -  **CREATING**: A file is being generated and the download link is being prepared.                                                |
      |                       |                       | -  **FAILED**: The log file fails to be prepared.                                                                                  |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | count                 | Integer               | Number of error log links.                                                                                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_05_0040__en-us_topic_0245436507_table222815913918:

   .. table:: **Table 4** Data structure description of the list field

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                     |
      +=======================+=======================+=================================================================================================+
      | workflow_id           | String                | Task ID.                                                                                        |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | file_name             | String                | Name of the generated file for downloading.                                                     |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | status                | String                | Status of the current link.                                                                     |
      |                       |                       |                                                                                                 |
      |                       |                       | -  **SUCCESS**: The download link is successfully generated.                                    |
      |                       |                       | -  **FAILED**: The download link failed to be generated.                                        |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | file_size             | String                | File size, in bytes.                                                                            |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | file_link             | String                | Download link.                                                                                  |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | create_at             | Long                  | Generation time in the UNIX timestamp format. The unit is millisecond and the time zone is UTC. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
      | update_at             | Long                  | Update time in the UNIX timestamp format. The unit is millisecond and the time zone is UTC.     |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+

-  Example normal response

   Link for downloading error logs obtained successfully.

   .. code-block::

      {
         "list" : [ {
           "workflow_id" : "44fb1d85-2fcc-4d63-ad3b-c3d1ecd7000e",
           "file_name" : "054bc9c1f680d55c1f36c006e5a9f67b_errorlog_download_20200515080614589",
           "status" : "success",
           "file_size" : "0",
           "file_link" : "****.com:443/054bc9c1f680d55c1f36c006e5a9f67b_errorlog_download_20200515080614589?AWSAccessKeyId=1BQ38TBCQHAVQXBUMUTC&Expires=1589530200&response-cache-control=no-cache%2Cno-store&Signature=Fgi4%2BLOJ9frAXyOkz5hRoW5O%2BUM%3D",
           "create_at" : 1589529991385,
           "update_at" : 1589529991385
         } ],
         "status" : "finish",
         "count" : 1
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
