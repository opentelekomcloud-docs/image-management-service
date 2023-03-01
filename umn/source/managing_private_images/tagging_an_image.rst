:original_name: en-us_topic_0068002265.html

.. _en-us_topic_0068002265:

Tagging an Image
================

Scenarios
---------

You can use tags to classify images. You can add, modify, or delete image tags, or search for required images by tag in the image list.

.. note::

   When adding predefined tags to an image or searching for an image using predefined tags, you must have permission to access the Tag Management Service (TMS).

Constraints
-----------

An image can have a maximum of 10 tags.

Add, Delete, and Modify Image Tags
----------------------------------

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Compute**, click **Image Management Service**.

      The IMS console is displayed.

#. Click the **Private Images** tab and click the image name to display the image details.

   -  To modify an image tag, go to :ref:`3 <en-us_topic_0068002265__en-us_topic_0029124542_li41380655103827>`.
   -  To delete an image tag, go to :ref:`4 <en-us_topic_0068002265__li29841739193722>`.
   -  To add an image tag, go to :ref:`5 <en-us_topic_0068002265__li185112015308>`.

#. .. _en-us_topic_0068002265__en-us_topic_0029124542_li41380655103827:

   Click the **Tags** tab, locate the target tag, and click **Edit** in the **Operation** column. In the displayed dialog box, modify the tag.

#. .. _en-us_topic_0068002265__li29841739193722:

   Click the **Tags** tab, locate the target tag, and click **Delete** in the **Operation** column. In the displayed dialog box, click **Yes**.

#. .. _en-us_topic_0068002265__li185112015308:

   Click the **Tags** tab and then **Add Tag**. In the displayed dialog box, add a tag.

Search for Private Images by Tag
--------------------------------

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Compute**, click **Image Management Service**.

      The IMS console is displayed.

#. Click the **Private Images** tab and then **Search by Tag**.

#. Enter the tag key and value.

   Neither the tag key nor tag value can be empty. When the tag key and tag value are matched, the system automatically shows your desired private images.

#. Click |image1| to add a tag.

   You can add multiple tags to search for private images. The system will display private images that match all tags.

#. Click **Search**.

   The system searches for private images based on tag keys or tag values.

Search for Shared Images by Tag
-------------------------------

You can search for a private image that has a tag and is shared with you by another tenant.

After you accept private image **image_test** with tag (Enterprise=A) which is shared by another tenant, you can search for the image by tag.

.. note::

   You cannot add tags to a shared image. The tags of a shared image are added by the tenant who shares the image with you.

#. Log in to the management console.

#. Under **Compute**, click **Image Management Service**.

   The **Private Images** page is displayed.

#. Click the **Images Shared with Me** tab and then **Search by Tag**.

#. Enter the tag key and value.

   Neither the tag key nor tag value can be empty. When the tag key and tag value are matched, the system automatically shows your desired shared images.

#. Click |image2| to add a tag.

   You can add multiple tags to search for shared images. The system will display private images that match all tags.

#. Click **Search**.

   The system searches for shared images based on tag keys or tag values.

.. |image1| image:: /_static/images/en-us_image_0187517327.png
.. |image2| image:: /_static/images/en-us_image_0187518440.png
