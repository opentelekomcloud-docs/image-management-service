:original_name: en-us_topic_0036994323.html

.. _en-us_topic_0036994323:

Updating the Image Sharing Status of a Recipient
================================================

Function
--------

This is an extended API used to accept or reject images shared with other users.

This is an asynchronous API. If **job_id** is returned, the job is successfully delivered. You need to query the status of the asynchronous job. If the status is **success**, the job is successfully executed. If the status is **failed**, the job fails. For details about how to query an asynchronous job, see :ref:`Querying the Progress of an Asynchronous Job <en-us_topic_0000001263414852>`.

URI
---

PUT /v1/cloudimages/members

Request
-------

Request parameters

+-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                            |
+=================+=================+==================+========================================================================================================================================================================================================+
| images          | Yes             | Array of strings | **Definition**                                                                                                                                                                                         |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | Image IDs.                                                                                                                                                                                             |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | **Constraints**                                                                                                                                                                                        |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | N/A                                                                                                                                                                                                    |
+-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| project_id      | Yes             | String           | **Definition**                                                                                                                                                                                         |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | Project ID.                                                                                                                                                                                            |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | **Constraints**                                                                                                                                                                                        |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | N/A                                                                                                                                                                                                    |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | **Range**                                                                                                                                                                                              |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | N/A                                                                                                                                                                                                    |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | **Default Value**                                                                                                                                                                                      |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | N/A                                                                                                                                                                                                    |
+-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| status          | Yes             | String           | **Definition**                                                                                                                                                                                         |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | Whether images shared with a recipient will be accepted or rejected.                                                                                                                                   |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | **Constraints**                                                                                                                                                                                        |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | N/A                                                                                                                                                                                                    |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | **Range**                                                                                                                                                                                              |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | -  **accepted**: indicates that the shared images will be accepted. After an image is accepted, the image is displayed in the image list. You can use the image to create ECSs.                        |
|                 |                 |                  | -  **rejected**: indicates that the shared images will be rejected. After you reject an image, the image will disappear from your image list, but you can still use the image to create cloud servers. |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | **Default Value**                                                                                                                                                                                      |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | N/A                                                                                                                                                                                                    |
+-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| vault_id        | No              | String           | **Definition**                                                                                                                                                                                         |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | Vault ID.                                                                                                                                                                                              |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | You can obtain a vault ID from the CBR console or by referring to "Querying the Vault List" in *Cloud Backup and Recovery API Reference*.                                                              |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | **Constraints**                                                                                                                                                                                        |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | This parameter is mandatory if you want to accept a shared full-ECS image created from a CBR backup.                                                                                                   |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | **Range**                                                                                                                                                                                              |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | N/A                                                                                                                                                                                                    |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | **Default Value**                                                                                                                                                                                      |
|                 |                 |                  |                                                                                                                                                                                                        |
|                 |                 |                  | N/A                                                                                                                                                                                                    |
+-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

-  Updating the image sharing status to **accepted** in a batch

   .. code-block:: text

      PUT https://{Endpoint}/v1/cloudimages/members
      {
         "images": [
                "d164b5df-1bc3-4c3f-893e-3e471fd16e64",
                "0b680482-acaa-4045-b14c-9a8c7dfe9c70"
            ],
            "project_id": "edc89b490d7d4392898e19b2deb34797",
            "status": "accepted"
      }

-  Updating the sharing status of images created from CBR backups to **accepted** in a batch (vault ID: d14r5tef-1bc3-4c4f-823e-3e471rg65e65)

   .. code-block:: text

      PUT https://{Endpoint}/v1/cloudimages/members
      {
         "images": [
                "d164b5df-1bc3-4c3f-893e-3e471fd16e64",
                "0b680482-acaa-4045-b14c-9a8c7dfe9c70"
            ],
            "project_id": "edc89b490d7d4392898e19b2deb34797",
            "status": "accepted",
            "vault_id": "d14r5tef-1bc3-4c4f-823e-3e471rg65e65"
      }

Response
--------

-  Response parameters

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                          |
   +=======================+=======================+======================================================================================================+
   | job_id                | String                | **Definition**                                                                                       |
   |                       |                       |                                                                                                      |
   |                       |                       | Asynchronous job ID.                                                                                 |
   |                       |                       |                                                                                                      |
   |                       |                       | For details, see :ref:`Querying the Progress of an Asynchronous Job <en-us_topic_0000001263414852>`. |
   |                       |                       |                                                                                                      |
   |                       |                       | **Range**                                                                                            |
   |                       |                       |                                                                                                      |
   |                       |                       | N/A                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block:: text

      STATUS CODE 200

   ::

      {
          "job_id": "edc89b490d7d4392898e19b2deb34797"
      }

Returned Values
---------------

-  Normal

   200

-  Abnormal

   +---------------------------+------------------------------------------------------------------------------+
   | Returned Value            | Description                                                                  |
   +===========================+==============================================================================+
   | 400 Bad Request           | Request error. For details, see :ref:`Error Codes <en-us_topic_0022473689>`. |
   +---------------------------+------------------------------------------------------------------------------+
   | 401 Unauthorized          | Authentication failed.                                                       |
   +---------------------------+------------------------------------------------------------------------------+
   | 403 Forbidden             | Insufficient permissions.                                                    |
   +---------------------------+------------------------------------------------------------------------------+
   | 404 Not Found             | Requested resource not found.                                                |
   +---------------------------+------------------------------------------------------------------------------+
   | 500 Internal Server Error | Internal service error.                                                      |
   +---------------------------+------------------------------------------------------------------------------+
   | 503 Service Unavailable   | Service unavailable.                                                         |
   +---------------------------+------------------------------------------------------------------------------+
