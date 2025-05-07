:original_name: en-us_topic_0022473688.html

.. _en-us_topic_0022473688:

Querying the Status of an Asynchronous Job
==========================================

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

Request parameters

None

Example Request
---------------

Querying the status of an asynchronous job

.. code-block:: text

   GET /v1/ac234de25c6741d2b1273da49eea1b9e/jobs/ff8080814dbd65d7014dbe0d84db0013

Response
--------

-  Response parameters

   .. note::

      The response parameters vary depending on the value of **job_type**. For details, see :ref:`Example Response <en-us_topic_0022473688__section1652181591718>`.

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
   |                       |                       | -  **imsVolumeCreateImageJob**: Creating a system disk image from a data disk                                                      |
   |                       |                       | -  **imsVolumesToSysDataImagesJob**: Creating a data disk image from a data disk                                                   |
   |                       |                       | -  **imsImportDataImageJob**: Creating a data disk image from an external image file                                               |
   |                       |                       | -  **imsCreateWholeImageByInstanceJob**: Creating a full-ECS image from an ECS                                                     |
   |                       |                       | -  **imsCreateWholeImageByBackupJob**: Creating a full-ECS image from a CBR or CSBS backup                                         |
   |                       |                       | -  **imsNativeImportImageJob**: Registering an image                                                                               |
   |                       |                       | -  **imsNativeExportImageJob**: Exporting an image                                                                                 |
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

      +-----------------------+-------------------------+--------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                    | Description                                                                                                        |
      +=======================+=========================+====================================================================================================================+
      | image_id              | String                  | Specifies the image ID.                                                                                            |
      |                       |                         |                                                                                                                    |
      |                       |                         | This parameter is returned only when the value of **job_type** is one of the following:                            |
      |                       |                         |                                                                                                                    |
      |                       |                         | -  imsCreateImageByInstance                                                                                        |
      |                       |                         | -  imsImportImageJob                                                                                               |
      |                       |                         | -  imsVolumeCreateImageJob                                                                                         |
      |                       |                         | -  imsImportDataImageJob                                                                                           |
      |                       |                         | -  imsCreateWholeImageByInstanceJob                                                                                |
      |                       |                         | -  imsCreateWholeImageByBackupJob                                                                                  |
      |                       |                         | -  imsNativeImportImageJob                                                                                         |
      |                       |                         | -  imsNativeExportImageJob                                                                                         |
      |                       |                         | -  imsCopyImageInRegionJob                                                                                         |
      +-----------------------+-------------------------+--------------------------------------------------------------------------------------------------------------------+
      | current_task          | String                  | Specifies the job name.                                                                                            |
      +-----------------------+-------------------------+--------------------------------------------------------------------------------------------------------------------+
      | image_name            | String                  | Specifies the image name.                                                                                          |
      +-----------------------+-------------------------+--------------------------------------------------------------------------------------------------------------------+
      | process_percent       | Double                  | Specifies the job progress.                                                                                        |
      +-----------------------+-------------------------+--------------------------------------------------------------------------------------------------------------------+
      | results               | Array of result objects | Specifies job execution results. For details, see :ref:`Table 3 <en-us_topic_0022473688__table12914173422713>`.    |
      +-----------------------+-------------------------+--------------------------------------------------------------------------------------------------------------------+
      | sub_jobs_result       | Array of objects        | Specifies sub-job execution results. For details, see :ref:`Table 4 <en-us_topic_0022473688__table1966074735019>`. |
      +-----------------------+-------------------------+--------------------------------------------------------------------------------------------------------------------+
      | sub_jobs_list         | Array of string         | Specifies the sub-job IDs.                                                                                         |
      +-----------------------+-------------------------+--------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0022473688__table12914173422713:

   .. table:: **Table 3** Data structure description of the results field

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                             |
      +=======================+=======================+=========================================================================================+
      | image_id              | String                | Specifies the image ID.                                                                 |
      |                       |                       |                                                                                         |
      |                       |                       | This parameter is returned only when the value of **job_type** is one of the following: |
      |                       |                       |                                                                                         |
      |                       |                       | -  imsAddImageMembersJob                                                                |
      |                       |                       | -  imsUpdateImageMembersJob                                                             |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | project_id            | String                | Specifies the project ID.                                                               |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | status                | String                | Specifies the job status.                                                               |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+

   .. _en-us_topic_0022473688__table1966074735019:

   .. table:: **Table 4** Data structure description of the sub_jobs_result field

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
      | entities              | Object                | Specifies the custom attributes of the sub-job. For details, see :ref:`Table 5 <en-us_topic_0022473688__table294510331539>`. |
      |                       |                       |                                                                                                                              |
      |                       |                       | -  If a sub-job is properly executed, an image ID is returned.                                                               |
      |                       |                       | -  If an exception occurs on the sub-job, an error code and associated information are returned.                             |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0022473688__table294510331539:

   .. table:: **Table 5** Data structure description of the sub_jobs_result.entities field

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

