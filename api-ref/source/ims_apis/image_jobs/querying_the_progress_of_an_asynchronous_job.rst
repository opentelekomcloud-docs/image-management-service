:original_name: en-us_topic_0000001263414852.html

.. _en-us_topic_0000001263414852:

Querying the Progress of an Asynchronous Job
============================================

Function
--------

This is an extension API. It is used to query the progress of an asynchronous job.

URI
---

GET /v1/cloudimages/job/{job_id}

:ref:`Table 1 <en-us_topic_0000001263414852__table4357530317543>` lists the parameters in the URI.

.. _en-us_topic_0000001263414852__table4357530317543:

.. table:: **Table 1** Parameter description

   ========= ========= ====================
   Parameter Mandatory Description
   ========= ========= ====================
   job_id    Yes       Asynchronous job ID.
   ========= ========= ====================

Request
-------

-  Request parameters

   None

Example Request
---------------

Querying the progress of an asynchronous job

.. code-block:: text

   GET /v1/cloudimages/job/ff8080814dbd65d7014dbe0d84db0013

Response
--------

-  Response parameters

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                        |
   +=======================+=======================+====================================================================================================================================+
   | job_id                | String                | Job ID.                                                                                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | job_type              | String                | Job type.                                                                                                                          |
   |                       |                       |                                                                                                                                    |
   |                       |                       | -  **imsCreateImageByInstance**: Creating a system disk image from a cloud server                                                  |
   |                       |                       | -  **imsImportImageJob**: Creating a system disk image from an external image file                                                 |
   |                       |                       | -  **imsImportOvaImageJob**: Creating an image from an OVA image file                                                              |
   |                       |                       | -  **imsVolumeCreateImageJob**: Creating a system disk image from a data disk                                                      |
   |                       |                       | -  **imsVolumesToSysDataImagesJob**: Creating a data disk image from a data disk                                                   |
   |                       |                       | -  **imsImportDataImageJob**: Creating a data disk image from an external image file                                               |
   |                       |                       | -  **imsCreateWholeImageByInstanceJob**: Creating a full-ECS image from an ECS                                                     |
   |                       |                       | -  **imsCreateWholeImageByBackupJob**: Creating a full-ECS image from a CBR or CSBS backup                                         |
   |                       |                       | -  **imsNativeImportImageJob**: Registering an image                                                                               |
   |                       |                       | -  **imsNativeExportImageJob**: Exporting an image                                                                                 |
   |                       |                       | -  **imsAddImageMembersJob**: Adding image recipients                                                                              |
   |                       |                       | -  **imsDelImageMembersJob**: Deleting image recipients                                                                            |
   |                       |                       | -  **imsUpdateImageMembersJob**: Updating the image sharing status of a recipient                                                  |
   |                       |                       | -  **imsCopyImageInRegionJob**: Replicating images                                                                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | begin_time            | String                | Start time of a job. The value is in UTC format.                                                                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | end_time              | String                | End time of a job. The value is in UTC format.                                                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                | Job status. The value can be:                                                                                                      |
   |                       |                       |                                                                                                                                    |
   |                       |                       | -  **SUCCESS**: The job is successfully executed.                                                                                  |
   |                       |                       | -  **FAIL**: The job failed to be executed.                                                                                        |
   |                       |                       | -  **RUNNING**: The job is in progress.                                                                                            |
   |                       |                       | -  **INIT**: The job is being initialized.                                                                                         |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code.                                                                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | fail_reason           | String                | Failure cause.                                                                                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | entities              | Object                | Custom job attributes.                                                                                                             |
   |                       |                       |                                                                                                                                    |
   |                       |                       | If the job status is normal, the image ID will be returned. If the status is abnormal, an error code and details will be returned. |
   |                       |                       |                                                                                                                                    |
   |                       |                       | For details, see :ref:`Table 2 <en-us_topic_0000001263414852__table791935535712>`.                                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0000001263414852__table791935535712:

   .. table:: **Table 2** Data structure description of the entities field

      +-----------------+-------------------------------+----------------------------------------------------------------------------------------------------------------+
      | Parameter       | Type                          | Description                                                                                                    |
      +=================+===============================+================================================================================================================+
      | image_name      | String                        | Image name.                                                                                                    |
      +-----------------+-------------------------------+----------------------------------------------------------------------------------------------------------------+
      | process_percent | Double                        | Job progress.                                                                                                  |
      +-----------------+-------------------------------+----------------------------------------------------------------------------------------------------------------+
      | current_task    | String                        | Job name.                                                                                                      |
      +-----------------+-------------------------------+----------------------------------------------------------------------------------------------------------------+
      | subJobId        | String                        | Sub-job ID.                                                                                                    |
      +-----------------+-------------------------------+----------------------------------------------------------------------------------------------------------------+
      | image_id        | String                        | Image ID.                                                                                                      |
      +-----------------+-------------------------------+----------------------------------------------------------------------------------------------------------------+
      | sub_jobs_result | Array of SubJobResult objects | Sub-job execution results. For details, see :ref:`Table 3 <en-us_topic_0000001263414852__table1966074735019>`. |
      +-----------------+-------------------------------+----------------------------------------------------------------------------------------------------------------+
      | sub_jobs_list   | Array of string               | Sub-job IDs.                                                                                                   |
      +-----------------+-------------------------------+----------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0000001263414852__table1966074735019:

   .. table:: **Table 3** Data structure description of the SubJobResult field

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                   |
      +=======================+=======================+===============================================================================================================+
      | status                | String                | Sub-job status. The value can be:                                                                             |
      |                       |                       |                                                                                                               |
      |                       |                       | -  **SUCCESS**: The sub-job is successfully executed.                                                         |
      |                       |                       | -  **FAIL**: The sub-job failed to be executed.                                                               |
      |                       |                       | -  **RUNNING**: The sub-job is in progress.                                                                   |
      |                       |                       | -  **INIT**: The sub-job is being initialized.                                                                |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+
      | job_id                | String                | Sub-job ID.                                                                                                   |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+
      | job_type              | String                | Sub-job type.                                                                                                 |
      |                       |                       |                                                                                                               |
      |                       |                       | The value can be:                                                                                             |
      |                       |                       |                                                                                                               |
      |                       |                       | **imsGoofysImportImageJob**: Importing an image                                                               |
      |                       |                       |                                                                                                               |
      |                       |                       | **imsGoofysImportImageWithoutconfigJob**: Importing an image                                                  |
      |                       |                       |                                                                                                               |
      |                       |                       | **imsGoofysUploadImageJob**: Importing an image                                                               |
      |                       |                       |                                                                                                               |
      |                       |                       | **imsGoofysExportImageJob**: Exporting an image                                                               |
      |                       |                       |                                                                                                               |
      |                       |                       | **imsImportBigFileImageJob**: Importing an image                                                              |
      |                       |                       |                                                                                                               |
      |                       |                       | **imsQuickExportImageJob**: Fast export of an image                                                           |
      |                       |                       |                                                                                                               |
      |                       |                       | **imsImportIsoFileImageJob**: Creating an ISO image                                                           |
      |                       |                       |                                                                                                               |
      |                       |                       | **imsImportDataImageJob**: Creating a data disk image                                                         |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+
      | begin_time            | String                | Start time of a sub-job. The value is in UTC format.                                                          |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+
      | end_time              | String                | End time of a sub-job. The value is in UTC format.                                                            |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+
      | error_code            | String                | Error code.                                                                                                   |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+
      | fail_reason           | String                | Failure cause.                                                                                                |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+
      | entities              | Object                | Custom sub-job attributes. For details, see :ref:`Table 4 <en-us_topic_0000001263414852__table294510331539>`. |
      |                       |                       |                                                                                                               |
      |                       |                       | -  If a sub-job is properly executed, an image ID is returned.                                                |
      |                       |                       | -  If an exception occurs on the sub-job, an error code and associated information are returned.              |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0000001263414852__table294510331539:

   .. table:: **Table 4** Data structure description of the sub_jobs_result.entities field

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                             |
      +=======================+=======================+=========================================================================================+
      | image_id              | String                | Specifies the image ID.                                                                 |
      |                       |                       |                                                                                         |
      |                       |                       | This parameter is returned only when the value of **job_type** is one of the following: |
      |                       |                       |                                                                                         |
      |                       |                       | -  imsImportOvaImageJob                                                                 |
      |                       |                       | -  imsVolumesToSysDataImagesJob                                                         |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | image_name            | String                | Specifies the image name.                                                               |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+

