:original_name: en-us_topic_0085214115.html

.. _en-us_topic_0085214115:

How Do I Enable NIC Multi-Queue for an Image?
=============================================

Scenarios
---------

With the increase of network I/O bandwidth, a single vCPU cannot meet the requirement of processing NIC interruptions. NIC multi-queue allows multiple vCPUs to process NIC interruptions, thereby improving network PPS and I/O performance.

.. _en-us_topic_0085214115__en-us_topic_0058758453_section892862210138:

ECSs Supporting NIC Multi-Queue
-------------------------------

NIC multi-queue can be enabled on an ECS only when the ECS specifications, virtualization type, and image meet the requirements described in this section.

-  For details about the ECS flavors that support NIC multi-queue, see section "Instances" in *Elastic Cloud Server User Guide*.

   .. note::

      If the number of NIC queues is greater than 1, NIC multi-queue is supported.

-  Only KVM ECSs support NIC multi-queue.
-  The Linux public images listed in :ref:`Table 1 <en-us_topic_0085214115__en-us_topic_0058758453_table1572993710538>` support NIC multi-queue.

   .. note::

      -  Windows public images have not supported NIC multi-queue. If you enable NIC multi-queue for a Windows public image, starting an ECS created using such an image may be slow.

      -  You are advised to upgrade the kernel version of Linux ECSs to 2.6.35 or later. Otherwise, NIC multi-queue is not supported.

         Run the **uname -r** command to check the kernel version. If the version is earlier than 2.6.35, contact technical support to upgrade it.

.. _en-us_topic_0085214115__en-us_topic_0058758453_table1572993710538:

.. table:: **Table 1** KVM ECSs that support NIC multi-queue

   +---------+-------------------------------------------------------------+----------------+
   | OS      | Image                                                       | Supported By   |
   +=========+=============================================================+================+
   | Windows | Windows Server 2008 WEB R2 64bit                            | Private images |
   +---------+-------------------------------------------------------------+----------------+
   |         | Windows Server 2008 R2 Standard/Datacenter/Enterprise 64bit | Private images |
   +---------+-------------------------------------------------------------+----------------+
   |         | Windows Server 2012 R2 Standard/Datacenter 64bit            | Private images |
   +---------+-------------------------------------------------------------+----------------+
   |         | Windows Server 2016 Standard/Datacenter 64bit               | Private images |
   +---------+-------------------------------------------------------------+----------------+
   | Linux   | Ubuntu 14.04/16.04 Server 64bit                             | Public images  |
   +---------+-------------------------------------------------------------+----------------+
   |         | openSUSE 42.2 64bit                                         | Public images  |
   +---------+-------------------------------------------------------------+----------------+
   |         | SUSE Enterprise 12 SP1/SP2 64bit                            | Public images  |
   +---------+-------------------------------------------------------------+----------------+
   |         | CentOS 6.8/6.9/7.0/7.1/7.2/7.3/7.4/7.5/7.6 64bit            | Public images  |
   +---------+-------------------------------------------------------------+----------------+
   |         | Debian 8.0.0/8.8.0/8.9.0/9.0.0 64bit                        | Public images  |
   +---------+-------------------------------------------------------------+----------------+
   |         | Fedora 24/25 64bit                                          | Public images  |
   +---------+-------------------------------------------------------------+----------------+
   |         | EulerOS 2.2 64bit                                           | Public images  |
   +---------+-------------------------------------------------------------+----------------+

Operation Instructions
----------------------

Assume that an ECS has the required specifications and virtualization type.

-  If the ECS was created using a public image listed in :ref:`ECSs Supporting NIC Multi-Queue <en-us_topic_0085214115__en-us_topic_0058758453_section892862210138>`, NIC multi-queue has been enabled on the ECS by default. Therefore, you do not need to manually enable NIC multi-queue for it.
-  If the ECS was created using an external image file with an OS listed in :ref:`ECSs Supporting NIC Multi-Queue <en-us_topic_0085214115__en-us_topic_0058758453_section892862210138>`, perform the following operations to enable NIC multi-queue:

   #. :ref:`Register the external image file as a private image <en-us_topic_0085214115__en-us_topic_0058758453_section1659682611504>`.
   #. :ref:`Set NIC Multi-Queue for the Image <en-us_topic_0085214115__en-us_topic_0058758453_section1949113217282>`.
   #. :ref:`Create an ECS from the Private Image <en-us_topic_0085214115__en-us_topic_0058758453_section1841681225617>`.
   #. :ref:`Enable NIC Multi-Queue <en-us_topic_0085214115__en-us_topic_0058758453_section214227201118>`.

