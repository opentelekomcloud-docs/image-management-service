:original_name: en-us_topic_0036994323.html

.. _en-us_topic_0036994323:

Updating the Status of Image Members in Batches
===============================================

Function
--------

This API is an extension one and used to update the image sharing status after the tenant accepts or rejects the shared images.

This API is an asynchronous one. If **job_id** is returned, the task is successfully delivered. You need to query the status of the asynchronous task. If the status is **success**, the task is successfully executed. If the status is **failed**, the task fails. For details about how to query the status of an asynchronous task, see :ref:`Asynchronous Job Query <en-us_topic_0022473688>`.

URI
---

PUT /v1/cloudimages/members

Request
-------

-  Request parameters

   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                |
   +=================+=================+==================+============================================================================================================================================================================================+
   | images          | Yes             | Array of strings | Specifies the image IDs.                                                                                                                                                                   |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id      | Yes             | String           | Specifies the project ID.                                                                                                                                                                  |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | Yes             | String           | Specifies whether a shared image will be accepted or declined.                                                                                                                             |
   |                 |                 |                  |                                                                                                                                                                                            |
   |                 |                 |                  | The value can be one of the following:                                                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                                            |
   |                 |                 |                  | -  **accepted**: indicates that a shared image is accepted. After an image is accepted, the image is displayed in the image list. You can use the image to create ECSs.                    |
   |                 |                 |                  | -  **rejected**: indicates that a shared image is declined. After an image is declined, the image is not displayed in the image list. However, you can still use the image to create ECSs. |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vault_id        | No              | String           | Specifies the ID of a vault.                                                                                                                                                               |
   |                 |                 |                  |                                                                                                                                                                                            |
   |                 |                 |                  | This parameter is mandatory if you want to accept a shared full-ECS image created from a CBR backup.                                                                                       |
   |                 |                 |                  |                                                                                                                                                                                            |
   |                 |                 |                  | You can obtain the vault ID from the CBR console or section "Querying the Vault List" in *Cloud Backup and Recovery API Reference*.                                                        |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   -  If the shared images do not include full-ECS images:

      .. code-block:: text

         PUT https://{Endpoint}/v1/cloudimages/members

      ::

         {
            "images": [
                   "d164b5df-1bc3-4c3f-893e-3e471fd16e64",
                   "0b680482-acaa-4045-b14c-9a8c7dfe9c70"
               ],
               "project_id": "edc89b490d7d4392898e19b2deb34797",
               "status": "accepted"
         }

   -  If the shared images include full-ECS images:

      .. code-block:: text

         PUT https://{Endpoint}/v1/cloudimages/members

      ::

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

   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                              |
   +=======================+=======================+==========================================================================+
   | job_id                | String                | Specifies the asynchronous job ID.                                       |
   |                       |                       |                                                                          |
   |                       |                       | For details, see :ref:`Asynchronous Job Query <en-us_topic_0022473688>`. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+

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
   | 403 Forbidden             | You do not have the rights to perform the operation.                         |
   +---------------------------+------------------------------------------------------------------------------+
   | 404 Not Found             | The requested resource was not found.                                        |
   +---------------------------+------------------------------------------------------------------------------+
   | 500 Internal Server Error | Internal service error.                                                      |
   +---------------------------+------------------------------------------------------------------------------+
   | 503 Service Unavailable   | The service is unavailable.                                                  |
   +---------------------------+------------------------------------------------------------------------------+