Example Response
----------------

-  If the **job_type** is **imsCreateImageByInstance**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac79d2a54ad019d2d11f02349b4",
          "job_type": "imsCreateImageByInstance",
          "begin_time": "2026-03-27T02:14:03.552Z",
          "end_time": "2026-03-27T02:17:11.351Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "image_name": "name",
              "image_id": "eacac5cb-1153-4b8c-873c-73e036f5a988",
              "process_percent": 1,
              "current_task": ""
          }
      }

-  If the **job_type** is **imsImportImageJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac89d2a5e14019d2cde77f03a0f",
          "job_type": "imsImportImageJob",
          "begin_time": "2026-03-27T01:17:50.446Z",
          "end_time": "2026-03-27T01:57:11.143Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "image_name": "name",
              "subJobId": "0825e1f7fae2477b9db78d7ea34a1a10",
              "image_id": "698a61e2-abde-4151-a778-f9035e214c92",
              "process_percent": 1,
              "current_task": ""
          }
      }

-  If the **job_type** is **imsImportOvaImageJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac79d2a54ad019d4c35cf71260b",
          "job_type": "imsImportOvaImageJob",
          "begin_time": "2026-04-02T03:21:28.174Z",
          "end_time": "2026-04-02T03:59:13.786Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "sub_jobs_result": [
                  {
                      "job_id": "9a175ac79d2a54ad019d4c37b9772673",
                      "job_type": "imsImportImageJob",
                      "begin_time": "2026-04-02T03:23:33.620Z",
                      "end_time": "2026-04-02T03:58:55.831Z",
                      "status": "SUCCESS",
                      "error_code": null,
                      "fail_reason": null,
                      "entities": {
                          "image_name": "name",
                          "image_id": "6d0c5c0e-5505-4ba8-ab65-7e78efe77130"
                      }
                  },
                  {
                      "job_id": "9a175ac79d2a54ad019d4c37b9862674",
                      "job_type": "imsImportDataImageJob",
                      "begin_time": "2026-04-02T03:23:33.635Z",
                      "end_time": "2026-04-02T03:25:45.953Z",
                      "status": "SUCCESS",
                      "error_code": null,
                      "fail_reason": null,
                      "entities": {
                          "image_name": "name",
                          "image_id": "3e0c2b6c-e56f-435a-bcb5-e6a45cccdd75"
                      }
                  }
              ]
          }
      }

