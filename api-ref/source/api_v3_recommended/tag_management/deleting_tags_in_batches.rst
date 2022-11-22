:original_name: rds_06_0038.html

.. _rds_06_0038:

Deleting Tags in Batches
========================

Function
--------

This API is used to delete tags in batches.

-  Learn how to :ref:`authorize and authenticate <rds_03_0001>` this API before using it.
-  Before calling this API, obtain the required `region and endpoint <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

URI
---

-  URI format

   POST https://{*Endpoint*}/v3/{project_id}/instances/{instance_id}/tags/action

-  Example

   https://rds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/cee5265e1e5845649e354841234567dfin01/tags/action

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

      +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type             | Description                                                                                             |
      +=================+=================+==================+=========================================================================================================+
      | action          | Yes             | String           | Specifies the operation identifier (case sensitive), which is **delete** during the deletion operation. |
      +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------+
      | tags            | Yes             | Array of objects | Specifies the tag list.                                                                                 |
      |                 |                 |                  |                                                                                                         |
      |                 |                 |                  | For details, see :ref:`Table 3 <rds_06_0038__table9331195513220>`.                                      |
      +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------+

   .. _rds_06_0038__table9331195513220:

   .. table:: **Table 3** tags field data structure description

      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                  |
      +=================+=================+=================+==============================================================================+
      | key             | Yes             | String          | Specifies the tag key, which contains a maximum of 127 Unicode characters.   |
      |                 |                 |                 |                                                                              |
      |                 |                 |                 | The key cannot be left blank or an empty string.                             |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------+
      | value           | No              | String          | Specifies the tag value, which contains a maximum of 255 Unicode characters. |
      |                 |                 |                 |                                                                              |
      |                 |                 |                 | Deletion remarks:                                                            |
      |                 |                 |                 |                                                                              |
      |                 |                 |                 | -  If **value** is not empty, delete tags by **key**/**value**.              |
      |                 |                 |                 | -  If **value** is empty, delete tags by **key**.                            |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      {
          "action": "delete",
          "tags": [{
              "key": "key1"
          }, {
              "key": "key2",
              "value": "value2"
          }]
      }

Response
--------

-  Normal Response

   None

-  Abnormal Response

   For details, see :ref:`Abnormal Request Results <en-us_topic_0032488197>`.

Status Code
-----------

For details, see :ref:`Status Codes <en-us_topic_0032488240>`.

Error Code
----------

For details, see :ref:`Error Codes <en-us_topic_0032488241>`.
