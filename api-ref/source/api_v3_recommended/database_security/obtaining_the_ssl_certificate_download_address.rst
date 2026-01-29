:original_name: rds_05_0021.html

.. _rds_05_0021:

Obtaining the SSL Certificate Download Address
==============================================

Function
--------

This API is used to obtain the address for downloading the SSL certificate of a DB instance.

-  Before calling an API, you need to understand the API in :ref:`Authentication <rds_03_0001>`.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{*project_id*}/instances/{instance_id}/ssl-cert/download-link

-  Parameter description

   .. table:: **Table 1** URL Parameters

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

-  Parameter parameters

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

      GET https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/c90928717dc747e2a20099894a87c468in01/ssl-cert/download-link

Response
--------

-  Normal response

   .. table:: **Table 3** Response body parameters

      +----------------+-------+------------------------------------------------------------------------------------------------------------------+
      | Parameter      | Type  | Description                                                                                                      |
      +================+=======+==================================================================================================================+
      | cert_info_list | Array | Certificate list. For details, see :ref:`Table 4 <rds_05_0021__en-us_topic_0000001474025574_table155872321234>`. |
      +----------------+-------+------------------------------------------------------------------------------------------------------------------+

   .. _rds_05_0021__en-us_topic_0000001474025574_table155872321234:

   .. table:: **Table 4** cert_info_list field data structure description

      +-----------------------+-----------------------+--------------------------------------+
      | Parameter             | Type                  | Description                          |
      +=======================+=======================+======================================+
      | download_link         | String                | Download link.                       |
      +-----------------------+-----------------------+--------------------------------------+
      | category              | String                | Certificate type. Enumerated values: |
      |                       |                       |                                      |
      |                       |                       | -  **international**                 |
      |                       |                       | -  **national**                      |
      +-----------------------+-----------------------+--------------------------------------+

-  Example normal response

   .. code-block::

      {
        "cert_info_list": [
          {
            "category": "international",
            "download_link": "****.com/rds/Certificate_Download.zip"
          }
        ]
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
