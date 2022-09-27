:original_name: en-us_topic_0093842586.html

.. _en-us_topic_0093842586:

How Do I Install the NVIDIA Driver on a P1 ECS?
===============================================

Prerequisites
-------------

-  The target ECS has had an EIP bound.
-  You have obtained the driver installation package required for an OS. For details, see :ref:`Table 1 <en-us_topic_0093842586__en-us_topic_0093345963_table121731221584>`.

.. _en-us_topic_0093842586__en-us_topic_0093345963_table121731221584:

.. table:: **Table 1** NVIDIA drivers

   +--------------+---------------------------------------------------------------------+---------------------------------------------------------------------------------------------------+
   | OS           | Driver                                                              | How to Obtain                                                                                     |
   +==============+=====================================================================+===================================================================================================+
   | Ubuntu 16.04 | GPU driver installation package **NVIDIA-Linux-x86_64-375.66.run**  | http://www.nvidia.com/download/driverResults.aspx/118955/en-us                                    |
   +--------------+---------------------------------------------------------------------+---------------------------------------------------------------------------------------------------+
   |              | CUDA Toolkit installation package **cuda_8.0.61_375.26_linux.run**  | https://developer.nvidia.com/compute/cuda/8.0/Prod2/local_installers/cuda_8.0.61_375.26_linux-run |
   +--------------+---------------------------------------------------------------------+---------------------------------------------------------------------------------------------------+
   | CentOS 7.4   | GPU driver installation package **NVIDIA-Linux-x86_64-375.66.run**  | http://www.nvidia.com/download/driverResults.aspx/118955/en-us                                    |
   +--------------+---------------------------------------------------------------------+---------------------------------------------------------------------------------------------------+
   |              | CUDA Toolkit installation package **cuda_8.0.61_375.26_linux.run**  | https://developer.nvidia.com/compute/cuda/8.0/Prod2/local_installers/cuda_8.0.61_375.26_linux-run |
   +--------------+---------------------------------------------------------------------+---------------------------------------------------------------------------------------------------+
   | Debian 9.0   | GPU driver installation package **NVIDIA-Linux-x86_64-384.81.run**  | http://www.nvidia.com/download/driverResults.aspx/124722/en-us                                    |
   +--------------+---------------------------------------------------------------------+---------------------------------------------------------------------------------------------------+
   |              | CUDA Toolkit installation package **cuda_9.0.176_384.81_linux.run** | https://developer.nvidia.com/compute/cuda/9.0/Prod/local_installers/cuda_9.0.176_384.81_linux-run |
   +--------------+---------------------------------------------------------------------+---------------------------------------------------------------------------------------------------+

Procedure
---------

The procedure for installing the NVIDIA driver varies according to the OS.

-  **Ubuntu 16.04 64bit**

#. Log in to the target ECS and run the following command to switch to user **root**:

   **sudo su**

#. (Optional) Install the GCC and g++ software.

   Perform this step only if the GCC and g++ software has not been installed.

   **apt-get install gcc**

   **apt-get install g++**

   **apt-get install make**

#. (Optional) Disable the Nouveau driver.

   Perform this step if the Nouveau driver has been installed on the target ECS. This prevents conflict with the NVIDIA driver installation.

   a. Run the following command to check whether the Nouveau driver is running on the target ECS:

      **lsmod \| grep nouveau**

      -  If yes, go to :ref:`3.b <en-us_topic_0093842586__en-us_topic_0093345963_li2691446193813>`.
      -  If no, go to :ref:`4 <en-us_topic_0093842586__en-us_topic_0093345963_li7971016194610>`.

   b. .. _en-us_topic_0093842586__en-us_topic_0093345963_li2691446193813:

      Add the following statement to the end of the **/etc/modprobe.d/blacklist.conf** file:

      **blacklist nouveau**

      **options nouveau modeset=0**

   c. Run the following commands to back up and create an initramfs application:

      **mv /boot/initramfs-$(uname -r).img /boot/initramfs-$(uname -r).img.bak**

      **update-initramfs -u**

   d. Run the following command to restart the ECS:

      **reboot**

