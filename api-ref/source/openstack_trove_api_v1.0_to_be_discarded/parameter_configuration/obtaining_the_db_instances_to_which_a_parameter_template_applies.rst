:original_name: en-us_topic_0056890262.html

.. _en-us_topic_0056890262:

Obtaining the DB Instances to Which a Parameter Template Applies
================================================================

Function
--------

This API is used to obtain the DB instances to which a specified parameter template applies.

URI
---

-  URI format

   PATH: /v1.0/{project_id}/configurations/{id}/instances

   Method: GET

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      id         Yes       Specifies the parameter template ID.
      ========== ========= =================================================

-  Restrictions

   Currently, the DB engines MySQL and PostgreSQL support obtaining DB instances to which the specified parameter template applies.

Request
-------

None

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------+-----------------------------------------------------------------------------------------------------+---------------------------------------------+
      | Name      | Type                                                                                                | Description                                 |
      +===========+=====================================================================================================+=============================================+
      | instances | List data structure. For details, see :ref:`Table 3 <en-us_topic_0056890262__table47861511102930>`. | Indicates the DB instance list information. |
      +-----------+-----------------------------------------------------------------------------------------------------+---------------------------------------------+

   .. _en-us_topic_0056890262__table47861511102930:

   .. table:: **Table 3** instances field data structure description

      ==== ====== ===============================
      Name Type   Description
      ==== ====== ===============================
      id   String Indicates the DB instance ID.
      name String Indicates the DB instance name.
      ==== ====== ===============================

-  Response example

   .. code-block:: text

      {
        "instances": [
          {
            "id": "53754eff-3f95-4da8-a908-a88e6ea2f65a",
            "name": "instances_test_1"
      },
      {
            "id": "53754eff-3f95-4da8-a908-a88e6ea2f65b",
            "name": "instances_test_2"
          }
        ]
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
