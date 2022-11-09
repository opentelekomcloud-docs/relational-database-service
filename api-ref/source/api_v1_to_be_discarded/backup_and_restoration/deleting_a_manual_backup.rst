:original_name: en-us_topic_0037139103.html

.. _en-us_topic_0037139103:

Deleting a Manual Backup
========================

Function
--------

This API is used to delete a manual backup.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/backups/{backupId}

   Method: DELETE

-  Parameter description

   .. table:: **Table 1** Parameter description

      +------------+-----------+--------------------------------------------------------------+
      | Name       | Mandatory | Description                                                  |
      +============+===========+==============================================================+
      | project_id | Yes       | Specifies the project ID of a tenant in a region.            |
      +------------+-----------+--------------------------------------------------------------+
      | backupId   | Yes       | Specifies the backup file ID compliant with the UUID format. |
      +------------+-----------+--------------------------------------------------------------+

Request
-------

None

Normal Response
---------------

{}

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
