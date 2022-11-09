:original_name: en-us_topic_0056890266.html

.. _en-us_topic_0056890266:

Deleting a Parameter Template
=============================

Function
--------

This API is used to delete a specified parameter template.

URI
---

-  URI format

   PATH: /v1.0/{project_id}/configurations/{id}

   Method: DELETE

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      id         Yes       Specifies the parameter template ID.
      ========== ========= =================================================

-  Restrictions

   -  Currently, the DB engines MySQL and PostgreSQL support deleting parameter templates.
   -  Parameter templates being applied to DB instances cannot be deleted.
   -  Default parameter templates cannot be deleted.

Request
-------

None

Normal Response
---------------

.. code-block:: text

   {
     "errCode": "RDS.0041",
     "externalMessage": "Operation successful."
   }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
