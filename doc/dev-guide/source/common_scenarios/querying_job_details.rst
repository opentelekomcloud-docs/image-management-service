:original_name: en-us_topic_0109822371.html

.. _en-us_topic_0109822371:

Querying Job Details
====================

Scenario
--------

After a request is successfully received, a job id is returned. You can run the job to query the execution status. This part describes how to use a job ID to query job details.

.. note::

   The token obtained from IAM is valid for only 24 hours. If you want to use a token for authentication, you can cache it to avoid frequently calling the IAM API.

Involved APIs
-------------

If you use a token for authentication, you must obtain the token and add **X-Auth-Token** to the request header of the IMS API when making an API call.

-  IAM API used to obtain the token

   URI format: POST https://*IAM endpoint*/v3/auth/tokens

-  IMS API used to query an asynchronous job

   URI format: GET https://*IMS endpoint*/v1/*Project ID*/jobs/*Job ID*

Procedure
---------

#. Obtain the token.
#. Send **GET https://**\ *IMS endpoint*\ **/v1/**\ *Project ID*\ **/jobs/**\ *Job ID*.
#. Add **X-Auth-Token** to the request header.
#. Check the job details after the request is successfully processed. For details about the parameters, see "Asynchronous Job Query" in *Image Management Service API Reference*.
