:original_name: en-us_topic_0037147508.html

.. _en-us_topic_0037147508:

Restoring Data to the Original DB Instance
==========================================

Function
--------

This API is used to restore data to the original DB instance.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/instances/{instanceId}/action

   Method: POST

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

-  Restrictions

   The DB engine Microsoft SQL Server is not supported.

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +---------+-----------+---------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name    | Mandatory | Type                                                                                                    | Description                                                                                                                                                                             |
      +=========+===========+=========================================================================================================+=========================================================================================================================================================================================+
      | restore | Yes       | Dictionary data structure. For details, see :ref:`Table 3 <en-us_topic_0037147508__table634280816954>`. | Specifies the restore information, including **backupRef** and **restoreTime**. At least one of them must be specified. If both of them are specified, only **backupRef** takes effect. |
      +---------+-----------+---------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0037147508__table634280816954:

   .. table:: **Table 3** restore field data structure description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                  |
      +=================+=================+=================+==============================================================================================+
      | backupRef       | No              | String          | Specifies the full backup file ID.                                                           |
      |                 |                 |                 |                                                                                              |
      |                 |                 |                 | .. important::                                                                               |
      |                 |                 |                 |                                                                                              |
      |                 |                 |                 |    NOTICE:                                                                                   |
      |                 |                 |                 |    If **backupRef** is empty, **restoreTime** is mandatory. Otherwise, an error is reported. |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
      | restoreTime     | No              | Long            | Specifies the time point to which the DB instance is restored.                               |
      |                 |                 |                 |                                                                                              |
      |                 |                 |                 | .. important::                                                                               |
      |                 |                 |                 |                                                                                              |
      |                 |                 |                 |    NOTICE:                                                                                   |
      |                 |                 |                 |    If **restoreTime** is empty, **backupRef** is mandatory. Otherwise, an error is reported. |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      {
      "restore": {
              "backupRef":"a9832168-7541-4536-b8d9-a8a9b79cf1b4"
          }
      }

Normal Response
---------------

-  Parameter description

   .. table:: **Table 4** Parameter description

      +-------------+-----------------------------------------------------------------------------------------------------+--------------------------------------------------------+
      | Name        | Type                                                                                                | Description                                            |
      +=============+=====================================================================================================+========================================================+
      | extendparam | Dictionary data structure. For details, see :ref:`Table 5 <en-us_topic_0037147508__table52869820>`. | Indicates the returned **extendparam** key-value pair. |
      +-------------+-----------------------------------------------------------------------------------------------------+--------------------------------------------------------+

   .. _en-us_topic_0037147508__table52869820:

   .. table:: **Table 5** extendparam field data structure description

      +------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------+
      | Name | Type                                                                                          | Description                                            |
      +======+===============================================================================================+========================================================+
      | jobs | List data structure. For details, see :ref:`Table 6 <en-us_topic_0037147508__table32267243>`. | Indicates the returned **jobs** parameter information. |
      +------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------+

   .. _en-us_topic_0037147508__table32267243:

   .. table:: **Table 6** jobs field data structure description

      ==== ====== ======================
      Name Type   Description
      ==== ====== ======================
      id   String Indicates the task ID.
      ==== ====== ======================

-  Response example

   .. code-block:: text

      {
          "extendparam": {
              "jobs": [
                  {
                      "id": "ff80808156fa51c50156fa7c20210bc9"
                  }
              ]
          }
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