.. _en-us_topic_0085214115__en-us_topic_0058758453_section1659682611504:

Register the external image file as a private image
---------------------------------------------------

Register the external image file as a private image. For details, see :ref:`Registering an External Image File as a Private Image <en-us_topic_0030713193>`.

.. _en-us_topic_0085214115__en-us_topic_0058758453_section1949113217282:

Set NIC Multi-Queue for the Image
---------------------------------

Windows OSs have not commercially supported NIC multi-queue. If you enable NIC multi-queue in a Windows image, starting an ECS created using such an image may be slow.

Use either of the following methods to set NIC multi-queue.

**Method 1:**

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Compute**, click **Image Management Service**.

      The IMS console is displayed.

#. On the displayed **Private Images** page, locate the row that contains the target image and click **Modify** in the **Operation** column.
#. Set NIC multi-queue for the image.

**Method 2:**

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Compute**, click **Image Management Service**.

      The IMS console is displayed.

#. On the displayed **Private Images** page, click the name of the target image.
#. In the upper right corner of the displayed image details page, click **Modify**. In the displayed **Modify Image** dialog box, set NIC multi-queue for the image.

**Method 3:** Add **hw_vif_multiqueue_enabled** to the image using an API.

#. .. _en-us_topic_0085214115__en-us_topic_0058758453_en-us_topic_0085214115_li13762086162643:

   Obtain a token. For details, see `Token Authentication <https://docs.otc.t-systems.com/en-us/api/apiug/apig-en-api-180328003.html>`__.

#. Call an API to update image information. For details, see "Updating Image Information (Native OpenStack API)" in *Image Management Service API Reference*.

#. Add **X-Auth-Token** to the request header.

   The value of **X-Auth-Token** is the token obtained in step :ref:`1 <en-us_topic_0085214115__en-us_topic_0058758453_en-us_topic_0085214115_li13762086162643>`.

#. Add **Content-Type** to the request header.

   The value of **Content-Type** is **application/openstack-images-v2.1-json-patch**.

   The request URI is in the following format:

   PATCH /v2/images/{*image_id*}

   The request body is as follows:

   .. code-block::

      [
               {
                "op":"add",
                "path":"/hw_vif_multiqueue_enabled",
                "value": "true"
               }
       ]

   :ref:`Figure 1 <en-us_topic_0085214115__en-us_topic_0058758453_en-us_topic_0085214115_fig3215821216479>` shows an example request body for setting NIC multi-queue.

   .. _en-us_topic_0085214115__en-us_topic_0058758453_en-us_topic_0085214115_fig3215821216479:

   .. figure:: /_static/images/en-us_image_0196045691.png
      :alt: **Figure 1** Example request body


      **Figure 1** Example request body

.. _en-us_topic_0085214115__en-us_topic_0058758453_section1841681225617:

Create an ECS from the Private Image
------------------------------------

Use the registered private image to create an ECS. For details, see *Elastic Cloud Server User Guide*. Note the following when setting the parameters:

-  **Region**: Select the region where the private image is located.
-  **Image**: Select **Private image** and then the desired image from the drop-down list.

.. _en-us_topic_0085214115__en-us_topic_0058758453_section214227201118:

Enable NIC Multi-Queue
----------------------

KVM ECSs running Windows use private images to support NIC multi-queue.

For Linux ECSs, which run CentOS 7.4 as an example, perform the following operations to enable NIC multi-queue:

