:original_name: rds_09_0308.html

.. _rds_09_0308:

Deleting a Parameter Template
=============================

Function
--------

This API is used to delete a specified parameter template.

-  Learn how to :ref:`authorize and authenticate <rds_03_0001>` this API before using it.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  The following DB engines are supported: MySQL, PostgreSQL, and Microsoft SQL Server.
-  For Microsoft SQL Server, only the following editions are supported: Microsoft SQL Server 2014 SE, 2016 SE, and 2016 EE.

-  Default parameter templates cannot be deleted.

URI
---

-  URI format

   DELETE https://{*Endpoint*}/v3/{project_id}/configurations/{config_id}

-  Example

   https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/configurations/463b4b58-d0e8-4e2b-9560-5dea4552fde9

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

None

Response
--------

-  Normal response

   None

-  Abnormal response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
