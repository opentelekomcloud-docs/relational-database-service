:original_name: en-us_topic_0034943367.html

.. _en-us_topic_0034943367:

Changing DB Instance Volume
===========================

Function
--------

This API is used to change the DB instance volume.

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

   #. The adjusted volume size must be greater than the original one and the desired volume size must be a multiple of 10.
   #. The sizes of the primary and standby DB instances are the same. When you scale the primary DB instance, its standby DB instance is also scaled.
   #. The DB instances can be scaled when they are in the **Available** state.

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +--------+---------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
      | Name   | Type                                                                                                    | Description                                                       |
      +========+=========================================================================================================+===================================================================+
      | resize | Dictionary data structure. For details, see :ref:`Table 3 <en-us_topic_0034943367__table634280816954>`. | Specifies the information about the request parameter **volume**. |
      +--------+---------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+

   .. _en-us_topic_0034943367__table634280816954:

   .. table:: **Table 3** resize field data structure description

      +--------+----------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
      | Name   | Type                                                                                                     | Description                                                     |
      +========+==========================================================================================================+=================================================================+
      | volume | Dictionary data structure. For details, see :ref:`Table 4 <en-us_topic_0034943367__table5971833216954>`. | Specifies the information about the request parameter **size**. |
      +--------+----------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+

   .. _en-us_topic_0034943367__table5971833216954:

   .. table:: **Table 4** volume field data structure description

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                       |
      +=======================+=======================+===================================================================================================+
      | size                  | Int                   | Specifies the volume size after scaling up. The value must a multiple of 10.                      |
      |                       |                       |                                                                                                   |
      |                       |                       | Its value range is from 50 GB to 4000 GB.                                                         |
      |                       |                       |                                                                                                   |
      |                       |                       | .. important::                                                                                    |
      |                       |                       |                                                                                                   |
      |                       |                       |    NOTICE:                                                                                        |
      |                       |                       |    The adjusted volume size of must be greater than or equal to that of the original volume size. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      {
      "resize": {
              "volume": {
                  "size": 400
              }
          }
      }

Normal Response
---------------

-  Parameter description

   .. table:: **Table 5** Parameter description

      +-------------+-----------------------------------------------------------------------------------------------------+--------------------------------------------------------+
      | Name        | Type                                                                                                | Description                                            |
      +=============+=====================================================================================================+========================================================+
      | extendparam | Dictionary data structure. For details, see :ref:`Table 6 <en-us_topic_0034943367__table52869820>`. | Indicates the returned **extendparam** key-value pair. |
      +-------------+-----------------------------------------------------------------------------------------------------+--------------------------------------------------------+

   .. _en-us_topic_0034943367__table52869820:

   .. table:: **Table 6** extendparam field data structure description

      +------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------+
      | Name | Type                                                                                          | Description                                            |
      +======+===============================================================================================+========================================================+
      | jobs | List data structure. For details, see :ref:`Table 7 <en-us_topic_0034943367__table32267243>`. | Indicates the returned **jobs** parameter information. |
      +------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------+

   .. _en-us_topic_0034943367__table32267243:

   .. table:: **Table 7** jobs field data structure description

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
                      "id": "2b414788-a600-4883-a023-90e2eb0ea227"
                  }
              ]
          }
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
