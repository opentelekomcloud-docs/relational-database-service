:original_name: rds_09_0305.html

.. _rds_09_0305:

Modifying Parameters of a Specified DB Instance
===============================================

Function
--------

This API is used to modify parameters in the parameter template of a specified DB instance.

-  Learn how to :ref:`authorize and authenticate <rds_03_0001>` this API before using it.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  The following DB engines are supported: MySQL, PostgreSQL, and Microsoft SQL Server.
-  For Microsoft SQL Server, only the following editions are supported: Microsoft SQL Server 2014 SE, 2016 SE, and 2016 EE.

-  The values of the edited parameters must be within the default value range of the specified database version. For details about the range of parameter values, see the "Modifying Parameters in a Parameter Template" section in the *Relational Database Service User Guide*.

URI
---

-  URI format

   PUT https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/configurations

-  Example

   https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/configurations

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

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                               |
      +=================+=================+=================+===========================================================================================+
      | values          | Yes             | Object          | Specifies the parameter values defined by users based on the default parameter templates. |
      |                 |                 |                 |                                                                                           |
      |                 |                 |                 | For details, see :ref:`Table 3 <rds_09_0305__table12745180163820>`.                       |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+

   .. _rds_09_0305__table12745180163820:

   .. table:: **Table 3** values field data structure description

      +-------+-----------+--------+------------------------------------------------------------------------------------------------------------+
      | Name  | Mandatory | Type   | Description                                                                                                |
      +=======+===========+========+============================================================================================================+
      | key   | Yes       | String | Specifies the parameter name. For example, in **"max_connections": "10"**, the key is **max_connections**. |
      +-------+-----------+--------+------------------------------------------------------------------------------------------------------------+
      | value | Yes       | String | Specifies the parameter value. For example, in **"max_connections": "10"**, the value is **10**.           |
      +-------+-----------+--------+------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      {
          "values": {
             "max_connections": "10",
             "autocommit": "OFF"
          }
      }

Response
--------

-  Normal response

   .. table:: **Table 4** Parameter description

      +-----------------------+-----------------------+-----------------------------------------+
      | Name                  | Type                  | Description                             |
      +=======================+=======================+=========================================+
      | restart_required      | Boolean               | Indicates whether a reboot is required. |
      |                       |                       |                                         |
      |                       |                       | -  **true**: A reboot is required.      |
      |                       |                       | -  **false**: A reboot is not required. |
      +-----------------------+-----------------------+-----------------------------------------+

-  Example normal response

   .. code-block:: text

      {
        "restart_required": false
      }

-  Abnormal Response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
