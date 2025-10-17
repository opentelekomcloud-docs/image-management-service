:original_name: en-us_topic_0109822404.html

.. _en-us_topic_0109822404:

Queries Details About an Image
==============================

Scenario
--------

Details about a private or public image can be queried.

.. note::

   The token obtained from IAM is valid for only 24 hours. If you want to use a token for authentication, you can cache it to avoid frequently calling the IAM API.

Involved APIs
-------------

If you use a token for authentication, you must obtain the token and add **X-Auth-Token** to the request header of the IMS API when making an API call.

-  IAM API used to obtain the token

   URI format: POST https://*IAM endpoint*/v3/auth/tokens

-  IMS API used to query image details (Native OpenStack API)

   URI format: GET https://*IMS endpoint*/v2/images/*Image ID*

Procedure
---------

#. Obtain the token.

#. Send **GET https://**\ *IMS endpoint*\ **/v2/images/**\ *Image ID*.

#. Add **X-Auth-Token** to the request header.

   An example request is as follows: https://*IMS endpoint*/v2/images/33ad552d-1149-471c-8190-ff6776174a00.

#. Refer to "Querying Image Details (Native OpenStack API)" in *Image Management Service API Reference* for parameter descriptions and response details.

   For details about status codes for request errors, see :ref:`Status Codes <en-us_topic_0124290300>`.
