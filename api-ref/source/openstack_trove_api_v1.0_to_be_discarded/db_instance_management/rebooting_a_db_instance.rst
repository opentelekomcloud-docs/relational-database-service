:original_name: en-us_topic_0056890051.html

.. _en-us_topic_0056890051:

Rebooting a DB Instance
=======================

Function
--------

This API is used to reboot a DB instance.

.. important::

   The RDS DB instance will be unavailable during the reboot process. Exercise caution when performing this operation.

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

   The DB instance cannot reboot when it is being created, scaled, backed up, restored, or its instance class is being changed.

   Currently, only the DB engines MySQL and PostgreSQL are supported by the API.

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      ======= ========= ====== =============================
      Name    Mandatory Type   Description
      ======= ========= ====== =============================
      restart Yes       String This parameter is left blank.
      ======= ========= ====== =============================

-  Request example

   .. code-block:: text

      {
            "restart": {}
      }

Normal Response
---------------

None

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
