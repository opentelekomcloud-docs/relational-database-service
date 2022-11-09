:original_name: rds_09_0001.html

.. _rds_09_0001:

Binding or Unbinding an EIP
===========================

Function
--------

This API is used to bind or unbind an EIP.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/instances/{instanceId}/action

   Method: POST

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                  |
      +=======================+=======================+==============================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                            |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | instanceId            | Yes                   | Specifies the primary node ID of the DB instance.                                                                            |
      |                       |                       |                                                                                                                              |
      |                       |                       | .. note::                                                                                                                    |
      |                       |                       |                                                                                                                              |
      |                       |                       |    This field is not the DB instance ID. You are advised to use API v3 and the DB instance ID to perform related operations. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+

-  Restrictions

   First, invoke the VPC API to query EIPs by referring to section "Querying Elastic IP Addresses" in the *Virtual Private Cloud API Reference*. If no EIP is available for the tenant, invoke the VPC API to create an EIP by referring to section "Applying for an Elastic IP Address" in the *Virtual Private Cloud API Reference*.

   EIPs cannot be bound to or unbound from primary/standby DB instances of earlier versions.

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-------------+-----------+------------------------------------------------------------------------------------------------+--------------------------+
      | Name        | Mandatory | Type                                                                                           | Description              |
      +=============+===========+================================================================================================+==========================+
      | setPublicIp | Yes       | Dictionary data structure. For details, see :ref:`Table 3 <rds_09_0001__table16417881161621>`. | Returns EIP information. |
      +-------------+-----------+------------------------------------------------------------------------------------------------+--------------------------+

   .. _rds_09_0001__table16417881161621:

   .. table:: **Table 3** setPublicIp field data structure description

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                   |
      +=================+=================+=================+===============================================================================================================================+
      | action          | Yes             | String          | If this parameter is **enablePublicAccess**, the EIP is bound to the target DB instance.                                      |
      |                 |                 |                 |                                                                                                                               |
      |                 |                 |                 | If this parameter is **disablePublicAccess**, the EIP is unbound from the target DB instance.                                 |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
      | publicIP        | Yes             | String          | Specifies the EIP obtained by invoking the VPC API. This parameter is not contained in the request when unbinding the EIP.    |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
      | publicIPId      | Yes             | String          | Specifies the EIP ID obtained by invoking the VPC API. This parameter is not contained in the request when unbinding the EIP. |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   Binding an EIP:

   .. code-block:: text

      {
          "setPublicIp":{
              "action":"enablePublicAccess",
              "publicIP":"10.145.49.92",
              "publicIPId":"4c9c30f5-54fb-4e44-8c6e-df4ea8790e93"
          }
      }

   Unbinding an EIP:

   .. code-block:: text

      {
          "setPublicIp":{
              "action":"disablePublicAccess"
          }
      }

Normal Response
---------------

.. code-block:: text

   {}

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
