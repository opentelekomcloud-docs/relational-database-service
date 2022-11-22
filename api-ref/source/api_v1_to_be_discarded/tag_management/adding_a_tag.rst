:original_name: rds_01_0006.html

.. _rds_01_0006:

Adding a Tag
============

Function
--------

This API is used to add a tag to a DB instance.

URI
---

-  URI format

   PATH: /v1/{project_id}/rds/{instanceId}/tags

   Method: POST

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      instanceId Yes       Specifies the primary node ID of the DB instance.
      ========== ========= =================================================

-  Restrictions

   -  A maximum of 20 tags can be added for each DB instance. The tag key must be unique.
   -  If the key in the request body is the same as an existing key in the specified DB instance, the value of the key is overwritten.
   -  Standby DB instances do not support tag adding.

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +------+-----------+--------------------------------------------------------------------------------------------------------------+--------------------------------+
      | Name | Mandatory | Type                                                                                                         | Description                    |
      +======+===========+==============================================================================================================+================================+
      | tag  | Yes       | Dictionary data structure. For details, see :ref:`Table 3 <rds_01_0006__teb132a9896b14904b643d3159d0c06eb>`. | Specifies the tag information. |
      +------+-----------+--------------------------------------------------------------------------------------------------------------+--------------------------------+

   .. _rds_01_0006__teb132a9896b14904b643d3159d0c06eb:

   .. table:: **Table 3** tag field data structure description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                      |
      +=================+=================+=================+==================================================================================================================================================================================+
      | key             | Yes             | String          | Specifies the tag key.                                                                                                                                                           |
      |                 |                 |                 |                                                                                                                                                                                  |
      |                 |                 |                 | Its value cannot be empty and must be 1 to 36 Unicode characters in length. It cannot contain nonprintable ASCII characters (0-31) and the following special characters: \*<>\\= |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | value           | Yes             | String          | Specifies the tag value.                                                                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                                  |
      |                 |                 |                 | Its value can be empty or 1 to 43 Unicode characters in length. It cannot contain nonprintable ASCII characters (0-31) and the following special characters: \*<>\\=             |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      {
           "tag":
              {
                  "key": "ENV",
                  "value":"DEV"
              }
      }

Normal Response
---------------

.. code-block:: text

   {}

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
