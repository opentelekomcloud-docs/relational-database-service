:original_name: rds_09_0011.html

.. _rds_09_0011:

Querying the Restoration Time Range
===================================

Function
--------

This API is used to query the restoration time range of a DB instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/restore-time

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                        |
      +=======================+=======================+====================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                  |
      |                       |                       |                                                                                                    |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`.   |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the DB instance ID.                                                                      |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------+
      | date                  | No                    | Specifies the date to be queried. The value is in the yyyy-mm-dd format, and the time zone is UTC. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

-  Example

   GET https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/restore-time

Response
--------

-  Normal response

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+-------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                       |
      +=======================+=======================+===================================================================+
      | restore_time          | Array of objects      | Indicates the list of the restoration time range.                 |
      |                       |                       |                                                                   |
      |                       |                       | For details, see :ref:`Table 3 <rds_09_0011__table163715367507>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------+

   .. _rds_09_0011__table163715367507:

   .. table:: **Table 3** restore_time field data structure description

      +------------+---------+----------------------------------------------------------------------------------------------------------------------------------------+
      | Name       | Type    | Description                                                                                                                            |
      +============+=========+========================================================================================================================================+
      | start_time | Integer | Indicates the start time of the restoration time range in the UNIX timestamp format. The unit is millisecond and the time zone is UTC. |
      +------------+---------+----------------------------------------------------------------------------------------------------------------------------------------+
      | end_time   | Integer | Indicates the end time of the restoration time range in the UNIX timestamp format. The unit is millisecond and the time zone is UTC.   |
      +------------+---------+----------------------------------------------------------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "restore_time": [
              {
                  "start_time": 1532001446987,
                  "end_time": 1532742139000
              }
          ]
      }

-  Abnormal Response

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