-  If the **job_type** is **imsVolumeCreateImageJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac79d2a54ad019d3c757c246c47",
          "job_type": "imsVolumeCreateImageJob",
          "begin_time": "2026-03-30T01:57:05.698Z",
          "end_time": "2026-03-30T02:01:45.927Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "image_name": "name",
              "image_id": "67891716-2e40-4cff-924e-e609017294fc",
              "process_percent": 1,
              "current_task": ""
          }
      }

-  If the **job_type** is **imsVolumesToSysDataImagesJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac69d2a5466019d4c2294462ed9",
          "job_type": "imsVolumesToSysDataImagesJob",
          "begin_time": "2026-04-02T03:00:27.845Z",
          "end_time": "2026-04-02T03:03:30.540Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "sub_jobs_result": [
                  {
                      "job_id": "9a175ac69d2a5466019d4c2299782edd",
                      "job_type": "imsCopyVolumeToImageJob",
                      "begin_time": "2026-04-02T03:00:29.173Z",
                      "end_time": "2026-04-02T03:03:05.904Z",
                      "status": "SUCCESS",
                      "error_code": null,
                      "fail_reason": null,
                      "entities": {
                          "image_id": "51a2a39b-622e-411f-a1a3-9745393baf3d",
                          "image_name": "name"
                      }
                  }
              ]
          }
      }

-  If the **job_type** is **imsImportDataImageJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac69d2a5466019d4c2fcc6a32cb",
          "job_type": "imsImportDataImageJob",
          "begin_time": "2026-04-02T03:14:54.184Z",
          "end_time": "2026-04-02T03:17:07.450Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "image_name": "name",
              "subJobId": "98ac8511d1274186afc1f50df6ed6ecd",
              "image_id": "b4609d4a-dcdc-4a54-bb33-8b9778bb9656",
              "process_percent": 1,
              "current_task": ""
          }
      }

