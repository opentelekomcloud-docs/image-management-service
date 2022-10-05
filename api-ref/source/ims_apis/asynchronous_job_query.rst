:original_name: en-us_topic_0000001361199224.html

.. _en-us_topic_0000001361199224:

Asynchronous Job Query
======================

Function
--------

This API is an extension one. It is used to query the execution status of an asynchronous job, for example, an image exporting job.

URI
---

GET /v1/{project_id}/jobs/{job_id}

:ref:`Table 1 <en-us_topic_0000001361199224__table4357530317543>` lists the parameters in the URI.

.. _en-us_topic_0000001361199224__table4357530317543:

.. table:: **Table 1** Parameter description

   ========== ========= ==================================
   Parameter  Mandatory Description
   ========== ========= ==================================
   project_id Yes       Specifies the project ID.
   job_id     Yes       Specifies the asynchronous job ID.
   ========== ========= ==================================

Request
-------

-  Request parameters

   None

-  Example request

   .. code-block:: text

      GET /v1/ac234de25c6741d2b1273da49eea1b9e/jobs/ff8080814dbd65d7014dbe0d84db0013

Response
--------

-  Response parameters

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                        |
   +=======================+=======================+====================================================================================================================================+
   | status                | String                | Specifies the job status. The value can be:                                                                                        |
   |                       |                       |                                                                                                                                    |
   |                       |                       | -  **SUCCESS**: The job is successfully executed.                                                                                  |
   |                       |                       | -  **FAIL**: The job failed to be executed.                                                                                        |
   |                       |                       | -  **RUNNING**: The job is in progress.                                                                                            |
   |                       |                       | -  **INIT**: The job is being initialized.                                                                                         |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | job_id                | String                | Specifies the task ID.                                                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | job_type              | String                | Specifies the job type.                                                                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | begin_time            | String                | Specifies the start time of the job. The value is in UTC format.                                                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | end_time              | String                | Specifies the end time of the job. The value is in UTC format.                                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Specifies the error code.                                                                                                          |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | fail_reason           | String                | Specifies the cause of the failure.                                                                                                |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | entities              | Object                | Specifies the custom attributes of the job.                                                                                        |
   |                       |                       |                                                                                                                                    |
   |                       |                       | If the job status is normal, the image ID will be returned. If the status is abnormal, an error code and details will be returned. |
   |                       |                       |                                                                                                                                    |
   |                       |                       | For details, see :ref:`Table 2 <en-us_topic_0000001361199224__table791935535712>`.                                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0000001361199224__table791935535712:

   .. table:: **Table 2** Data structure description of the entities field

      ========= ====== =======================
      Parameter Type   Description
      ========= ====== =======================
      image_id  String Specifies the image ID.
      ========= ====== =======================

-  Example response

   .. code-block:: text

      STATUS CODE 200

   ::

      {
          "status": "SUCCESS",
          "entities": {
              "image_id": "e9e91bff-14b6-4a0b-8377-4ed0813e3360"
          },
          "job_id": "ff8080814dbd65d7014dbe0d84db0013",
          "job_type": "createImageByInstance",
          "begin_time": "04-Jun-2015 18:11:06:586",
          "end_time": "",
          "error_code": null,
          "fail_reason": null
      }

Returned Values
---------------

-  Normal

   200

-  Abnormal

   +---------------------------+------------------------------------------------------+
   | Returned Value            | Description                                          |
   +===========================+======================================================+
   | 400 Bad Request           | Request error.                                       |
   +---------------------------+------------------------------------------------------+
   | 401 Unauthorized          | Authentication failed.                               |
   +---------------------------+------------------------------------------------------+
   | 403 Forbidden             | You do not have the rights to perform the operation. |
   +---------------------------+------------------------------------------------------+
   | 500 Internal Server Error | Internal service error.                              |
   +---------------------------+------------------------------------------------------+
   | 503 Service Unavailable   | The service is unavailable.                          |
   +---------------------------+------------------------------------------------------+
