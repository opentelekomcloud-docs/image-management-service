:original_name: en-us_topic_0030713142.html

.. _en-us_topic_0030713142:

OSs Supported by Different Types of ECSs
========================================

This section describes the OSs supported by different types of ECSs.

x86 ECSs
--------

-  :ref:`Table 1 <en-us_topic_0030713142__table124398125555>` lists the OSs supported by the following ECSs:

   General computing S7n, S2, S3

   Dedicated general-purpose C7n, C3, C4

   Memory-optimized M7n, M3, M4

   Disk-intensive D2

   Ultra-high I/O I3

-  :ref:`Table 2 <en-us_topic_0030713142__table14709182711556>` lists the OSs supported by large-memory ECSs (E6 and E3).

-  :ref:`Table 3 <en-us_topic_0030713142__table3436728145315>` lists the OSs supported by GPU-accelerated ECSs (G7, G6, P3, P2s, P2v and Pi2).

.. note::

   -  It is recommended that you use the official OS release versions. Do not tailor or customize the release versions, or problems may occur.
   -  OS vendors do not always update OS release versions regularly. Some versions are no longer maintained, and these deprecated versions no longer receive security patches. Ensure that you read the update notifications from OS vendors and update your OS so that it runs properly.

.. _en-us_topic_0030713142__table124398125555:

