:original_name: en-us_topic_0081795392.html

.. _en-us_topic_0081795392:

(Optional) Installing Special Windows Drivers
=============================================

Scenarios
---------

Before using some types of ECSs to create private images, you need to install special drivers on the ECSs.

GPU Driver
----------

If you want to use the created private image to create GPU-accelerated ECSs, install a proper GPU driver for the image to enable GPU acceleration. There are two types of NVIDIA Tesla GPU drivers for GPU-accelerated ECSs, Tesla and GRID/vGPU drivers.

-  To use graphics acceleration, such as OpenGL, DirectX, or Vulcan, install the GRID/vGPU driver and separately configure a GRID license. The GRID/vGPU driver with a vDWS license also supports CUDA for both computing and graphics acceleration.
-  To use NVIDIA CUDA computing acceleration, install the Tesla driver.

Related Operations
------------------

To install a GRID driver on a GPU-accelerated ECS, see `Manually Installing a GRID Driver on a GPU-accelerated ECS <https://docs.otc.t-systems.com/elastic-cloud-server/umn/instances/managing_gpu_drivers_of_gpu-accelerated_ecss/manually_installing_a_grid_driver_on_a_gpu-accelerated_ecs.html#en-us-topic-0149610914>`__.

To install a Tesla driver and CUDA toolkit on a GPU-accelerated ECS, see `Manually Installing a Tesla Driver on a GPU-accelerated ECS <https://docs.otc.t-systems.com/elastic-cloud-server/umn/instances/managing_gpu_drivers_of_gpu-accelerated_ecss/manually_installing_a_tesla_driver_on_a_gpu-accelerated_ecs.html>`__.
