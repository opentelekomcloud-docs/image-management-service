:original_name: en-us_topic_0146480985.html

.. _en-us_topic_0146480985:

Configuring the ECS and Creating a Windows System Disk Image
============================================================

Scenarios
---------

After installing an OS for the temporary ECS, configure the ECS and install the Guest OS drivers provided by the cloud platform to ensure that ECSs created subsequently are available.

This section describes how to configure a Windows ECS, install the Guest OS drivers, and create a Windows system disk image.

Procedure
---------

#. .. _en-us_topic_0146480985__li108111309459:

   Configure the ECS.

   a. Check whether NICs are set to DHCP. If the ECS is configured with a static IP address, change its IP address assignment mode to DHCP as instructed in :ref:`Setting the NIC to DHCP <en-us_topic_0030713152>`.

   b. Enable remote desktop connection for the ECS as needed. For details about how to enable this function, see :ref:`Enabling Remote Desktop Connection <en-us_topic_0030713155>`.

   c. Install and configure Cloudbase-Init. User data injection on the management console is available for the new ECSs created from the image only after this tool is installed. For example, you can use data injection to set the login password for a new ECS. For details, see :ref:`Installing and Configuring Cloudbase-Init <en-us_topic_0030730602>`.

   d. (Optional) Configure value-added functions.

      Enable NIC multi-queue. For details, see :ref:`How Do I Enable NIC Multi-Queue for an Image? <en-us_topic_0085214115>`

      -  Enable NIC multi-queue. For details, see :ref:`How Do I Enable NIC Multi-Queue for an Image? <en-us_topic_0085214115>`

#. Stop the ECS to make the configurations take effect.

#. Use the ECS to create a Windows system disk image.

   For details, see :ref:`Creating a System Disk Image from a Windows ECS <en-us_topic_0030713149>`.

Follow-up Procedure
-------------------

After the system disk image is created, delete the temporary ECS in a timely manner to prevent it from occupying compute resources.
