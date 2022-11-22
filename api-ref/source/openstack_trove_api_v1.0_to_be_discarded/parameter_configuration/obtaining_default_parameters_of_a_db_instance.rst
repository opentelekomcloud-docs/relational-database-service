:original_name: en-us_topic_0056890259.html

.. _en-us_topic_0056890259:

Obtaining Default Parameters of a DB Instance
=============================================

Function
--------

This API is used to obtain default parameters of a specified DB instance.

URI
---

-  URI format

   PATH: /v1.0/{project_id}/instances/{instanceId}/configuration

   Method: GET

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      instanceId Yes       Specifies the DB instance ID.
      ========== ========= =================================================

-  Restrictions

   Currently, only the DB engines MySQL and PostgreSQL are supported by the API.

Request
-------

None

Normal Response
---------------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +----------+-----------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
      | Name     | Type                                                                                                | Description                                                       |
      +==========+=====================================================================================================+===================================================================+
      | instance | List data structure. For details, see :ref:`Table 3 <en-us_topic_0056890259__table16731081102411>`. | Indicates the parameter information of the specified DB instance. |
      +----------+-----------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+

   .. _en-us_topic_0056890259__table16731081102411:

   .. table:: **Table 3** instance field data structure description

      +---------------+-----------------------------------------------------------------------------------------------------------+----------------------------------------+
      | Name          | Type                                                                                                      | Description                            |
      +===============+===========================================================================================================+========================================+
      | configuration | Dictionary data structure. For details, see :ref:`Table 4 <en-us_topic_0056890259__table39720807102411>`. | Indicates the default parameter value. |
      +---------------+-----------------------------------------------------------------------------------------------------------+----------------------------------------+

   .. _en-us_topic_0056890259__table39720807102411:

   .. table:: **Table 4** configuration field data structure description

      +-------+--------+------------------------------------------------------------------------------------------------------------+
      | Name  | Type   | Description                                                                                                |
      +=======+========+============================================================================================================+
      | key   | String | Indicates the parameter name. For example, in **"max_connections": "10"**, the key is **max_connections**. |
      +-------+--------+------------------------------------------------------------------------------------------------------------+
      | value | String | Indicates the parameter value. For example, in **"max_connections": "10"**, the value is **10**.           |
      +-------+--------+------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
          "instance": {
              "configuration": {
                  "basedir": "/usr",
                  "connect_timeout": "15",
                  "datadir": "/var/lib/mysql",
                  "default_storage_engine": "innodb",
                  "innodb_buffer_pool_size": "600M",
                  "innodb_data_file_path": "ibdata1:10M:autoextend",
                  "innodb_file_per_table": "1",
                  "innodb_log_buffer_size": "25M",
                  "innodb_log_file_size": "50M",
                  "innodb_log_files_in_group": "2",
                  "join_buffer_size": "1M",
                  "key_buffer_size": "200M",
                  "local-infile": "0",
                  "max_allowed_packet": "4096K",
                  "max_connections": "400",
                  "max_heap_table_size": "64M",
                  "max_user_connections": "400",
                  "myisam-recover": "BACKUP",
                  "open_files_limit": "2048",
                  "pid_file": "/var/run/mysqld/mysqld.pid",
                  "port": "3306",
                  "query_cache_limit": "1M",
                  "query_cache_size": "32M",
                  "query_cache_type": "1",
                  "read_buffer_size": "512K",
                  "read_rnd_buffer_size": "512K",
                  "server_id": "334596",
                  "skip-external-locking": "1",
                  "sort_buffer_size": "1M",
                  "table_definition_cache": "1024",
                  "table_open_cache": "1024",
                  "thread_cache_size": "16",
                  "thread_stack": "192K",
                  "tmp_table_size": "64M",
                  "tmpdir": "/var/tmp",
                  "user": "mysql",
                  "wait_timeout": "120"
              }
      }
      }

Abnormal Response
-----------------

For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.
