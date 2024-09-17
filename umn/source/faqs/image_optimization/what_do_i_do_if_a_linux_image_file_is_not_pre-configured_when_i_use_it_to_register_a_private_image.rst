:original_name: en-us_topic_0030713211.html

.. _en-us_topic_0030713211:

What Do I Do If a Linux Image File Is Not Pre-Configured When I Use It to Register a Private Image?
===================================================================================================

If an image file is not configured as instructed in :ref:`Table 1 <en-us_topic_0030713198__table184016916467>` before it is exported from the original platform, you can use it to create an ECS, configure the ECS, and use the ECS to create a private image. :ref:`Figure 1 <en-us_topic_0030713211__fig18196115421120>` shows the process.

.. caution::

   An ECS can run properly only after KVM drivers are installed on it. If no such drivers are installed, the performance of the ECS will be affected and some functions will be unavailable. Ensure that KVM drivers have been installed for the image file before it is exported from the original platform. Otherwise, the ECSs created from the image will fail to start.

   For details, see :ref:`Installing Native KVM Drivers <en-us_topic_0000001120952155>`.

.. _en-us_topic_0030713211__fig18196115421120:

.. figure:: /_static/images/en-us_image_0208476701.png
   :alt: **Figure 1** Image creation process

   **Figure 1** Image creation process

.. _en-us_topic_0030713211__section1049514242043:

Step 1: Upload the Image File
-----------------------------

Upload the external image file to an OBS bucket. For details, see :ref:`Uploading an External Image File <en-us_topic_0030713192>`.

.. _en-us_topic_0030713211__section4198749842:

Step 2 Register the Image File as a Private Image
-------------------------------------------------

On the management console, select the uploaded image file and register it as a private image. For details, see :ref:`Registering an External Image File as a Private Image <en-us_topic_0030713193>`.

.. _en-us_topic_0030713211__section1762434871317:

Step 3: Create an ECS
---------------------

Create an ECS from the private image.

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Computing**, click **Image Management Service**.

      The IMS console is displayed.

#. Click the **Private Images** tab.

#. Locate the row that contains the private image and click **Apply for Server** in the **Operation** column.

#. Set parameters as promoted to create an ECS. Pay attention to the following:

   -  You must add inbound rules for security groups of the ECS to ensure that the ECS can be accessed.
   -  If Cloud-Init has been installed in the image file, set a login password as prompted. If Cloud-Init is not installed, use the password or certificate contained in the image file to log in.

   For details, see *Elastic Cloud Server User Guide*.

#. Check the ECS to see if the private image used to create the ECS has been pre-configured.

   a. Check whether the ECS can be successfully started. If the start succeeds, KVM drivers have been installed for the external image file on the original platform or the drivers have been automatically installed for the private image on the cloud platform. If the start failed, install KVM drivers for the image file and start from :ref:`Step 1: Upload the Image File <en-us_topic_0030713211__section1049514242043>` again.
   b. Check whether you can log in to the ECS using your configured password or key. If you can, Cloud-Init has been installed. If you cannot, use the password or key contained in the image file to log in to the ECS and install Cloud-Init as instructed in :ref:`Installing Cloud-Init <en-us_topic_0030730603>`.
   c. Check the network configuration by referring to :ref:`Step 4: Configure the ECS <en-us_topic_0030713211__section51410413191>`.

   If the ECS meets the preceding requirements, the private image has been pre-configured. Skip :ref:`Step 4: Configure the ECS <en-us_topic_0030713211__section51410413191>` and :ref:`Step 5: Create a Private Image from the ECS <en-us_topic_0030713211__section18481126192819>`.

.. _en-us_topic_0030713211__section51410413191:

Step 4: Configure the ECS
-------------------------

Remotely log in to the ECS created in :ref:`Step 3: Create an ECS <en-us_topic_0030713211__section1762434871317>` to configure it.

#. Log in to the ECS.
#. Configure the network.

   -  Run the **ifconfig** command to check whether the private IP address of the ECS is the same as that displayed on the console. If they are inconsistent, delete files from the network rule directory as instructed in :ref:`Deleting Files from the Network Rule Directory <en-us_topic_0069904570>`.
   -  Check whether NICs are set to DHCP. If the ECS is configured with a static IP address, change its IP address assignment mode to DHCP as instructed in :ref:`Setting the NIC to DHCP <en-us_topic_0030713176>`.
   -  Run the **service sshd status** command to check whether SSH is enabled. If it is disabled, run the **service sshd start** command to enable it. Ensure that your firewall (for example, Linux iptables) allows SSH access.

#. Configure a file system.

   -  Change the disk identifier in the GRUB configuration file to UUID. For details, see :ref:`Changing the Disk Identifier in the GRUB Configuration File to UUID <en-us_topic_0086020895>`.
   -  Change the disk identifier in the fstab file to UUID. For details, see :ref:`Changing the Disk Identifier in the fstab File to UUID <en-us_topic_0086024961>`.
   -  Clear the automatic mount configuration of non-system disks in the **/etc/fstab** file. For details, see :ref:`Detaching Data Disks from an ECS <en-us_topic_0030713179>`.

#. (Optional) Configure value-added functions.

   -  Install and configure Cloud-Init. For details, see :ref:`Installing Cloud-Init <en-us_topic_0030730603>` and :ref:`Configuring Cloud-Init <en-us_topic_0122876047>`.
   -  Enable NIC multi-queue. For details, see :ref:`How Do I Enable NIC Multi-Queue for an Image? <en-us_topic_0085214115>`

.. _en-us_topic_0030713211__section18481126192819:

Step 5: Create a Private Image from the ECS
-------------------------------------------

Create a private image from the ECS. For details, see :ref:`Creating a System Disk Image from a Linux ECS <en-us_topic_0030713180>`.

(Optional) Clear the Environment
--------------------------------

After the image registration is complete, delete the image file as well as the intermediate private image and ECS to prevent them from occupying storage and compute resources.

-  Delete the image registered in :ref:`Step 2 Register the Image File as a Private Image <en-us_topic_0030713211__section4198749842>`.
-  Delete the ECS created in :ref:`Step 3: Create an ECS <en-us_topic_0030713211__section1762434871317>`.
-  Delete the image file from the OBS bucket.
