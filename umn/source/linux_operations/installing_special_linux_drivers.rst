:original_name: en-us_topic_0082002007.html

.. _en-us_topic_0082002007:

Installing Special Linux Drivers
================================

Before using a private image to create GPU-accelerated ECSs, install a GPU driver for the image.

There are two types of GPU drivers: GRID and Tesla.

-  To use graphics acceleration, such as OpenGL, DirectX, or Vulkan, install a GRID driver and separately purchase and configure a GRID license. The GRID driver with a vDWS license also supports CUDA for both computing and graphics acceleration.

   -  A graphics-accelerated (G series) ECS created from a Linux public image does not have a GRID driver installed by default. To install a GRID driver, see `Installing a GRID Driver on a GPU-accelerated ECS <https://docs.otc.t-systems.com/elastic-cloud-server/umn/instances/optional_installing_a_driver_and_toolkit/installing_a_grid_driver_on_a_gpu-accelerated_ecs.html>`__.
   -  To install a GRID driver on a GPU-accelerated ECS created from a private image, see `Installing a GRID Driver on a GPU-accelerated ECS <https://docs.otc.t-systems.com/elastic-cloud-server/umn/instances/optional_installing_a_driver_and_toolkit/installing_a_grid_driver_on_a_gpu-accelerated_ecs.html>`__.

-  To use computing acceleration, install a Tesla driver.

   -  A computing-accelerated (P series) ECS created from a Linux public image does not have a Tesla driver installed by default. To install a Tesla driver, see `Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <https://docs.otc.t-systems.com/elastic-cloud-server/umn/instances/optional_installing_a_driver_and_toolkit/installing_a_tesla_driver_and_cuda_toolkit_on_a_gpu-accelerated_ecs.html>`__.
   -  To install a Tesla driver on a GPU-accelerated ECS created from a private image, see `Installing a Tesla Driver and CUDA Toolkit on a GPU-accelerated ECS <https://docs.otc.t-systems.com/elastic-cloud-server/umn/instances/optional_installing_a_driver_and_toolkit/installing_a_tesla_driver_and_cuda_toolkit_on_a_gpu-accelerated_ecs.html>`__.

.. table:: **Table 1** Acceleration supported by GPU drivers

   +--------+--------------+-----------+---------------+---------------+---------------+------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | Driver | License      | CUDA      | OpenGL        | DirectX       | Vulkan        | Application Scenario                                       | Description                                                                                                                        |
   +========+==============+===========+===============+===============+===============+============================================================+====================================================================================================================================+
   | GRID   | Required     | Supported | Supported     | Supported     | Supported     | 3D rendering, graphics workstation, and game acceleration  | The GRID driver must be paid and requires a license to accelerate graphics and image applications.                                 |
   +--------+--------------+-----------+---------------+---------------+---------------+------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | Tesla  | Not required | Supported | Not supported | Not supported | Not supported | Scientific computing, deep learning training and inference | The Tesla driver is downloaded free of charge and usually used with NVIDIA CUDA SDKs to accelerate general-computing applications. |
   +--------+--------------+-----------+---------------+---------------+---------------+------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------+
