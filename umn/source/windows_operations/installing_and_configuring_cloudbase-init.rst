:original_name: en-us_topic_0030730602.html

.. _en-us_topic_0030730602:

Installing and Configuring Cloudbase-Init
=========================================

Scenarios
---------

To ensure that you can use the user data injection function to inject initial custom information into ECSs created from a private image (such as setting the ECS login password), install Cloudbase-Init on the ECS used to create the image.

-  If Cloudbase-Init is not installed, you cannot configure an ECS. As a result, you can only use the password in the image file to log in to the ECS.
-  By default, ECSs created from a public image have Cloudbase-Init installed. You do not need to install or configure Cloudbase-Init on such ECSs.
-  For ECSs created from external image files, install and configure Cloudbase-Init by performing the operations in this section.

Prerequisites
-------------

-  An EIP has been bound to the ECS.
-  You have logged in to the ECS.
-  The IP address obtaining mode of the ECS is DHCP.

Install Cloudbase-Init
----------------------

#. On the Windows **Start** menu, choose **Control Panel** > **Programs** > **Programs and Features** and check whether Cloudbase-Init is installed.

   -  If yes, go to :ref:`Configure Cloudbase-Init <en-us_topic_0030730602__section67455211370>`.
   -  If no, go to the next step.

#. Check whether the version of the OS is Windows desktop.

   -  If yes, go to :ref:`3 <en-us_topic_0030730602__li5127112791712>`.
   -  If the OS is Windows Server, go to :ref:`4 <en-us_topic_0030730602__en-us_topic_0029124575_li6098361192920>`.

#. .. _en-us_topic_0030730602__li5127112791712:

   Enable the administrator account (Windows 7 is used as an example).

   a. Click **Start** and choose **Control Panel** > **System and Security** > **Administrative Tools**.
   b. Double-click **Computer Management**.
   c. Choose **System Tools** > **Local Users and Groups** > **Users**.
   d. Right-click **Administrator** and select **Properties**.
   e. Deselect **Account is disabled**.

#. .. _en-us_topic_0030730602__en-us_topic_0029124575_li6098361192920:

   Download the Cloudbase-Init installation package.

   Download the Cloudbase-Init installation package of the appropriate version based on the OS architecture from the Cloudbase-Init official website (http://www.cloudbase.it/cloud-init-for-windows-instances/).

   Cloudbase-Init has two versions: stable and beta.

   To obtain the stable version, visit the following paths:

   -  64-bit: https://www.cloudbase.it/downloads/CloudbaseInitSetup_Stable_x64.msi
   -  32-bit: https://www.cloudbase.it/downloads/CloudbaseInitSetup_Stable_x86.msi

   To obtain the beta version, visit the following paths:

   -  64-bit: https://www.cloudbase.it/downloads/CloudbaseInitSetup_x64.msi
   -  32-bit: https://www.cloudbase.it/downloads/CloudbaseInitSetup_x86.msi

#. Double-click the Cloudbase-Init installation package.

#. Click **Next**.

#. Select **I accept the terms in the License Agreement** and click **Next**.

#. Retain the default path and click **Next**.

#. In the **Configuration options** window, enter **Administrator** for **Username**, select **COM1** for **Serial port for logging**, and ensure that **Run Cloudbase-Init service as LocalSystem** is not selected.

   .. note::

      The version number shown in the figure is for reference only.


   .. figure:: /_static/images/en-us_image_0087083593.png
      :alt: **Figure 1** Configuring parameters


      **Figure 1** Configuring parameters

#. Click **Next**.

#. Click **Install**.

#. In the **Files in Use** dialog box, select **Close the application and attempt to restart them** and click **OK**.

#. Check whether the version of the OS is Windows desktop.

   -  If yes, go to :ref:`15 <en-us_topic_0030730602__li8450150161333>`.
   -  If no, go to :ref:`14 <en-us_topic_0030730602__li208441311639>`.

#. .. _en-us_topic_0030730602__li208441311639:

   In the **Completed the Cloudbase-Init Setup Wizard** window, ensure that neither option is selected.


   .. figure:: /_static/images/en-us_image_0085074510.png
      :alt: **Figure 2** Completing the Cloudbase-Init installation


      **Figure 2** Completing the Cloudbase-Init installation

   .. note::

      The version number shown in the figure is for reference only.

#. .. _en-us_topic_0030730602__li8450150161333:

   Click **Finish**.

.. _en-us_topic_0030730602__section67455211370:

Configure Cloudbase-Init
------------------------

#. Edit the configuration file **C:\Program Files\Cloudbase Solutions\Cloudbase-Init\conf\cloudbase-init.conf** in the Cloudbase-Init installation path.

   a. Add **netbios_host_name_compatibility=false** to the last line of the file so that the hostname supports a maximum of 63 characters.

      .. note::

         NetBIOS contains no more than 15 characters due to Windows system restrictions.

   b. Add **metadata_services=cloudbaseinit.metadata.services.httpservice.HttpService** to enable the agent to access the IaaS OpenStack data source.

   c. (Optional) Add the following configuration items to configure the number of retry times and interval for obtaining metadata:

      .. code-block::

         retry_count=40
         retry_count_interval=5

   d. (Optional) Add the following configuration item to prevent metadata network disconnections caused by the default route added by Windows:

      .. code-block::

         [openstack]
         add_metadata_private_ip_route=False

   e. (Optional) When the Cloudbase-Init version is 0.9.12 or later, you can customize the length of the password.

      Change the value of **user_password_length** to customize the password length.

#. Release the current DHCP address so that the created ECSs can obtain correct addresses.

   In the Windows command line, run the following command to release the current DHCP address:

   **ipconfig /release**

   .. note::

      This operation will interrupt network connection and adversely affect ECS use. The network will automatically recover after the ECSs are started again.

#. When creating an image using a Windows ECS, you need to change the SAN policy of the ECS to **OnlineAll**. Otherwise, EVS disks attached to the ECSs created from the image may be offline.

   Windows has three types of SAN policies: **OnlineAll**, **OfflineShared**, and **OfflineInternal**.

   .. table:: **Table 1** SAN policies

      +-----------------+------------------------------------------------------------------------------------------------------------------------------------+
      | Type            | Description                                                                                                                        |
      +=================+====================================================================================================================================+
      | OnlineAll       | All newly detected disks are automatically brought online.                                                                         |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------+
      | OfflineShared   | All disks on sharable buses, such as iSCSI and FC, are left offline by default, while disks on non-sharable buses are kept online. |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------+
      | OfflineInternal | All newly detected disks are left offline.                                                                                         |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------+

   a. Execute **cmd.exe** and run the following command to query the current SAN policy of the ECS using DiskPart:

      **diskpart**

   b. Run the following command to view the SAN policy of the ECS:

      **san**

      -  If the SAN policy is **OnlineAll**, run the **exit** command to exit DiskPart.

      -  If the SAN policy is not **OnlineAll**, go to :ref:`3.c <en-us_topic_0030730602__li1823793883810>`.

   c. .. _en-us_topic_0030730602__li1823793883810:

      Run the following command to change the SAN policy of the ECS to **OnlineAll**:

      **san policy=onlineall**
