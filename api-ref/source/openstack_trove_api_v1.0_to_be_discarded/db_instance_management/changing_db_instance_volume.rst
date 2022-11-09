:original_name: en-us_topic_0056890049.html

.. _en-us_topic_0056890049:

Changing DB Instance Volume
===========================

Function
--------

This API is used to change the DB instance volume.

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

   #. The adjusted volume size must be greater than the original one and the desired volume size must be a multiple of 10.
   #. The sizes of the primary and standby DB instances are the same. When you scale the primary DB instance, its standby DB instance is also scaled.
   #. The DB instances can be scaled when they are in the **Available** state.
   #. Currently, only the DB engines MySQL and PostgreSQL are supported by the API.

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +--------+-----------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------+
      | Name   | Type                                                                                                      | Description                                                        |
      +========+===========================================================================================================+====================================================================+
      | resize | Dictionary data structure. For details, see :ref:`Table 3 <en-us_topic_0056890049__table46186408101854>`. | Specifies the information about the returned parameter **volume**. |
      +--------+-----------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------+

   .. _en-us_topic_0056890049__table46186408101854:

   .. table:: **Table 3** resize field data structure description

      +--------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
      | Name   | Type                                                                                                      | Description                                                      |
      +========+===========================================================================================================+==================================================================+
      | volume | Dictionary data structure. For details, see :ref:`Table 4 <en-us_topic_0056890049__table20238213101854>`. | Specifies the information about the returned parameter **size**. |
      +--------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+

   .. _en-us_topic_0056890049__table20238213101854:

   .. table:: **Table 4** volume field data structure description

      +-----------------------+-----------------------+------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                  |
      +=======================+=======================+==============================================================================+
      | size                  | Int                   | Specifies the volume size after scaling up. The value must a multiple of 10. |
      |                       |                       |                                                                              |
      |                       |                       | Its value range is from 50 GB to 4000 GB.                                    |
      +-----------------------+-----------------------+------------------------------------------------------------------------------+

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

None

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
