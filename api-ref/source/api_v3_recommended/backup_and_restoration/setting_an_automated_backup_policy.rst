:original_name: rds_09_0002.html

.. _rds_09_0002:

Setting an Automated Backup Policy
==================================

Function
--------

This API is used to set an automated backup policy.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   PUT https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/backups/policy

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the DB instance ID.                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                              |
      +=================+=================+=================+==========================================================================================================+
      | backup_policy   | Yes             | Object          | Specifies the backup policy objects, including the backup retention period (days) and backup start time. |
      |                 |                 |                 |                                                                                                          |
      |                 |                 |                 | For details, see :ref:`Table 3 <rds_09_0002__table163715367507>`.                                        |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+

   .. _rds_09_0002__table163715367507:

   .. table:: **Table 3** backup_policy field data structure description

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                      |
      +=================+=================+=================+==================================================================================================================================================================================================+
      | keep_days       | Yes             | Integer         | Specifies the number of days to retain the generated backup files.                                                                                                                               |
      |                 |                 |                 |                                                                                                                                                                                                  |
      |                 |                 |                 | The value range is from 1 to 732.                                                                                                                                                                |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | start_time      | No              | String          | Specifies the backup time window. Automated backups will be triggered during the backup time window. This parameter is mandatory except that the automated backup policy is disabled.            |
      |                 |                 |                 |                                                                                                                                                                                                  |
      |                 |                 |                 | The value must be a valid value in the "hh:mm-HH:MM" format. The current time is in the UTC format.                                                                                              |
      |                 |                 |                 |                                                                                                                                                                                                  |
      |                 |                 |                 | -  The **HH** value must be 1 greater than the **hh** value.                                                                                                                                     |
      |                 |                 |                 | -  The values of **mm** and **MM** must be the same and must be set to any of the following: **00**, **15**, **30**, or **45**.                                                                  |
      |                 |                 |                 |                                                                                                                                                                                                  |
      |                 |                 |                 | Example value:                                                                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                                                                  |
      |                 |                 |                 | -  08:15-09:15                                                                                                                                                                                   |
      |                 |                 |                 | -  23:00-00:00                                                                                                                                                                                   |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | period          | No              | String          | Specifies the backup cycle configuration. Data will be automatically backed up on the selected days every week. This parameter is mandatory except that the automated backup policy is disabled. |
      |                 |                 |                 |                                                                                                                                                                                                  |
      |                 |                 |                 | Value range: The value is digits separated by commas (,), indicating the day of the week and starting from Monday.                                                                               |
      |                 |                 |                 |                                                                                                                                                                                                  |
      |                 |                 |                 | For example, the value **1,2,3,4** indicates that the backup period is Monday, Tuesday, Wednesday, and Thursday.                                                                                 |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example

   PUT https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/backups/policy

-  Request example

   Modifying the automated backup policy:

   .. code-block:: text

      {
          "backup_policy": {
              "keep_days": 7,
              "start_time": "19:00-20:00",
              "period": "1,2"
          }
      }

Response
--------

-  Normal response

   None

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
