:original_name: rds_05_0016.html

.. _rds_05_0016:

Configuring the Maintenance Window
==================================

Function
--------

This API is used to change the maintenance window as required. To prevent service interruption, the maintenance window should fall within the off-peak hours.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   PUT https://{*Endpoint*}/v3/{*project_id*}/instances/{*instance_id*}/ops-window

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the DB instance ID.                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                   |
      +=================+=================+=================+===============================================================================================+
      | start_time      | Yes             | String          | Specifies the start time.                                                                     |
      |                 |                 |                 |                                                                                               |
      |                 |                 |                 | The value must be a valid value in the "HH:MM" format. The current time is in the UTC format. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+
      | end_time        | Yes             | String          | Specifies the end time.                                                                       |
      |                 |                 |                 |                                                                                               |
      |                 |                 |                 | The value must be a valid value in the "HH:MM" format. The current time is in the UTC format. |
      |                 |                 |                 |                                                                                               |
      |                 |                 |                 | .. note::                                                                                     |
      |                 |                 |                 |                                                                                               |
      |                 |                 |                 |    The interval between the start time and end time must be four hours.                       |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+

-  Example

   PUT https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/dsfae23fsfdsae3435in01/ops-window

-  Request example

   .. code-block:: text

      {
           "start_time": "22:00",
           "end_time":"02:00"
      }

Response
--------

-  Example normal response

   .. code-block:: text

      {}

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
