:original_name: en-us_topic_0056890265.html

.. _en-us_topic_0056890265:

Adding Custom Parameters
========================

Function
--------

This API is used to add parameter information to a parameter template identified by a specified ID.

URI
---

-  URI format

   PATH: /v1.0/{project_id}/configurations/{id}

   Method: PATCH

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      id         Yes       Specifies the parameter template ID.
      ========== ========= =================================================

-  Restrictions

   -  Currently, the DB engines MySQL and PostgreSQL support modifying parameter templates.
   -  The values of the newly added parameters must be within the default value range of the specified database version. For details about the range of parameter values, see section "Modifying Parameters in a Parameter Template" in the *Relational Database Service User Guide*.
   -  Parameter template modifications will take effect for DB instances to which the parameter template applies. Some modifications take effect only after the DB instance reboots.

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +---------------+-----------+-----------------------------------------------------------------------------------------------------------+------------------------------------------+
      | Name          | Mandatory | Type                                                                                                      | Description                              |
      +===============+===========+===========================================================================================================+==========================================+
      | configuration | Yes       | Dictionary data structure. For details, see :ref:`Table 3 <en-us_topic_0056890265__table23308179103438>`. | Specifies the parameter template object. |
      +---------------+-----------+-----------------------------------------------------------------------------------------------------------+------------------------------------------+

   .. _en-us_topic_0056890265__table23308179103438:

   .. table:: **Table 3** configuration field data structure description

      +--------+-----------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------+
      | Name   | Mandatory | Type                                                                                                      | Description                                                                              |
      +========+===========+===========================================================================================================+==========================================================================================+
      | values | No        | Dictionary data structure. For details, see :ref:`Table 4 <en-us_topic_0056890265__table25655849103438>`. | Specifies the parameter values defined by users based on the default parameter template. |
      +--------+-----------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------+

   .. _en-us_topic_0056890265__table25655849103438:

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
     "externalMessage": "Operation successful."
   }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
