:original_name: en-us_topic_0056890050.html

.. _en-us_topic_0056890050:

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

   PATH: /v1.0/{project_id}/instances/{instanceId}/action

   Method: POST

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      instanceId Yes       Specifies the DB instance ID.
      ========== ========= =================================================

-  Restrictions

   #. The new specifications cannot be the same as the original specifications.
   #. The instance class can be modified only for DB instances whose status is **Available**.
   #. Currently, only the DB engines MySQL and PostgreSQL are supported by the API.

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +--------+-----------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
      | Name   | Type                                                                                                      | Description                                                           |
      +========+===========================================================================================================+=======================================================================+
      | resize | Dictionary data structure. For details, see :ref:`Table 3 <en-us_topic_0056890050__table50214959101956>`. | Specifies the information about the returned parameter **flavorRef**. |
      +--------+-----------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+

   .. _en-us_topic_0056890050__table50214959101956:

   .. table:: **Table 3** resize field data structure description

      +-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name      | Type   | Description                                                                                                                                              |
      +===========+========+==========================================================================================================================================================+
      | flavorRef | String | Specifies the specification ID (**flavors.str_id** in the response message in :ref:`Obtaining All DB Instance Specifications <en-us_topic_0056890255>`). |
      +-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      {
          "resize":{
              "flavorRef":"0d922098-553c-4123-80df-e627a1d41a0d"
          }
      }

Normal Response
---------------

None

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
