:original_name: en-us_topic_0036994318.html

.. _en-us_topic_0036994318:

Updating the Image Sharing Status in Batches (Native OpenStack API)
===================================================================

Function
--------

This API is used to update the image sharing status when a tenant accepts or rejects a shared image.

URI
---

PUT /v2/images/{image_id}/members/{member_id}

:ref:`Table 1 <en-us_topic_0036994318__table37590215162351>` lists the parameters in the URI.

.. _en-us_topic_0036994318__table37590215162351:

.. table:: **Table 1** Parameter description

   ========= ========= ====== ========================
   Parameter Mandatory Type   Description
   ========= ========= ====== ========================
   image_id  Yes       String Specifies the image ID.
   member_id Yes       String Specifies the member ID.
   ========= ========= ====== ========================

Request
-------

-  Request parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================================================================+
   | status          | Yes             | String          | Specifies whether a shared image will be accepted or declined.                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                            |
   |                 |                 |                 | Available values include:                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                            |
   |                 |                 |                 | -  **accepted**: indicates that a shared image is accepted. After an image is accepted, the image is displayed in the image list. You can use the image to create ECSs.                    |
   |                 |                 |                 | -  **rejected**: indicates that a shared image is declined. After an image is rejected, the image is not displayed in the image list. However, you can still use the image to create ECSs. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vault_id        | No              | String          | Specifies the ID of a vault.                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                            |
   |                 |                 |                 | This parameter is mandatory if you want to accept a shared full-ECS image created from a CBR backup.                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                            |
   |                 |                 |                 | You can obtain the vault ID from the CBR console or section "Querying the Vault List" in *Cloud Backup and Recovery API Reference*.                                                        |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   -  If the image is not a full-ECS image:

      .. code-block:: text

         PUT https://{Endpoint}/v2/images/d164b5df-1bc3-4c3f-893e-3e471fd16e64/members/edc89b490d7d4392898e19b2deb34797

      ::

         {
             "status": "accepted"
         }

   -  If the image is a full-ECS image:

      .. code-block:: text

         PUT https://{Endpoint}/v2/images/d164b5df-1bc3-4c3f-893e-3e471fd16e64/members/edc89b490d7d4392898e19b2deb34797

      ::

         {
             "status": "accepted",
             "vault_id": "6yhtb5df-1bc3-4c3f-893e-3e4716yhgt61"
         }

Response
--------

-  Response parameters

   +------------+--------+---------------------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                                     |
   +============+========+=================================================================================+
   | status     | String | Specifies the image sharing status.                                             |
   +------------+--------+---------------------------------------------------------------------------------+
   | created_at | String | Specifies the time when a shared image was created. The value is in UTC format. |
   +------------+--------+---------------------------------------------------------------------------------+
   | updated_at | String | Specifies the time when a shared image was updated. The value is in UTC format. |
   +------------+--------+---------------------------------------------------------------------------------+
   | image_id   | String | Specifies the image ID.                                                         |
   +------------+--------+---------------------------------------------------------------------------------+
   | member_id  | String | Specifies the member ID.                                                        |
   +------------+--------+---------------------------------------------------------------------------------+
   | schema     | String | Specifies the sharing schema.                                                   |
   +------------+--------+---------------------------------------------------------------------------------+

-  Example response

   .. code-block:: text

      STATUS CODE 200

   ::

      {
          "status": "accepted",
          "created_at": "2016-09-01T02:05:14Z",
          "updated_at": "2016-09-01T02:37:11Z",
          "image_id": "d164b5df-1bc3-4c3f-893e-3e471fd16e64",
          "member_id": "edc89b490d7d4392898e19b2deb34797",
          "schema": "/v2/schemas/member"
      }

Returned Values
---------------

-  Normal

   200

-  Abnormal

   +---------------------------+------------------------------------------------------+
   | Returned Value            | Description                                          |
   +===========================+======================================================+
   | 400 Bad Request           | Request error.                                       |
   +---------------------------+------------------------------------------------------+
   | 401 Unauthorized          | Authentication failed.                               |
   +---------------------------+------------------------------------------------------+
   | 403 Forbidden             | You do not have the rights to perform the operation. |
   +---------------------------+------------------------------------------------------+
   | 404 Not Found             | The requested resource was not found.                |
   +---------------------------+------------------------------------------------------+
   | 500 Internal Server Error | Internal service error.                              |
   +---------------------------+------------------------------------------------------+
   | 503 Service Unavailable   | The service is unavailable.                          |
   +---------------------------+------------------------------------------------------+
