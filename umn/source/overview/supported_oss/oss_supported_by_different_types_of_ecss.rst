:original_name: en-us_topic_0030713142.html

.. _en-us_topic_0030713142:

OSs Supported by Different Types of ECSs
========================================

This section describes the OSs supported by different types of ECSs.

x86 ECSs
--------

-  :ref:`Table 1 <en-us_topic_0030713142__table124398125555>` lists the OSs supported by the following ECSs:

   General computing S9, S7n, S2, S3, X1

   Dedicated general-purpose C7n, C7t, C3, C4, X1e, C9

   Memory-optimized M7n, M3, M4, M9

   Disk-intensive D2

   Ultra-high I/O I3, I3m

-  :ref:`Table 2 <en-us_topic_0030713142__table14709182711556>` lists the OSs supported by large-memory ECSs (E6 and E3).

-  :ref:`Table 3 <en-us_topic_0030713142__table3436728145315>` lists the OSs supported by GPU-accelerated ECSs (G7v, G7, G6, P5s, P3, P2s, P2v, Pi2, and Pi5e).

.. note::

   -  It is recommended that you use the official OS release versions. Do not tailor or customize the release versions, or problems may occur.
   -  OS vendors do not always update OS release versions regularly. Some versions are no longer maintained, and these deprecated versions no longer receive security patches. Ensure that you read the update notifications from OS vendors and update your OS so that it runs properly.

.. _en-us_topic_0030713142__table124398125555:

.. table:: **Table 1** Supported OS versions

   +-----------------------------------+---------------------------------------------------+
   | OS                                | Version                                           |
   +===================================+===================================================+
   | AlmaLinux                         | -  AlmaLinux 9 64bit                              |
   |                                   | -  AlmaLinux 8 64bit                              |
   +-----------------------------------+---------------------------------------------------+
   | CentOS                            | CentOS Stream 9 64bit                             |
   +-----------------------------------+---------------------------------------------------+
   | Debian                            | -  Debian GNU/Linux 13 64bit                      |
   |                                   | -  Debian GNU/Linux 12 64bit                      |
   +-----------------------------------+---------------------------------------------------+
   | EulerOS                           | -  EulerOS 2.10 64bit                             |
   |                                   | -  Cloud-EulerOS 2.0                              |
   +-----------------------------------+---------------------------------------------------+
   | Fedora                            | -  Fedora Linux 43 64bit                          |
   |                                   | -  Fedora Linux 41 64bit                          |
   +-----------------------------------+---------------------------------------------------+
   | openSUSE                          | openSUSE Leap 16.0 64bit                          |
   +-----------------------------------+---------------------------------------------------+
   | Oracle Linux                      | -  Oracle Linux Server 9 64bit                    |
   |                                   | -  Oracle Linux Server 8 64bit                    |
   +-----------------------------------+---------------------------------------------------+
   | Red Hat                           | -  Red Hat Enterprise Linux Server 9 64bit        |
   |                                   | -  Red Hat Enterprise Linux Server 8 64bit        |
   |                                   | -  Red Hat Enterprise Linux Server 7 64bit        |
   +-----------------------------------+---------------------------------------------------+
   | Rocky Linux                       | -  Rocky Linux 9 64bit                            |
   |                                   | -  Rocky Linux 8 64bit                            |
   +-----------------------------------+---------------------------------------------------+
   | SUSE                              | -  Novell SUSE Linux Enterprise Server 16.0 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15.7 64bit |
   +-----------------------------------+---------------------------------------------------+
   | SUSE-SAP                          | Novell SUSE Linux Enterprise Server 15.7          |
   +-----------------------------------+---------------------------------------------------+
   | Ubuntu                            | -  Ubuntu 24.04 server 64bit                      |
   |                                   | -  Ubuntu 22.04 server 64bit                      |
   +-----------------------------------+---------------------------------------------------+
   | Windows                           | -  Windows Server 2025 Standard 64bit             |
   |                                   | -  Windows Server 2025 Standard Core 64bit        |
   |                                   | -  Windows Server 2025 Datacenter 64bit           |
   |                                   | -  Windows Server 2022 Standard 64bit             |
   |                                   | -  Windows Server 2022 Standard Core 64bit        |
   |                                   | -  Windows Server 2022 Datacenter 64bit           |
   |                                   | -  Windows Server 2019 Standard 64bit             |
   |                                   | -  Windows Server 2019 Standard Core 64bit        |
   |                                   | -  Windows Server 2019 Datacenter 64bit           |
   |                                   | -  Windows Server 2016 Standard 64bit             |
   |                                   | -  Windows Server 2016 Standard Core 64bit        |
   |                                   | -  Windows Server 2016 Datacenter 64bit           |
   +-----------------------------------+---------------------------------------------------+

