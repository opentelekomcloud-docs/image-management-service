:original_name: en-us_topic_0109822381.html

.. _en-us_topic_0109822381:

Creating an Image Using an ECS
==============================

Scenario
--------

A Windows or Linux ECS can be used to create a private image.

.. note::

   -  Before creating the image, ensure that the ECS is stopped.
   -  The token obtained from Identity and Access Management (IAM) is valid for only 24 hours. If you want to use a token for authentication, you can cache it to avoid frequently calling the IAM API.

Involved APIs
-------------

If you use a token for authentication, you must obtain the token and add **X-Auth-Token** to the request header of the IMS API when making an API call.

-  IAM API used to obtain the token

   URI format: POST https://*IAM endpoint*/v3/auth/tokens

-  IMS API used to create an image

   URI format: POST https://*IMS endpoint*/v2/cloudimages/action

Procedure
---------

#. Obtain the token.

#. Send **POST https://**\ *IMS endpoint*\ **/v2/cloudimages/action**.

#. Add **X-Auth-Token** to the request header.

#. Specify the following parameters in the request body:

   .. code-block::

      {
          "name": "ims_test",  //Image name (mandatory, string)
          "description": "Image creation from an ECS",  //Image description (optional, string)
          "instance_id": "877a2cda-ba63-4e1e-b95f-e67e48b6129a",  //ECS ID (mandatory, string)
          "tags": [
                   "aaa.111",
                   "bbb.333",
                   "ccc.444"
               ]  //Image tag list (optional, array of objects)
      }

   -  If the request is successful, a job ID is returned.
   -  If the request fails, an error code and error details are returned. For details, see :ref:`Error Codes <en-us_topic_0110943799>`.

5. Query job details using the job ID by referring to :ref:`Querying Job Details <en-us_topic_0109822371>`.

   If the job status is **SUCCESS**, the private image is successfully created.

   For details about status codes for request exceptions, see :ref:`Status Codes <en-us_topic_0124290300>`.

6. Obtain the image ID from the job body and query, delete, and export the private image using the image ID.
