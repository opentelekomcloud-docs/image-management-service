:original_name: en-us_topic_0032042422.html

.. _en-us_topic_0032042422:

Stopping Sharing Images
=======================

Scenarios
---------

You can stop sharing images. After you stop sharing an image:

-  The image will be invisible to the recipient on the management console and no data will be returned when the recipient query the image through an API.
-  The recipient cannot use the image to create an ECS or EVS disk, or change the OS of an ECS.
-  The recipient cannot reinstall the OS of the ECSs created from the shared image or create instances identical with these ECSs.

Prerequisites
-------------

You have shared private images with others.

Procedure
---------

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Compute**, click **Image Management Service**.

      The IMS console is displayed.

#. Click the **Private Images** tab.
#. Locate the row that contains the private image that you no longer want to share, and choose **More** > **Share** in the **Operation** column.
#. In the **Share Image** dialog box, click the **Stop Sharing** tab.
#. Select the project ID that you want to stop image sharing and click **OK**.