#. .. _en-us_topic_0093842586__en-us_topic_0093345963_li7971016194610:

   (Optional) Disable the X service.

   If the ECS has been logged in using the GUI, disable the X service before installing the NVIDIA driver.

   a. Run the following command to switch to multi-user mode:

      **systemctl set-default multi-user.target**

   b. Run the following command to restart the ECS:

      **reboot**

#. (Optional) Install the GPU driver.

   You can either use the GPU driver provided in the CUDA Toolkit installation package or download the required GPU driver. Unless otherwise specified, you are advised to install GPU driver **NVIDIA-Linux-x86_64-375.66.run**, which has been fully verified.

   a. Upload the GPU driver installation package **NVIDIA-Linux-x86_64-xxx.yy.run** to the **/tmp** directory of the ECS.

      To download the GPU driver, log in at http://www.nvidia.com/Download/index.aspx?lang=en.


      .. figure:: /_static/images/en-us_image_0099872706.png
         :alt: **Figure 1** Downloading the GPU driver


         **Figure 1** Downloading the GPU driver

   b. Run the following command to install the GPU driver:

      **sh ./NVIDIA-Linux-x86_64-xxx.yy.run**

   c. Run the following command to delete the installation package:

      **rm -f NVIDIA-Linux-x86_64-xxx.yy.run**

#. Install the CUDA Toolkit.

   Unless otherwise specified, you are advised to install CUDA Toolkit **cuda_8.0.61_375.26_linux.run**, which has been fully verified.

   a. Upload the CUDA Toolkit installation package **cuda\_\ a.b.cc\ \_\ xxx.yy\ \_linux.run** to the **/tmp** directory of the ECS.

      To download the CUDA Toolkit, log in at https://developer.nvidia.com/cuda-downloads.

   b. Run the following command to change the permission:

      **chmod +x cuda\_\ a.b.cc\ \_\ xxx.yy\ \_linux.run**

   c. Run the following command to install the CUDA Toolkit:

      **./cuda\_\ a.b.cc\ \_\ xxx.yy\ \_linux.run -toolkit -samples -silent -override --tmpdir=/tmp/**

   d. Run the following command to delete the installation package:

      **rm -f cuda\_\ a.b.cc\ \_\ xxx.yy\ \_linux.run**

   e. Run the following commands to check whether the installation is successful:

      **cd /usr/local/cuda/samples/1_Utilities/deviceQueryDrv/**

      **make**

      **./deviceQueryDrv**

      If the terminal display contains "Result = PASS", both CUDA Toolkit and GPU driver have been installed.

      .. code-block::

         ./deviceQueryDrv Starting...

          CUDA Device Query (Driver API) statically linked version
          Detected 1 CUDA Capable device(s)

          Device 0: "Tesla P100-PCIE-16GB"
            CUDA Driver Version:                           8.0
            CUDA Capability Major/Minor version number:    6.0
            Total amount of global memory:                 16276 MBytes (17066885120 bytes)
            (56) Multiprocessors, ( 64) CUDA Cores/MP:     3584 CUDA Cores
            GPU Max Clock rate:                            1329 MHz (1.33 GHz)
            Memory Clock rate:                             715 Mhz
            Memory Bus Width:                              4096-bit
            L2 Cache Size:                                 4194304 bytes
            Max Texture Dimension Sizes                    1D=(131072) 2D=(131072, 65536) 3D=(16384, 16384, 16384)
            Maximum Layered 1D Texture Size, (num) layers  1D=(32768), 2048 layers
            Maximum Layered 2D Texture Size, (num) layers  2D=(32768, 32768), 2048 layers
            Total amount of constant memory:               65536 bytes
            Total amount of shared memory per block:       49152 bytes
            Total number of registers available per block: 65536
            Warp size:                                     32
            Maximum number of threads per multiprocessor:  2048
            Maximum number of threads per block:           1024
            Max dimension size of a thread block (x,y,z): (1024, 1024, 64)
            Max dimension size of a grid size (x,y,z):    (2147483647, 65535, 65535)
            Texture alignment:                             512 bytes
            Maximum memory pitch:                          2147483647 bytes
            Concurrent copy and kernel execution:          Yes with 2 copy engine(s)
            Run time limit on kernels:                     No
            Integrated GPU sharing Host Memory:            No
            Support host page-locked memory mapping:       Yes
            Concurrent kernel execution:                   Yes
            Alignment requirement for Surfaces:            Yes
            Device has ECC support:                        Enabled
            Device supports Unified Addressing (UVA):      Yes
            Device PCI Domain ID / Bus ID / location ID:   0 / 0 / 6
            Compute Mode:
               < Default (multiple host threads can use ::cudaSetDevice() with device simultaneously) >
          Result = PASS

-  **CentOS 7.4**

#. Log in to the target ECS and run the following command to switch to user **root**:

   **sudo su**

#. (Optional) Install GCC, g++, and kernel-devel.

   Perform this step only if GCC, g++, and kernel-devel have not been installed.

   **yum install gcc**

   **yum install gcc-c++**

   **yum install make**

   **yum install kernel-devel-`uname -r\`**

#. (Optional) Disable the Nouveau driver.

   Perform this step if the Nouveau driver has been installed on the target ECS. This prevents conflict with the NVIDIA driver installation.

   a. Run the following command to check whether the Nouveau driver is running on the target ECS:

      **lsmod \| grep nouveau**

      -  If yes, go to :ref:`3.b <en-us_topic_0093842586__en-us_topic_0093345963_li17783295461>`.
      -  If no, go to :ref:`4 <en-us_topic_0093842586__en-us_topic_0093345963_li7971016194610>`.

   b. .. _en-us_topic_0093842586__en-us_topic_0093345963_li17783295461:

      Add the following statement to the end of the **/etc/modprobe.d/blacklist.conf** file:

      **blacklist nouveau**

   c. Run the following commands to back up and create an initramfs application:

      **mv /boot/initramfs-$(uname -r).img /boot/initramfs-$(uname -r).img.bak**

      **dracut -v /boot/initramfs-$(uname -r).img $(uname -r)**

   d. Run the following command to restart the ECS:

      **reboot**

