:original_name: en-us_topic_0047501112.html

.. _en-us_topic_0047501112:

Optimization Process
====================

The proper running of ECSs depends on KVM Guest OS driver (UVP VMTools). To ensure that ECSs support KVM and to improve network performance, the UVP VMTools must be installed for the image.

#. Create an ECS using the Windows private image to be optimized and log in to the ECS.

#. .. _en-us_topic_0047501112__en-us_topic_0036684057_li24121565:

   Install the UVP VMTools which is required to create ECSs using KVM virtual resources.

   For details, see :ref:`Installing UVP VMTools <en-us_topic_0037352061>`.

#. On the ECS, choose **Control Panel** > **Power Options**. Click **Choose when to turn off the display**, select **Never** for **Turn off the display**, and save the changes.

#. .. _en-us_topic_0047501112__en-us_topic_0036684057_li19262089:

   Clear system logs and then stop the ECS.

   For details, see :ref:`Clearing System Logs <en-us_topic_0125075472>`.

#. Create a Windows private image from the ECS.
