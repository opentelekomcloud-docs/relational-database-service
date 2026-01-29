:original_name: rds_05_0032.html

.. _rds_05_0032:

Querying Available Instance Classes for a DB Instance
=====================================================

Function
--------

This API is used to query available instance classes for a DB instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET https://{endpoint}/v3/{project_id}/instances/{instance_id}/flavors-resize

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

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | Specifies the user token.                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | The user token is a response to the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Query available instance classes for a DB instance.

.. code-block:: text

   GET https://rds.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/instances/d674b54d5e0241c49eeb50c82ef3efe0in03/flavors-resize

Response
--------

.. table:: **Table 3** Response body parameters

   +---------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Type             | Description                                                                                                                          |
   +===============+==================+======================================================================================================================================+
   | flavor_groups | Array of objects | List of available instance classes. For details, see :ref:`Table 4 <rds_05_0032__en-us_topic_0000001560574042_table19464718184511>`. |
   +---------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------+

.. _rds_05_0032__en-us_topic_0000001560574042_table19464718184511:

.. table:: **Table 4** Data structure description of field flavor_groups

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                    |
   +=======================+=======================+================================================================================================================================+
   | group_type            | String                | Instance class. Its value can be any of the following:                                                                         |
   |                       |                       |                                                                                                                                |
   |                       |                       | -  **general**: general-purpose                                                                                                |
   |                       |                       | -  **dedicated**: dedicated                                                                                                    |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | compute_flavors       | Array of objects      | List of compute specifications. For details, see :ref:`Table 5 <rds_05_0032__en-us_topic_0000001560574042_table145112545559>`. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+

.. _rds_05_0032__en-us_topic_0000001560574042_table145112545559:

.. table:: **Table 5** Data structure description of field compute_flavors

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                    |
   +=======================+=======================+================================================================================================================================================================================+
   | id                    | String                | Specification ID, which is unique.                                                                                                                                             |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | code                  | String                | Resource specification code. Example: **rds.mysql.n1.xlarge.4.rr**                                                                                                             |
   |                       |                       |                                                                                                                                                                                |
   |                       |                       | For more specifications, see :ref:`Querying Database Specifications <rds_06_0002>`.                                                                                            |
   |                       |                       |                                                                                                                                                                                |
   |                       |                       | -  **rds**: indicates the RDS product.                                                                                                                                         |
   |                       |                       | -  **mysql**: indicates the DB engine.                                                                                                                                         |
   |                       |                       | -  **n1.xlarge.4**: indicates the high memory specifications.                                                                                                                  |
   |                       |                       | -  **rr**: indicates read replicas (**.ha** indicates primary/standby DB instances).                                                                                           |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vcpus                 | String                | Number of vCPUs. For example, the value **1** indicates one vCPU.                                                                                                              |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ram                   | String                | Memory size in GB.                                                                                                                                                             |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | az_status             | Map<String,String>    | AZ information. **key** indicates the AZ associated with the specification, and **value** indicates the specification status in the AZ. The value can be any of the following: |
   |                       |                       |                                                                                                                                                                                |
   |                       |                       | -  **normal**: The specification is normal.                                                                                                                                    |
   |                       |                       | -  **abandon**: The specification is abandoned.                                                                                                                                |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block::

      {
        "flavor_groups" : [ {
          "group_type" : "general",
          "compute_flavors" : [ {
            "id" : "400fd0df-0502-34f1-99be-ccf2a04241ae",
            "code" : "rds.pg.n1.medium.2",
            "vcpus" : "1",
            "ram" : "2",
            "az_status" : {
              "****" : "normal"
            }
          }, {
            "id" : "4937f920-ba42-37a8-a375-ab46ef030814",
            "code" : "rds.pg.n1.xlarge.4",
            "vcpus" : "4",
            "ram" : "16",
            "az_status" : {
              "****" : "normal"
            }
          }, {
            "id" : "32a8aa95-72cc-34c7-873b-827e23f3ccec",
            "code" : "rds.pg.n1.2xlarge.2",
            "vcpus" : "8",
            "ram" : "16",
            "az_status" : {
              "****" : "normal"
            }
          }, {
            "id" : "98c033ca-a0f2-34be-8b27-c5dda5e6bee1",
            "code" : "rds.pg.n1.2xlarge.4",
            "vcpus" : "8",
            "ram" : "32",
            "az_status" : {
              "****" : "normal"
            }
          } ]
        } ]
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
