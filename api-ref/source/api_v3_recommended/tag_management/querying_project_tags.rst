:original_name: rds_06_0039.html

.. _rds_06_0039:

Querying Project Tags
=====================

Function
--------

This API is used to query project tags.

-  Learn how to :ref:`authorize and authenticate <rds_03_0001>` this API before using it.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/tags

-  Example

   https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/tags

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

None

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                         |
      +=======================+=======================+=====================================================================================+
      | tags                  | Array of objects      | Specifies the tag list. If there is no tag in the list, an empty array is returned. |
      |                       |                       |                                                                                     |
      |                       |                       | For details, see :ref:`Table 3 <rds_06_0039__table136451019132019>`.                |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------+

   .. _rds_06_0039__table136451019132019:

   .. table:: **Table 3** tags field data structure description

      ====== ====== ===================================
      Name   Type   Description
      ====== ====== ===================================
      key    String Specifies the tag key.
      values String Specifies the lists the tag values.
      ====== ====== ===================================

-  Example normal response

   .. code-block:: text

      {
          "tags": [{
              "key": "key1",
              "values": ["value1"]
          }, {
              "key": "key2",
              "values": ["value2"]
          }]
      }

-  Abnormal Response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