.. _en-us_topic_0022473688__section1652181591718:

Example Response
----------------

-  If the **job_type** is **imsCreateImageByInstance**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac792fa12d20193002100dd2762",
          "job_type": "imsCreateImageByInstance",
          "begin_time": "2024-11-06T06:19:43.195Z",
          "end_time": "2024-11-06T06:23:25.158Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "image_name": "test",
              "image_id": "3f7185de-b59a-4bb8-aa1d-7a513528b0e9"
          }
      }

-  If the **job_type** is **imsImportImageJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac892fa1342019300224f22218e",
          "job_type": "imsImportImageJob",
          "begin_time": "2024-11-06T06:21:08.769Z",
          "end_time": "2024-11-06T06:27:03.742Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "image_name": "test",
              "image_id": "431df7fd-a898-4dc0-86b1-22cfefb8a517"
          }
      }

-  If the **job_type** is **imsImportOvaImageJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac892fa13420193006a49173317",
          "job_type": "imsImportOvaImageJob",
          "begin_time": "2024-11-06T07:39:45.814Z",
          "end_time": "2024-11-06T07:49:45.814Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "sub_jobs_result": [
                  {
                      "job_id": "9a175ac892fa13420193006c29e133f0",
                      "job_type": "imsImportImageJob",
                      "begin_time": "2024-11-06T07:41:48.896Z",
                      "end_time": "2024-11-06T07:49:45.814Z",
                      "status": "SUCCESS",
                      "error_code": null,
                      "fail_reason": null,
                      "entities": {
                          "image_name": "test",
                          "image_id": "fc496c19-40c2-4220-8b1a-eba9d53fca7b"
                      }
                  }
              ],
              "sub_jobs_list": [
                  "9a175ac892fa13420193006c29e133f0"
              ]
          }
      }

-  If the **job_type** is **imsVolumeCreateImageJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac692fa125401930037d9e329aa",
          "job_type": "imsVolumeCreateImageJob",
          "begin_time": "2024-11-06T06:44:40.545Z",
          "end_time": "2024-11-06T06:47:40.545Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "image_name": "test",
              "image_id": "21b04ab5-e817-40ee-8d56-7ccdb8820335"
          }
      }

-  If the **job_type** is **imsImportDataImageJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac692fa125401930027b9c026b3",
          "job_type": "imsImportDataImageJob",
          "begin_time": "2024-11-06T06:27:03.742Z",
          "end_time": "2024-11-06T06:37:03.742Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "image_name": "test",
              "image_id": "aa5306f7-bc95-4fa3-aa40-dd38fbdf2031"
          }
      }

-  If the **job_type** is **imsCreateWholeImageByInstanceJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac792fa12d201930028cddb29c6",
          "job_type": "imsCreateWholeImageByInstanceJob",
          "begin_time": "2024-11-06T06:28:14.425Z",
          "end_time": "2024-11-06T06:37:03.742Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "image_name": "test",
              "image_id": "17b7bdeb-2e72-43a0-a202-d36ce344e902"
          }
      }

