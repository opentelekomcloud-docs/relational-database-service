:original_name: rds_01_0151.html

.. _rds_01_0151:

Changing the Storage Type of a DB Instance
==========================================

Function
--------

This API is used to change the storage type of a DB instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Constraints
-----------

-  The storage type of an instance can be changed only when the instance is in the **Available** state.
-  Changing the storage type may affect storage performance, so the storage type should be changed during off-peak hours.
-  If the storage type of a read replica is different from that of its associated DB instance, the data synchronization may be affected. To change the storage type of a DB instance, change that of its read replica (if any) first to ensure that the storage type of the read replica is the same as that of the DB instance.

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/action

-  Parameter description

   .. table:: **Table 1** URI Parameters

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
   | Content-Type    | Yes             | String          | The content type.                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | The default value is **application/json**.                                                                                                          |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token    | Yes             | String          | Specifies the user token.                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | The user token is a response to the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                      |
   +=================+=================+=================+==================================================================================================+
   | change_volume   | Yes             | Object          | Target storage type.                                                                             |
   |                 |                 |                 |                                                                                                  |
   |                 |                 |                 | For details, see :ref:`Table 4 <rds_01_0151__en-us_topic_0000002496892257_table17521151123114>`. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+

.. _rds_01_0151__en-us_topic_0000002496892257_table17521151123114:

.. table:: **Table 4** change_volume field data structure description

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                              |
   +=================+=================+=================+==========================================================================================================+
   | volume_code     | Yes             | Integer         | Specification code of the target storage type.                                                           |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 | -  Values for RDS for MySQL:                                                                             |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 |    -  If the target storage type is ESSD:                                                                |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 |       -  **rds.mysql.volume.essd.ha**: ESSD specification code for primary/standby DB instances          |
   |                 |                 |                 |       -  **rds.mysql.volume.essd.rr**: ESSD specification code for read replicas                         |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 |    -  If the target storage type is cloud SSD:                                                           |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 |       -  **rds.mysql.volume.cloudssd.ha**: cloud SSD specification code for primary/standby DB instances |
   |                 |                 |                 |       -  **rds.mysql.volume.cloudssd.rr**: cloud SSD specification code for read replicas                |
   |                 |                 |                 |       -  **rds.mysql.volume.cloudssd**: cloud SSD specification code for single-node DB instances        |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 | -  Values for RDS for PostgreSQL:                                                                        |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 |    -  If the target storage type is ESSD:                                                                |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 |       -  **rds.pg.volume.essd.ha**: ESSD specification code for primary/standby DB instances             |
   |                 |                 |                 |       -  **rds.pg.volume.essd.rr**: ESSD specification code for read replicas                            |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 |    -  If the target storage type is cloud SSD:                                                           |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 |       -  **rds.pg.volume.cloudssd.ha**: cloud SSD specification code for primary/standby DB instances    |
   |                 |                 |                 |       -  **rds.pg.volume.cloudssd.rr**: cloud SSD specification code for read replicas                   |
   |                 |                 |                 |       -  **rds.pg.volume.cloudssd**: cloud SSD specification code for single-node DB instances           |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 | -  Values for RDS for SQL Server:                                                                        |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 |    -  If the target storage type is ESSD:                                                                |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 |       -  **rds.mssql.volume.essd.ha**: ESSD specification code for primary/standby DB instances          |
   |                 |                 |                 |       -  **rds.mssql.volume.essd.rr**: ESSD specification code for read replicas                         |
   |                 |                 |                 |       -  **rds.mssql.volume.essd**: ESSD specification code for single-node DB instances                 |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 |    -  If the target storage type is cloud SSD:                                                           |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 |       -  **rds.mssql.volume.cloudssd.ha**: cloud SSD specification code for primary/standby DB instances |
   |                 |                 |                 |       -  **rds.mssql.volume.cloudssd.rr**: cloud SSD specification code for read replicas                |
   |                 |                 |                 |       -  **rds.mssql.volume.cloudssd**: cloud SSD specification code for single-node DB instances        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+

Example Request
---------------

Change the storage type of an RDS for MySQL primary/standby DB instance to ESSD.

.. code-block:: text

   POST https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/action

   {
       "change_volume": {
           "volume_code": "rds.mysql.volume.essd.ha"
       }
   }

Response
--------

-  Normal response

   .. table:: **Table 5** Response body parameters

      ========= ====== ===========
      Parameter Type   Description
      ========= ====== ===========
      job_id    String Task ID.
      ========= ====== ===========

-  Example normal response

   .. code-block::

      {
          "job_id": "2b414788a6004883a02390e2eb0ea227"
      }

-  Abnormal response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

-  Normal

   202

-  Abnormal

   For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
