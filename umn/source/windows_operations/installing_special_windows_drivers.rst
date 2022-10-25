:original_name: en-us_topic_0081795392.html

.. _en-us_topic_0081795392:

Installing Special Windows Drivers
==================================

Scenarios
---------

Before using some types of ECSs to create private images, you need to install special drivers on the ECSs.

GPU Driver
----------

If you want to use the created private image to create GPU-accelerated ECSs, install a proper GPU driver for the image to enable GPU acceleration. There are two types of NVIDIA Tesla GPU drivers for GPU-accelerated ECSs, Tesla and GRID/vGPU drivers.

-  To use graphics acceleration, such as OpenGL, DirectX, or Vulcan, install the GRID/vGPU driver and separately configure a GRID license. The GRID/vGPU driver with a vDWS license also supports CUDA for both computing and graphics acceleration.
-  To use NVIDIA CUDA computing acceleration, install the Tesla driver.

.. table:: **Table 1** Installing the GRID driver

   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ECS Type                          | How to Install the Driver                                                                                                                                                                                                          |
   +===================================+====================================================================================================================================================================================================================================+
   | G1                                | For details, see **Downloading GRID Driver and Software License Packages** in `Installing a GRID Driver on a GPU-accelerated ECS <https://docs.otc.t-systems.com/en-us/usermanual/ecs/en-us_topic_0149610914.html>`__.             |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | G2                                | Log in at http://www.nvidia.com/Download/index.aspx?lang=en-us. You are advised to select the latest CUDA Toolkit version.                                                                                                         |
   |                                   |                                                                                                                                                                                                                                    |
   |                                   | .. important::                                                                                                                                                                                                                     |
   |                                   |                                                                                                                                                                                                                                    |
   |                                   |    NOTICE:                                                                                                                                                                                                                         |
   |                                   |    After the GPU driver is installed, run the following command to switch the GPU working mode and restart the ECS (for example, the GPU driver is installed in **C:\\Program Files\\NVIDIA Corporation\\NVSMI\\nvidia-smi.exe**): |
   |                                   |                                                                                                                                                                                                                                    |
   |                                   |    **"C:\\Program Files\\NVIDIA Corporation\\NVSMI\\nvidia-smi.exe" -dm 0**                                                                                                                                                        |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

SR-IOV NIC Driver
-----------------

If you want to use the created private image to create G2 ECSs, install the SR-IOV NIC driver for the image to improve performance and scalability.

To download the SR-IOV driver, log in at `https://downloadcenter.intel.com/search?keyword=Intel++Ethernet+Connections+CD <https://downloadcenter.intel.com/search?keyword=Intel%2B%2BEthernet%2BConnections%2BCD>`__. You are advised to select version 20.4.1 or later.

If error "No Intel adapter found" occurs during the driver installation, refer to :ref:`What Do I Do If a Windows 7 ECS Equipped with an Intel 82599 NIC Reports an Error in SR-IOV Scenarios? <en-us_topic_0081802526>` for troubleshooting.
