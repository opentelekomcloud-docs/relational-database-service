:original_name: en-us_topic_0032348280.html

.. _en-us_topic_0032348280:

Obtaining a DB Instance List
============================

Function
--------

This API is used to obtain a DB instance list.

URI
---

-  URI format

   PATH: /rds/v1/{project_id}/instances

   Method: GET

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      ========== ========= =================================================

Request
-------

None

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------+----------------------------------------------------------------------------------------------------+----------------------------------------+
      | Name      | Type                                                                                               | Description                            |
      +===========+====================================================================================================+========================================+
      | instances | List data structure. For details, see :ref:`Table 3 <en-us_topic_0032348280__table4062895917262>`. | Indicates the DB instance information. |
      +-----------+----------------------------------------------------------------------------------------------------+----------------------------------------+

   .. _en-us_topic_0032348280__table4062895917262:

   .. table:: **Table 3** instances field data structure description

      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                                                                                                      | Description                                                                                                                  |
      +=======================+===========================================================================================================+==============================================================================================================================+
      | id                    | String                                                                                                    | Indicates the primary node ID of the DB instance.                                                                            |
      |                       |                                                                                                           |                                                                                                                              |
      |                       |                                                                                                           | .. note::                                                                                                                    |
      |                       |                                                                                                           |                                                                                                                              |
      |                       |                                                                                                           |    This field is not the DB instance ID. You are advised to use API v3 and the DB instance ID to perform related operations. |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                                                                                                    | Indicates the DB instance status.                                                                                            |
      |                       |                                                                                                           |                                                                                                                              |
      |                       |                                                                                                           | Value:                                                                                                                       |
      |                       |                                                                                                           |                                                                                                                              |
      |                       |                                                                                                           | -  If the value is **BUILD**, the instance is being created.                                                                 |
      |                       |                                                                                                           | -  If the value is **ACTIVE**, the instance is normal.                                                                       |
      |                       |                                                                                                           | -  If the value is **FAILED**, the instance is abnormal.                                                                     |
      |                       |                                                                                                           | -  If the value is **MODIFYING**, the instance is being scaled up.                                                           |
      |                       |                                                                                                           | -  If the value is **REBOOTING**, the instance is being rebooted.                                                            |
      |                       |                                                                                                           | -  If the value is **RESTORING**, the instance is being restored.                                                            |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                                                                                                    | Indicates the created DB instance name.                                                                                      |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | created               | String                                                                                                    | Indicates the creation time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                            |
      |                       |                                                                                                           |                                                                                                                              |
      |                       |                                                                                                           | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.           |
      |                       |                                                                                                           |                                                                                                                              |
      |                       |                                                                                                           | .. note::                                                                                                                    |
      |                       |                                                                                                           |                                                                                                                              |
      |                       |                                                                                                           |    The value is empty when the DB instance is being created. After the DB instance is created, the value is not empty.       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | hostname              | String                                                                                                    | Indicates the DB instance connection address. It is a blank string until an ECS is created.                                  |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | type                  | String                                                                                                    | Indicates the DB instance type, which can be **master**, **slave**, or **readreplica**.                                      |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | region                | String                                                                                                    | Indicates the region where the DB instance is deployed.                                                                      |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | updated               | String                                                                                                    | Indicates the updated time, which is the same as **created** in the format.                                                  |
      |                       |                                                                                                           |                                                                                                                              |
      |                       |                                                                                                           | .. note::                                                                                                                    |
      |                       |                                                                                                           |                                                                                                                              |
      |                       |                                                                                                           |    The value is empty when the DB instance is being created. After the DB instance is created, the value is not empty.       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | availabilityZone      | String                                                                                                    | Indicates the AZ ID.                                                                                                         |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | vpc                   | String                                                                                                    | Indicates the VPC ID.                                                                                                        |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | nics                  | Dictionary data structure. For details, see :ref:`Table 4 <en-us_topic_0032348280__table37920950175250>`. | Indicates the nics information.                                                                                              |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | securityGroup         | Dictionary data structure. For details, see :ref:`Table 5 <en-us_topic_0032348280__table3309421917534>`.  | Indicates the security group information.                                                                                    |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | flavor                | Dictionary data structure. For details, see :ref:`Table 6 <en-us_topic_0032348280__table6373831917584>`.  | Indicates the specification information.                                                                                     |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | volume                | Dictionary data structure. For details, see :ref:`Table 7 <en-us_topic_0032348280__table35005463173456>`. | Indicates the volume information.                                                                                            |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | dataStoreInfo         | Dictionary data structure. For details, see :ref:`Table 8 <en-us_topic_0032348280__table16797672173620>`. | Indicates the database information.                                                                                          |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | dbPort                | Int                                                                                                       | Indicates the database port number.                                                                                          |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | backupStrategy        | Dictionary data structure. For details, see :ref:`Table 9 <en-us_topic_0032348280__table50876711173859>`. | Indicates the advanced backup policy.                                                                                        |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | slaveId               | String                                                                                                    | Returned only when you create primary/standby DB instances.                                                                  |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | ha                    | Dictionary data structure. For details, see :ref:`Table 10 <en-us_topic_0032348280__table497888411810>`.  | Indicates the primary/standby DB instance information. Returned only when you obtain a primary/standby DB instance list.     |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | replicaOf             | String                                                                                                    | Returned only when you obtain the read replica information.                                                                  |
      +-----------------------+-----------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0032348280__table37920950175250:

   .. table:: **Table 4** nics field data structure description

      ======== ====== =======================================
      Name     Type   Description
      ======== ====== =======================================
      subnetId String Indicates the network ID of the subnet.
      ======== ====== =======================================

   .. _en-us_topic_0032348280__table3309421917534:

   .. table:: **Table 5** securityGroup field data structure description

      ==== ====== ================================
      Name Type   Description
      ==== ====== ================================
      id   String Indicates the security group ID.
      ==== ====== ================================

   .. _en-us_topic_0032348280__table6373831917584:

   .. table:: **Table 6** flavor field data structure description

      ==== ====== ===============================
      Name Type   Description
      ==== ====== ===============================
      id   String Indicates the specification ID.
      ==== ====== ===============================

   .. _en-us_topic_0032348280__table35005463173456:

   .. table:: **Table 7** volume field data structure description

      ==== ====== ==========================
      Name Type   Description
      ==== ====== ==========================
      type String Indicates the volume type.
      size Int    Indicates the volume size.
      ==== ====== ==========================

   .. _en-us_topic_0032348280__table16797672173620:

   .. table:: **Table 8** dataStoreInfo field data structure description

      ======= ====== ===============================
      Name    Type   Description
      ======= ====== ===============================
      type    String Indicates the DB engine.
      version String Indicates the database version.
      ======= ====== ===============================

   .. _en-us_topic_0032348280__table50876711173859:

   .. table:: **Table 9** backupStrategy field data structure description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                                                                                            |
      +=======================+=======================+========================================================================================================================================================================================================================+
      | startTime             | String                | Indicates the backup start time that has been set. The backup task will be triggered within one hour after the backup start time.                                                                                      |
      |                       |                       |                                                                                                                                                                                                                        |
      |                       |                       | The time is in the UTC format.                                                                                                                                                                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | keepDays              | Int                   | Indicates the number of days to retain the generated backup files.                                                                                                                                                     |
      |                       |                       |                                                                                                                                                                                                                        |
      |                       |                       | The value range is from 0 to 732. If this parameter is **0**, the automated backup policy is not set. To extend the retention period, contact customer service. Automated backups can be retained for up to 2562 days. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0032348280__table497888411810:

   .. table:: **Table 10** ha field data structure description

      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                         |
      +=======================+=======================+=====================================================================+
      | replicationMode       | String                | Indicates the replication mode for the standby DB instance.         |
      |                       |                       |                                                                     |
      |                       |                       | The value cannot be empty.                                          |
      |                       |                       |                                                                     |
      |                       |                       | -  For MySQL, the value is **async** or **semisync**.               |
      |                       |                       | -  For PostgreSQL, the value is **async** or **sync**.              |
      |                       |                       | -  For Microsoft SQL Server, the value is **sync**.                 |
      |                       |                       |                                                                     |
      |                       |                       | .. note::                                                           |
      |                       |                       |                                                                     |
      |                       |                       |    -  **async** indicates the asynchronous replication mode.        |
      |                       |                       |    -  **semisync** indicates the semi-synchronous replication mode. |
      |                       |                       |    -  **sync** indicates the synchronous replication mode.          |
      +-----------------------+-----------------------+---------------------------------------------------------------------+