-  If the **job_type** is **imsCreateWholeImageByBackupJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac892fa13420193002961972392",
          "job_type": "imsCreateWholeImageByBackupJob",
          "begin_time": "2024-11-06T06:28:52.245Z",
          "end_time": "2024-11-06T06:28:58.399Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "image_name": "test",
              "image_id": "ea0d5dce-ddb2-4f6f-83e3-55da065347fd"
          }
      }

-  If the **job_type** is **imsNativeImportImageJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac692fa12540193005389023059",
          "job_type": "imsNativeImportImageJob",
          "begin_time": "2024-11-06T07:14:54.848Z",
          "end_time": "2024-11-06T07:19:54.848Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "image_id": "af8ea1dc-02f2-4019-8fa9-c9952a0077ce"
          }
      }

-  If the **job_type** is **imsNativeExportImageJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac892fa134201930039db1a27b1",
          "job_type": "imsNativeExportImageJob",
          "begin_time": "2024-11-06T06:46:51.929Z",
          "end_time": "2024-11-06T06:49:53.657Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "image_id": "1ab4df10-fe18-48b7-91c9-53695fcd9df5"
          }
      }

-  If the **job_type** is **imsAddImageMembersJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac692fa12540193002a6d4b2720",
          "job_type": "imsAddImageMembersJob",
          "begin_time": "2024-11-06T06:30:00.778Z",
          "end_time": "2024-11-06T06:30:03.179Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "results": [
                  {
                      "image_id": "30e55148-deb9-4923-adb9-91618de16ba0",
                      "status": "success"
                  }
              ]
          }
      }

-  If the **job_type** is **imsDelImageMembersJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac792fa12d20193002da96f2ac2",
          "job_type": "imsDelImageMembersJob",
          "begin_time": "2024-11-06T06:33:32.781Z",
          "end_time": "2024-11-06T06:33:34.181Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "results": []
          }
      }

-  If the **job_type** is **imsUpdateImageMembersJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac692fa12540193005c340f321c",
          "job_type": "imsUpdateImageMembersJob",
          "begin_time": "2024-11-06T07:24:22.925Z",
          "end_time": "2024-11-06T07:24:23.773Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "results": [
                  {
                      "image_id": "6596628c-42d4-4ff1-8660-8ea5ae61f243",
                      "status": "success"
                  }
              ]
          }
      }

-  If the **job_type** is **imsCopyImageInRegionJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac892fa13420193001c2e62205a",
          "job_type": "imsCopyImageInRegionJob",
          "begin_time": "2024-11-06T06:14:27.168Z",
          "end_time": "2024-11-06T06:16:38.446Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "image_name": "test",
              "image_id": "30e55148-deb9-4923-adb9-91618de16ba0"
          }
      }

-  If the **job_type** is **imsVolumesToSysDataImagesJob**, the response example is as follows:

   .. code-block::

      {
          "job_id": "9a175ac792fa12d201930031febf2bdd",
          "job_type": "imsVolumesToSysDataImagesJob",
          "begin_time": "2024-11-06T06:38:16.765Z",
          "end_time": "2024-11-06T06:48:16.765Z",
          "status": "SUCCESS",
          "error_code": null,
          "fail_reason": null,
          "entities": {
              "sub_jobs_result": [
                  {
                      "job_id": "9a175ac792fa12d20193003205b22be1",
                      "job_type": "imsCopyVolumeToImageJob",
                      "begin_time": "2024-11-06T06:38:18.545Z",
                      "end_time": "2024-11-06T06:48:16.765Z",
                      "status": "SUCCESS",
                      "error_code": null,
                      "fail_reason": null,
                      "entities": {
                          "image_name": "test",
                          "image_id": "bfb2de92-e7b9-4820-9522-416d8f2c812a"
                      }
                  }
              ],
              "sub_jobs_list": [
                  "9a175ac792fa12d20193003205b22be1"
              ]
          }
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
