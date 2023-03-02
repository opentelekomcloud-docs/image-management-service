:original_name: en-us_topic_0107462582.html

.. _en-us_topic_0107462582:

Viewing Traces
==============

Scenarios
---------

Once CTS is enabled, it starts recording IMS operations. You can view operations recorded in the last seven days on the CTS management console.

This section describes how to view the records.

Procedure
---------

#. Access the CTS console.

   a. Log in to the management console.
   b. Click **Cloud Trace Service** under **Management & Deployment**.

#. In the navigation pane on the left, choose **Trace List**.

#. Set the filter criteria and click **Query**.

   The following filters are available:

   -  **Trace Type**, **Trace Source**, **Resource Type**, and **Search By**.

      Select **Management** for **Trace Type** and **IMS** for **Trace Source**.

      Note that:

      -  If you select **Resource ID** for **Search By**, you need to enter a resource ID. Only whole word match is supported.
      -  If you select **Resource name** for **Search By**, you need to select or enter a specific resource name.

   -  **Operator**: Select a specific operator from the drop-down list.

   -  **Trace Status**: Available values are **All trace statuses**, **Normal**, **Warning**, and **Incident**.

   -  **Time Range**: You can select **Last 1 hour**, **Last 1 day**, **Last 1 week**, or **Customize**.

#. Locate the target trace and click |image1| to expand the trace details.

#. Click **View Trace** in the upper right corner of the trace details area.

.. |image1| image:: /_static/images/en-us_image_0285376505.png