-  If the **job_type** is **imsCreateWholeImageByInstanceJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac79d2a54ad019d2ece15ca4808",
          "job_type": "imsCreateWholeImageByInstanceJob",
          "begin_time": "2026-03-27T10:19:11.176Z",
          "end_time": "2026-03-28T10:19:23.952Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "image_name": "name",
              "image_id": "698a61e2-abde-4151-a778-f9035e214c92",
              "process_percent": 1,
              "current_task": ""
          }
      }

-  If the **job_type** is **imsCreateWholeImageByBackupJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac89d2a5e14019d3c71ee087693",
          "job_type": "imsCreateWholeImageByBackupJob",
          "begin_time": "2026-03-27T01:17:50.446Z",
          "end_time": "2026-03-27T01:57:11.143Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "image_name": "name",
              "image_id": "698a61e2-abde-4151-a778-f9035e214c92",
              "process_percent": 1,
              "current_task": ""
          }
      }

-  If the **job_type** is **imsNativeImportImageJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac89d2a5e14019d3c76e7cc774c",
          "job_type": "imsNativeImportImageJob",
          "begin_time": "2026-03-27T01:17:50.446Z",
          "end_time": "2026-03-27T01:57:11.143Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "image_name": "name",
              "image_id": "698a61e2-abde-4151-a778-f9035e214c92",
              "process_percent": 1,
              "current_task": ""
          }
      }

-  If the **job_type** is **imsNativeExportImageJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac79d2a54ad019d2d0a1f074696",
          "job_type": "imsNativeExportImageJob",
          "begin_time": "2026-03-27T01:17:50.446Z",
          "end_time": "2026-03-27T01:57:11.143Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "image_name": "name",
              "image_id": "698a61e2-abde-4151-a778-f9035e214c92",
              "process_percent": 1,
              "current_task": ""
          }
      }

-  If the **job_type** is **imsAddImageMembersJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac79d84d201019d85a1aaa33350",
          "job_type": "imsAddImageMembersJob",
          "begin_time": "2026-04-13T06:57:37.953Z",
          "end_time": "2026-04-13T06:57:40.252Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "process_percent": 1,
              "current_task": ""
          }
      }

-  If the **job_type** is **imsDelImageMembersJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac89d84d1fe019d85a549ea35c5",
          "job_type": "imsDelImageMembersJob",
          "begin_time": "2026-04-13T07:01:35.336Z",
          "end_time": "2026-04-13T07:01:36.277Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "process_percent": 1,
              "current_task": ""
          }
      }

-  If the **job_type** is **imsUpdateImageMembersJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac79d89b857019d89da380f07f3",
          "job_type": "imsUpdateImageMembersJob",
          "begin_time": "2026-04-14T02:37:53.036Z",
          "end_time": "2026-04-14T02:37:53.645Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "process_percent": 1,
              "current_task": ""
          }
      }

-  If the **job_type** is **imsCopyImageInRegionJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac79d2a54ad019d2eb4a0e640a4",
          "job_type": "imsCopyImageInRegionJob",
          "begin_time": "2026-03-27T01:17:50.446Z",
          "end_time": "2026-03-27T01:57:11.143Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "image_name": "name",
              "image_id": "698a61e2-abde-4151-a778-f9035e214c92",
              "process_percent": 1,
              "current_task": ""
          }
      }

-  If the **job_type** is **imsCrossRegionCopyImageJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac79d2a54ad019d47145b8f78cd",
          "job_type": "imsCrossRegionCopyImageJob",
          "begin_time": "2026-03-27T01:17:50.446Z",
          "end_time": "2026-03-27T01:57:11.143Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "image_name": "name",
              "image_id": "698a61e2-abde-4151-a778-f9035e214c92",
              "process_percent": 1,
              "current_task": ""
          }
      }

Returned Values
---------------

-  Normal

   200

-  Abnormal

   ========================= =========================
   Returned Value            Description
   ========================= =========================
   400 Bad Request           Request error.
   401 Unauthorized          Authentication failed.
   403 Forbidden             Insufficient permissions.
   500 Internal Server Error Internal service error.
   503 Service Unavailable   Service unavailable.
   ========================= =========================
