:original_name: rds_09_0304.html

.. _rds_09_0304:

Applying a Parameter Template
=============================

Function
--------

This API is used to apply a parameter template to one or more DB instances.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   PUT https://{*Endpoint*}/v3/{*project_id*}/configurations/{config_id}/apply

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                |
      |                       |                       |                                                                                                  |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <rds_03_0002>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | config_id             | Yes                   | Specifies the parameter template ID.                                                             |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +--------------+-----------+------------------+-------------------------------------------+
      | Name         | Mandatory | Type             | Description                               |
      +==============+===========+==================+===========================================+
      | instance_ids | Yes       | Array of strings | Specifies the DB instance ID list object. |
      +--------------+-----------+------------------+-------------------------------------------+

-  Example

   PUT https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/configurations/463b4b58-d0e8-4e2b-9560-5dea4552fde9/apply

-  Request example

.. code-block:: text

   {
       "instance_ids": ["73ea2bf70c73497f89ee0ad4ee008aa2in01", "fe5f5a07539c431181fc78220713aebein01"]
   }

Response
--------

-  Normal response

   .. table:: **Table 3** Parameter description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                        |
      +=======================+=======================+====================================================================================+
      | configuration_id      | String                | Specifies the parameter template ID.                                               |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------+
      | configuration_name    | String                | Specifies the parameter template name.                                             |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------+
      | apply_results         | Array of objects      | Specifies the result of applying the parameter template.                           |
      |                       |                       |                                                                                    |
      |                       |                       | For details, see :ref:`Table 4 <rds_09_0304__table19602151563612>`.                |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------+
      | success               | Boolean               | Specifies whether each parameter template is applied to DB instances successfully. |
      |                       |                       |                                                                                    |
      |                       |                       | -  **true**: Each parameter template is applied to DB instances successfully.      |
      |                       |                       | -  **false**: One or more parameter templates failed to be applied.                |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------+
      | job_id                | String                | Job ID.                                                                            |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------+

   .. _rds_09_0304__table19602151563612:

   .. table:: **Table 4** apply_results field data structure description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                        |
      +=======================+=======================+====================================================================================+
      | instance_id           | String                | Indicates the DB instance ID.                                                      |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------+
      | instance_name         | String                | Indicates the DB instance name.                                                    |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------+
      | restart_required      | Boolean               | Indicates whether a reboot is required.                                            |
      |                       |                       |                                                                                    |
      |                       |                       | -  **true**: A reboot is required.                                                 |
      |                       |                       | -  **false**: A reboot is not required.                                            |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------+
      | success               | Boolean               | Indicates whether each parameter template is applied to DB instances successfully. |
      |                       |                       |                                                                                    |
      |                       |                       | -  **true**: The application is successful.                                        |
      |                       |                       | -  **false**: The application failed.                                              |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------+

-  Example normal response

   .. code-block:: text

      {
          "configuration_id": "cf49bbd7d2384878bc3808733c9e9d8bpr01",
          "configuration_name": "paramsGroup-bcf9",
          "apply_results": [{
              "instance_id": "fe5f5a07539c431181fc78220713aebein01",
              "instance_name": "zyy1",
              "restart_required": false,
              "success": false
          }, {
              "instance_id": "73ea2bf70c73497f89ee0ad4ee008aa2in01",
              "instance_name": "zyy2",
              "restart_required": false,
              "success": false
          }],
          "success": false,
              "job_id":"3b5ddc07-a230-46e5-bBc9-6e76526cbb3e"
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
