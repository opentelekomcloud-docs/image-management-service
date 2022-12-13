:original_name: en-us_topic_0109822369.html

.. _en-us_topic_0109822369:

Exporting an Image
==================

Scenario
--------

If you need to use a private image in a storage device or on other platforms, you can export the image.

All available private images can be exported to an OBS bucket in a specific format. After you have exported an image, you can download it from the OBS bucket to the specified storage device.

Images exported in different formats may vary in size. You will be charged for the space used to store these images.

.. note::

   -  The storage class of the OBS bucket must be **Standard**.
   -  The token obtained from Identity and Access Management (IAM) is valid for only 24 hours. If you want to use a token for authentication, you can cache it to avoid frequently calling the IAM API.

Involved APIs
-------------

If you use a token for authentication, you must obtain the token and add **X-Auth-Token** to the request header of the IMS API when making an API call.

-  IAM API used to obtain the token

   URI format: POST https://*IAM endpoint*/v3/auth/tokens

-  IMS API used to export an image

   URI format: POST https://*IMS endpoint*/v1/cloudimages/*Image ID*/file

Procedure
---------

#. Obtain the token.

#. Send **POST https://**\ *IMS endpoint*\ **/v1/cloudimages/**\ *Image ID*\ **/file**.

#. Add **X-Auth-Token** to the request header.

#. Specify the following parameters in the request body:

   .. code-block::

      {
         "bucket_url":"ims-image:centos7_5.qcow2",  //URL of the target file in the format of <Bucket name>:<File name> (mandatory, string)
         "file_format":"qcow2"  //File format, which can be qcow2, vhd, zvhd, or vmdk (mandatory, string)
      }

   If the request is successful, a job ID is returned.

#. Query job details using the job ID by referring to :ref:`Querying Job Details <en-us_topic_0109822371>`.

   If the job status is **SUCCESS**, the private image is successfully created.

   For details about status codes for request errors, see :ref:`Status Codes <en-us_topic_0124290300>`.
