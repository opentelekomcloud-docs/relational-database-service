:original_name: rds_05_0019.html

.. _rds_05_0019:

Changing a Security Group
=========================

Function
--------

This API is used to change the security group of a DB instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  Changing of Security Group will affect RDS instances access.

   Relevant Security group rules will need to be adapted. Also access from application/ECS side will need to change accordingly.

-  The security group cannot be changed if the DB instance is in any of the following statuses: creating, upgrading, changing instance class, creating users, or deleting users.

URI
---

-  URI format

   PUT /v3/{*project_id*}/instances/{*instance_id*}/security-group

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

      ================= ========= ====== ================================
      Name              Mandatory Type   Description
      ================= ========= ====== ================================
      security_group_id Yes       String Specifies the security group ID.
      ================= ========= ====== ================================

-  Example

   PUT https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/security-group

-  Request example

   .. code-block:: text

      {
           "security_group_id": "23423kljlj432lk0sdf0234eaa"
      }

Response
--------

-  Normal response

   +-----------------------------------+-----------------------------------------------------------------------------------------------------+
   | Name                              | Description                                                                                         |
   +===================================+=====================================================================================================+
   | workflowId                        | Indicates the workflow ID.                                                                          |
   |                                   |                                                                                                     |
   |                                   | For details about how to query this parameter, see :ref:`Obtaining Task Information <rds_01_0009>`. |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------+

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
