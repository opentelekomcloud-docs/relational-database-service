:original_name: rds_09_0309.html

.. _rds_09_0309:

Replicating a Parameter Template
================================

Function
--------

This API is used to replicate a parameter template.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{*project_id*}/configurations/{config_id}/copy

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | config_id             | Yes                   | Specifies the parameter template ID.                                                             |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

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

   .. table:: **Table 3** Parameter description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                        |
      +=================+=================+=================+====================================================================================================================================================+
      | name            | Yes             | String          | Name of the new parameter template.                                                                                                                |
      |                 |                 |                 |                                                                                                                                                    |
      |                 |                 |                 | The name can contain 1 to 64 characters. It is case-sensitive and can contain only letters, digits, periods (.), underscores (_), and hyphens (-). |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
      | description     | No              | String          | Description of the new parameter template.                                                                                                         |
      |                 |                 |                 |                                                                                                                                                    |
      |                 |                 |                 | The description can contain 0 to 256 characters and cannot contain the following characters: ! < > = & " '                                         |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   POST https://rds.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/configurations/66251c9024774eeb9edd8663a4cbb0a1pr04/copy

   {
      "name" : "copy_by_v31",
      "description" : "copy"
    }

Response
--------

-  Normal response

   .. table:: **Table 4** Parameter description

      +------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                   | Type                  | Description                                                                                                                                                         |
      +========================+=======================+=====================================================================================================================================================================+
      | id                     | String                | Parameter template ID.                                                                                                                                              |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name                   | String                | Parameter template name.                                                                                                                                            |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description            | String                | Parameter template description.                                                                                                                                     |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | datastore_version_name | String                | Database version name.                                                                                                                                              |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | datastore_name         | String                | Database name.                                                                                                                                                      |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | create_time            | String                | Creation time.                                                                                                                                                      |
      |                        |                       |                                                                                                                                                                     |
      |                        |                       | The value is in the yyyy-MM-ddTHH:mm:ssZ format. **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | update_time            | String                | Update time.                                                                                                                                                        |
      |                        |                       |                                                                                                                                                                     |
      |                        |                       | The value is in the yyyy-MM-ddTHH:mm:ssZ format. **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block::

      {
        "id" : "a73a272e50ba427397e90992fbb96f3cpr04",
        "name" : "copy_by_v31",
        "description" : "copy",
        "datastore_version_name" : "mysql5.7",
        "datastore_name" : "mysql",
        "create_time" : "2022-10-31T08:24:06+0000",
        "update_time" : "2022-10-31T08:24:06+0000"
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
