:original_name: en-us_topic_0032347781.html

.. _en-us_topic_0032347781:

Deleting a DB Instance
======================

Function
--------

This API is used to delete a DB instance.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/instances/{instanceId}

   Method: DELETE

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

   Standby DB instances cannot be deleted.

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                        |
      +=======================+=======================+====================================================================================================================+
      | keepLastManualBackup  | No                    | This parameter is obsolete. Its value can be left empty or set to an integer and has no impact on calling the API. |
      |                       |                       |                                                                                                                    |
      |                       |                       | All automated backups will be deleted and all manual backups will be retained.                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      {
      "keepLastManualBackup": "0"
      }

Normal Response
---------------

-  Parameter description

   .. table:: **Table 3** Parameter description

      +-------------+-----------------------------------------------------------------------------------------------------+--------------------------------------------------------+
      | Name        | Type                                                                                                | Description                                            |
      +=============+=====================================================================================================+========================================================+
      | extendparam | Dictionary data structure. For details, see :ref:`Table 4 <en-us_topic_0032347781__table32267243>`. | Indicates the returned **extendparam** key-value pair. |
      +-------------+-----------------------------------------------------------------------------------------------------+--------------------------------------------------------+

   .. _en-us_topic_0032347781__table32267243:

   .. table:: **Table 4** extendparam field data structure description

      +------+-----------------------------------------------------------------------------------------------------+--------------------------------------------------------+
      | Name | Type                                                                                                | Description                                            |
      +======+=====================================================================================================+========================================================+
      | jobs | List data structure. For details, see :ref:`Table 5 <en-us_topic_0032347781__table57556452151811>`. | Indicates the returned **jobs** parameter information. |
      +------+-----------------------------------------------------------------------------------------------------+--------------------------------------------------------+

   .. _en-us_topic_0032347781__table57556452151811:

   .. table:: **Table 5** jobs field data structure description

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
                   "id":"ff8080815a88d52c015a8a0db2250003"
               }
            ]
         }
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