.. _en-us_topic_0030713142__table14709182711556:

.. table:: **Table 2** Supported OS versions

   +-----------------------------------+---------------------------------------------------+
   | OS                                | Version                                           |
   +===================================+===================================================+
   | AlmaLinux                         | -  AlmaLinux 9 64bit                              |
   |                                   | -  AlmaLinux 8 64bit                              |
   +-----------------------------------+---------------------------------------------------+
   | CentOS                            | CentOS Stream 9 64bit                             |
   +-----------------------------------+---------------------------------------------------+
   | Debian                            | -  Debian GNU/Linux 12 64bit                      |
   |                                   | -  Debian GNU/Linux 11 64bit                      |
   +-----------------------------------+---------------------------------------------------+
   | EulerOS                           | EulerOS 2.0 64bit                                 |
   +-----------------------------------+---------------------------------------------------+
   | Fedora                            | -  Fedora Linux 43 64bit                          |
   |                                   | -  Fedora Linux 41 64bit                          |
   +-----------------------------------+---------------------------------------------------+
   | OpenSUSE                          | openSUSE Leap 16.0 64bit                          |
   +-----------------------------------+---------------------------------------------------+
   | Oracle Linux                      | -  Oracle Linux Server 9 64bit                    |
   |                                   | -  Oracle Linux Server 8 64bit                    |
   +-----------------------------------+---------------------------------------------------+
   | Red Hat                           | -  Red Hat Enterprise Linux Server 9 64bit        |
   |                                   | -  Red Hat Enterprise Linux Server 8 64bit        |
   |                                   | -  Red Hat Enterprise Linux Server 7 64bit        |
   +-----------------------------------+---------------------------------------------------+
   | Rocky Linux                       | -  Rocky Linux 9 64bit                            |
   |                                   | -  Rocky Linux 8 64bit                            |
   +-----------------------------------+---------------------------------------------------+
   | SUSE                              | -  Novell SUSE Linux Enterprise Server 16.0 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15.7 64bit |
   +-----------------------------------+---------------------------------------------------+
   | Ubuntu                            | -  Ubuntu 24.04 server 64bit                      |
   |                                   | -  Ubuntu 22.04 server 64bit                      |
   +-----------------------------------+---------------------------------------------------+
   | Windows                           | -  Windows Server 2025 Standard 64bit             |
   |                                   | -  Windows Server 2025 Datacenter 64bit           |
   |                                   | -  Windows Server 2022 Standard 64bit             |
   |                                   | -  Windows Server 2022 Datacenter 64bit           |
   |                                   | -  Windows Server 2019 Standard 64bit             |
   |                                   | -  Windows Server 2019 Datacenter 64bit           |
   |                                   | -  Windows Server 2016 Standard 64bit             |
   |                                   | -  Windows Server 2016 Datacenter 64bit           |
   +-----------------------------------+---------------------------------------------------+

.. _en-us_topic_0030713142__table3436728145315:

