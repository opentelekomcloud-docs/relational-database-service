:original_name: rds_05_0010.html

.. _rds_05_0010:

Querying the Available SQL Server Character Set
===============================================

Function
--------

This API is used to query the SQL Server character set list.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/collations

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

-  Parameter description

   None

-  Example

   GET https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/collations

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      ======== ============ =============================================
      Name     Type         Description
      ======== ============ =============================================
      charSets List<String> Indicates the character set information list.
      ======== ============ =============================================

-  Example normal response

   .. code-block:: text

      {
          "charSets": ["Chinese_PRC_CI_AS", "SQL_Latin1_General_CP1_CI_AS", "French_BIN", "Chinese_PRC_Stroke_BIN", "Chinese_PRC_CI_AI"]
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
