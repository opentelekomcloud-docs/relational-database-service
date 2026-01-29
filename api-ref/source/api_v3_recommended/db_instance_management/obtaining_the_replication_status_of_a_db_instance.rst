:original_name: rds_05_0033.html

.. _rds_05_0033:

Obtaining the Replication Status of a DB Instance
=================================================

Function
--------

This API is used to obtain the primary/standby replication status of a DB instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

This API is available only to RDS for MySQL and RDS for SQL Server.

URI
---

-  URI format

   GET https://{endpoint}/v3/{project_id}/instances/{instance_id}/replication/status

-  Parameter description

   .. table:: **Table 1** Parameters

      +-----------------------+-----------------------+-----------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                           |
      +=======================+=======================+=======================================================================+
      | project_id            | Yes                   | Project ID of a tenant in a region.                                   |
      |                       |                       |                                                                       |
      |                       |                       | To obtain the value, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------+
      | instance_id           | Yes                   | Instance ID.                                                          |
      +-----------------------+-----------------------+-----------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Request header parameters

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
      +=================+=================+=================+=====================================================================================================================================================+
      | X-Auth-Token    | Yes             | String          | Specifies the user token.                                                                                                                           |
      |                 |                 |                 |                                                                                                                                                     |
      |                 |                 |                 | The user token is a response to the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

-  URI example

   .. code-block:: text

      GET https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/c90928717dc747e2a20099894a87c468in01/replication/status

Response
--------

-  Normal response

   .. table:: **Table 3** Parameters

      +-----------------------+-----------------------+------------------------------------------+
      | Parameter             | Type                  | Description                              |
      +=======================+=======================+==========================================+
      | replication_status    | String                | Replication status:                      |
      |                       |                       |                                          |
      |                       |                       | -  normal                                |
      |                       |                       | -  abnormal                              |
      +-----------------------+-----------------------+------------------------------------------+
      | abnormal_reason       | String                | Reasons why the replication is abnormal. |
      +-----------------------+-----------------------+------------------------------------------+

-  Example normal response

   .. code-block::

      {
          "replication_status": "normal",
          "abnormal_reason": ""
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