#. (Optional) Disable the X service.

   If the ECS has been logged in using the GUI, disable the X service before installing the NVIDIA driver.

   a. Run the following command to switch to multi-user mode:

      **systemctl set-default multi-user.target**

   b. Run the following command to restart the ECS:

      **reboot**

#. (Optional) Install the GPU driver.

   You can either use the GPU driver provided in the CUDA Toolkit installation package or download the required GPU driver. Unless otherwise specified, you are advised to install GPU driver **NVIDIA-Linux-x86_64-375.66.run**, which has been fully verified.

   a. Upload the GPU driver installation package **NVIDIA-Linux-x86_64-xxx.yy.run** to the **/tmp** directory of the ECS.

      To download the GPU driver, log in at http://www.nvidia.com/Download/index.aspx?lang=en.


      .. figure:: /_static/images/en-us_image_0099872707.png
         :alt: **Figure 2** Downloading the driver installation package


         **Figure 2** Downloading the driver installation package

   b. Run the following command to install the GPU driver:

      **sh ./NVIDIA-Linux-x86_64-xxx.yy.run**

   c. Run the following command to delete the installation package:

      **rm -f NVIDIA-Linux-x86_64-xxx.yy.run**

#. Install the CUDA Toolkit.

   Unless otherwise specified, you are advised to install CUDA Toolkit **cuda_8.0.61_375.26_linux.run**, which has been fully verified.

   a. Upload the CUDA Toolkit installation package **cuda\_\ a.b.cc\ \_\ xxx.yy\ \_linux.run** to the **/tmp** directory of the ECS.

      To download the CUDA Toolkit, log in at https://developer.nvidia.com/cuda-downloads.

   b. Run the following command to change the permission:

      **chmod +x cuda\_\ a.b.cc\ \_\ xxx.yy\ \_linux.run**

   c. Run the following command to install the CUDA Toolkit:

      **./cuda\_\ a.b.cc\ \_\ xxx.yy\ \_linux.run -toolkit -samples -silent -override --tmpdir=/tmp/**

   d. Run the following command to delete the installation package:

      **rm -f cuda\_\ a.b.cc\ \_\ xxx.yy\ \_linux.run**

   e. Run the following commands to check whether the installation is successful:

      **cd /usr/local/cuda/samples/1_Utilities/deviceQueryDrv/**

      **make**

      **./deviceQueryDrv**

      If the terminal display contains "Result = PASS", both CUDA Toolkit and GPU driver have been installed.

      .. code-block::

         ./deviceQueryDrv Starting...

          CUDA Device Query (Driver API) statically linked version
          Detected 1 CUDA Capable device(s)

          Device 0: "Tesla P100-PCIE-16GB"
            CUDA Driver Version:                           8.0
            CUDA Capability Major/Minor version number:    6.0
            Total amount of global memory:                 16276 MBytes (17066885120 bytes)
            (56) Multiprocessors, ( 64) CUDA Cores/MP:     3584 CUDA Cores
            GPU Max Clock rate:                            1329 MHz (1.33 GHz)
            Memory Clock rate:                             715 Mhz
            Memory Bus Width:                              4096-bit
            L2 Cache Size:                                 4194304 bytes
            Max Texture Dimension Sizes                    1D=(131072) 2D=(131072, 65536) 3D=(16384, 16384, 16384)
            Maximum Layered 1D Texture Size, (num) layers  1D=(32768), 2048 layers
            Maximum Layered 2D Texture Size, (num) layers  2D=(32768, 32768), 2048 layers
            Total amount of constant memory:               65536 bytes
            Total amount of shared memory per block:       49152 bytes
            Total number of registers available per block: 65536
            Warp size:                                     32
            Maximum number of threads per multiprocessor:  2048
            Maximum number of threads per block:           1024
            Max dimension size of a thread block (x,y,z): (1024, 1024, 64)
            Max dimension size of a grid size (x,y,z):    (2147483647, 65535, 65535)
            Texture alignment:                             512 bytes
            Maximum memory pitch:                          2147483647 bytes
            Concurrent copy and kernel execution:          Yes with 2 copy engine(s)
            Run time limit on kernels:                     No
            Integrated GPU sharing Host Memory:            No
            Support host page-locked memory mapping:       Yes
            Concurrent kernel execution:                   Yes
            Alignment requirement for Surfaces:            Yes
            Device has ECC support:                        Enabled
            Device supports Unified Addressing (UVA):      Yes
            Device PCI Domain ID / Bus ID / location ID:   0 / 0 / 6
            Compute Mode:
               < Default (multiple host threads can use ::cudaSetDevice() with device simultaneously) >
          Result = PASS

-  **Debian 9.0 OS**

#. Log in to the target ECS and run the following command to switch to user **root**:

   **sudo su**

#. (Optional) Install the dependency software GCC and g++ of the NVIDIA driver.

   Perform this step only if the GCC and g++ software has not been installed.

   **apt-get install gcc**

   **apt-get install g++**

   **apt-get install make**

   **apt-get install linux-headers-$(uname -r)**

#. (Optional) Disable the Nouveau driver.

   Perform this step if the Nouveau driver has been installed on the target ECS. This prevents conflict with the NVIDIA driver installation.

   a. Run the following command to check whether the Nouveau driver is running on the target ECS:

      **lsmod \| grep nouveau**

      -  If yes, go to :ref:`3.b <en-us_topic_0093842586__en-us_topic_0093345963_li948211510131>`.
      -  If no, go to :ref:`4 <en-us_topic_0093842586__en-us_topic_0093345963_li151251998136>`.

   b. .. _en-us_topic_0093842586__en-us_topic_0093345963_li948211510131:

      Add the following statement to the end of the **/etc/modprobe.d/blacklist.conf** file:

      **blacklist nouveau**

      **options nouveau modeset=0**

   c. Run the following commands to back up and create an initramfs application:

      **mv /boot/initramfs-$(uname -r).img /boot/initramfs-$(uname -r).img.bak**

      **update-initramfs -u**

   d. Run the following command to restart the ECS:

      **reboot**

