:original_name: en-us_topic_0102682866.html

.. _en-us_topic_0102682866:

Querying All Image Tags
=======================

Function
--------

This API is used to query all the image tags.

URI
---

GET /v2/{project_id}/images/tags

:ref:`Table 1 <en-us_topic_0102682866__table49437288183829>` lists the parameters in the URI.

.. _en-us_topic_0102682866__table49437288183829:

.. table:: **Table 1** Parameter description

   ========== ========= ====== =========================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =========================
   project_id Yes       String Specifies the project ID.
   ========== ========= ====== =========================

Request
-------

-  Request parameters

   None

-  Example request

   .. code-block:: text

      GET https://{Endpoint}/v2/fd73a4a14a4a4dfb9771a8475e5198ea/images/tags

Response
--------

-  Response parameters

   +-----------+------------------+--------------------------------------------------------------------------------------------+
   | Parameter | Type             | Description                                                                                |
   +===========+==================+============================================================================================+
   | tags      | Array of objects | Lists tags. For details, see :ref:`Table 2 <en-us_topic_0102682866__table24852149183829>`. |
   +-----------+------------------+--------------------------------------------------------------------------------------------+

   .. _en-us_topic_0102682866__table24852149183829:

   .. table:: **Table 2** Data structure description of the tags field

      +-----------+------------------+---------------------------------------------------------------------------------------------------+
      | Parameter | Type             | Description                                                                                       |
      +===========+==================+===================================================================================================+
      | key       | String           | Specifies the tag key.                                                                            |
      +-----------+------------------+---------------------------------------------------------------------------------------------------+
      | values    | Array of strings | Lists the tag values. If a tag contains the key only, tag values will be empty character strings. |
      +-----------+------------------+---------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block:: text

      STATUS CODE 200

   ::

      {
         "tags": [{
            "values": ["value9"],
            "key": "key9"
         },
         {
            "values": [""],
            "key": "key8"
         },
         {
            "values":
              ["valueXX",
              "value3"],
            "key": "key3"
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
   | 400 Bad Request           | Request error                                        |
   +---------------------------+------------------------------------------------------+
   | 401 Unauthorized          | Authentication failed.                               |
   +---------------------------+------------------------------------------------------+
   | 403 Forbidden             | You do not have the rights to perform the operation. |
   +---------------------------+------------------------------------------------------+
   | 404 Not Found             | The requested resource was not found.                |
   +---------------------------+------------------------------------------------------+
   | 500 Internal Server Error | Internal service error                               |
   +---------------------------+------------------------------------------------------+
   | 503 Service Unavailable   | The service is unavailable.                          |
   +---------------------------+------------------------------------------------------+
