:original_name: en-us_topic_0030713216.html

.. _en-us_topic_0030713216:

What Are the Impacts If I Do Not Pre-configure an ECS Used to Create a Private Image?
=====================================================================================

Before using an ECS or external image file to create a private image, you need to pre-configure the ECS or the source VM of the image file. If you do not perform the pre-configuration, there will be the following impacts:

#. If you do not delete residual rule files from the **udev** directory, new ECSs will retain the configurations of the source ECS or image file. If you do not set the IP address assignment mode to DHCP, NICs of new ECSs will not start from eth0. You need to remotely log in to the new ECSs to perform configurations.
#. For Linux, the following issues may occur during the ECS creation:

   -  Custom passwords cannot be injected.
   -  Certificates cannot be injected.
   -  Other custom configurations cannot be applied on new ECSs.

#. If you do not delete information about automatic disk attachment detection from the **fstab** file, new ECSs may fail to start.
