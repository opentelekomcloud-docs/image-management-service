:original_name: en-us_topic_0082002007.html

.. _en-us_topic_0082002007:

Installing Special Linux Drivers
================================

Scenarios
---------

Before using some types of ECSs to create private images, you need to install special drivers on the ECSs.

NVIDIA Driver
-------------

If you want to use the private image to create P1 ECSs, install the NVIDIA driver for the image to enable computing acceleration. For details, see :ref:`How Do I Install the NVIDIA Driver on a P1 ECS? <en-us_topic_0093842586>`

InfiniBand NIC Driver
---------------------

#. If you want to use the private image to create H2 ECSs, install the InfiniBand NIC driver for the image. Download the required version (4.2-1.0.0.0) of InfiniBand NIC driver from the official website and install the driver by following the instructions provided by Mellanox.

   -  InfiniBand NIC: **Mellanox Technologies ConnectX-4 Infiniband HBA (MCX455A-ECAT)**
   -  Mellanox official website: http://www.mellanox.com/
   -  NIC driver download path: https://network.nvidia.com/products/infiniband-drivers/linux/mlnx_ofed/
   -  H2 ECSs: `High-Performance Computing ECSs <https://docs.otc.t-systems.com/en-us/usermanual/ecs/en-us_topic_0035470100.html>`__

#. If you want to use the private image to create HL1 ECSs, install the InfiniBand NIC driver for the image. Download the required version (4.2-1.0.0.0) of InfiniBand NIC driver from the official website and install the driver by following the instructions provided by Mellanox.

   -  InfiniBand NIC: **Mellanox Technologies ConnectX-4 Infiniband HBA (MCX455A-ECAT)**
   -  Mellanox official website: http://www.mellanox.com/
   -  HL1 ECS: `High-Performance Computing ECSs <https://docs.otc.t-systems.com/en-us/usermanual/ecs/en-us_topic_0035470100.html>`__
