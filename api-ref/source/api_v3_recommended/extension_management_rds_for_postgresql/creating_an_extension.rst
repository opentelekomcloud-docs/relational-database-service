:original_name: rds_11_0012.html

.. _rds_11_0012:

Creating an Extension
=====================

Function
--------

This API is used to create an extension for a specified database.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

This operation cannot be performed when the DB instance is in any of the following statuses: creating, changing instance class, changing port, or abnormal.

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/extensions

-  Parameter description

   .. table:: **Table 1** Parameters

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the DB instance ID.                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================+
   | Content-Type    | Yes             | String          | The content type.                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | The default value is **application/json**.                                                                                                          |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token    | Yes             | String          | Specifies the user token.                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | The user token is a response to the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Parameters

   +----------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                                                                            |
   +================+===========+========+========================================================================================================================================+
   | database_name  | Yes       | String | The name of the specific database created inside the RDS instance. This is the logical database name, not the RDS instance identifier. |
   +----------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------+
   | extension_name | Yes       | String | Extension name.                                                                                                                        |
   +----------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Create the extension **pg_stat_statements** for database **db1**.

.. code-block:: text

   POST https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/f569f1358436479dbcba8603c32cc4aein03/extensions
   {
     "database_name" : "db1",
     "extension_name" : "pg_stat_statements"
   }

Response
--------

-  Example normal response

   .. code-block::

      {}

-  Abnormal response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

-  Normal

   200

-  Abnormal

   For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
