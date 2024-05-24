:original_name: en-us_topic_0030713142.html

.. _en-us_topic_0030713142:

OSs Supported by Different Types of ECSs
========================================

This section describes the OSs supported by different types of ECSs.

x86 ECSs
--------

-  :ref:`Table 1 <en-us_topic_0030713142__table124398125555>` lists the OSs supported by the following ECSs:

   General-purpose S2, S3

   Dedicated general-purpose C3, C4

   Memory-optimized M3, M4

   Disk-intensive D2

   Ultra-high I/O I3

-  :ref:`Table 2 <en-us_topic_0030713142__table14709182711556>` lists the OSs supported by large-memory ECSs (E3).

-  :ref:`Table 3 <en-us_topic_0030713142__table3436728145315>` lists the OSs supported by GPU-accelerated ECSs (G6, P2s, P2v, PI2).

-  AI-accelerated AI1 ECSs support the following OSs:

   -  Ubuntu Server 16.04 64bit
   -  CentOS 7.4 64bit

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
   | CentOS                            | -  CentOS Stream 8.6 64bit                          |
   |                                   | -  CentOS 7.9 64bit                                 |
   |                                   | -  CentOS 7.7 64bit                                 |
   +-----------------------------------+-----------------------------------------------------+
   | Debian                            | -  Debian GNU/Linux 11 64bit                        |
   |                                   | -  Debian GNU/Linux 10 64bit                        |
   +-----------------------------------+-----------------------------------------------------+
   | EulerOS                           | EulerOS 2.5 64bit                                   |
   +-----------------------------------+-----------------------------------------------------+
   | Fedora                            | -  Fedora 35 64bit                                  |
   |                                   | -  Fedora 34 64bit                                  |
   |                                   | -  Fedora 33 64bit                                  |
   +-----------------------------------+-----------------------------------------------------+
   | OpenSUSE                          | OpenSUSE 15.3 64bit                                 |
   +-----------------------------------+-----------------------------------------------------+
   | Oracle Linux                      | -  Oracle Linux Server release 8.4 64bit            |
   |                                   | -  Oracle Linux Server release 7.6 64bit            |
   +-----------------------------------+-----------------------------------------------------+
   | Red Hat                           | -  Red Hat Enterprise Linux 7.9 64bit               |
   |                                   | -  Red Hat Enterprise Linux 6.10 64bit              |
   +-----------------------------------+-----------------------------------------------------+
   | Rocky                             | Rocky 8 64bit                                       |
   +-----------------------------------+-----------------------------------------------------+
   | SUSE                              | -  Novell SUSE Linux Enterprise Server 15 SP3 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 SP2 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 SP1 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 64bit     |
   |                                   | -  Novell SUSE Linux Enterprise Server 12 SP5 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 12 SP4 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 12 SP3 64bit |
   +-----------------------------------+-----------------------------------------------------+
   | Ubuntu                            | -  Ubuntu 20.04 server 64bit                        |
   |                                   | -  Ubuntu 18.04 server 64bit                        |
   +-----------------------------------+-----------------------------------------------------+
   | Windows                           | -  Windows Server 2019 Standard 64bit               |
   |                                   | -  Windows Server 2016 Standard 64bit               |
   |                                   | -  Windows Server 2012 R2 Standard 64bit            |
   +-----------------------------------+-----------------------------------------------------+
   | openEuler                         | openEuler 20.03 64bit                               |
   +-----------------------------------+-----------------------------------------------------+

.. _en-us_topic_0030713142__table14709182711556:

.. table:: **Table 2** Supported OS versions

   +-----------------------------------+-----------------------------------------------------+
   | OS                                | Version                                             |
   +===================================+=====================================================+
   | CentOS                            | -  CentOS 7.9 64bit                                 |
   |                                   | -  CentOS 7.7 64bit                                 |
   +-----------------------------------+-----------------------------------------------------+
   | EulerOS                           | EulerOS 2.5 64bit                                   |
   +-----------------------------------+-----------------------------------------------------+
   | Fedora                            | -  Fedora 35 64bit                                  |
   |                                   | -  Fedora 34 64bit                                  |
   |                                   | -  Fedora 33 64bit                                  |
   +-----------------------------------+-----------------------------------------------------+
   | OpenSUSE                          | OpenSUSE 15.3 64bit                                 |
   +-----------------------------------+-----------------------------------------------------+
   | Oracle Linux                      | -  Oracle Linux Server release 8.4 64bit            |
   |                                   | -  Oracle Linux Server release 7.6 64bit            |
   +-----------------------------------+-----------------------------------------------------+
   | Red Hat                           | Red Hat Enterprise Linux 7.9 64bit                  |
   +-----------------------------------+-----------------------------------------------------+
   | SUSE                              | -  Novell SUSE Linux Enterprise Server 15 SP3 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 SP2 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 SP1 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 15 64bit     |
   |                                   | -  Novell SUSE Linux Enterprise Server 12 SP5 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 12 SP4 64bit |
   |                                   | -  Novell SUSE Linux Enterprise Server 12 SP3 64bit |
   +-----------------------------------+-----------------------------------------------------+
   | Ubuntu                            | -  Ubuntu 20.04 server 64bit                        |
   |                                   | -  Ubuntu 18.04 server 64bit                        |
   +-----------------------------------+-----------------------------------------------------+
   | Windows                           | -  Windows Server 2019 Standard 64bit               |
   |                                   | -  Windows Server 2016 Standard 64bit               |
   |                                   | -  Windows Server 2012 R2 Standard 64bit            |
   +-----------------------------------+-----------------------------------------------------+

.. _en-us_topic_0030713142__table3436728145315:

.. table:: **Table 3** Supported OS versions

   +-----------------------------------+---------------------------------------------+
   | OS                                | OS Version                                  |
   +===================================+=============================================+
   | Rocky                             | Rocky 8 64 bit                              |
   +-----------------------------------+---------------------------------------------+
   | CentOS                            | CentOS 7.9 64bit                            |
   +-----------------------------------+---------------------------------------------+
   | EulerOS                           | EulerOS 2.5 64bit                           |
   |                                   |                                             |
   |                                   | .. note::                                   |
   |                                   |                                             |
   |                                   |    PI2 ECSs do not support this OS version. |
   +-----------------------------------+---------------------------------------------+
   | Oracle Linux                      | Oracle Linux Server release 7.6 64bit       |
   +-----------------------------------+---------------------------------------------+
   | Ubuntu                            | -  Ubuntu 20.04 server 64bit                |
   |                                   | -  Ubuntu 18.04 server 64bit                |
   +-----------------------------------+---------------------------------------------+
   | Windows                           | -  Windows Server 2019 Standard 64bit       |
   |                                   | -  Windows Server 2016 Standard 64bit       |
   |                                   | -  Windows Server 2012 R2 Standard 64bit    |
   +-----------------------------------+---------------------------------------------+
