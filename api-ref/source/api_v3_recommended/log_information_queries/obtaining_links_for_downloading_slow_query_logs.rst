:original_name: rds_05_0039.html

.. _rds_05_0039:

Obtaining Links for Downloading Slow Query Logs
===============================================

Function
--------

This API is used to obtain links for downloading slow query logs.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

.. _rds_05_0039__section1589084513270:

Description
-----------

You need to do this API in two steps:

**For MySQL and PostgreSQL:**

#. .. _rds_05_0039__li209621547152811:

   Sent empty object **"{}"** in request body, in order to initiate exporting of download link.

#. Repeat :ref:`1 <rds_05_0039__li209621547152811>` with same **"{}"** to receive download link.

**For SQLServer:**

#. .. _rds_05_0039__li34057532291:

   Sent **"file_name": "SQLTrace.trc"** in request body, in order to initiate exporting of download link.

#. Repeat :ref:`1 <rds_05_0039__li34057532291>` with same **"file_name": "SQLTrace.trc"** to receive download link.

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/slowlog-download

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

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+-----------------+--------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                      |
      +=================+=================+=================+==================================================+
      | file_name       | No              | String          | Specifies the name of the file to be downloaded. |
      |                 |                 |                 |                                                  |
      |                 |                 |                 | This parameter is mandatory for SQL Server.      |
      |                 |                 |                 |                                                  |
      |                 |                 |                 | The value is SQLTrace.trc                        |
      +-----------------+-----------------+-----------------+--------------------------------------------------+

-  Example

   POST https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/cee5265e1e5845649e354841234567dfin01/slowlog-download

-  Request example

   **For MySQL and PostgreSQL:**

   step 1 request:

   .. code-block:: text

      {}

   step 2 request:

   .. code-block:: text

      {}

   **For SQLServer:**

   step 1 request:

   .. code-block:: text

      {
          "file_name":"SQLTrace.trc"
      }

   step 2 request:

   .. code-block:: text

      {
          "file_name":"SQLTrace.trc"
      }

Response
--------

-  Normal response

   .. table:: **Table 3** Parameter description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                   |
      +=======================+=======================+===============================================================================================================================================+
      | list                  | List                  | Indicates the links for downloading slow query logs. For details, see :ref:`Table 4 <rds_05_0039__en-us_topic_0245436507_table222815913918>`. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the status of generating links for downloading slow query logs.                                                                     |
      |                       |                       |                                                                                                                                               |
      |                       |                       | -  **FINISH**: The download link has been generated.                                                                                          |
      |                       |                       | -  **CREATING**: A file is being generated and the download link is to be prepared.                                                           |
      |                       |                       | -  **FAILED**: Log files fail to be prepared.                                                                                                 |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | count                 | Integer               | Indicates the number of links for downloading slow query logs.                                                                                |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_05_0039__en-us_topic_0245436507_table222815913918:

   .. table:: **Table 4** linkInfo field data structure description

      +-----------------------+-----------------------+---------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                               |
      +=======================+=======================+===========================================================================+
      | workflow_id           | String                | Indicates the workflow ID.                                                |
      +-----------------------+-----------------------+---------------------------------------------------------------------------+
      | file_name             | String                | Indicates the name of the generated file for downloading slow query logs. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------+
      | status                | String                | Indicates the generation status of the current link.                      |
      |                       |                       |                                                                           |
      |                       |                       | -  **EXPORTING**: The download link is being generated.                   |
      |                       |                       | -  **SUCCESS**: The download link is successfully generated.              |
      |                       |                       | -  **FAILED**: The download link failed to be generated.                  |
      +-----------------------+-----------------------+---------------------------------------------------------------------------+
      | file_size             | String                | Indicates the file size.                                                  |
      +-----------------------+-----------------------+---------------------------------------------------------------------------+
      | file_link             | String                | Indicates the download link.                                              |
      |                       |                       |                                                                           |
      |                       |                       | This link is valid for 5 minutes.                                         |
      +-----------------------+-----------------------+---------------------------------------------------------------------------+
      | create_at             | Long                  | Indicates the generation time.                                            |
      +-----------------------+-----------------------+---------------------------------------------------------------------------+

-  Example normal response

   Generating the link for downloading slow query logs:

   .. code-block:: text

      {
          "list": [
              {
                  "workflow_id": "0202bf1a-4181-48b9-bdd8-27ea4cef05b2",
                  "file_name": "054bc98b0a80d39b1faec01373f2f339_slowlog_download_20211117091141667",
                  "status": "EXPORTING",
                  "create_at": 1637140301659
              }
          ],
          "status": "CREATING",
          "count": 1
      }

   Link for downloading slow query logs obtained successfully:

   .. code-block:: text

      {
          "list": [
              {
                  "workflow_id": "0202bf1a-4181-48b9-bdd8-27ea4cef05b2",
                  "file_name": "054bc98b0a80d39b1faec01373f2f339_slowlog_download_20211117091141667",
                  "status": "SUCCESS",
                  "file_size": "922",
                  "file_link": "https://rdsbucket.opxxx.svc.rds.xxxxx",
                  "create_at": 1637140315066
              }
          ],
          "status": "FINISH",
          "count": 1
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
