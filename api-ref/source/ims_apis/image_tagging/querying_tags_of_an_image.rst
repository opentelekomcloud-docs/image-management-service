:original_name: en-us_topic_0102682865.html

.. _en-us_topic_0102682865:

Querying Tags of an Image
=========================

Function
--------

This API is used to query all the tags of a specified image.

URI
---

GET /v2/{project_id}/images/{image_id}/tags

:ref:`Table 1 <en-us_topic_0102682865__table16231211183747>` lists the parameters in the URI.

.. _en-us_topic_0102682865__table16231211183747:

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

   None

-  Example request

   .. code-block:: text

      GET https://{Endpoint}/v2/fd73a4a14a4a4dfb9771a8475e5198ea/images/67e17426-359e-49fb-aa12-0bd1756ec240/tags

Response
--------

-  Response parameters

   +-----------+------------------+---------------------------------------------------------------------------------------------------------+
   | Parameter | Type             | Description                                                                                             |
   +===========+==================+=========================================================================================================+
   | tags      | Array of objects | Lists the returned tags. For details, see :ref:`Table 2 <en-us_topic_0102682865__table47961066183747>`. |
   +-----------+------------------+---------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0102682865__table47961066183747:

   .. table:: **Table 2** Data structure description of the tags field

      ========= ====== ========================
      Parameter Type   Description
      ========= ====== ========================
      key       String Specifies the tag key.
      value     String Specifies the tag value.
      ========= ====== ========================

-  Example response

   .. code-block:: text

      STATUS CODE 200

   ::

      {
         "tags": [{
            "value": "value0",
            "key": "key0"
         },
         {
            "value": "value0",
            "key": "key1"
         }]
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