#. .. _en-us_topic_0093842586__en-us_topic_0093345963_li151251998136:

   (Optional) Disable the X service.

   If the ECS has been logged in using the GUI, disable the X service before installing the NVIDIA driver.

   a. Run the following command to switch to multi-user mode:

      **systemctl set-default multi-user.target**

   b. Run the following command to restart the ECS:

      **reboot**

#. (Optional) Install the GPU driver.

   You can either use the GPU driver provided in the CUDA Toolkit installation package or download the required GPU driver. Unless otherwise specified, you are advised to install GPU driver **NVIDIA-Linux-x86_64-384.81.run**, which has been fully verified.

   a. Upload the GPU driver installation package **NVIDIA-Linux-x86_64-xxx.yy.run** to the **/tmp** directory of the ECS.

      To download the GPU driver, log in at http://www.nvidia.com/Download/index.aspx?lang=en.


      .. figure:: /_static/images/en-us_image_0099872708.png
         :alt: **Figure 3** Downloading the GPU driver


         **Figure 3** Downloading the GPU driver

   b. Run the following command to install the GPU driver:

      **sh ./NVIDIA-Linux-x86_64-xxx.yy.run**

   c. Run the following command to delete the installation package:

      **rm -f NVIDIA-Linux-x86_64-xxx.yy.run**

