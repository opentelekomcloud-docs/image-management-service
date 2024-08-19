:original_name: en-us_topic_0047501112.html

.. _en-us_topic_0047501112:

Optimization Process
====================

An ECS can run properly only after KVM Guest OS drivers (VirtIO drivers) are installed on it. To ensure that ECSs support KVM and to improve network performance, VirtIO drivers must be installed for the image.

#. Create an ECS from the Windows private image to be optimized and log in to the ECS.

#. .. _en-us_topic_0047501112__li1314146174813:

   Install VirtIO drivers that are needed to create KVM ECSs.

   For details, see :ref:`Installing VirtIO Drivers <en-us_topic_0000001841305273>`.

#. On the ECS, choose **Control Panel** > **Power Options**. Click **Choose when to turn off the display**, select **Never** for **Turn off the display**, and save the changes.

#. .. _en-us_topic_0047501112__en-us_topic_0036684057_li19262089:

   Clear system logs and then stop the ECS.

   For details, see :ref:`Clearing System Logs <en-us_topic_0125075472>`.

#. Create a Windows private image from the ECS.
