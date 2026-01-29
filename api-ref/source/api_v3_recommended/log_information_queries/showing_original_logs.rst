:original_name: rds_06_0101.html

.. _rds_06_0101:

Showing Original Logs
=====================

Function
--------

This API is used to enable or disable Show Original Log.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

This API is available only to RDS for MySQL and RDS for PostgreSQL.

URI
---

-  URI format

   PUT https://{Endpoint}/v3/{project_id}/instances/{instance_id}/slowlog-sensitization/{status}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                      |
      +=================+=================+=================+==================================================================================================+
      | project_id      | Yes             | String          | Specifies the project ID of a tenant in a region.                                                |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
      | instance_id     | Yes             | String          | Specifies the ID of the queried DB instance.                                                     |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
      | status          | Yes             | String          | Whether to enable Show Original Log. The value can be **on** or **off**.                         |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | -  **on**: Enable this function.                                                                 |
      |                 |                 |                 | -  **off**: Disable this function.                                                               |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   .. table:: **Table 2** Request header parameters

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
      +=================+=================+=================+=====================================================================================================================================================+
      | X-Auth-Token    | Yes             | String          | Specifies the user token.                                                                                                                           |
      |                 |                 |                 |                                                                                                                                                     |
      |                 |                 |                 | The user token is a response to the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

-  URI example

   .. code-block:: text

      PUT https://rds.eu-de.otc.t-systems.com/v3/054ea741f700d4a32f1bc00f5c80dd4c/instances/88a31c96daa0464482599360c34a7a6bin01/slowlog-sensitization/on

Response
--------

-  Normal response

   None

-  Abnormal Response

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
