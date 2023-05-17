:original_name: en-us_topic_0022473688.html

.. _en-us_topic_0022473688:

Asynchronous Job Query
======================

Function
--------

This is an extension API. It is used to query for the execution status of an asynchronous job, for example, querying for the execution status of an image exporting job.

URI
---

GET /v1/{project_id}/jobs/{job_id}

:ref:`Table 1 <en-us_topic_0022473688__table4357530317543>` lists the parameters in the URI.

.. _en-us_topic_0022473688__table4357530317543:

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
   | job_id                | String                | Specifies the job ID.                                                                                                              |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | job_type              | String                | Specifies the job type.                                                                                                            |
   |                       |                       |                                                                                                                                    |
   |                       |                       | -  **imsCreateImageByInstance**: Creating a system disk image from a cloud server                                                  |
   |                       |                       | -  **imsImportImageJob**: Creating a system disk image from an external image file                                                 |
   |                       |                       | -  **imsImportOvaImageJob**: Creating an image from an OVA image file                                                              |
   |                       |                       | -  **imsVolumeCreateImageJob**: Creating a data disk image from a cloud server                                                     |
   |                       |                       | -  **imsImportDataImageJob**: Creating a data disk image from an external image file                                               |
   |                       |                       | -  **imsCreateWholeImageByInstanceJob**: Creating a full-ECS image from an ECS                                                     |
   |                       |                       | -  **imsCreateWholeImageByBackupJob**: Creating a full-ECS image from a CBR or CSBS backup                                         |
   |                       |                       | -  **imsNativeImportImageJob**: Registering an image                                                                               |
   |                       |                       | -  **imsNativeExportImageJob**: Exporting image                                                                                    |
   |                       |                       | -  **imsAddImageMembersJob**: Adding tenants that can use a shared image                                                           |
   |                       |                       | -  **imsDelImageMembersJob**: Deleting tenants that can use a shared image                                                         |
   |                       |                       | -  **imsUpdateImageMembersJob**: Updating status of tenants who will accept or reject shared images                                |
   |                       |                       | -  **imsCopyImageInRegionJob**: Replicating images                                                                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | begin_time            | String                | Specifies the start time of the job. The value is in UTC format.                                                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | end_time              | String                | Specifies the end time of the job. The value is in UTC format.                                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Specifies the error code.                                                                                                          |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | fail_reason           | String                | Specifies the failure cause.                                                                                                       |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | entities              | Object                | Specifies the custom attributes of the job.                                                                                        |
   |                       |                       |                                                                                                                                    |
   |                       |                       | If the job status is normal, the image ID will be returned. If the status is abnormal, an error code and details will be returned. |
   |                       |                       |                                                                                                                                    |
   |                       |                       | For details, see :ref:`Table 2 <en-us_topic_0022473688__table791935535712>`.                                                       |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0022473688__table791935535712:

   .. table:: **Table 2** Data structure description of the entities field

      +-----------------+-------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Type                          | Description                                                                                                        |
      +=================+===============================+====================================================================================================================+
      | image_id        | String                        | Specifies the image ID.                                                                                            |
      +-----------------+-------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | current_task    | String                        | Specifies the job name.                                                                                            |
      +-----------------+-------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | image_name      | String                        | Specifies the image name.                                                                                          |
      +-----------------+-------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | process_percent | Double                        | Specifies the job progress.                                                                                        |
      +-----------------+-------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | results         | Array of result objects       | Specifies job execution results. For details, see :ref:`Table 3 <en-us_topic_0022473688__table12914173422713>`.    |
      +-----------------+-------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | sub_jobs_result | Array of SubJobResult objects | Specifies sub-job execution results. For details, see :ref:`Table 4 <en-us_topic_0022473688__table1966074735019>`. |
      +-----------------+-------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | sub_jobs_list   | Array of string               | Specifies the sub-job IDs.                                                                                         |
      +-----------------+-------------------------------+--------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0022473688__table12914173422713:

   .. table:: **Table 3** Data structure description of the result field

      ========== ====== =========================
      Parameter  Type   Description
      ========== ====== =========================
      image_id   String Specifies the image ID.
      project_id String Specifies the project ID.
      status     String Specifies the job status.
      ========== ====== =========================

   .. _en-us_topic_0022473688__table1966074735019:

   .. table:: **Table 4** Data structure description of the SubJobResult field

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                                  |
      +=======================+=======================+==============================================================================================================================+
      | status                | String                | Specifies the sub-job status. The value can be:                                                                              |
      |                       |                       |                                                                                                                              |
      |                       |                       | -  **SUCCESS**: The sub-job is successfully executed.                                                                        |
      |                       |                       | -  **FAIL**: The sub-job failed to be executed.                                                                              |
      |                       |                       | -  **RUNNING**: The sub-job is in progress.                                                                                  |
      |                       |                       | -  **INIT**: The sub-job is being initialized.                                                                               |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | job_id                | String                | Specifies a sub-job ID.                                                                                                      |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | job_type              | String                | Specifies the sub-job type.                                                                                                  |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | begin_time            | String                | Specifies the start time of the sub-job. The value is in UTC format.                                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | end_time              | String                | Specifies the end time of the sub-job. The value is in UTC format.                                                           |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | error_code            | String                | Specifies the error code.                                                                                                    |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | fail_reason           | String                | Specifies the failure cause.                                                                                                 |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | entities              | Object SubJobEntities | Specifies the custom attributes of the sub-job. For details, see :ref:`Table 5 <en-us_topic_0022473688__table294510331539>`. |
      |                       |                       |                                                                                                                              |
      |                       |                       | -  If a sub-job is properly executed, an image ID is returned.                                                               |
      |                       |                       | -  If an exception occurs on the sub-job, an error code and associated information are returned.                             |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0022473688__table294510331539:

   .. table:: **Table 5** Data structure description of the SubJobEntities field

      ========== ====== =========================
      Parameter  Type   Description
      ========== ====== =========================
      image_id   String Specifies the image ID.
      image_name String Specifies the image name.
      ========== ====== =========================

-  Example response

   .. code-block:: text

      STATUS CODE 200

   ::

      {
          "status": "SUCCESS",
          "entities": {
              "image_id": "e9e91bff-14b6-4a0b-8377-4ed0813e3360",
              "image_name": "asdfasdfasdfas",
              "process_percent": 0.20,
              "current_task": "CreateImageByInstanceTask",
              "results": [{
                      "image_id": "49e9447f-7dff-41e0-8036-f66fe5488c8b",
                      "project_id": "089b2f9a3d80d3062f24c00ca4ed5cbd",
                      "status": "success"
                  }
              ]
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
