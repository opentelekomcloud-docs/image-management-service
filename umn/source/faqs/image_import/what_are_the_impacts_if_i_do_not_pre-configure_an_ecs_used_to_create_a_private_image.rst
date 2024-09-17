:original_name: en-us_topic_0030713216.html

.. _en-us_topic_0030713216:

What Are the Impacts If I Do Not Pre-configure an ECS Used to Create a Private Image?
=====================================================================================

Before using an ECS or external image file to create a private image, you need to pre-configure the ECS or the source VM of the image file. If you do not perform the pre-configuration, there are some potential impacts:

#. If you do not delete network rule files from the **udev** directory, those rules will be applied to newly created ECSs. Also, if you do not configure DHCP, the NICs of newly created ECSs will not start from eth0. You need to remotely log in to the new ECSs to resolve these issues.
#. When creating Linux ECSs:

   -  Custom passwords cannot be injected.
   -  Certificates cannot be injected.
   -  Other custom configurations cannot be applied to new ECSs.

#. If you do not delete the automatic mount configuration from the **fstab** file, new ECSs may fail to start.
