:original_name: en-us_topic_0000001360879684.html

.. _en-us_topic_0000001360879684:

Deleting an Image (Native OpenStack API)
========================================

Function
--------

This API is used to delete a private image. You can only delete your own private images.

URI
---

DELETE /v2/images/{image_id}

:ref:`Table 1 <en-us_topic_0000001360879684__table27262282>` lists the parameters in the URI.

.. _en-us_topic_0000001360879684__table27262282:

.. table:: **Table 1** Parameter description

   ========= ========= ====== =======================
   Parameter Mandatory Type   Description
   ========= ========= ====== =======================
   image_id  Yes       String Specifies the image ID.
   ========= ========= ====== =======================

Request
-------

-  Request parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================+
   | delete_backup   | No              | Boolean         | Specifies whether to delete the CSBS backups associated with a full-ECS image when the image is deleted. The value can be **true** or **false**. |
   |                 |                 |                 |                                                                                                                                                  |
   |                 |                 |                 | -  **true**: When a full-ECS image is deleted, its CSBS backups are also deleted.                                                                |
   |                 |                 |                 | -  **false**: When a full-ECS image is deleted, its CSBS backups are not deleted.                                                                |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      DELETE https://{Endpoint}/v2/images/4ca46bf1-5c61-48ff-b4f3-0ad4e5e3ba90

   ::

      {
          "delete_backup": true
      }

Response
--------

-  Response parameters

   None

-  Example response

   .. code-block:: text

      STATUS CODE 204

Returned Values
---------------

-  Normal

   204

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
