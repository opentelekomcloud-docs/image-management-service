:original_name: en-us_topic_0030713176.html

.. _en-us_topic_0030713176:

Setting the NIC to DHCP
=======================

Scenarios
---------

If a private image is created from an ECS or external image file and the VM where the ECS or external image file is located is configured with a static IP address, you need to change the NIC attribute to DHCP so that the new ECSs created from the private image can dynamically obtain an IP address.

The configuration method varies depending on OSs.

.. note::

   When registering an external image file as a private image, configure DHCP on the VM where the external image file is located. You are advised to configure DHCP on the VM and then export the image file.

Prerequisites
-------------

You have logged in to the ECS used to create a Windows private image.

For details about how to log in to an ECS, see *Elastic Cloud Server User Guide*.

Procedure
---------

This section uses Ubuntu 16.04 as an example to describe how to query and configure NIC attributes of an ECS.

#. Run the following command on the ECS to open the **/etc/network/interfaces** file using the vi editor and query the IP address obtaining mode:

   **vi /etc/network/interfaces**

   -  If DHCP has been configured on all NICs, enter **:q** to exit the vi editor.

      .. code-block::

         auto lo
         iface lo inet loopback
         auto eth0
         iface eth0 inet dhcp

         auto eth1
         iface eth1 inet dhcp

   -  If static IP addresses are set on the NICs, go to :ref:`2 <en-us_topic_0030713176__en-us_topic_0029124465_li47654828194142>`.

      .. code-block::

         auto lo
         iface lo inet loopback
         auto eth0
         #iface eth0 inet dhcp
         iface eth0 inet static
         address 192.168.1.109
         netmask 255.255.255.0
         gateway 192.168.1.1

#. .. _en-us_topic_0030713176__en-us_topic_0029124465_li47654828194142:

   Press **i** to enter editing mode.

#. Delete the static IP address configuration and configure DHCP for the NICs.

   You can insert a number sign (#) in front of each line of static IP address configuration to comment it out.

   .. code-block::

      auto lo
      iface lo inet loopback
      auto eth0
      iface eth0 inet dhcp

   If the ECS has multiple NICs, you must configure DHCP for all the NICs.

   .. code-block::

      auto lo
      iface lo inet loopback
      auto eth0
      iface eth0 inet dhcp
      auto eth1
      iface eth1 inet dhcp

#. Press **Esc**, enter **:wq**, and press **Enter**.

   The system saves the configuration and exits the vi editor.

Related Operations
------------------

Configure DHCP to enable the ECS to obtain IP addresses continuously.

-  For CentOS and EulerOS, use the vi editor to add **PERSISTENT_DHCLIENT="y"** to configuration file **/etc/sysconfig/network-scripts/ifcfg-ethX**.
-  For SUSE Linux Enterprise, use the vi editor to set **DHCLIENT_USE_LAST_LEASE** to **no** in the configuration file **/etc/sysconfig/network/dhcp**.
-  For Ubuntu 12.04 or later, upgrade dhclient to ISC dhclient 4.2.4 so that the NIC can consistently obtain IP addresses from the DHCP server. To perform the upgrade, you need to install isc-dhcp-server first.
