:original_name: en-us_topic_0000002320384084.html

.. _en-us_topic_0000002320384084:

Querying Application Records of a Parameter Template
====================================================

Function
--------

This API is used to query application records of a parameter template.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  Default parameter templates cannot be deleted.
-  The following DB engines are supported: MySQL, Microsoft SQL Server, and PostgreSQL.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/configurations/{config_id}/apply-histories?offset={offset}&limit={limit}

-  Parameter description

   .. table:: **Table 1** Parameters

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                      |
      +=================+=================+=================+==================================================================================================+
      | project_id      | Yes             | String          | Specifies the project ID of a tenant in a region.                                                |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
      | config_id       | Yes             | String          | Specifies the parameter template ID.                                                             |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
      | offset          | No              | Integer         | Index offset. The query starts from the next piece of data indexed by this parameter.            |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | **Range**:                                                                                       |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | The value must be a non-negative number.                                                         |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | **Default Value**:                                                                               |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | The default value is **0**, indicating that the query starts from the first data record.         |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
      | limit           | No              | Integer         | Number of records to be queried.                                                                 |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | **Range**:                                                                                       |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | 1-100                                                                                            |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | **Default Value**:                                                                               |
      |                 |                 |                 |                                                                                                  |
      |                 |                 |                 | If this parameter is not specified, the default value **10** is used.                            |
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

-  Example

   GET https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/configurations/6a906cd03be84aff81cd41c4c61234e0pr01/apply-histories

Response
--------

-  Normal response

   .. table:: **Table 3** Parameters

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                          |
      +=======================+=======================+======================================================================================+
      | total_count           | Integer               | Total number of parameter template application records.                              |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------+
      | histories             | Array of objects      | Event details list.                                                                  |
      |                       |                       |                                                                                      |
      |                       |                       | For details, see :ref:`Table 4 <en-us_topic_0000002320384084__table19183193052719>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------+

   .. _en-us_topic_0000002320384084__table19183193052719:

   .. table:: **Table 4** Data structure description of field histories

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                |
      +=======================+=======================+============================================================================================================+
      | instance_id           | String                | ID of the instance to which the parameter template is applied.                                             |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
      | instance_name         | String                | Name of the instance to which the parameter template is applied.                                           |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
      | apply_result          | String                | Result of applying the parameter template.                                                                 |
      |                       |                       |                                                                                                            |
      |                       |                       | -  SUCCESS                                                                                                 |
      |                       |                       | -  FAILED                                                                                                  |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
      | apply_time            | String                | Time when the parameter template is applied.                                                               |
      |                       |                       |                                                                                                            |
      |                       |                       | The value is in the "yyyy-mm-ddThh:mm:ssZ" format.                                                         |
      |                       |                       |                                                                                                            |
      |                       |                       | T is the separator between the calendar and the hourly notation of time. Z indicates the time zone offset. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
      | error_code            | String                | Error code displayed when you submit the request to apply the parameter template.                          |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block::

      {
        "histories" : [ {
          "instance_id" : "08dbfde762034d5a9ace8f73c156e2e5in01",
          "instance_name" : "TestInstance",
          "apply_result" : "SUCCESS",
          "apply_time" : "2025-07-07T07:34:08+0000",
          "error_code" : ""
        } ],
        "total_count" : 1
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
