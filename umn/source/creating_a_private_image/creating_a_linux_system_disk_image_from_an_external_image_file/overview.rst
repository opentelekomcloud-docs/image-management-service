:original_name: en-us_topic_0030713191.html

.. _en-us_topic_0030713191:

Overview
========

You can import a local image or a system disk image from another cloud platform to the current cloud. After an image is imported, you can use it to create ECSs or reinstall the OSs of existing ECSs.

Creation Process
----------------

:ref:`Figure 1 <en-us_topic_0030713191__fig178711229102512>` shows the process of creating a private image.

.. _en-us_topic_0030713191__fig178711229102512:

.. figure:: /_static/images/en-us_image_0214265355.png
   :alt: **Figure 1** Creating a Linux system disk image

   **Figure 1** Creating a Linux system disk image

The procedure is as follows:

#. Prepare an external image file that meets platform requirements. For details, see :ref:`Preparing an Image File <en-us_topic_0030713198>`.
#. Upload the external image file to your OBS bucket. For details, see :ref:`Uploading an External Image File <en-us_topic_0030713192>`.
#. On the management console, select the uploaded image file and register it as a private image. For details, see :ref:`Registering an External Image File as a Private Image <en-us_topic_0030713193>`.
#. After the private image is registered, you can use it to create ECSs. For details, see :ref:`Creating a Linux ECS from an Image <en-us_topic_0030713197>`.
