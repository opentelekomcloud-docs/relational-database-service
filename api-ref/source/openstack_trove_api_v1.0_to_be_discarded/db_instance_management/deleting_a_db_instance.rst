:original_name: en-us_topic_0056890052.html

.. _en-us_topic_0056890052:

Deleting a DB Instance
======================

Function
--------

This API is used to delete a DB instance.

URI
---

-  URI format

   PATH: /v1.0/{project_id}/instances/{instanceId}

   Method: DELETE

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= ==================================================
      Name       Mandatory Description
      ========== ========= ==================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      instanceId Yes       Specifies the ID of the DB instance to be deleted.
      ========== ========= ==================================================

-  Restrictions

   -  The standby DB instance cannot be deleted.
   -  All automated backups will be deleted and all manual backups will be retained.
   -  Currently, only the DB engines MySQL and PostgreSQL are supported by the API.

Request
-------

None

Normal Response
---------------

None

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
