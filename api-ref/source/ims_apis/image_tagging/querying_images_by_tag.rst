:original_name: en-us_topic_0102682861.html

.. _en-us_topic_0102682861:

Querying Images by Tag
======================

Function
--------

This API is used to filter or count images using tags or other conditions.

Constraints
-----------

To be compatible with remaining tags, the system will not verify the character set of the tag keys and values in the query condition when parameters **tags** **not_tags**, **tags_any**, and **not_tags_any** are used.

URI
---

POST /v2/{project_id}/images/resource_instances/action

:ref:`Table 1 <en-us_topic_0102682861__table27444833173551>` lists the parameters in the URI.

.. _en-us_topic_0102682861__table27444833173551:

.. table:: **Table 1** Parameter description

   ========== ========= ====== =========================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =========================
   project_id Yes       String Specifies the project ID.
   ========== ========= ====== =========================

Request
-------

-  Request parameters

   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                                                                                                                                                                                    |
   +=================+=================+==================+================================================================================================================================================================================================================================================================================================================================================================+
   | action          | Yes             | String           | Identifies the operation. This parameter is case sensitive and its value can be **filter** or **count**.                                                                                                                                                                                                                                                       |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                  | -  The value **filter** indicates pagination query.                                                                                                                                                                                                                                                                                                            |
   |                 |                 |                  | -  The value **count** indicates that the total number of query results meeting the search criteria will be returned.                                                                                                                                                                                                                                          |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags            | No              | Array of objects | Includes all specified tags. A maximum of 10 tag keys are allowed for each query operation. Each tag key can contain a maximum of 10 tag values. Both tag keys and values must be unique. The tag keys cannot be left blank.                                                                                                                                   |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                  | For details, see :ref:`Table 2 <en-us_topic_0102682861__table45012720173551>`.                                                                                                                                                                                                                                                                                 |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags_any        | No              | Array of objects | Includes any of specified tags. A maximum of 10 tag keys are allowed for each query operation. Each tag key can contain a maximum of 10 tag values. Both tag keys and values must be unique. The tag keys cannot be left blank and set to an empty string.                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                  | For details, see :ref:`Table 3 <en-us_topic_0102682861__table18634235114814>`.                                                                                                                                                                                                                                                                                 |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not_tags        | No              | Array of objects | Excludes all specified tags. A maximum of 10 tag keys are allowed for each query operation. Each tag key can contain a maximum of 10 tag values. Both tag keys and values must be unique. The tag keys cannot be left blank.                                                                                                                                   |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                  | For details, see :ref:`Table 4 <en-us_topic_0102682861__table6138181054913>`.                                                                                                                                                                                                                                                                                  |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not_tags_any    | No              | Array of objects | Excludes any of specified tags. A maximum of 10 tag keys are allowed for each query operation. Each tag key can contain a maximum of 10 tag values. Both tag keys and values must be unique. The tag keys cannot be left blank.                                                                                                                                |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                  | For details, see :ref:`Table 5 <en-us_topic_0102682861__table1556162310506>`.                                                                                                                                                                                                                                                                                  |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | without_any_tag | No              | Boolean          | If this parameter is set to **true**, all resources without tags are queried. In this case, the **tag**, **not_tags**, **tags_any**, and **not_tags_any** fields are ignored.                                                                                                                                                                                  |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | String           | Specifies the maximum number of query records. This parameter is invalid when **action** is set to **count**. If **action** is set to **filter**, the parameter **limit** takes effect and its default value is **10**. The value of **limit** ranges from 1 to 1000.                                                                                          |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | String           | Specifies the index position. The query starts from the next image indexed by this parameter. This parameter is not required when data on the first page is queried, and it is invalid when **action** is set to **count**. If **action** is set to **filter**, the default value of **offset** is **0**. The value of **offset** cannot be a negative number. |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | matches         | No              | Array of objects | Specifies the search criteria. The tag key is the field to match, for example, **resource_name** or **resource_id**. **value** indicates the matched value. Keys in this list must be unique. The parameter cannot be left blank and may not be transferred.                                                                                                   |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                  | For details, see :ref:`Table 6 <en-us_topic_0102682861__table194603471868>`.                                                                                                                                                                                                                                                                                   |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0102682861__table45012720173551:

   .. table:: **Table 2** Data structure description of the tags field

      +-----------+-----------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Mandatory | Type             | Description                                                                                                                                                                                                                  |
      +===========+===========+==================+==============================================================================================================================================================================================================================+
      | key       | Yes       | String           | Specifies the tag key. The tag key contains a maximum of 127 Unicode characters and cannot be left blank.                                                                                                                    |
      +-----------+-----------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | values    | Yes       | Array of strings | Lists the tag values. Each value can contain a maximum of 255 Unicode characters. If this parameter is left blank, any value is matched. If multiple values are listed, images that have any of the values will be returned. |
      +-----------+-----------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0102682861__table18634235114814:

   .. table:: **Table 3** Data structure description of the tags_any field

      +-----------+-----------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Mandatory | Type             | Description                                                                                                                                                                                                                  |
      +===========+===========+==================+==============================================================================================================================================================================================================================+
      | key       | Yes       | String           | Specifies the tag key. The tag key contains a maximum of 127 Unicode characters and cannot be left blank.                                                                                                                    |
      +-----------+-----------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | values    | Yes       | Array of strings | Lists the tag values. Each value can contain a maximum of 255 Unicode characters. If this parameter is left blank, any value is matched. If multiple values are listed, images that have any of the values will be returned. |
      +-----------+-----------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0102682861__table6138181054913:

   .. table:: **Table 4** Data structure description of the not_tags field

      +-----------+-----------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Mandatory | Type             | Description                                                                                                                                                                                                                  |
      +===========+===========+==================+==============================================================================================================================================================================================================================+
      | key       | Yes       | String           | Specifies the tag key. The tag key contains a maximum of 127 Unicode characters and cannot be left blank.                                                                                                                    |
      +-----------+-----------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | values    | Yes       | Array of strings | Lists the tag values. Each value can contain a maximum of 255 Unicode characters. If this parameter is left blank, any value is matched. If multiple values are listed, images that have any of the values will be returned. |
      +-----------+-----------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0102682861__table1556162310506:

   .. table:: **Table 5** Data structure description of the not_tags_any field

      +-----------+-----------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Mandatory | Type             | Description                                                                                                                                                                                                                                                             |
      +===========+===========+==================+=========================================================================================================================================================================================================================================================================+
      | key       | Yes       | String           | Specifies the tag key. The tag key contains a maximum of 127 Unicode characters and cannot be left blank.                                                                                                                                                               |
      +-----------+-----------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | values    | Yes       | Array of strings | Lists the tag values. Each value can contain a maximum of 255 Unicode characters. If this parameter is left blank, any value is matched. When multiple values are specified and the key requirements are met, images that have any of the specified values are queried. |
      +-----------+-----------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0102682861__table194603471868:

   .. table:: **Table 6** Data structure description of the matches field

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                           |
      +=================+=================+=================+=======================================================================================================================================================================================================================================================+
      | key             | Yes             | String          | Specifies the tag key, that is to say, the field name for the query operation. Valid values include **resource_name** and **resource_id**.                                                                                                            |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | If the field name is **resource_name** and the value is an empty string, exact query is performed. Otherwise, fuzzy query is performed based on the image name. If the field name is **resource_id**, exact query is performed based on the image ID. |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | value           | Yes             | String          | Specifies the tag value. It cannot be left blank. Each value can contain a maximum of 255 Unicode characters.                                                                                                                                         |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example requests

   .. code-block:: text

      POST https://{Endpoint}/v2/fd73a4a14a4a4dfb9771a8475e5198ea/images/resource_instances/action

   -  Request body when **action** is set to **count**

      ::

         {
            "action": "count",
            "matches": [{
               "key": "resource_name",
               "value": "test100"
            }],
            "tags": [
            {
               "key": "key3",
               "values": ["valueXX"]
            }],
            "tags_any": [
            {
               "key": "key0",
               "values": ["valueXX"]
            }],
               "not_tags": [
            {
               "key": "key9",
               "values": ["value9"]
            }],
            "not_tags_any": [{
               "key": "key7",
               "values": ["value7"]
            }]
         }

   -  Request body when **action** is set to **filter**

      ::

         {
            "action": "filter",
            "limit": "1",
            "offset": "0",
            "matches": [{
               "key": "resource_name",
               "value": "test100"
            }],
            "tags": [
            {
               "key": "key3",
               "values": ["valueXX"]
            }],
            "tags_any": [
            {
               "key": "key0",
               "values": ["valueXX"]
            }],
            "not_tags": [
            {
               "key": "key9",
               "values": ["value9"]
            }],
            "not_tags_any": [{
               "key": "key7",
               "values": ["value7"]
            }]
         }

