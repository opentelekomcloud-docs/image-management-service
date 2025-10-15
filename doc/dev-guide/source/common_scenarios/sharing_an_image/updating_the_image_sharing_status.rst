:original_name: en-us_topic_0110300593.html

.. _en-us_topic_0110300593:

Updating the Image Sharing Status
=================================

Scenario
--------

The status of a shared image can be updated after the tenant accepts or rejects the image.

.. note::

   The token obtained from IAM is valid for only 24 hours. If you want to use a token for authentication, you can cache it to avoid frequently calling the IAM API.

Involved APIs
-------------

If you use a token for authentication, you must obtain the token and add **X-Auth-Token** to the request header of the IMS API when making an API call.

-  IAM API used to obtain the token

   URI format: POST https://*IAM endpoint*/v3/auth/tokens

-  IMS API used to update the image sharing status (Native OpenStack API)

   URI format: PUT https://*IMS endpoint*/v2/images/*Image ID*/members/*Member ID*

Procedure
---------

#. Obtain the token.

#. Send **PUT https://**\ *IMS endpoint*\ **/v2/images/**\ *Image ID*\ **/members/**\ *Member ID*. *Member ID* indicates the project ID of the image recipient.

#. Add **X-Auth-Token** to the request header.

#. Specify the following parameters in the request body:

   .. code-block::

      {
          "status": "accepted"  //Value: accepted or rejected
      }

#. Check the response parameters.

   .. code-block::

      {
          "status": "accepted",  //Sharing status (value: accepted or rejected)
          "created_at": "2016-09-01T02:05:14Z",  //Time when the image is shared
          "updated_at": "2016-09-01T02:37:11Z",  //Time when the image status is updated
          "image_id": "d164b5df-1bc3-4c3f-893e-3e471fd16e64",  //Image ID
          "member_id": "edc89b490d7d4392898e19b2deb34797"  //Member ID (that is, project ID of the image recipient)
          "schema": "/v2/schemas/member"  //Image sharing schema
      }

   For details about status codes for request errors, see :ref:`Status Codes <en-us_topic_0124290300>`.
