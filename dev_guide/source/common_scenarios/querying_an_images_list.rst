:original_name: en-us_topic_0109822403.html

.. _en-us_topic_0109822403:

Querying an Images List
=======================

Scenario
--------

Images can be created using search criteria.

.. note::

   -  You can type question marks (?) and ampersands (&) at the end of the URI to define multiple search criteria. For details, see the example request.
   -  The token obtained from Identity and Access Management (IAM) is valid for only 24 hours. If you want to use a token for authentication, you can cache it to avoid frequently calling the IAM API.

Involved APIs
-------------

If you use a token for authentication, you must obtain the token and add **X-Auth-Token** to the request header of the IMS API when making an API call.

-  IAM API used to obtain the token

   URI format: POST https://*IAM endpoint*/v3/auth/tokens

-  IMS API used to query the image list

   URI format: GET https://*IMS endpoint*/v2/cloudimages

Procedure
---------

#. Obtain the token.

#. Send **GET https://**\ *IMS endpoint*\ **/v2/cloudimages**.

#. Add **X-Auth-Token** to the request header.

#. Type question marks (?) and ampersands (&) at the end of the URI to define multiple search criteria, for example, https://*IMS endpoint*/v2/cloudimages?__imagetype=gold&sort_key=name&limit=1.

#. Refer to "Querying Images" in the **Image Management Service API Reference** for parameter descriptions and response details.

   For details about status codes for request exceptions, see :ref:`Status Codes <en-us_topic_0124290300>`.

Common Query Methods
--------------------

-  Public images

   GET /v2/images?__imagetype=gold&visibility=public&protected=true

-  Private images

   GET /v2/images?owner={project_id}

-  Available shared images

   GET /v2/images?member_status=accepted&visibility=shared&__imagetype=shared

-  Rejected images

   GET /v2/images?member_status=rejected&visibility=shared&__imagetype=shared

-  Unaccepted images

   GET /v2/images?member_status=pending&visibility=shared&__imagetype=shared
