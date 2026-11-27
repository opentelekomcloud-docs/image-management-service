:original_name: en-us_topic_0032042422.html

.. _en-us_topic_0032042422:

Stopping Sharing Images
=======================

Scenarios
---------

You can stop sharing images. After you stop sharing an image:

-  The image will be invisible to the recipients on the management console and no data will be returned when the recipients query the image through an API.
-  The recipients cannot use the image to create an ECS or EVS disk, or change the OS of an ECS.
-  The recipients cannot reinstall the OS of the ECSs created from that shared image, nor can they use the shared image to create ECSs identical to existing ones.

Prerequisites
-------------

You have shared private images with others.

Procedure
---------

#. Log in to the management console.

   a. Under **Computing**, click **Image Management Service**. The IMS console is displayed.

#. Click the **Private Images** tab.
#. Locate the row that contains the private image that you no longer want to share, and choose **More** > **Share** in the **Operation** column.
#. In the **Share Image** dialog box, click the **Stop Sharing** tab.
#. Select the project for which you want to stop the image sharing and click **OK**.
