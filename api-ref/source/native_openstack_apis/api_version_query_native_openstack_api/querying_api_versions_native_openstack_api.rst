:original_name: en-us_topic_0066978719.html

.. _en-us_topic_0066978719:

Querying API Versions (Native OpenStack API)
============================================

Function
--------

This API is used to query API versions, such as version compatibility and domain name information of APIs.

URI
---

GET /

Request
-------

-  Request parameters

   None

-  Example request

   .. code-block:: text

      GET https://{Endpoint}/

Response
--------

-  Response parameters

   +-----------------------+-----------------------+------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                  |
   +=======================+=======================+==============================================================================+
   | versions              | Array of objects      | Specifies the versions.                                                      |
   |                       |                       |                                                                              |
   |                       |                       | For details, see :ref:`Table 1 <en-us_topic_0066978719__table854484962011>`. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------+

   .. _en-us_topic_0066978719__table854484962011:

   .. table:: **Table 1** Data structure description of the versions field

      +-----------------------+-----------------------+-------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                   |
      +=======================+=======================+===============================================================================+
      | status                | String                | Specifies the API status.                                                     |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------+
      | id                    | String                | Specifies the API ID.                                                         |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------+
      | links                 | Array of objects      | Specifies the description.                                                    |
      |                       |                       |                                                                               |
      |                       |                       | For details, see :ref:`Table 2 <en-us_topic_0066978719__table9477147162314>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------+

   .. _en-us_topic_0066978719__table9477147162314:

   .. table:: **Table 2** Data structure description of the versions.links field

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
                  "status": "CURRENT",
                  "id": "v2.2",
                  "links": [
                      {
                          "href": "https://image.az1.dc1.domainname.com/v2/",
                          "rel": "self"
                      }
                  ]
              },
              {
                  "status": "SUPPORTED",
                  "id": "v2.1",
                  "links": [
                      {
                          "href": "https://image.az1.dc1.domainname.com/v2/",
                          "rel": "self"
                      }
                  ]
              },
              {
                  "status": "SUPPORTED",
                  "id": "v2.0",
                  "links": [
                      {
                          "href": "https://image.az1.dc1.domainname.com/v2/",
                          "rel": "self"
                      }
                  ]
              },
              {
                  "status": "DEPRECATED",
                  "id": "v1.1",
                  "links": [
                      {
                          "href": "https://image.az1.dc1.domainname.com/v1/",
                          "rel": "self"
                      }
                  ]
              },
              {
                  "status": "DEPRECATED",
                  "id": "v1.0",
                  "links": [
                      {
                          "href": "https://image.az1.dc1.domainname.com/v1/",
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
