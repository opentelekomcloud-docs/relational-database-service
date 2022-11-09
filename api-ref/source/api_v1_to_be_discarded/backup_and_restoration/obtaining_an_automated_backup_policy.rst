:original_name: en-us_topic_0037139085.html

.. _en-us_topic_0037139085:

Obtaining an Automated Backup Policy
====================================

Function
--------

This API is used to obtain an automated backup policy information.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/instances/{instanceId}/backups/policy

   Method: GET

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                  |
      +=======================+=======================+==============================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                            |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | instanceId            | Yes                   | Specifies the primary node ID of the DB instance.                                                                            |
      |                       |                       |                                                                                                                              |
      |                       |                       | .. note::                                                                                                                    |
      |                       |                       |                                                                                                                              |
      |                       |                       |    This field is not the DB instance ID. You are advised to use API v3 and the DB instance ID to perform related operations. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +--------+-----------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------+
      | Name   | Type                                                                                                      | Description                                                                                              |
      +========+===========================================================================================================+==========================================================================================================+
      | policy | Dictionary data structure. For details, see :ref:`Table 3 <en-us_topic_0037139085__table35260043174853>`. | Indicates the backup policy objects, including the backup retention period (days) and backup start time. |
      +--------+-----------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0037139085__table35260043174853:

   .. table:: **Table 3** policy field data structure description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                                                                                            |
      +=======================+=======================+========================================================================================================================================================================================================================+
      | keepday               | Int                   | Indicates the number of days to retain the generated backup files.                                                                                                                                                     |
      |                       |                       |                                                                                                                                                                                                                        |
      |                       |                       | The value range is from 0 to 732. If this parameter is **0**, the automated backup policy is not set. To extend the retention period, contact customer service. Automated backups can be retained for up to 2562 days. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | starttime             | String                | Indicates the backup start time that has been set. The backup task will be triggered within one hour after the backup start time.                                                                                      |
      |                       |                       |                                                                                                                                                                                                                        |
      |                       |                       | Valid value:                                                                                                                                                                                                           |
      |                       |                       |                                                                                                                                                                                                                        |
      |                       |                       | The value cannot be empty. The format can be hh:mm:ss or hh:mm and must be valid. The time is in the UTC format.                                                                                                       |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
        "policy": {
        "keepday": 7,
        "starttime": "00:00:00"
       }
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