Response
--------

-  Response parameters

   +-------------+----------------------------------------------------------------------------+----------------------------------------------+
   | Parameter   | Type                                                                       | Description                                  |
   +=============+============================================================================+==============================================+
   | resources   | Array of :ref:`resource <en-us_topic_0102682861__table3856915489>` objects | Lists the images.                            |
   +-------------+----------------------------------------------------------------------------+----------------------------------------------+
   | total_count | Integer                                                                    | Specifies the total number of query records. |
   +-------------+----------------------------------------------------------------------------+----------------------------------------------+

   .. _en-us_topic_0102682861__table3856915489:

   .. table:: **Table 7** Data structure description of the resource field

      +-----------------+---------------------------------------------------------------------------+---------------------------+
      | Parameter       | Type                                                                      | Description               |
      +=================+===========================================================================+===========================+
      | resource_id     | String                                                                    | Specifies the image ID.   |
      +-----------------+---------------------------------------------------------------------------+---------------------------+
      | resource_detail | :ref:`ResourceDetail <en-us_topic_0102682861__table1835694225516>` object | Provides image details.   |
      +-----------------+---------------------------------------------------------------------------+---------------------------+
      | tags            | Array of :ref:`Tags <en-us_topic_0102682861__table1526715341887>` objects | Lists the image tags.     |
      +-----------------+---------------------------------------------------------------------------+---------------------------+
      | resource_name   | String                                                                    | Specifies the image name. |
      +-----------------+---------------------------------------------------------------------------+---------------------------+

   .. _en-us_topic_0102682861__table1835694225516:

   .. table:: **Table 8** ResourceDetail object

      ========= ====== ========= ===========================
      Parameter Type   Mandatory Description
      ========= ====== ========= ===========================
      status    string Yes       Specifies the image status.
      ========= ====== ========= ===========================

   .. _en-us_topic_0102682861__table1526715341887:

   .. table:: **Table 9** Data structure description of the resource_tag field

      ========= ====== ===============================
      Parameter Type   Description
      ========= ====== ===============================
      key       String Specifies the key of the tag.
      value     String Specifies the value of the tag.
      ========= ====== ===============================

