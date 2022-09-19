:original_name: en-us_topic_0086024961.html

.. _en-us_topic_0086024961:

Changing the Disk Identifier in the fstab File to UUID
======================================================

Scenarios
---------

When optimizing a Linux private image, you need to change the disk identifier to UUID in the fstab configuration file of the ECS.

Procedure
---------

-  Take CentOS 7.0 as an example. Run **blkid** to obtain the UUIDs of all partitions. Modify the **/etc/fstab** file and use the partition UUIDs to configure automatic partition mounting.

#. Log in to the ECS as user **root**.

#. Run the following command to query all types of mounted file systems and device UUIDs:

   **blkid**

   The following information is displayed:

   .. code-block::

      /dev/xvda2: UUID="4eb40294-4c6f-4384-bbb6-b8795bbb1130" TYPE="xfs"
      /dev/xvda1: UUID="2de37c6b-2648-43b4-a4f5-40162154e135" TYPE="swap"

#. Run the following command to query the **fstab** file:

   **cat /etc/fstab**

   The following information is displayed:

   .. code-block:: console

      [root@CTU1000028010 ~]# cat /etc/fstab
      /dev/xvda2  /       xfs     defaults    0 0
      /dev/xvda1  swap    swap    defaults    0 0

#. Check whether the disk identifier in the **fstab** file is the device name.

   -  If the disk is represented by UUID, no further operation is required.
   -  If the disk is represented by the device name, go to :ref:`5 <en-us_topic_0086024961__li63646666154817>`.

#. .. _en-us_topic_0086024961__li63646666154817:

   Run the following command to open the **fstab** file:

   **vi /etc/fstab**

#. Press **i** to enter editing mode and change the disk identifier in the **fstab** file to UUID.

-  Take CentOS 7.1 as an example. Run **blkid** to obtain the UUIDs of all partitions. Modify the **/etc/fstab** file and use the partition UUIDs to configure automatic partition mounting.

#. Log in to the ECS as user **root**.

#. Run the following command to query all types of mounted file systems and device UUIDs:

   **blkid**

   .. code-block::

      /dev/xvda2: UUID="4eb40294-4c6f-4384-bbb6-b8795bbb1130" TYPE="xfs"
      /dev/xvda1: UUID="2de37c6b-2648-43b4-a4f5-40162154e135" TYPE="swap"

   Before the change:

   .. code-block:: console

      [root@CTU1000028010 ~]# cat /etc/fstab
      /dev/xvda2  /       xfs     defaults    0 0
      /dev/xvda1  swap    swap    defaults    0 0

   After the change:

   .. code-block:: console

      [root@CTU1000028010 ~]# cat /etc/fstab
      UUID=4eb40294-4c6f-4384-bbb6-b8795bbb1130  /       xfs     defaults    0 0
      UUID=2de37c6b-2648-43b4-a4f5-40162154e135  swap    swap    defaults    0 0

#. Press **Esc**, enter **:wq**, and press **Enter**. The system saves the configuration and exits the vi editor.

#. Run the following command to verify the change:

   **cat /etc/fstab**

   The change is successful if information similar to the following is displayed:

   .. code-block:: console

      [root@CTU1000028010 ~]# cat /etc/fstab
      UUID=4eb40294-4c6f-4384-bbb6-b8795bbb1130  /       xfs     defaults    0 0
      UUID=2de37c6b-2648-43b4-a4f5-40162154e135  swap    swap    defaults    0 0
