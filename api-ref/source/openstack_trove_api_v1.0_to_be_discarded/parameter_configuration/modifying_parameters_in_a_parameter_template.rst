:original_name: en-us_topic_0056890264.html

.. _en-us_topic_0056890264:

Modifying Parameters in a Parameter Template
============================================

Function
--------

This API is used to modify parameters in a specified parameter template, including the parameter names, descriptions, and values.

URI
---

-  URI format

   PATH: /v1.0/{project_id}/configurations/{id}

   Method: PUT

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      id         Yes       Specifies the parameter template ID.
      ========== ========= =================================================

-  Restrictions

   -  The modified parameter template name must be different from the name of an existing or a default parameter template. Default parameter templates cannot be modified.
   -  Currently, the DB engines MySQL and PostgreSQL support modifying parameter templates.
   -  The values of the edited parameters must be within the default value range of the specified database version. For details about the range of parameter values, see section "Modifying Parameters in a Parameter template " in the *Relational Database Service User Guide*.
   -  Parameter template modifications will take effect for DB instances to which the parameter template applies. Some modifications take effect only after the DB instance reboots.

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +---------------+-----------+-----------------------------------------------------------------------------------------------------------+------------------------------------------+
      | Name          | Mandatory | Type                                                                                                      | Description                              |
      +===============+===========+===========================================================================================================+==========================================+
      | configuration | Yes       | Dictionary data structure. For details, see :ref:`Table 3 <en-us_topic_0056890264__table23308179103438>`. | Specifies the parameter template object. |
      +---------------+-----------+-----------------------------------------------------------------------------------------------------------+------------------------------------------+

   .. _en-us_topic_0056890264__table23308179103438:

   .. table:: **Table 3** configuration field data structure description

      +-------------+-----------+-----------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name        | Mandatory | Type                                                                                                      | Description                                                                                                                                                                                     |
      +=============+===========+===========================================================================================================+=================================================================================================================================================================================================+
      | name        | No        | String                                                                                                    | Specifies the parameter template name. It contains a maximum of 64 characters and can contain only uppercase letters, lowercase letters, digits, hyphens (-), underscores (_), and periods (.). |
      +-------------+-----------+-----------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description | No        | String                                                                                                    | Specifies the parameter template description. It contains a maximum of 256 characters and does not support the following special characters: !<>='&"                                            |
      +-------------+-----------+-----------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | values      | No        | Dictionary data structure. For details, see :ref:`Table 4 <en-us_topic_0056890264__table25655849103438>`. | Specifies the parameter values defined by users based on the default parameter template.                                                                                                        |
      +-------------+-----------+-----------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0056890264__table25655849103438:

   .. table:: **Table 4** values field data structure description

      +-------+-----------+--------+------------------------------------------------------------------------------------------------------------+
      | Name  | Mandatory | Type   | Description                                                                                                |
      +=======+===========+========+============================================================================================================+
      | key   | No        | String | Specifies the parameter name. For example, in **"max_connections": "10"**, the key is **max_connections**. |
      +-------+-----------+--------+------------------------------------------------------------------------------------------------------------+
      | value | No        | String | Specifies the parameter value. For example, in **"max_connections": "10"**, the value is **10**.           |
      +-------+-----------+--------+------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      {
        "configuration": {
          "name": "configuration_test",
          "description": "configuration_test",
          "values": {
             "max_connections": "10",
             "autocommit": "OFF"
          }
        }
      }

Normal Response
---------------

.. code-block:: text

   {
     "errCode": "RDS.0041",
     "externalMessage": "Operation accepted success."
   }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
