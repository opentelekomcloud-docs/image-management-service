:original_name: en-us_topic_0102682864.html

.. _en-us_topic_0102682864:

Deleting an Image Tag
=====================

Function
--------

This API is used to delete a specified tag from an image.

Constraints
-----------

-  To be compatible with remaining tags, the system will not verify the character set and length of the keys and values in the query condition.
-  This API is a non-idempotent one. If the key to be deleted does not exist, status code 404 is returned.

URI
---

DELETE /v2/{project_id}/images/{image_id}/tags/{key}

:ref:`Table 1 <en-us_topic_0102682864__table33665774183714>` lists the parameters in the URI.

.. _en-us_topic_0102682864__table33665774183714:

.. table:: **Table 1** Parameter description

   ========== ========= ====== ===========================================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========================================
   project_id Yes       String Specifies the project ID.
   image_id   Yes       String Specifies the image ID.
   key        Yes       String Specifies the key of the tag to be deleted.
   ========== ========= ====== ===========================================

Request
-------

-  Request parameters

   None

-  Example request

   .. code-block:: text

      DELETE https://{Endpoint}/v2/fd73a4a14a4a4dfb9771a8475e5198ea/images/67e17426-359e-49fb-aa12-0bd1756ec240/tags/key1

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
