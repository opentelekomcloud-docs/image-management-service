:original_name: en-us_topic_0036994318.html

.. _en-us_topic_0036994318:

Updating the Image Sharing Status of a Recipient (Native OpenStack API)
=======================================================================

Function
--------

This is an extended API. It is used to batch accept or reject images shared with a user.

URI
---

PUT /v2/images/{image_id}/members/{member_id}

:ref:`Table 1 <en-us_topic_0036994318__table37590215162351>` lists the parameters in the URI.

.. _en-us_topic_0036994318__table37590215162351:

.. table:: **Table 1** Parameter description

   ========= ========= ====== =============
   Parameter Mandatory Type   Description
   ========= ========= ====== =============
   image_id  Yes       String Image ID.
   member_id Yes       String Recipient ID.
   ========= ========= ====== =============

Request
-------

Request parameters

+-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                        |
+=================+=================+=================+====================================================================================================================================================================================================+
| status          | Yes             | String          | Whether images shared with a recipient will be accepted or rejected.                                                                                                                               |
|                 |                 |                 |                                                                                                                                                                                                    |
|                 |                 |                 | Available values include:                                                                                                                                                                          |
|                 |                 |                 |                                                                                                                                                                                                    |
|                 |                 |                 | -  **accepted**: indicates that the shared images will be accepted. After an image is accepted, the image is displayed in the image list. You can use the image to create ECSs.                    |
|                 |                 |                 | -  **rejected**: indicates that the shared images will be rejected. After an image is rejected, the image is not displayed in the image list. However, you can still use the image to create ECSs. |
+-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| vault_id        | No              | String          | Vault ID.                                                                                                                                                                                          |
|                 |                 |                 |                                                                                                                                                                                                    |
|                 |                 |                 | This parameter is mandatory if you want to accept a shared full-ECS image created from a CBR backup.                                                                                               |
|                 |                 |                 |                                                                                                                                                                                                    |
|                 |                 |                 | You can obtain the vault ID from the CBR console or section "Querying the Vault List" in *Cloud Backup and Recovery API Reference*.                                                                |
+-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

-  Updating the image sharing status to **accepted**

   .. code-block:: text

      PUT https://{Endpoint}/v2/images/d164b5df-1bc3-4c3f-893e-3e471fd16e64/members/edc89b490d7d4392898e19b2deb34797
      {
          "status": "accepted"
      }

-  Updating the sharing status of an image created from a CBR backup to **accepted** (vault ID: 6yhtb5df-1bc3-4c3f-893e-3e4716yhgt61)

   .. code-block:: text

      PUT https://{Endpoint}/v2/images/d164b5df-1bc3-4c3f-893e-3e471fd16e64/members/edc89b490d7d4392898e19b2deb34797
      {
          "status": "accepted",
          "vault_id": "6yhtb5df-1bc3-4c3f-893e-3e4716yhgt61"
      }

Response
--------

-  Response parameters

   +------------+--------+-----------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                           |
   +============+========+=======================================================================+
   | status     | String | Image sharing status.                                                 |
   +------------+--------+-----------------------------------------------------------------------+
   | created_at | String | Time when the sharing was performed. The value is in UTC format.      |
   +------------+--------+-----------------------------------------------------------------------+
   | updated_at | String | Time when the sharing status was updated. The value is in UTC format. |
   +------------+--------+-----------------------------------------------------------------------+
   | image_id   | String | Image ID.                                                             |
   +------------+--------+-----------------------------------------------------------------------+
   | member_id  | String | Recipient ID.                                                         |
   +------------+--------+-----------------------------------------------------------------------+
   | schema     | String | Sharing schema.                                                       |
   +------------+--------+-----------------------------------------------------------------------+

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
