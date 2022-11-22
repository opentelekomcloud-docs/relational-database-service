:original_name: en-us_topic_0034973639.html

.. _en-us_topic_0034973639:

Resetting Parameters to Their Default Values
============================================

Function
--------

This API is used to reset parameters of a specified DB instance to their default values.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/instances/{nodeId}/parameters/default

   Method: PUT

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                  |
      +=======================+=======================+==============================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                            |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | nodeId                | Yes                   | Specifies the primary node ID of the DB instance.                                                                            |
      |                       |                       |                                                                                                                              |
      |                       |                       | .. note::                                                                                                                    |
      |                       |                       |                                                                                                                              |
      |                       |                       |    This field is not the DB instance ID. You are advised to use API v3 and the DB instance ID to perform related operations. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+

-  Restrictions

   -  If a parameter of the primary DB instance is reset to the default value, the corresponding parameter of the standby DB instance is reset to the default setting simultaneously. You cannot reset the parameters of the standby DB instance to their default values. You can reset the parameters of read replicas to their default values.

Request
-------

{}

Note: Curly brackets {} indicate that the API does not obtain the data in the request body.

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                          |
      +=======================+=======================+======================================================================================================================================+
      | shouldRestart         | String                | Indicates whether the parameter needs to be restarted for the modifications to take effect.                                          |
      |                       |                       |                                                                                                                                      |
      |                       |                       | -  The value **1** indicates that the parameter needs to be restarted for the modifications to take effect.                          |
      |                       |                       | -  The value **0** indicates that the parameter does not need to be restarted for the modifications to take effect                   |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
      | setParameteResult     | String                | Indicates the parameter modification result.                                                                                         |
      |                       |                       |                                                                                                                                      |
      |                       |                       | -  The value **1** indicates that the modifications are successful on the primary DB instance but failed on the standby DB instance. |
      |                       |                       | -  **0** indicates that the modifications are successful on every DB instance.                                                       |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
           "shouldRestart": "1",
           "setParameteResult": "0"
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
