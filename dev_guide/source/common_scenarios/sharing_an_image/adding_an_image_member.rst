:original_name: en-us_topic_0110300592.html

.. _en-us_topic_0110300592:

Adding an Image Member
======================

Scenario
--------

A private image can be shared with other tenants. When sharing an image, you need add a project ID of the tenant with whom you are going to share the image.

.. note::

   -  Currently, images can be shared only within the same region.
   -  The token obtained from Identity and Access Management (IAM) is valid for only 24 hours. If you want to use a token for authentication, you can cache it to avoid frequently calling the IAM API.

Involved APIs
-------------

If you use a token for authentication, you must obtain the token and add **X-Auth-Token** to the request header of the IMS API when making an API call.

-  IAM API used to obtain the token

   URI format: POST https://*IAM endpoint*/v3/auth/tokens

-  IMS API used to add an image member (Native OpenStack API)

   URI format: POST https://*IMS endpoint*/v2/images/*Image ID*/members

Procedure
---------

#. Obtain the token.

#. Send **POST https://**\ *IMS endpoint*\ **/v2/images/**\ *Image ID*\ **/members**.

#. Add **X-Auth-Token** to the request header.

#. Specify the following parameters in the request body:

   .. code-block::

      {
          "member": "edc89b490d7d4392898e19b2deb34797"  //Member ID (that is, project ID of the image recipient)
      }

#. Check the response parameters.

   .. code-block::

      {
          "status": "pending",  //Image is being shared
          "created_at": "2016-09-01T02:05:14Z",  //Time when the image is shared
          "updated_at": "2016-09-01T02:05:14Z", //Time when the image is updated
          "image_id": "d164b5df-1bc3-4c3f-893e-3e471fd16e64",  //Image ID
          "member_id": "edc89b490d7d4392898e19b2deb34797"  //Member ID (that is, project ID of the image recipient)
          "schema": "/v2/schemas/member"  //Image sharing schema
      }

   For details about status codes for request exceptions, see :ref:`Status Codes <en-us_topic_0124290300>`.
