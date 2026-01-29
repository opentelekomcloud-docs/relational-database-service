:original_name: rds_11_0014.html

.. _rds_11_0014:

Obtaining the Value of a Specified Parameter for an Instance
============================================================

Function
--------

This API is used to obtain the value of a specified parameter for an instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  This operation cannot be performed when the instance is in the abnormal state.
-  Only the value of **shared_preload_libraries** can be queried.

URI
---

-  URI format

   GET /v3/{project_id}/instances/{instance_id}/parameter/{name}

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
      | name                  | Yes                   | Parameter name.                                                                                  |
      |                       |                       |                                                                                                  |
      |                       |                       | Only the **shared_preload_libraries** parameter can be modified.                                 |
      |                       |                       |                                                                                                  |
      |                       |                       | The default value is **shared_preload_libraries**.                                               |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

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

-  Example

   GET https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/f569f1358436479dbcba8603c32cc4aein03/parameter/shared_preload_libraries

Response
--------

-  Normal response

   .. table:: **Table 3** Parameters

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                                        |
      +=======================+=======================+====================================================================================================================================+
      | name                  | String                | Parameter name.                                                                                                                    |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | value                 | String                | Parameter value.                                                                                                                   |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | restart_required      | Boolean               | Whether a reboot is required.                                                                                                      |
      |                       |                       |                                                                                                                                    |
      |                       |                       | -  **true**: A reboot is required.                                                                                                 |
      |                       |                       | -  **false**: A reboot is not required.                                                                                            |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | value_range           | String                | Parameter value range.                                                                                                             |
      |                       |                       |                                                                                                                                    |
      |                       |                       | If the parameter type is **integer**, the value is **0** or **1**. If the type is **boolean**, the value is **true** or **false**. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | type                  | String                | Parameter type.                                                                                                                    |
      |                       |                       |                                                                                                                                    |
      |                       |                       | The value can be **string**, **integer**, **boolean**, **list**, or **float**.                                                     |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | description           | String                | Parameter description.                                                                                                             |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block::

      {
        "name" : "shared_preload_libraries",
        "value" : "passwordcheck.so,pg_sql_history",
        "restart_required" : true,
        "value_range" : "passwordcheck.so,pg_stat_statements,pg_sql_history",
        "type" : "list",
        "description" : "Lists shared libraries to preload into server."
      }

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
