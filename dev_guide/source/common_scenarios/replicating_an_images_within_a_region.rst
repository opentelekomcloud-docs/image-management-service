:original_name: en-us_topic_0109822370.html

.. _en-us_topic_0109822370:

Replicating an Images Within a Region
=====================================

Scenario
--------

A private image can be copied within a region as another one. The API used is an extension API. When replicating an image, you can change the image attributes to meet the requirements of different scenarios.

.. note::

   The token obtained from IAM is valid for only 24 hours. If you want to use a token for authentication, you can cache it to avoid frequently calling the IAM API.

Involved APIs
-------------

If you use a token for authentication, you must obtain the token and add **X-Auth-Token** to the request header of the IMS API when making an API call.

-  IAM API used to obtain the token

   URI format: POST https://*IAM endpoint*/v3/auth/tokens

-  IMS API used to copy an image within a region

   URI format: POST https://*IMS endpoint*/v1/cloudimages/*Image ID*/copy

Procedure
---------

#. Obtain the token.

#. Send **POST https://**\ *IMS endpoint*/v1/cloudimages/*Image ID*\ **/copy**.

#. Add **X-Auth-Token** to the request header.

#. Specify the following parameters in the request body:

   .. code-block::

      {
          "name": "ims_encrypted_copy3",  //Image name (mandatory, string)
          "description": "test copy",  //Image description (optional, string)
          "cmk_id": "bd66288c-9081-460a-8227-4cbd0c814cb4"  //Encryption key (optional, string)
      }

   If the request is successful, a job ID is returned.

#. Query job details using the job ID by referring to :ref:`Querying Job Details <en-us_topic_0109822371>`.

   If the job status is **SUCCESS**, the image is successfully replicated.

   For details about status codes for request exceptions, see :ref:`Status Codes <en-us_topic_0124290300>`.
