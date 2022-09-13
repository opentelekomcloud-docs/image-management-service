:original_name: en-us_topic_0047501112.html

.. _en-us_topic_0047501112:

Optimization Process
====================

ECSs require Xen Guest OS driver (PV driver) and KVM Guest OS driver (UVP VMTools) for proper running. To ensure that ECSs support both Xen and KVM and to improve network performance, the PV driver and UVP VMTools must be installed for the image.

#. Create an ECS using the Windows private image to be optimized and log in to the ECS.

#. .. _en-us_topic_0047501112__en-us_topic_0036684057_li46245228:

   Install the latest version of PV driver on the ECS.

   For details, see :ref:`Installing the PV Driver <en-us_topic_0037352182>`.

#. Install the UVP VMTools required for creating ECSs in the KVM virtual resource pool.

   For details, see :ref:`Installing UVP VMTools <en-us_topic_0037352061>`.

#. On the ECS, choose **Control Panel** > **Power Options**. Click **Choose when to turn off the display**, select **Never** for **Turn off the display**, and save the changes.

#. .. _en-us_topic_0047501112__en-us_topic_0036684057_li19262089:

   Clear system logs and then stop the ECS.

   For details, see :ref:`Clearing System Logs <en-us_topic_0125075472>`.

#. Create a Windows private image using the ECS.
