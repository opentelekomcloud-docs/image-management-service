:original_name: en-us_topic_0109822368.html

.. _en-us_topic_0109822368:

Deleting an Image
=================

Scenario
--------

A private image can be deleted if it is no longer needed.

.. note::

   The token obtained from IAM is valid for only 24 hours. If you want to use a token for authentication, you can cache it to avoid frequently calling the IAM API.

Involved APIs
-------------

If you use a token for authentication, you must obtain the token and add **X-Auth-Token** to the request header of the IMS API when making an API call.

-  IAM API used to obtain the token

   URI format: POST https://*IAM endpoint*/v3/auth/tokens

-  IMS API used to delete an image (Native OpenStack API)

   URI format: DELETE https://*IMS endpoint*/v2/images/*Image ID*

Procedure
---------

#. Obtain the token.

#. Send **DELETE https://**\ *IMS endpoint*\ **/v2/images/**\ *Image ID*.

#. Add **X-Auth-Token** to the request header.

#. Check the status code. If the request is successful, **204** is returned.

   For details about status codes for request exceptions, see :ref:`Status Codes <en-us_topic_0124290300>`.
