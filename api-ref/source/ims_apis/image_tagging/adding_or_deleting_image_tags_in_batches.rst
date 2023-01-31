:original_name: en-us_topic_0102682862.html

.. _en-us_topic_0102682862:

Adding or Deleting Image Tags in Batches
========================================

Function
--------

This API is used to add tags to, update tags of, or delete tags from an image in batches.

Constraints
-----------

-  Each tag consists of a key and a value. The key contains at most 36 characters, and the value contains at most 43 characters. The key cannot be left blank or an empty character string. The value cannot be left blank but can be an empty character string.

-  An image can have a maximum of 10 tags.

-  The keys of multiple tags in the request body must be unique.

-  This API is an idempotent one.

   If a tag to be added has the same key as an existing tag, but the tag values are different, this tag will be added and overwrite the existing one. If a tag to be added has the same key and value as an existing tag, this tag will not be added.

   If the specified tag does not exist, the deletion is considered successful by default.

-  Restrictions on tag keys and values during batch deletion

   During the deletion, the system will not verify the character set range of the key and value. The key cannot be left blank or an empty character string. The value is optional and will not be not verified. If the tag to be deleted does not exist, the deletion is considered successful and no error is reported. Also, the system will not verify the length of both the key and value. The key can contain a maximum of 127 characters, and the value contains a maximum of 255 characters.

URI
---

POST /v2/{project_id}/images/{image_id}/tags/action

:ref:`Table 1 <en-us_topic_0102682862__table1543205183533>` lists the parameters in the URI.

.. _en-us_topic_0102682862__table1543205183533:

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

   +-----------+-----------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                                                                                                                                                                                                  |
   +===========+===========+==================+==============================================================================================================================================================================================================================+
   | tags      | Yes       | Array of objects | Lists the tags to be added or deleted. For details, see :ref:`Table 2 <en-us_topic_0102682862__table107083563918>`.                                                                                                          |
   +-----------+-----------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | action    | Yes       | String           | Specifies the tag operation to be performed. The value is case sensitive and can be **create** or **delete**. **create** indicates that tags will be added or updated, while **delete** indicates that tags will be deleted. |
   +-----------+-----------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0102682862__table107083563918:

   .. table:: **Table 2** Data structure description of the tags field

      +-----------+-----------+--------+----------------------------------------------------------+
      | Parameter | Mandatory | Type   | Description                                              |
      +===========+===========+========+==========================================================+
      | key       | Yes       | String | Specifies the tag key. The tag key cannot be left blank. |
      +-----------+-----------+--------+----------------------------------------------------------+
      | value     | Yes       | String | Specifies the tag value.                                 |
      +-----------+-----------+--------+----------------------------------------------------------+

-  Example request

   -  Adding image tags in batches

      .. code-block:: text

         POST https://{Endpoint}/v2/fd73a4a14a4a4dfb9771a8475e5198ea/images/67e17426-359e-49fb-aa12-0bd1756ec240/tags/action

      ::

         {
            "tags": [{
               "value": "value1",
               "key": "key1"
            },
            {
               "value": "value2",
               "key": "key2"
            },
            {
               "value": "",
               "key": "key3"
            }],
            "action": "create"
         }

   -  Deleting image tags in batches

      .. code-block:: text

         POST https://{Endpoint}/v2/fd73a4a14a4a4dfb9771a8475e5198ea/images/67e17426-359e-49fb-aa12-0bd1756ec240/tags/action

      ::

         {
            "tags": [{
               "value": "value1",
               "key": "key1"
            },
            {
               "value": "value2",
               "key": "key2"
            },
            {
               "value": "",
               "key": "key3"
            }],
               "action": "delete"
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