-  Example response

   -  Example response when **action** is set to **count**

      .. code-block:: text

         STATUS CODE 200

      ::

         {
            "total_count": 36
         }

   -  Example response when **action** is set to **filter**

      .. code-block:: text

         STATUS CODE 200

      ::

         {
            "total_count": 36,
            "resources": [{
               "resource_name": "test10002",
               "resource_detail": {"status": "active"},
               "tags": [{
                  "value": "value4",
                  "key": "key4"
               },
               {
                  "value": "valueXX",
                  "key": "key3"
               },
               {
                  "value": "value2",
                  "key": "key2"
               },
               {
                  "value": "value5",
                  "key": "key5"
               },
               {
                  "value": "value8",
                  "key": "key8"
               },
               {
                  "value": "valueXX",
                  "key": "key6"
               },
               {
                  "value": "valueXX",
                  "key": "key0"
               },
               {
                  "value": "value1",
                  "key": "key1"
               },
               {
                  "value": "value7",
                  "key": "key7"
               },
               {
                  "value": "valueXX",
                  "key": "key9"
               }],
               "resource_id": "8693187d-1590-4f9f-ae34-eb9e3037cf68"
            }]
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
   | 404 Not Found             | The requested resource was not found.                |
   +---------------------------+------------------------------------------------------+
   | 500 Internal Server Error | Internal service error.                              |
   +---------------------------+------------------------------------------------------+
   | 503 Service Unavailable   | The service is unavailable.                          |
   +---------------------------+------------------------------------------------------+