.. table:: **Table 3** Images supported by GPU-accelerated ECSs

   +-----------------------+-----------------------+--------------------------------------------+
   | Type                  | Series                | Supported Image                            |
   +=======================+=======================+============================================+
   | Graphics-accelerated  | G7v                   | -  Rocky Linux 9 64bit                     |
   |                       |                       | -  Windows Server 2025 Standard 64bit      |
   |                       |                       | -  Windows Server 2022 Standard 64bit      |
   |                       |                       | -  Windows Server 2019 Standard 64bit      |
   +-----------------------+-----------------------+--------------------------------------------+
   | Graphics-accelerated  | G7                    | -  AlmaLinux 9 64bit                       |
   |                       |                       | -  AlmaLinux 8 64bit                       |
   |                       |                       | -  Debian GNU/Linux 13 64bit               |
   |                       |                       | -  Debian GNU/Linux 12 64bit               |
   |                       |                       | -  Oracle Linux Server 8 64bit             |
   |                       |                       | -  Red Hat Enterprise Linux Server 9 64bit |
   |                       |                       | -  Red Hat Enterprise Linux Server 8 64bit |
   |                       |                       | -  Red Hat Enterprise Linux Server 7 64bit |
   |                       |                       | -  Rocky Linux 8 64bit                     |
   |                       |                       | -  Ubuntu 24.04 server 64bit               |
   |                       |                       | -  Ubuntu 22.04 server 64bit               |
   |                       |                       | -  Windows Server 2025 Standard 64bit      |
   |                       |                       | -  Windows Server 2022 Standard 64bit      |
   |                       |                       | -  Windows Server 2019 Standard 64bit      |
   +-----------------------+-----------------------+--------------------------------------------+
   | Graphics-accelerated  | G6                    | -  AlmaLinux 9 64bit                       |
   |                       |                       | -  AlmaLinux 8 64bit                       |
   |                       |                       | -  Debian GNU/Linux 13 64bit               |
   |                       |                       | -  Debian GNU/Linux 12 64bit               |
   |                       |                       | -  Oracle Linux Server 9 64bit             |
   |                       |                       | -  Oracle Linux Server 8 64bit             |
   |                       |                       | -  Red Hat Enterprise Linux Server 9 64bit |
   |                       |                       | -  Red Hat Enterprise Linux Server 8 64bit |
   |                       |                       | -  Red Hat Enterprise Linux Server 7 64bit |
   |                       |                       | -  Rocky Linux 9 64bit                     |
   |                       |                       | -  Rocky Linux 8 64bit                     |
   |                       |                       | -  Ubuntu 24.04 64bit                      |
   |                       |                       | -  Ubuntu 22.04 64bit                      |
   |                       |                       | -  Windows Server 2025 Standard 64bit      |
   |                       |                       | -  Windows Server 2022 Standard 64bit      |
   |                       |                       | -  Windows Server 2019 Standard 64bit      |
   +-----------------------+-----------------------+--------------------------------------------+
   | Computing-accelerated | P6e                   | -  CentOS 7.9 64bit                        |
   |                       |                       | -  CentOS 7.8 64bit                        |
   |                       |                       | -  CentOS 7.7 64bit                        |
   |                       |                       | -  CentOS 7.6 64bit                        |
   |                       |                       | -  Ubuntu 22.04 64bit                      |
   |                       |                       | -  Ubuntu 20.04 64bit                      |
   |                       |                       | -  Ubuntu 18.04 64bit                      |
   |                       |                       | -  Ubuntu 16.04 64bit                      |
   +-----------------------+-----------------------+--------------------------------------------+
   | Computing-accelerated | P5e                   | -  CentOS 7.9 64bit                        |
   |                       |                       | -  CentOS 7.8 64bit                        |
   |                       |                       | -  CentOS 7.7 64bit                        |
   |                       |                       | -  CentOS 7.6 64bit                        |
   |                       |                       | -  Ubuntu 22.04 64bit                      |
   |                       |                       | -  Ubuntu 20.04 64bit                      |
   |                       |                       | -  Ubuntu 18.04 64bit                      |
   |                       |                       | -  Ubuntu 16.04 64bit                      |
   +-----------------------+-----------------------+--------------------------------------------+
   | Computing-accelerated | P5s                   | -  Ubuntu 24.04 64bit                      |
   |                       |                       | -  Ubuntu 22.04 64bit                      |
   |                       |                       | -  Windows Server 2025 Standard 64bit      |
   |                       |                       | -  Windows Server 2022 Standard 64bit      |
   |                       |                       | -  Windows Server 2019 Standard 64bit      |
   +-----------------------+-----------------------+--------------------------------------------+
   | Computing-accelerated | P3                    | -  AlmaLinux 9 64bit                       |
   |                       |                       | -  AlmaLinux 8 64bit                       |
   |                       |                       | -  Debian GNU/Linux 13 64bit               |
   |                       |                       | -  Debian GNU/Linux 12 64bit               |
   |                       |                       | -  Oracle Linux Server 9 64bit             |
   |                       |                       | -  Oracle Linux Server 8 64bit             |
   |                       |                       | -  Red Hat Enterprise Linux Server 9 64bit |
   |                       |                       | -  Red Hat Enterprise Linux Server 8 64bit |
   |                       |                       | -  Red Hat Enterprise Linux Server 7 64bit |
   |                       |                       | -  Rocky Linux 9 64bit                     |
   |                       |                       | -  Rocky Linux 8 64bit                     |
   |                       |                       | -  Ubuntu 24.04 server 64bit               |
   |                       |                       | -  Ubuntu 22.04 server 64bit               |
   |                       |                       | -  Windows Server 2025 Standard 64bit      |
   |                       |                       | -  Windows Server 2022 Standard 64bit      |
   |                       |                       | -  Windows Server 2019 Standard 64bit      |
   +-----------------------+-----------------------+--------------------------------------------+
   | Computing-accelerated | P2s                   | -  AlmaLinux 9 64bit                       |
   |                       |                       | -  AlmaLinux 8 64bit                       |
   |                       |                       | -  Debian GNU/Linux 13 64bit               |
   |                       |                       | -  Debian GNU/Linux 12 64bit               |
   |                       |                       | -  Oracle Linux Server 9 64bit             |
   |                       |                       | -  Oracle Linux Server 8 64bit             |
   |                       |                       | -  Red Hat Enterprise Linux Server 9 64bit |
   |                       |                       | -  Red Hat Enterprise Linux Server 8 64bit |
   |                       |                       | -  Red Hat Enterprise Linux Server 7 64bit |
   |                       |                       | -  Rocky Linux 9 64bit                     |
   |                       |                       | -  Rocky Linux 8 64bit                     |
   |                       |                       | -  Ubuntu 24.04 server 64bit               |
   |                       |                       | -  Ubuntu 22.04 server 64bit               |
   |                       |                       | -  Windows Server 2025 Standard 64bit      |
   |                       |                       | -  Windows Server 2022 Standard 64bit      |
   |                       |                       | -  Windows Server 2019 Standard 64bit      |
   +-----------------------+-----------------------+--------------------------------------------+
   | Computing-accelerated | P2v                   | -  AlmaLinux 9 64bit                       |
   |                       |                       | -  AlmaLinux 8 64bit                       |
   |                       |                       | -  Debian GNU/Linux 13 64bit               |
   |                       |                       | -  Debian GNU/Linux 12 64bit               |
   |                       |                       | -  Oracle Linux Server 9 64bit             |
   |                       |                       | -  Oracle Linux Server 8 64bit             |
   |                       |                       | -  Red Hat Enterprise Linux Server 9 64bit |
   |                       |                       | -  Red Hat Enterprise Linux Server 8 64bit |
   |                       |                       | -  Red Hat Enterprise Linux Server 7 64bit |
   |                       |                       | -  Rocky Linux 9 64bit                     |
   |                       |                       | -  Rocky Linux 8 64bit                     |
   |                       |                       | -  Ubuntu 24.04 server 64bit               |
   |                       |                       | -  Ubuntu 22.04 server 64bit               |
   |                       |                       | -  Windows Server 2025 Standard 64bit      |
   |                       |                       | -  Windows Server 2022 Standard 64bit      |
   |                       |                       | -  Windows Server 2019 Standard 64bit      |
   +-----------------------+-----------------------+--------------------------------------------+
   | Inference-accelerated | Pi5e                  | -  Ubuntu 24.04 server 64bit               |
   |                       |                       | -  Ubuntu 22.04 server 64bit               |
   |                       |                       | -  Windows Server 2025 Standard 64bit      |
   |                       |                       | -  Windows Server 2022 Standard 64bit      |
   |                       |                       | -  Windows Server 2019 Standard 64bit      |
   +-----------------------+-----------------------+--------------------------------------------+
   | Inference-accelerated | Pi2                   | -  AlmaLinux 9 64bit                       |
   |                       |                       | -  AlmaLinux 8 64bit                       |
   |                       |                       | -  Debian GNU/Linux 13 64bit               |
   |                       |                       | -  Debian GNU/Linux 12 64bit               |
   |                       |                       | -  Red Hat Enterprise Linux Server 9 64bit |
   |                       |                       | -  Red Hat Enterprise Linux Server 8 64bit |
   |                       |                       | -  Red Hat Enterprise Linux Server 7 64bit |
   |                       |                       | -  Rocky Linux 9 64bit                     |
   |                       |                       | -  Rocky Linux 8 64bit                     |
   |                       |                       | -  Oracle Linux Server 9 64bit             |
   |                       |                       | -  Oracle Linux Server 8 64bit             |
   |                       |                       | -  Ubuntu 24.04 server 64bit               |
   |                       |                       | -  Ubuntu 22.04 server 64bit               |
   |                       |                       | -  Windows Server 2025 Standard 64bit      |
   |                       |                       | -  Windows Server 2022 Standard 64bit      |
   |                       |                       | -  Windows Server 2019 Standard 64bit      |
   +-----------------------+-----------------------+--------------------------------------------+
