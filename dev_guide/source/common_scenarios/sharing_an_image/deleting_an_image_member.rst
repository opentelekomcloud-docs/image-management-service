:original_name: en-us_topic_0110300596.html

.. _en-us_topic_0110300596:

Deleting an Image Member
========================

Scenario
--------

Image sharing can be stopped if you do not want to share your images any more.

.. note::

   The token obtained from IAM is valid for only 24 hours. If you want to use a token for authentication, you can cache it to avoid frequently calling the IAM API.

Involved APIs
-------------

If you use a token for authentication, you must obtain the token and add **X-Auth-Token** to the request header of the IMS API when making an API call.

-  IAM API used to obtain the token

   URI format: POST https://*IAM endpoint*/v3/auth/tokens

-  IMS API used to delete an image member (Native OpenStack API)

   URI format: DELETE https://*IMS endpoint*/v2/images/*Image ID*/members/*Member ID*

Procedure
---------

#. Obtain the token.

#. Send **DELETE https://**\ *IMS endpoint*\ **/v2/images/**\ *Image ID*\ **/members/**\ *Member ID*. *Member ID* indicates the project ID of the image recipient.

#. Add **X-Auth-Token** to the request header.

   If the request is successful, status code 204 is returned.

   For details about status codes for request exceptions, see :ref:`Status Codes <en-us_topic_0124290300>`.
