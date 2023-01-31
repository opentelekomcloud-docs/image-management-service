:original_name: en-us_topic_0102682863.html

.. _en-us_topic_0102682863:

Adding an Image Tag
===================

Function
--------

This API is used to add a tag to an image or update a tag.

Constraints
-----------

-  Each tag consists of a key and a value. The key contains at most 36 characters, and the value contains at most 43 characters. The key cannot be left blank or an empty character string. The value cannot be left blank but can be an empty character string.
-  An image can have a maximum of 10 tags.
-  This API is an idempotent API. If a tag to be added has the same key as an existing tag, but the tag values are different, this tag will be added and overwrite the existing one. If a tag to be added has the same key and value as an existing tag, this tag will not be added.

URI
---

POST /v2/{project_id}/images/{image_id}/tags

:ref:`Table 1 <en-us_topic_0102682863__table51217005183640>` lists the parameters in the URI.

.. _en-us_topic_0102682863__table51217005183640:

.. table:: **Table 1** Parameter description

   ========== ========= ====== =========================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =========================
   project_id Yes       String Specifies the project ID.
   image_id   Yes       String Specifies the image ID.
   ========== ========= ====== =========================

Request
-------

-  Request parameters

   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                              |
   +===========+===========+========+==========================================================================================================================+
   | tag       | Yes       | Object | Specifies the tag to be added or updated. For details, see :ref:`Table 2 <en-us_topic_0102682863__table65193697183640>`. |
   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0102682863__table65193697183640:

   .. table:: **Table 2** Data structure description of the tag field

      +-----------+-----------+--------+----------------------------------------------------------+
      | Parameter | Mandatory | Type   | Description                                              |
      +===========+===========+========+==========================================================+
      | key       | Yes       | String | Specifies the tag key. The tag key cannot be left blank. |
      +-----------+-----------+--------+----------------------------------------------------------+
      | value     | Yes       | String | Specifies the tag value.                                 |
      +-----------+-----------+--------+----------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{Endpoint}/v2/fd73a4a14a4a4dfb9771a8475e5198ea/images/67e17426-359e-49fb-aa12-0bd1756ec240/tags

   ::

      {
         "tag": {
            "value": "value1",
            "key": "key1"
         }
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
