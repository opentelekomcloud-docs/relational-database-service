:original_name: rds_06_0040.html

.. _rds_06_0040:

Querying Tags of a DB Instance
==============================

Function
--------

This API is used to query tags of a DB instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/tags

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

      GET https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/ab67f50938cb4d189cc2163ca0098fe7in03/tags

Response
--------

-  Normal response

   .. table:: **Table 3** Parameter description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                         |
      +=======================+=======================+=====================================================================================+
      | tags                  | Array of objects      | Specifies the tag list. If there is no tag in the list, an empty array is returned. |
      |                       |                       |                                                                                     |
      |                       |                       | For details, see :ref:`Table 4 <rds_06_0040__table136451019132019>`.                |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------+

   .. _rds_06_0040__table136451019132019:

   .. table:: **Table 4** tags field data structure description

      +-----------------------+-----------------------+---------------------------------------------+
      | Name                  | Type                  | Description                                 |
      +=======================+=======================+=============================================+
      | key                   | String                | Specifies the tag key.                      |
      +-----------------------+-----------------------+---------------------------------------------+
      | values                | String                | Specifies the lists the tag values.         |
      +-----------------------+-----------------------+---------------------------------------------+
      | tag_type              | String                | Tag type.                                   |
      |                       |                       |                                             |
      |                       |                       | Enumerated values: **user** and **system**. |
      +-----------------------+-----------------------+---------------------------------------------+

-  Example normal response

   .. code-block::

      {
           "tags": [{
              "key": "keyName",
              "value": "keyValue",
              "tag_type": "user"
              }]
      }

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
