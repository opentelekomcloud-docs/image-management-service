:original_name: en-us_topic_0172473649.html

.. _en-us_topic_0172473649:

Replicating a Shared Image
==========================

Scenarios
---------

Replicate a private image that was shared with you. That image will be displayed in your private image list. You can export, share, and replicate this image, or use it to create ECSs.

If the shared image to be replicated is an encrypted image, you can replace the key of the image with your own key when replicating the image. This prevents the shared image from being unavailable when the tenant who shares the image cancels the key authorization.

Constraints
-----------

-  Currently, only system and data disk images can be replicated.
-  Currently, shared images can only be replicated within a region.
-  An image to be replicated cannot be larger than 128 GiB.

Procedure
---------

#. Log in to the management console.

   a. Under **Computing**, click **Image Management Service**. The IMS console is displayed.

#. On the displayed IMS console, click the **Images Shared with Me** tab.

   Accept shared images are displayed.

#. Locate the target shared image and click **Replicate** under **More** in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0172485503.png
      :alt: **Figure 1** Replicating an image

      **Figure 1** Replicating an image

#. In the displayed dialog box, specify the name, enterprise project, and description for the new image.

   .. table:: **Table 1** Parameters for replicating an image

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                                               | Example Value         |
      +=======================+===========================================================================================================================================================================================================================================================+=======================+
      | Name                  | Enter a name that is easy to identify.                                                                                                                                                                                                                    | copy_CentOS7.9        |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Enterprise Project    | This parameter is for enterprise users. To use this function, contact customer service to enable it.                                                                                                                                                      | default               |
      |                       |                                                                                                                                                                                                                                                           |                       |
      |                       | An enterprise project groups cloud resources, so you can manage resources and users by project. The default project is **default**.                                                                                                                       |                       |
      |                       |                                                                                                                                                                                                                                                           |                       |
      |                       | Select an enterprise project from the drop-down list. For more information about enterprise projects, see `Accessing the Enterprise Center <https://docs.otc.t-systems.com/enterprise-project-service/umn/accessing_the_project_management_page.html>`__. |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | This parameter is optional. Enter a description for the image.                                                                                                                                                                                            | ``-``                 |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

   You can click the **Private Images** tab and view the creation progress of the image in the private image list. When the image status changes to **Normal**, the image creation is complete.
