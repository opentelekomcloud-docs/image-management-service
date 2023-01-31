:original_name: en-us_topic_0170918588.html

.. _en-us_topic_0170918588:

Querying an API Version (Native OpenStack API)
==============================================

Function
--------

This API is used to query a specified API version, such as version compatibility and domain name information of an API.

URI
---

GET /{api_version}

:ref:`Table 1 <en-us_topic_0170918588__table6209770492526>` lists the parameters in the URI.

.. _en-us_topic_0170918588__table6209770492526:

.. table:: **Table 1** Parameter description

   +-------------+-----------+--------+----------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                  |
   +=============+===========+========+==============================================+
   | api_version | Yes       | String | Specifies the API version, for example v2.0. |
   +-------------+-----------+--------+----------------------------------------------+

Request
-------

-  Request parameters

   None

-  Example request

   .. code-block:: text

      GET https://{Endpoint}/v2.0

Response
--------

-  Response parameters

   +-----------------------+-----------------------+------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                  |
   +=======================+=======================+==============================================================================+
   | versions              | Array of objects      | Specifies the version.                                                       |
   |                       |                       |                                                                              |
   |                       |                       | For details, see :ref:`Table 2 <en-us_topic_0170918588__table854484962011>`. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------+

   .. _en-us_topic_0170918588__table854484962011:

   .. table:: **Table 2** Data structure description of the versions field

      +-----------------------+-----------------------+-------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                   |
      +=======================+=======================+===============================================================================+
      | status                | String                | Specifies the API status.                                                     |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------+
      | id                    | String                | Specifies the API ID.                                                         |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------+
      | links                 | Array of objects      | Specifies the description.                                                    |
      |                       |                       |                                                                               |
      |                       |                       | For details, see :ref:`Table 3 <en-us_topic_0170918588__table9477147162314>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------+

   .. _en-us_topic_0170918588__table9477147162314:

   .. table:: **Table 3** Data structure description of the versions.links field

      ========= ====== ======================================
      Parameter Type   Description
      ========= ====== ======================================
      href      String Specifies the domain name.
      rel       String Specifies the domain name description.
      ========= ====== ======================================

-  Example response

   .. code-block:: text

      STATUS CODE 300

   ::

      {
          "versions": [
              {
                  "status": "SUPPORTED",
                  "id": "v2.0",
                  "links": [
                      {
                          "href": "https://image.az1.dc1.domainname.com/v2/",
                          "rel": "self"
                      }
                  ]
              }
          ]
      }

Returned Values
---------------

-  Normal

   300

-  Abnormal

   +---------------------------+------------------------------------------------------+
   | Returned Values           | Description                                          |
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
