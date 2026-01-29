:original_name: rds_05_0018.html

.. _rds_05_0018:

Changing a Database Port
========================

Function
--------

This API is used to change a database port.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  Changing of port will affect RDS instance access. Relevant Security group rules will need to be adapted. Also access from application/ECS side will need to change accordingly.
-  The database port cannot be changed when a DB instance is being created or rebooted, its specifications are being modified, database users are being created or deleted, or backups are being created for the DB instance.

URI
---

-  URI format

   PUT https://{*Endpoint*}/v3/{*project_id*}/instances/{*instance_id*}/port

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

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                |
      +=================+=================+=================+============================================================================================================================================+
      | port            | Yes             | Integer         | Specifies port information for all DB engines.                                                                                             |
      |                 |                 |                 |                                                                                                                                            |
      |                 |                 |                 | -  The MySQL database port ranges from 1024 to 65535 (excluding 12017 and 33071, which are occupied by the RDS system and cannot be used). |
      |                 |                 |                 | -  The PostgreSQL database port ranges from 2100 to 9500.                                                                                  |
      |                 |                 |                 | -  The Microsoft SQL Server database port is 1433 or ranges from 2100 to 9500 (excluding 5355 and 5985).                                   |
      |                 |                 |                 |                                                                                                                                            |
      |                 |                 |                 | The default values is as follows:                                                                                                          |
      |                 |                 |                 |                                                                                                                                            |
      |                 |                 |                 | -  The default value of MySQL is 3306.                                                                                                     |
      |                 |                 |                 | -  The default value of PostgreSQL is 5432.                                                                                                |
      |                 |                 |                 | -  The default value of Microsoft SQL Server is 1433.                                                                                      |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+

-  Example

   PUT https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/port

-  Request example

   .. code-block:: text

      {
           "port": 8836
      }

Response
--------

-  Normal response

   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Name                              | Description                                                                                                                     |
   +===================================+=================================================================================================================================+
   | workflowId                        | Indicates the workflow ID.                                                                                                      |
   |                                   |                                                                                                                                 |
   |                                   | For details about how to query this parameter, see :ref:`Obtaining Information About a Task with a Specified ID <rds_13_0003>`. |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "workflowId":"83abc7bc-2c70-4534-8565-351187b37715"
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
