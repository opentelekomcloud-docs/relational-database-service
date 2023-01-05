:original_name: rds_05_0005.html

.. _rds_05_0005:

Changing a DB Instance Name
===========================

Function
--------

This API is used to change a DB instance name.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   PUT https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/name

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the DB instance ID.                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                              |
      +=================+=================+=================+==========================================================================================================================================================+
      | name            | Yes             | String          | Specifies the DB instance name.                                                                                                                          |
      |                 |                 |                 |                                                                                                                                                          |
      |                 |                 |                 | DB instances of the same type can have same names under the same tenant.                                                                                 |
      |                 |                 |                 |                                                                                                                                                          |
      |                 |                 |                 | The parameter must be 4 to 64 characters long, start with a letter, and contain only letters (case-sensitive), digits, hyphens (-), and underscores (_). |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example

   PUT https://rds.eu-de.otc.t-systems.com/v3/054ea741f700d4a32f1bc00f5c80dd4c/instances/5b409baece064984a1b3eef6addae50cin01/name

-  Request example

   .. code-block:: text

      {
           "name": "Test_2345674"
      }

Response
--------

-  Normal response

   None

-  Example normal response

   None

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