.. table:: **Table 1** Supported OS versions

   +-----------------------------------+-----------------------------------------------------+
   | OS                                | Version                                             |
   +===================================+=====================================================+
   | Alma                              | Alma 8 64bit                                        |
   +-----------------------------------+-----------------------------------------------------+
   | CentOS                            | -  CentOS Stream 9.6 64bit                          |
   |                                   | -  CentOS Stream 8.6 64bit                          |
   |                                   | -  CentOS 8.5 64bit                                 |
   |                                   | -  CentOS 8.4 64bit                                 |
   |                                   | -  CentOS 8.3 64bit                                 |
   |                                   | -  CentOS 8.2 64bit                                 |
   |                                   | -  CentOS 8.1 64bit                                 |
   |                                   | -  CentOS 7.9 64bit                                 |
   |                                   | -  CentOS 7.7 64bit                                 |
   +-----------------------------------+-----------------------------------------------------+
   | Debian                            | -  Debian GNU/Linux 12.0.0 64bit                    |
   |                                   | -  Debian GNU/Linux 11.7.0 64bit                    |
   |                                   | -  Debian GNU/Linux 11.6.0 64bit                    |
   |                                   | -  Debian GNU/Linux 11.5.0 64bit                    |
   |                                   | -  Debian GNU/Linux 11.4.0 64bit                    |
   |                                   | -  Debian GNU/Linux 11.3.0 64bit                    |
   |                                   | -  Debian GNU/Linux 11.2.0 64bit                    |
   |                                   | -  Debian GNU/Linux 11.1.0 64bit                    |
   |                                   | -  Debian GNU/Linux 11.0.0 64bit                    |
   |                                   | -  Debian GNU/Linux 10.13.0 64bit                   |
   |                                   | -  Debian GNU/Linux 10.12.0 64bit                   |
   |                                   | -  Debian GNU/Linux 10.11.0 64bit                   |
   |                                   | -  Debian GNU/Linux 10.10.0 64bit                   |
   |                                   | -  Debian GNU/Linux 10.9.0 64bit                    |
   |                                   | -  Debian GNU/Linux 10.8.0 64bit                    |
   |                                   | -  Debian GNU/Linux 10.7.0 64bit                    |
   |                                   | -  Debian GNU/Linux 10.6.0 64bit                    |
   |                                   | -  Debian GNU/Linux 10.5.0 64bit                    |
   |                                   | -  Debian GNU/Linux 10.4.0 64bit                    |
   |                                   | -  Debian GNU/Linux 10.3.0 64bit                    |
   |                                   | -  Debian GNU/Linux 10.2.0 64bit                    |
   |                                   | -  Debian GNU/Linux 10.1.0 64bit                    |
   |                                   | -  Debian GNU/Linux 10 64bit                        |
   +-----------------------------------+-----------------------------------------------------+
   | EulerOS                           | -  EulerOS 2.12 64bit                               |
   |                                   | -  EulerOS 2.11 64bit                               |
   |                                   | -  EulerOS 2.10 64bit                               |
   |                                   | -  EulerOS 2.8 64bit                                |
   |                                   | -  EulerOS 2.7 64bit                                |
   |                                   | -  EulerOS 2.5 64bit                                |
   +-----------------------------------+-----------------------------------------------------+
   | Fedora                            | -  Fedora 39 64bit                                  |
   |                                   | -  Fedora 38 64bit                                  |
   |                                   | -  Fedora 37 64bit                                  |
   |                                   | -  Fedora 36 64bit                                  |
   |                                   | -  Fedora 35 64bit                                  |
   |                                   | -  Fedora 34 64bit                                  |
   |                                   | -  Fedora 33 64bit                                  |
   |                                   | -  Fedora 32 64bit                                  |
   |                                   | -  Fedora 31 64bit                                  |
   +-----------------------------------+-----------------------------------------------------+
   | OpenSUSE                          | -  OpenSUSE 15.5 64bit                              |
   |                                   | -  OpenSUSE 15.4 64bit                              |
   |                                   | -  OpenSUSE 15.3 64bit                              |
   |                                   | -  OpenSUSE 15.2 64bit                              |
   +-----------------------------------+-----------------------------------------------------+
   | Oracle Linux                      | -  Oracle Linux Server release 8.4 64bit            |
   |                                   | -  Oracle Linux Server release 7.6 64bit            |
   +-----------------------------------+-----------------------------------------------------+
   | Red Hat                           | -  Red Hat Enterprise Linux 9.1 64bit               |
   |                                   | -  Red Hat Enterprise Linux 9.0 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.7 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.6 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.5 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.4 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.3 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.2 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.1 64bit               |
   |                                   | -  Red Hat Enterprise Linux 7.9 64bit               |
   |                                   | -  Red Hat Enterprise Linux 6.10 64bit              |
   +-----------------------------------+-----------------------------------------------------+
   | Rocky                             | -  9.2 64bit                                        |
   |                                   | -  9.1 64bit                                        |
   |                                   | -  9.0 64bit                                        |
   |                                   | -  8.8 64bit                                        |
   |                                   | -  8.7 64bit                                        |
   |                                   | -  8.6 64bit                                        |
   |                                   | -  8.5 64bit                                        |
   |                                   | -  8.4 64bit                                        |
   |                                   | -  8.3 64bit                                        |
   |                                   | -  8 64bit                                          |
   +-----------------------------------+-----------------------------------------------------+
   | SUSE                              | -  Novell SUSE Linux Enterprise Server 15 SP5 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 SP4 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 SP3 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 SP2 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 SP1 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 64bit     |
   |                                   | -  Novell SUSE Linux Enterprise Server 12 SP5 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 12 SP4 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 12 SP3 64bit |
   +-----------------------------------+-----------------------------------------------------+
   | Ubuntu                            | -  Ubuntu 22.04 Server 64bit                        |
   |                                   | -  Ubuntu 20.04 server 64bit                        |
   |                                   | -  Ubuntu 18.04 server 64bit                        |
   +-----------------------------------+-----------------------------------------------------+
   | Windows                           | -  Windows Server 2022 Standard 64bit               |
   |                                   | -  Windows Server 2022 Datacenter 64bit             |
   |                                   | -  Windows Server 2019 Datacenter 64bit             |
   |                                   | -  Windows Server 2019 Standard 64bit               |
   |                                   | -  Windows Server 2016 Standard 64bit               |
   |                                   | -  Windows Server 2012 R2 Standard 64bit            |
   +-----------------------------------+-----------------------------------------------------+
   | openEuler                         | -  openEuler 22.03 SP1 64bit                        |
   |                                   | -  openEuler 22.03 64bit                            |
   |                                   | -  openEuler 20.03 SP3 64bit                        |
   |                                   | -  openEuler 20.03 SP2 64bit                        |
   |                                   | -  openEuler 20.03 SP1 64bit                        |
   |                                   | -  openEuler 20.03 64bit                            |
   +-----------------------------------+-----------------------------------------------------+

