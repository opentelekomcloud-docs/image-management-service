:original_name: en-us_topic_0110300598.html

.. _en-us_topic_0110300598:

Updating the Image Sharing Status in Batches
============================================

Scenario
--------

The image sharing status can be updated in batches after a tenant accepts or rejects multiple shared images. The API used is an extension API.

.. note::

   The token obtained from IAM is valid for only 24 hours. If you want to use a token for authentication, you can cache it to avoid frequently calling the IAM API.

Involved APIs
-------------

If you use a token for authentication, you must obtain the token and add **X-Auth-Token** to the request header of the IMS API when making an API call.

-  IAM API used to obtain the token

   URI format: POST https://*IAM endpoint*/v3/auth/tokens

-  IMS API used to update the image sharing status in batches

   URI format: PUT https://*IMS endpoint*/v1/cloudimages/members

Procedure
---------

#. Obtain the token.

#. Send **PUT https://**\ *IMS endpoint*\ **/v1/cloudimages/members**.

#. Add **X-Auth-Token** to the request header.

#. Configure the request parameters. (The values are examples only.)

   .. code-block::

      {
          "images": [
              "d164b5df-1bc3-4c3f-893e-3e471fd16e64",
              "0b680482-acaa-4045-b14c-9a8c7dfe9c70"
            ],  //Image IDs (mandatory, list<string>)
            "project_id": "edc89b490d7d4392898e19b2deb34797",  //Project IDs (mandatory, string)
            "status": "accepted"  //Image sharing status: accepted indicates that shared images will be accepted. (mandatory, string)
      }

   If the request is successful, a job ID is returned.

#. Query job details using the job ID by referring to :ref:`Querying Job Details <en-us_topic_0109822371>`.

   If the job status is **SUCCESS**, the private image is successfully created.

   For details about status codes for request exceptions, see :ref:`Status Codes <en-us_topic_0124290300>`.
