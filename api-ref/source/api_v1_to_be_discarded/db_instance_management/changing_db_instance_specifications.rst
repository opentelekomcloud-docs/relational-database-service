:original_name: en-us_topic_0037365603.html

.. _en-us_topic_0037365603:

Changing DB Instance Specifications
===================================

Function
--------

This API is used to change DB instance specifications.

.. important::

   Services will be interrupted for 5 to 10 minutes when you change DB instance specifications. Exercise caution when performing this operation.

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

   #. The new specifications cannot be the same as the original specifications.
   #. The instance class can be modified only for DB instances whose status is **Available**.

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +--------+----------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
      | Name   | Type                                                                                                     | Description                                                           |
      +========+==========================================================================================================+=======================================================================+
      | resize | Dictionary data structure. For details, see :ref:`Table 3 <en-us_topic_0037365603__table5971833216954>`. | Specifies the information about the returned parameter **flavorRef**. |
      +--------+----------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+

   .. _en-us_topic_0037365603__table5971833216954:

   .. table:: **Table 3** resize field data structure description

      +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name      | Type   | Description                                                                                                                                                  |
      +===========+========+==============================================================================================================================================================+
      | flavorRef | String | Specifies the specification ID (**flavors.id** in the response message in section :ref:`Obtaining All DB Instance Specifications <en-us_topic_0032347783>`). |
      +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      {
      "resize":{
      "flavorRef":"0d922098-553c-4123-80df-e627a1d41a0d"
      }
      }

Normal Response
---------------

-  Parameter description

   .. table:: **Table 4** Parameter description

      ===== =================== ================================
      Name  Type                Description
      ===== =================== ================================
      jobId List data structure Indicates the jobId information.
      ===== =================== ================================

-  Response example

   .. code-block:: text

      {
      "jobId": [
      "ff8080815703e6de015703e98504001a"
      ]
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
