:original_name: rds_09_0303.html

.. _rds_09_0303:

Modifying a Parameter Template
==============================

Function
--------

This API is used to modify a specified parameter template, including the name, description, and values of specified parameters in the parameter template.

-  Learn how to :ref:`authorize and authenticate <rds_03_0001>` this API before using it.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  The following DB engines are supported: MySQL, PostgreSQL, and Microsoft SQL Server.
-  For Microsoft SQL Server, only the following editions are supported: Microsoft SQL Server 2014 SE, 2016 SE, and 2016 EE.

-  The modified parameter template name must be different from the name of an existing or a default parameter template. Default parameter templates cannot be modified.
-  The values of the edited parameters must be within the default value range of the specified database version. For details about the range of parameter values, see the "Modifying Parameters in a Parameter Template" section in the *Relational Database Service User Guide*.
-  The parameter values to be changed cannot be left blank at the same time.

URI
---

-  URI format

   PUT https://{*Endpoint*}/v3/{*project_id*}/configurations/{config_id}

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

-  Parameter description

   .. important::

      At least one parameter in the request body must be specified. Otherwise, the request fails to be delivered.

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                     |
      +=================+=================+=================+=================================================================================================================================================================================================+
      | name            | No              | String          | Specifies the parameter template name. It contains a maximum of 64 characters and can contain only uppercase letters, lowercase letters, digits, hyphens (-), underscores (_), and periods (.). |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description     | No              | String          | Specifies the parameter template description. It contains a maximum of 256 characters and does not support the following special characters: !<>='&" Its value is left blank by default.        |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | values          | No              | Object          | Specifies the parameter values defined by users based on the default parameter template. If this parameter is left blank, the parameter value cannot be changed.                                |
      |                 |                 |                 |                                                                                                                                                                                                 |
      |                 |                 |                 | For details, see :ref:`Table 3 <rds_09_0303__table597813911376>`.                                                                                                                               |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _rds_09_0303__table597813911376:

   .. table:: **Table 3** values field data structure description

      +-------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name  | Mandatory | Type   | Description                                                                                                                                                                          |
      +=======+===========+========+======================================================================================================================================================================================+
      | key   | No        | String | Specifies the parameter name. For example, in **"max_connections": "10"**, the key is **max_connections**. If **key** is not empty, the parameter **value** cannot be empty, either. |
      +-------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | value | No        | String | Specifies the parameter value. For example, in **"max_connections": "10"**, the value is **10**.                                                                                     |
      +-------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      {
          "name": "configuration_test",
          "description": "configuration_test",
          "values": {
             "max_connections": "10",
             "autocommit": "OFF"
          }
      }

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