.. _en-us_topic_0030713142__table14709182711556:

.. table:: **Table 2** Supported OS versions

   +-----------------------------------+-----------------------------------------------------+
   | OS                                | Version                                             |
   +===================================+=====================================================+
   | CentOS                            | -  CentOS 8.5 64bit                                 |
   |                                   | -  CentOS 8.4 64bit                                 |
   |                                   | -  CentOS 8.3 64bit                                 |
   |                                   | -  CentOS 8.2 64bit                                 |
   |                                   | -  CentOS 8.1 64bit                                 |
   |                                   | -  CentOS 7.9 64bit                                 |
   |                                   | -  CentOS 7.7 64bit                                 |
   +-----------------------------------+-----------------------------------------------------+
   | EulerOS                           | -  EulerOS 2.12 64bit                               |
   |                                   | -  EulerOS 2.11 64bit                               |
   |                                   | -  EulerOS 2.10 64bit                               |
   |                                   | -  EulerOS 2.8 64bit                                |
   |                                   | -  EulerOS 2.7 64bit                                |
   |                                   | -  EulerOS 2.5 64bit                                |
   +-----------------------------------+-----------------------------------------------------+
   | Fedora                            | -  Fedora 39 64bit                                  |
   |                                   | -  Fedora 38 64bit                                  |
   |                                   | -  Fedora 37 64bit                                  |
   |                                   | -  Fedora 36 64bit                                  |
   |                                   | -  Fedora 35 64bit                                  |
   |                                   | -  Fedora 34 64bit                                  |
   |                                   | -  Fedora 33 64bit                                  |
   |                                   | -  Fedora 32 64bit                                  |
   |                                   | -  Fedora 31 64bit                                  |
   +-----------------------------------+-----------------------------------------------------+
   | OpenSUSE                          | -  OpenSUSE 15.5 64bit                              |
   |                                   | -  OpenSUSE 15.4 64bit                              |
   |                                   | -  OpenSUSE 15.3 64bit                              |
   |                                   | -  OpenSUSE 15.2 64bit                              |
   +-----------------------------------+-----------------------------------------------------+
   | Oracle Linux                      | -  Oracle Linux Server release 8.4 64bit            |
   |                                   | -  Oracle Linux Server release 7.6 64bit            |
   +-----------------------------------+-----------------------------------------------------+
   | Red Hat                           | -  Red Hat Enterprise Linux 9.1 64bit               |
   |                                   | -  Red Hat Enterprise Linux 9.0 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.7 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.6 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.5 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.4 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.3 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.2 64bit               |
   |                                   | -  Red Hat Enterprise Linux 8.1 64bit               |
   |                                   | -  Red Hat Enterprise Linux 7.9 64bit               |
   +-----------------------------------+-----------------------------------------------------+
   | SUSE                              | -  Novell SUSE Linux Enterprise Server 15 SP5 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 SP4 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 SP3 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 SP2 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 SP1 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 64bit     |
   |                                   | -  Novell SUSE Linux Enterprise Server 12 SP5 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 12 SP4 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 12 SP3 64bit |
   +-----------------------------------+-----------------------------------------------------+
   | Ubuntu                            | -  Ubuntu 22.04 server 64bit                        |
   |                                   | -  Ubuntu 20.04 server 64bit                        |
   |                                   | -  Ubuntu 18.04 server 64bit                        |
   +-----------------------------------+-----------------------------------------------------+
   | Windows                           | -  Windows Server 2022 Standard 64bit               |
   |                                   | -  Windows Server 2022 Datacenter 64bit             |
   |                                   | -  Windows Server 2019 Standard 64bit               |
   |                                   | -  Windows Server 2019 Datacenter 64bit             |
   |                                   | -  Windows Server 2016 Standard 64bit               |
   |                                   | -  Windows Server 2012 R2 Standard 64bit            |
   +-----------------------------------+-----------------------------------------------------+

.. _en-us_topic_0030713142__table3436728145315:

