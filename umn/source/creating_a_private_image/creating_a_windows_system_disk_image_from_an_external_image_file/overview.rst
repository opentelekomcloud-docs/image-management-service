:original_name: en-us_topic_0030713182.html

.. _en-us_topic_0030713182:

Overview
========

You can import a local image or a system disk image from another cloud platform to the current cloud. After an image is imported, you can use it to create ECSs or reinstall the OSs of existing ECSs.

Creation Process
----------------

:ref:`Figure 1 <en-us_topic_0030713182__fig178711229102512>` shows the process of creating a private image.

.. _en-us_topic_0030713182__fig178711229102512:

.. figure:: /_static/images/en-us_image_0208252825.png
   :alt: **Figure 1** Creating a Windows system disk image

   **Figure 1** Creating a Windows system disk image

As shown in the figure, the following steps are required to register an external image file as a private image:

#. Prepare an external image file that meets platform requirements. For details, see :ref:`Preparing an Image File <en-us_topic_0030713189>`.
#. Upload the external image file to your OBS bucket. For details, see :ref:`Uploading an External Image File <en-us_topic_0030713183>`.
#. On the management console, select the uploaded image file and register it as a private image. For details, see :ref:`Registering an External Image File as a Private Image <en-us_topic_0030713184>`.
#. After the private image is registered, you can use it to create ECSs. For details, see :ref:`Creating a Windows ECS from an Image <en-us_topic_0030713188>`.