-  Response example

   Single DB instance:

   .. code-block:: text

      {
          "instances": [
            {
              "id": "252f11f1-2912-4c06-be55-1999bde659c5",
              "status": "BUILD",
              "name": "trove-instance-rep3",
              "created": "2016-06-18T21:21:50+0200",
              "hostname": "192.168.0.132",
              "type": "master",
              "region": "eu-de",
              "updated": "2016-06-18T21:21:50+0200",
              "availabilityZone": "eu-de-01",
              "vpc": "490a4a08-ef4b-44c5-94be-3051ef9e4fce",
              "nics": {
                "subnetId": "0e2eda62-1d42-4d64-a9d1-4e9aa9cd994f"
              },
              "securityGroup": {
                  "id": "2a1f7fc8-3307-42a7-aa6f-42c8b9b8f8c5"
              },
              "flavor": {
                  "id": "bf07a6d4-844a-4023-a776-fc5c5fb71fb4"
              },
              "volume": {
                  "type": "ULTRAHIGH",
                  "size": 100
              },
              "dataStoreInfo": {
                  "type": "MySQL",
                  "version": "5.7"
              },
              "dbPort": 3306,
              "backupStrategy": {
                  "startTime": "01:00:00",
                  "keepDays": 3
              }
          }
       ]
      }

   Primary/standby DB instances:

   .. code-block:: text

      {
          "instances": [
            {
              "id": "252f11f1-2912-4c06-be55-1999bde659c5",
              "status": "BUILD",
              "name": "trove-instance-rep3",
              "created": "2016-06-18T21:21:50+0200",
              "hostname": "192.168.0.132",
              "type": "master",
              "region": "eu-de",
              "updated": "2016-06-18T21:21:50+0200",
              "availabilityZone": "eu-de-01",
              "vpc": "490a4a08-ef4b-44c5-94be-3051ef9e4fce",
              "nics": {
                "subnetId": "0e2eda62-1d42-4d64-a9d1-4e9aa9cd994f"
              },
              "securityGroup": {
                  "id": "2a1f7fc8-3307-42a7-aa6f-42c8b9b8f8c5"
              },
              "flavor": {
                  "id": "bf07a6d4-844a-4023-a776-fc5c5fb71fb4"
              },
              "volume": {
                  "type": "ULTRAHIGH",
                  "size": 100
              },
              "dataStoreInfo": {
                  "type": "MySQL",
                  "version": "5.7"
              },
              "dbPort": 3306,
              "backupStrategy": {
                  "startTime": "01:00:00",
                  "keepDays": 3
              },
              "slaveId": "9405d8b8-a87d-4531-bd3a-e504c8434281",
              "ha": {
                  "replicationMode": "async"
              }
          }
        ]
      }

   Read replica:

   .. code-block:: text

      {
          "instances": [
            {
              "id": "252f11f1-2912-4c06-be55-1999bde659c5",
              "status": "BUILD",
              "name": "trove-instance-rep3",
              "created": "2016-06-18T21:21:50+0200",
              "hostname": "192.168.0.132",
              "type": "readreplica",
              "region": "eu-de",
              "updated": "2016-06-18T21:21:50+0200",
              "availabilityZone": "eu-de-01",
              "vpc": "490a4a08-ef4b-44c5-94be-3051ef9e4fce",
              "nics": {
                "subnetId": "0e2eda62-1d42-4d64-a9d1-4e9aa9cd994f"
              },
              "securityGroup": {
                  "id": "2a1f7fc8-3307-42a7-aa6f-42c8b9b8f8c5"
              },
              "flavor": {
                  "id": "bf07a6d4-844a-4023-a776-fc5c5fb71fb4"
              },
              "volume": {
                  "type": "ULTRAHIGH",
                  "size": 100
              },
              "dataStoreInfo": {
                  "type": "MySQL",
                  "version": "5.7"
              },
              "dbPort": 3306,
              "replicaOf": "252f11f1-2912-4c06-be55-1999bde659c5"
          }
        ]
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