#. Enable NIC multi-queue.

   a. Log in to the ECS.

   b. Run the following command to obtain the number of queues supported by the NIC and the number of queues with NIC multi-queue enabled:

      **ethtool -l** *NIC*

   c. Run the following command to configure the number of queues used by the NIC:

      **ethtool -L** *NIC* **combined** *Number of queues*

   Example:

   .. code-block:: console

      [root@localhost ~]# ethtool -l eth0  #View the number of queues used by NIC eth0.
      Channel parameters for eth0:
      Pre-set maximums:
      RX:               0
      TX:               0
      Other:                  0
      Combined: 4  #Indicates that a maximum of four queues can be enabled for the NIC.
      Current hardware settings:
      RX:               0
      TX:               0
      Other:                  0
      Combined: 1 #Indicates that one queue has been enabled.

      [root@localhost ~]# ethtool -L eth0 combined 4 #Enable four queues on NIC eth0.

#. (Optional) Enable irqbalance so that the system automatically allocates NIC interruptions to multiple vCPUs.

   a. Run the following command to enable irqbalance:

      **service irqbalance start**

   b. Run the following command to view the irqbalance status:

      **service irqbalance status**

      If the **Active** value in the command output contains **active (running)**, irqbalance has been enabled.


      .. figure:: /_static/images/en-us_image_0196045692.png
         :alt: **Figure 2** Enabled irqbalance


         **Figure 2** Enabled irqbalance

#. (Optional) Enable interrupt binding.

   Enabling irqbalance allows the system to automatically allocate NIC interruptions, improving network performance. If the improved network performance fails to meet your expectations, manually configure interrupt affinity on the target ECS.

   The detailed operations are as follows:

   Run the following script so that each ECS vCPU responds the interrupt requests initialized by one queue. That is, one queue corresponds to one interrupt, and one interrupt binds to one vCPU.

   .. code-block::

      #!/bin/bash
      service irqbalance stop

      eth_dirs=$(ls -d /sys/class/net/eth*)
      if [ $? -ne 0 ];then
          echo "Failed to find eth*  , sleep 30" >> $ecs_network_log
          sleep 30
          eth_dirs=$(ls -d /sys/class/net/eth*)
      fi

      for eth in $eth_dirs
      do
          cur_eth=$(basename $eth)
          cpu_count=`cat /proc/cpuinfo| grep "processor"| wc -l`
          virtio_name=$(ls -l /sys/class/net/"$cur_eth"/device/driver/ | grep pci |awk {'print $9'})

          affinity_cpu=0
          virtio_input="$virtio_name""-input"
          irqs_in=$(grep "$virtio_input" /proc/interrupts | awk -F ":" '{print $1}')
          for irq in ${irqs_in[*]}
          do
              echo $((affinity_cpu%cpu_count)) > /proc/irq/"$irq"/smp_affinity_list
              affinity_cpu=$[affinity_cpu+2]
          done

          affinity_cpu=1
          virtio_output="$virtio_name""-output"
          irqs_out=$(grep "$virtio_output" /proc/interrupts | awk -F ":" '{print $1}')
          for irq in ${irqs_out[*]}
          do
              echo $((affinity_cpu%cpu_count)) > /proc/irq/"$irq"/smp_affinity_list
              affinity_cpu=$[affinity_cpu+2]
          done
      done

#. (Optional) Enable XPS and RPS.

   XPS allows the system with NIC multi-queue enabled to select a queue by vCPU when sending a data packet.

   .. code-block::

      #!/bin/bash
      # enable XPS feature
      cpu_count=$(grep -c processor /proc/cpuinfo)
      dec2hex(){
        echo $(printf "%x" $1)
      }
      eth_dirs=$(ls -d /sys/class/net/eth*)
      if [ $? -ne 0 ];then
          echo "Failed to find eth* , sleep 30" >> $ecs_network_log
          sleep 30
          eth_dirs=$(ls -d /sys/class/net/eth*)
      fi
      for eth in $eth_dirs
      do
          cpu_id=1
          cur_eth=$(basename $eth)
          cur_q_num=$(ethtool -l $cur_eth | grep -iA5 current | grep -i combined | awk {'print $2'})
          for((i=0;i<cur_q_num;i++))
          do
              if [ $i -eq $ cpu_count ];then
                  cpu_id=1
              fi
              xps_file="/sys/class/net/${cur_eth}/queues/tx-$i/xps_cpus"
              rps_file="/sys/class/net/${cur_eth}/queues/rx-$i/rps_cpus"
              cpuset=$(dec2hex "$cpu_id")
              echo $cpuset > $xps_file
              echo $cpuset > $rps_file
              let cpu_id=cpu_id*2
          done
      done
