:original_name: rds_15_0001.html

.. _rds_15_0001:

Querying Resource Quotas
========================

Function
--------

This API is used to query resource quotas in a project.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/quotas

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Pequest parameters

   .. table:: **Table 2** Request header parameters

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
      +=================+=================+=================+=====================================================================================================================================================+
      | X-Auth-Token    | Yes             | String          | Specifies the user token.                                                                                                                           |
      |                 |                 |                 |                                                                                                                                                     |
      |                 |                 |                 | The user token is a response to the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

-  URI Example

   .. code-block:: text

      GET https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/quotas

Response
--------

-  Normal Response

   .. table:: **Table 3** Parameters

      +-----------------------+-----------------------+----------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                          |
      +=======================+=======================+======================================================================+
      | quotas                | Object                | Specifies the objects in the quota list.                             |
      |                       |                       |                                                                      |
      |                       |                       | For details, see :ref:`Table 4 <rds_15_0001__table136451019132019>`. |
      +-----------------------+-----------------------+----------------------------------------------------------------------+

   .. _rds_15_0001__table136451019132019:

   .. table:: **Table 4** quotas field data structure description

      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                        |
      +=======================+=======================+====================================================================+
      | resources             | Array of objects      | Indicates the resource list objects.                               |
      |                       |                       |                                                                    |
      |                       |                       | For details, see :ref:`Table 5 <rds_15_0001__table1298224684119>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------+

   .. _rds_15_0001__table1298224684119:

   .. table:: **Table 5** resources field data structure description

      +-----------------------+-----------------------+-----------------------------------------+
      | Parameter             | Type                  | Description                             |
      +=======================+=======================+=========================================+
      | quota                 | Integer               | Indicates the project resource quota.   |
      +-----------------------+-----------------------+-----------------------------------------+
      | used                  | Integer               | Indicates the number of used resources. |
      +-----------------------+-----------------------+-----------------------------------------+
      | type                  | String                | Indicates the project resource type.    |
      |                       |                       |                                         |
      |                       |                       | **instance**: instance resources        |
      +-----------------------+-----------------------+-----------------------------------------+

-  Example normal response

   .. code-block::

      {
        "quotas" : {
          "resources" : [ {
            "quota" : 100,
            "used" : 1,
            "type" : "instance"
          } ]
        }
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