#. Install the CUDA Toolkit.

   The CUDA Toolkit version required by Debian 9.0 GCC must be 9.0 or later. Unless otherwise specified, you are advised to install CUDA Toolkit **cuda_9.0.176_384.81_linux.run**, which has been fully verified.

   a. Upload the CUDA Toolkit installation package **cuda\_\ a.b.cc\ \_\ xxx.yy\ \_linux.run** to the **/tmp** directory of the ECS.

      To download the CUDA Toolkit, log in at https://developer.nvidia.com/cuda-downloads.

   b. Run the following command to change the permission:

      **chmod +x cuda\_\ a.b.cc\ \_\ xxx.yy\ \_linux.run**

   c. Run the following command to install the CUDA Toolkit:

      **./cuda\_\ a.b.cc\ \_\ xxx.yy\ \_linux.run -toolkit -samples -silent -override --tmpdir=/tmp/**

   d. Run the following command to delete the installation package:

      **rm -f cuda\_\ a.b.cc\ \_\ xxx.yy\ \_linux.run**

   e. Run the following commands to check whether the installation is successful:

      **cd /usr/local/cuda/samples/1_Utilities/deviceQueryDrv/**

      **make**

      **./deviceQueryDrv**

      If the terminal display contains "Result = PASS", both CUDA Toolkit and GPU driver have been installed.

      .. code-block::

         ./deviceQueryDrv Starting...

         CUDA Device Query (Driver API) statically linked version
         Detected 1 CUDA Capable device(s)

         Device 0: "Tesla P100-PCIE-16GB"
           CUDA Driver Version:                           9.0
           CUDA Capability Major/Minor version number:    6.0
           Total amount of global memory:                 16276 MBytes (17066885120 bytes)
           (56) Multiprocessors, ( 64) CUDA Cores/MP:     3584 CUDA Cores
           GPU Max Clock rate:                            1329 MHz (1.33 GHz)
           Memory Clock rate:                             715 Mhz
           Memory Bus Width:                              4096-bit
           L2 Cache Size:                                 4194304 bytes
           Max Texture Dimension Sizes                    1D=(131072) 2D=(131072, 65536) 3D=(16384, 16384, 16384)
           Maximum Layered 1D Texture Size, (num) layers  1D=(32768), 2048 layers
           Maximum Layered 2D Texture Size, (num) layers  2D=(32768, 32768), 2048 layers
           Total amount of constant memory:               65536 bytes
           Total amount of shared memory per block:       49152 bytes
           Total number of registers available per block: 65536
           Warp size:                                     32
           Maximum number of threads per multiprocessor:  2048
           Maximum number of threads per block:           1024
           Max dimension size of a thread block (x,y,z): (1024, 1024, 64)
           Max dimension size of a grid size (x,y,z):    (2147483647, 65535, 65535)
           Texture alignment:                             512 bytes
           Maximum memory pitch:                          2147483647 bytes
           Concurrent copy and kernel execution:          Yes with 2 copy engine(s)
           Run time limit on kernels:                     No
           Integrated GPU sharing Host Memory:            No
           Support host page-locked memory mapping:       Yes
           Concurrent kernel execution:                   Yes
           Alignment requirement for Surfaces:            Yes
           Device has ECC support:                        Enabled
           Device supports Unified Addressing (UVA):      Yes
           Supports Cooperative Kernel Launch:            Yes
           Supports MultiDevice Co-op Kernel Launch:      Yes
           Device PCI Domain ID / Bus ID / location ID:   0 / 0 / 6
           Compute Mode:
              < Default (multiple host threads can use ::cudaSetDevice() with device simultaneously) >
         Result = PASS