.. table:: **Table 3** Images supported by GPU-accelerated ECSs

   +-----------------------+-----------------------+------------------------------------------+
   | Type                  | Series                | Supported Image                          |
   +=======================+=======================+==========================================+
   | Graphics-accelerated  | G7                    | -  CentOS 8.2 64bit                      |
   |                       |                       | -  CentOS 7.6 64bit                      |
   |                       |                       | -  Ubuntu 20.04 Server 64bit             |
   |                       |                       | -  Ubuntu 18.04 Server 64bit             |
   |                       |                       | -  Windows Server 2019 Standard 64bit    |
   |                       |                       | -  Windows Server 2016 Standard 64bit    |
   +-----------------------+-----------------------+------------------------------------------+
   | Graphics-accelerated  | G6                    | -  EulerOS 2.5 64bit                     |
   |                       |                       | -  Windows Server 2019 Standard 64bit    |
   |                       |                       | -  Windows Server 2016 Standard 64bit    |
   |                       |                       | -  Windows Server 2012 R2 Standard 64bit |
   +-----------------------+-----------------------+------------------------------------------+
   | Computing-accelerated | P5s                   | -  CentOS 7.9 64bit                      |
   |                       |                       | -  CentOS 7.8 64bit                      |
   |                       |                       | -  CentOS 7.7 64bit                      |
   |                       |                       | -  CentOS 7.6 64bit                      |
   |                       |                       | -  Ubuntu 22.04 64bit                    |
   |                       |                       | -  Ubuntu 20.04 64bit                    |
   |                       |                       | -  Ubuntu 18.04 64bit                    |
   |                       |                       | -  Ubuntu 16.04 64bit                    |
   +-----------------------+-----------------------+------------------------------------------+
   | Computing-accelerated | P3                    | -  CentOS 8.2 64bit                      |
   |                       |                       | -  CentOS 8.1 64bit                      |
   |                       |                       | -  CentOS 8.0 64bit                      |
   |                       |                       | -  CentOS 7.9 64bit                      |
   |                       |                       | -  CentOS 7.8 64bit                      |
   |                       |                       | -  CentOS 7.7 64bit                      |
   |                       |                       | -  CentOS 7.6 64bit                      |
   |                       |                       | -  Ubuntu 20.04 server 64bit             |
   |                       |                       | -  Ubuntu 18.04 server 64bit             |
   +-----------------------+-----------------------+------------------------------------------+
   | Computing-accelerated | P2s                   | -  CentOS 7.9 64bit                      |
   |                       |                       | -  EulerOS 2.5 64bit                     |
   |                       |                       | -  Oracle Linux Server release 7.6 64bit |
   |                       |                       | -  Ubuntu 20.04 Server 64bit             |
   |                       |                       | -  Ubuntu 18.04 Server 64bit             |
   |                       |                       | -  Windows Server 2019 Standard 64bit    |
   |                       |                       | -  Windows Server 2016 Standard 64bit    |
   |                       |                       | -  Windows Server 2012 R2 Standard 64bit |
   +-----------------------+-----------------------+------------------------------------------+
   | Computing-accelerated | P2v                   | -  CentOS 7.9 64bit                      |
   |                       |                       | -  EulerOS 2.5 64bit                     |
   |                       |                       | -  Oracle Linux Server release 7.6 64bit |
   |                       |                       | -  Ubuntu 20.04 Server 64bit             |
   |                       |                       | -  Ubuntu 18.04 Server 64bit             |
   |                       |                       | -  Windows Server 2019 Standard 64bit    |
   |                       |                       | -  Windows Server 2016 Standard 64bit    |
   |                       |                       | -  Windows Server 2012 R2 Standard 64bit |
   +-----------------------+-----------------------+------------------------------------------+
   | Inference-accelerated | Pi2                   | -  CentOS 7.9 64bit                      |
   |                       |                       | -  Oracle Linux Server release 7.6 64bit |
   |                       |                       | -  Ubuntu 20.04 Server 64bit             |
   |                       |                       | -  Ubuntu 18.04 Server 64bit             |
   |                       |                       | -  Windows Server 2019 Standard 64bit    |
   |                       |                       | -  Windows Server 2016 Standard 64bit    |
   |                       |                       | -  Windows Server 2012 R2 Standard 64bit |
   +-----------------------+-----------------------+------------------------------------------+
