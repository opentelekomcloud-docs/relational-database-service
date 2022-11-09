:original_name: rds_01_0008.html

.. _rds_01_0008:

Deleting a Tag
==============

Function
--------

This API is used to delete the tag associated with a DB instance.

URI
---

-  URI format

   PATH: /v1/{project_id}/rds/{instanceId}/tags

   Method: DELETE

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      instanceId Yes       Specifies the primary node ID of the DB instance.
      ========== ========= =================================================

-  Restrictions

   Standby DB instances do not support tag deletion.

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                      |
      +=================+=================+=================+==================================================================================================================================================================================+
      | key             | Yes             | String          | Specifies the tag key.                                                                                                                                                           |
      |                 |                 |                 |                                                                                                                                                                                  |
      |                 |                 |                 | Its value cannot be empty and must be 1 to 36 Unicode characters in length. It cannot contain nonprintable ASCII characters (0-31) and the following special characters: \*<>\\= |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      {

          "key": "ENV"
      }

Normal Response
---------------

None

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
