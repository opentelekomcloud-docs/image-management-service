:original_name: en-us_topic_0036994317.html

.. _en-us_topic_0036994317:

Adding an Image Sharing Member (Native OpenStack API)
=====================================================

Function
--------

This API is used to add a project ID of a tenant the image is to be shared with.

Constraints
-----------

For an encrypted image, you need to authorize the key used by the image before using this API. For details, see "How Do I Authorize a Key?" in *Image Management Service User Guide*.

URI
---

POST /v2/images/{image_id}/members

Request
-------

-  Request parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                  |
   +=================+=================+=================+==============================================================+
   | member          | Yes             | String          | Specifies a tenant who will be able to use the shared image. |
   |                 |                 |                 |                                                              |
   |                 |                 |                 | The value is the project ID of the tenant.                   |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------+

Example Request
---------------

Adding a tenant who can use the shared image (project ID: edc89b490d7d4392898e19b2deb34797)

.. code-block:: text

   POST https://{Endpoint}/v2/images/d164b5df-1bc3-4c3f-893e-3e471fd16e64/members
   {
       "member":"edc89b490d7d4392898e19b2deb34797"
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
   | member_id  | String | Specifies the project ID of the tenant who is to accept the shared image.       |
   +------------+--------+---------------------------------------------------------------------------------+
   | schema     | String | Specifies the sharing schema.                                                   |
   +------------+--------+---------------------------------------------------------------------------------+

-  Example response

   .. code-block:: text

      STATUS CODE 200

   ::

      {
          "status": "pending",
          "created_at": "2016-09-01T02:05:14Z",
          "updated_at": "2016-09-01T02:05:14Z",
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
