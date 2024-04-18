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

Ubuntu 18 or Later
------------------

#. Run **vi /etc/netplan/01-netcfg.yaml** on the ECS to open the **/etc/netplan/01-netcfg.yaml** file, and check whether the value of **dhcp4** is **true**.

   -  If **dhcp4** is set to **true**, enter **:q** to exit the editor. No further action will be required.

      .. code-block::

          network:
             version:2
             renderer:NetworkManager
             ethernets:
                 eth0:
                     dhcp4: true

   -  If **dhcp4** is set to **no** and a static IP address is configured, go to the next step.

      .. code-block::

         network:
             version:2
             renderer:NetworkManager
             ethernets:
                 eth0:
                     dhcp4: no
                    addresses: [192.168.1.109/24]
                    gateway4: 192.168.1.1
                    nameservers:
                       addresses: [8.8.8.8,114.114.114.114]

#. Press **i** to enter the editing mode.

   Delete the static IP address settings and set **dhcp4** to **true**. You can also use a number sign (#) to comment out the static IP address settings.

   .. code-block::

      network:
          version:2
          renderer:NetworkManager
          ethernets:
              eth0:
                dhcp4: true   # Set dhcp4 to true.
                #dhcp4: no    # Delete or comment out the static IP address settings.
                #addresses: [192.168.1.109]
                #gateway4: 192.168.1.1
                #nameservers:
                # addresses: [8.8.8.8,114.114.114.114]

#. If your ECS has more than one NIC, configure DHCP for all of them.

   .. code-block::

      network:
          version:2
          renderer:NetworkManager
          ethernets:
               eth0:
                  dhcp4: true
               eth1:
                   dhcp4: true
               eth2:
                   dhcp4: true
               eth3:
                   dhcp4: true

#. Press **Esc**, enter **:wq**, and press **Enter** to save the settings and exit the vi editor.

#. Run the **netplan apply** command to make the settings take effect.

Ubuntu 16.04
------------

#. Run the following command on the ECS to open the **/etc/network/interfaces** file:

   **vi /etc/network/interfaces**

   -  If DHCP has been configured for all NICs, enter **:q** to exit the vi editor.

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

   Press **i** to enter the editing mode.

#. Delete the static IP address settings and configure DHCP for the NICs.

   You can also use a number sign (#) to comment out the static IP address settings.

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

   The system saves the settings and exits the vi editor.

Related Operations
------------------

Configure DHCP to enable the ECS to obtain IP addresses continuously.

-  For CentOS and EulerOS, use the vi editor to add **PERSISTENT_DHCLIENT="y"** to configuration file **/etc/sysconfig/network-scripts/ifcfg-ethX**.
-  For SUSE Linux Enterprise, use the vi editor to set **DHCLIENT_USE_LAST_LEASE** to **no** in the configuration file **/etc/sysconfig/network/dhcp**.
-  For Ubuntu 12.04 or later, upgrade dhclient to ISC dhclient 4.2.4 so that the NIC can consistently obtain IP addresses from the DHCP server. To perform the upgrade, you need to install isc-dhcp-server first.
