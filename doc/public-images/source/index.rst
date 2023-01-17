====================================================
Image Management Service - Public Image Introduction
====================================================

Customer documentation for public image at OpenTelekomCloud
===========================================================

The Image Management Service (IMS) provides a mandatory Elastic Cloud
Server (ECS) template and software, including at least OS, application
software and private software. Users can use an image to apply for an
ECS or make a new image using the existing ECS. Images are classified
into public images and private images. This document provides
information and handling instructions for the public images on the Open
Telekom Cloud.

DNS and NTP
-----------

While the correct time is injected from the host into a VM at boot time,
the time can diverge and lose synchronicity over time; NTP is
recommended in each VM. NTP service is provided and pre-configured in
all our public images. DNS is configured in the VPC /Subnet
configuration.

DNS names and IP addresses of internal services
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

We explicitly recommend using the internal DNS server; not only does it
provide better performance and avoids the need to allow outgoing traffic
into the internet, it also provides internal addresses for the API
endpoints, see below. The DNS server's are normally pushed to the VMs
via a DHCP setting which is configured through the subnet configuration
in OTC/OpenStack. The internal DNS servers (100.125.4.25,
100.125.129.199) are preconfigured in the subnet config in the Web
Interface ("Service Console"). When creating a subnet via API, you need
to specify the name server(s):

.. code:: shell

   openstack subnet create --dns-nameserver 100.125.4.25 --dns-nameserver 100.125.129.199 --dns-nameserver 8.8.8.8  --network <network> --subnet-range <subnet-range> --name <name>

Here we have used the google public nameserver (8.8.8.8) as tertiary DNS
-- feel free to use any server that suits your needs. Replace ``<name>``
with you desired name for the subnet, ``<network>`` with the name of a
configured network and ``<subnet-range>`` with the network IP range in
CIDR notation (such as e.g. 172.16.224/20). Note that ``8.8.8.8`` will
only work for VMs that have outgoing internet access (via an external IP
address or SNAT service). T-Systems operates the OTC public services in
the public service zone ``100.64.0.0/10`` and ``198.19.0.0/16`` of the
OTC provider network. These services can not be reached from outside the
OTC (unless you have a VPN tunnel); they are reachable by all VMs in OTC
without the need for an external IP address (EIP / Floating-IP).

+----------------+----------------+----------------+----------------+
| IP             | DNS Name       | Type of        | Notes          |
|                |                | Service        |                |
+================+================+================+================+
| **             |                | DNS            | HA Setup       |
| 100.125.4.25** |                |                |                |
+----------------+----------------+----------------+----------------+
| **100          |                | DNS            | HA Setup       |
| .125.129.199** |                |                |                |
+----------------+----------------+----------------+----------------+
| **             | ntp01.eu-de.o  | NTP            | AZ1            |
| 100.125.4.28** | tc-service.com |                |                |
+----------------+----------------+----------------+----------------+
| **             | ntp02.eu-de.o  | NTP            | AZ2            |
| 100.125.4.29** | tc-service.com |                |                |
+----------------+----------------+----------------+----------------+
| **             | ntp01.eu-nl.o  | NTP            | AZ1            |
| 100.125.0.15** | tc-service.com |                |                |
+----------------+----------------+----------------+----------------+
| **             | ntp02.eu-nl.o  | NTP            | AZ2            |
| 100.125.0.16** | tc-service.com |                |                |
+----------------+----------------+----------------+----------------+
| **1            | vend           | Vendordata     | first boot     |
| 98.19.33.237** | ordata.eu-de.o | OpenStack      | provisioning   |
|                | tc-service.com | (HTTP)         |                |
+----------------+----------------+----------------+----------------+
| **             | vend           | Vendordata     | first boot     |
| 100.125.1.10** | ordata.eu-nl.o | OpenStack      | provisioning   |
|                | tc-service.com | (HTTP)         |                |
+----------------+----------------+----------------+----------------+
| **             | smt.eu-de.o    | Repo (HTTP)    | openSUSE,      |
| 100.125.4.20** | tc-service.com |                | SLES, EulerOS, |
|                |                |                | OpenEuler,     |
|                |                |                | CentOS,        |
|                |                |                | Oracle,        |
|                |                |                | Fedora, Alma,  |
|                |                |                | Rocky          |
+----------------+----------------+----------------+----------------+
| **             | smt.eu-nl.o    | Repo (HTTP)    | openSUSE,      |
| 100.125.1.15** | tc-service.com |                | SLES, EulerOS, |
|                |                |                | OpenEuler,     |
|                |                |                | CentOS,        |
|                |                |                | Oracle,        |
|                |                |                | Fedora, Alma,  |
|                |                |                | Rocky          |
+----------------+----------------+----------------+----------------+
| **1            | deb            | Repo (HTTP)    | Debian, Ubuntu |
| 98.19.61.228** | mirror.eu-de.o |                |                |
|                | tc-service.com |                |                |
+----------------+----------------+----------------+----------------+
| **             | deb            | Repo (HTTP)    | Debian, Ubuntu |
| 100.125.1.11** | mirror.eu-nl.o |                |                |
|                | tc-service.com |                |                |
+----------------+----------------+----------------+----------------+
| **             | rhui.eu-de.o   | RHUI (HTTPS)   | RedHat 6/7/8/9 |
| 198.19.41.19** | tc-service.com |                | Update Infra   |
+----------------+----------------+----------------+----------------+
| **             | rhui.eu-nl.o   | RHUI (HTTPS)   | RedHat 6/7/8/9 |
| 100.125.1.25** | tc-service.com |                | Update Infra   |
+----------------+----------------+----------------+----------------+
| **1            | kms.eu-de.o    | KMS            | Windows        |
| 98.19.55.230** | tc-service.com |                | activation     |
+----------------+----------------+----------------+----------------+
| **             | kms.eu-nl.o    | KMS            | Windows        |
| 100.125.1.17** | tc-service.com |                | activation     |
+----------------+----------------+----------------+----------------+
| **1            | wsus.eu-de.o   | WSUS           | Windows        |
| 98.19.35.231** | tc-service.com |                | updates (WSUS) |
+----------------+----------------+----------------+----------------+
| **             | wsus.eu-nl.o   | WSUS           | Windows        |
| 100.125.1.18** | tc-service.com |                | updates (WSUS) |
+----------------+----------------+----------------+----------------+
| **             | gpulic         | NLS            | NVIDIA License |
| 198.19.34.77** | ence01.eu-de.o |                | Server         |
|                | tc-service.com |                |                |
+----------------+----------------+----------------+----------------+
| **1            | gpulic         | NLS            | NVIDIA License |
| 98.19.44.221** | ence02.eu-de.o |                | Server         |
|                | tc-service.com |                |                |
+----------------+----------------+----------------+----------------+
| **             | gpulic         | NLS            | NVIDIA License |
| 100.125.1.27** | ence01.eu-nl.o |                | Server         |
|                | tc-service.com |                |                |
+----------------+----------------+----------------+----------------+
| **             | gpulic         | NLS            | NVIDIA License |
| 100.125.1.28** | ence02.eu-nl.o |                | Server         |
|                | tc-service.com |                |                |
+----------------+----------------+----------------+----------------+

As part of that we recently migrated to new debmirrors (and also
vendordata servers => required at the first boot of an ECS/BMS server)
in a different IP address range.

!! Currently there are two ip address blocks, which contain OTC
services: 100.64.0.0/10 and 198.19.0.0/16. **Whitelisting** both blocks
is sufficient for the foreseeable future, since we do not plan to use
any addresses outside these ranges. Please do not whitelist single ip
addresses out of these ranges, because it is possible that we migrate to
different ip addresses within these ranges without any prior warning.

!! Also please note that the other package repositories (rhui, smt,
wsus/kms) and the Nvidia licence servers are destined to be migrated to
the 198.19.0.0/16 range.

Image types and naming convention
---------------------------------

On the Open Telekom Cloud platform the following public images are
provided.

Community
~~~~~~~~~

These are Freeware images, that come from the community as is. They have
not undergone any modification (e.g. hardening) by T-Systems.

Standard
~~~~~~~~

These are free self-managed Linux images, which have been build within
the T-Systems OTC Image Factory. They have received some general OTC
related settings and basic hardening.

Enterprise
~~~~~~~~~~

Password login: Only possible on the console. Default user is linux. A
random password is generated during ECS creation. The Password is shown
on the noVNC console. SSH login: With default user linux

REGULAR IMAGE BUILD FOR LINUX AND WINDOWS
-----------------------------------------

-  New images for Linux and Windows Enterprise and Linux standard images
   every month (at the 15th) including the latest patches
-  The new image name ends with \_latest
-  The previous \_latest image will renamed to end with \_prev
-  The previous \_prev image will not be deleted but made invisible
-  Old images will be deleted after 2 years

**Latest Image for Linux:**

-  There will be always an image with the name \_latest
-  Includes the latest or emergency bug/security fixes
-  Will be replaced as soon as a new image is available

.. _self-managed-images--user-management--login:

Self-managed images / User management / Login
---------------------------------------------

.. _community-1:

Community
~~~~~~~~~

Login with PW or SSH key as specified during ECS creation. For Ubuntu
images only SSH login with user ``ubuntu`` will work.

.. _standard-1:

Standard
~~~~~~~~

Password login: Only possible on the console. Default user is ``linux``.
A random password is generated during ECS creation. The Password is
shown on the noVNC console. SSH login: With default user ``linux`` For
Ubuntu images only SSH login with user ``ubuntu`` will work.

Enterprise Linux
~~~~~~~~~~~~~~~~

Password login: Only possible on the console. Default user is ``linux``.
A random password is generated during ECS creation. The Password is
shown on the noVNC console. SSH login: With default user ``linux``

Enterprise Windows
~~~~~~~~~~~~~~~~~~

A random password is generated during ECS creation. It has to be
decrypted with Private Key on the OTC Cloud Server Console:

|image01|

Patch Management and License Activation
---------------------------------------

Windows
~~~~~~~

T-Systems licenses are used for the Self-Managed OS. Licenses are
activated at the central KMS server (``kms.eu-de.otc-service.com`` or
``kms.eu-nl.otc-service.com``) automatically. The Microsoft updates
(security updates only) are provided via the WSUS server
(``wsus.eu-de.otc-service.com`` or ``wsus.eu-nl.otc-service.com``) and
can are installed automatically during the night.

Linux
~~~~~

The free Linux distributions come with the public online repositories
preconfigured but disabled in the images. These only work, when the VM
has outgoing internet access (be it via an EIP address or via SNAT). The
commercial Linux distributions do not come with preconfigured update
repositories.

If the image is booted without being set to bring you own license (BYOL)
/ bring your own subscription, a ``vendor_data`` script will configure
the internal repository servers to provide maintenance updates from the
Linux distribution / vendor. This way, we make it easy for customers to
stay up to date with updates; we highly recommend installing at least
security updates regularly and promptly -- it is the single most
important activity to keep your VMs secure.

**Important: Do not override bootcmd in ``user_data`` nor disable
``vendor_data`` if you need working update repositories in your VM
created from public images in OTC!**

For BYOL VMs, it is the customers responsibility to ensure license
compliance and to provide and configure working update repositories for
the VMs. (When booting a VM from one of the ImageFactory free Linux
images with BYOL set, the public internet repositories will remain
configured as opposed to the mirrors in OTC.)

Timezone and Keyboard Settings
------------------------------

The following default timezone and keyboard settings apply for the
public images.

.. _windows-1:

Windows
~~~~~~~

Timezone: UTC +01:00 (Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna)
Keyboard: English (United States) and German (Germany)

.. _linux-1:

Linux
~~~~~

Timezone: UTC Keyboard: en_US

API Endpoints
-------------

The API endpoints of OTC are available to the public internet, well
protected behind Web-Application Firewalls (WAF) and intrusion detection
systems. For VMs inside OTC, there are also internal IP addresses
available via the above DNS server. This shortens the internal network
path and provides a more reliable and better performing service, so we
explicitly recommend using the OTC APIs via VMs on OTC with the internal
DNS servers (``100.125.4.25`` and ``100.125.129.199``) resolving the
endpoint names.

.. code:: shell

    openstack endpoint list -f json | jq 'map( { service: ."Service Name" | ascii_downcase, region: .Region, endpoint: .URL}) | map(select(.region != null)) | unique_by({service, region, endpoint}) | sort_by(.service, .region)'

+---------------------------+------------+---------------------------+
| **service**               | **region** | **endpoint**              |
+===========================+============+===========================+
| anti-ddos                 | eu-de      | `https://antiddos.eu-     |
|                           |            | de.otc.t-systems.com/v1/$ |
|                           |            | (tenant_id)s <https://ant |
|                           |            | iddos.eu-de.otc.t-systems |
|                           |            | .com/v1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| anti-ddos                 | eu-nl      | `https://antiddos.eu-     |
|                           |            | nl.otc.t-systems.com/v1/$ |
|                           |            | (tenant_id)s <https://ant |
|                           |            | iddos.eu-nl.otc.t-systems |
|                           |            | .com/v1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| antiddos                  | eu-de      | `https://antiddos.eu      |
|                           |            | -de.otc.t-systems.com/v1/ |
|                           |            |  <https://antiddos.eu-de. |
|                           |            | otc.t-systems.com/v1/>`__ |
+---------------------------+------------+---------------------------+
| antiddos                  | eu-nl      | `https://antiddos.eu      |
|                           |            | -nl.otc.t-systems.com/v1/ |
|                           |            |  <https://antiddos.eu-nl. |
|                           |            | otc.t-systems.com/v1/>`__ |
+---------------------------+------------+---------------------------+
| asv1                      | eu-de      | `https://as.eu-d          |
|                           |            | e.otc.t-systems.com/autos |
|                           |            | caling-api/v1/$(tenant_id |
|                           |            | )s <https://as.eu-de.otc. |
|                           |            | t-systems.com/autoscaling |
|                           |            | -api/v1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| asv1                      | eu-nl      | `https://as.eu-n          |
|                           |            | l.otc.t-systems.com/autos |
|                           |            | caling-api/v1/$(tenant_id |
|                           |            | )s <https://as.eu-nl.otc. |
|                           |            | t-systems.com/autoscaling |
|                           |            | -api/v1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| autoscaling               | eu-de      | `https://as.e             |
|                           |            | u-de.otc.t-systems.com/au |
|                           |            | toscaling-api/v1 <https:/ |
|                           |            | /as.eu-de.otc.t-systems.c |
|                           |            | om/autoscaling-api/v1>`__ |
+---------------------------+------------+---------------------------+
| autoscaling               | eu-nl      | `https://as.e             |
|                           |            | u-nl.otc.t-systems.com/au |
|                           |            | toscaling-api/v1 <https:/ |
|                           |            | /as.eu-nl.otc.t-systems.c |
|                           |            | om/autoscaling-api/v1>`__ |
+---------------------------+------------+---------------------------+
| bms                       | eu-de      | `https://bm               |
|                           |            | s.eu-de.otc.t-systems.com |
|                           |            | /v1/$(tenant_id)s <https: |
|                           |            | //bms.eu-de.otc.t-systems |
|                           |            | .com/v1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| cbr                       | eu-de      | `https://cb               |
|                           |            | r.eu-de.otc.t-systems.com |
|                           |            | /v3/$(tenant_id)s <https: |
|                           |            | //cbr.eu-de.otc.t-systems |
|                           |            | .com/v3/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| cbr                       | eu-nl      | `https://cb               |
|                           |            | r.eu-nl.otc.t-systems.com |
|                           |            | /v3/$(tenant_id)s <https: |
|                           |            | //cbr.eu-nl.otc.t-systems |
|                           |            | .com/v3/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| ccev2.0                   | eu-de      | `h                        |
|                           |            | ttps://cce.eu-de.otc.t-sy |
|                           |            | stems.com <https://cce.eu |
|                           |            | -de.otc.t-systems.com>`__ |
+---------------------------+------------+---------------------------+
| ccev2.0                   | eu-nl      | `h                        |
|                           |            | ttps://cce.eu-nl.otc.t-sy |
|                           |            | stems.com <https://cce.eu |
|                           |            | -nl.otc.t-systems.com>`__ |
+---------------------------+------------+---------------------------+
| cesv1                     | eu-de      | `https://ces.eu           |
|                           |            | -de.otc.t-systems.com/V1. |
|                           |            | 0/$(tenant_id)s <https:// |
|                           |            | ces.eu-de.otc.t-systems.c |
|                           |            | om/V1.0/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| cesv1                     | eu-nl      | `https://ces.eu           |
|                           |            | -nl.otc.t-systems.com/V1. |
|                           |            | 0/$(tenant_id)s <https:// |
|                           |            | ces.eu-nl.otc.t-systems.c |
|                           |            | om/V1.0/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| cinder                    | eu-de      | `https://ev               |
|                           |            | s.eu-de.otc.t-systems.com |
|                           |            | /v2/$(tenant_id)s <https: |
|                           |            | //evs.eu-de.otc.t-systems |
|                           |            | .com/v2/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| cinder                    | eu-nl      | `https://ev               |
|                           |            | s.eu-nl.otc.t-systems.com |
|                           |            | /v2/$(tenant_id)s <https: |
|                           |            | //evs.eu-nl.otc.t-systems |
|                           |            | .com/v2/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| cinderv2                  | eu-de      | `https://ev               |
|                           |            | s.eu-de.otc.t-systems.com |
|                           |            | /v2/$(tenant_id)s <https: |
|                           |            | //evs.eu-de.otc.t-systems |
|                           |            | .com/v2/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| cinderv2                  | eu-nl      | `https://ev               |
|                           |            | s.eu-nl.otc.t-systems.com |
|                           |            | /v2/$(tenant_id)s <https: |
|                           |            | //evs.eu-nl.otc.t-systems |
|                           |            | .com/v2/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| cinderv3                  | eu-de      | `https://ev               |
|                           |            | s.eu-de.otc.t-systems.com |
|                           |            | /v3/$(tenant_id)s <https: |
|                           |            | //evs.eu-de.otc.t-systems |
|                           |            | .com/v3/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| cinderv3                  | eu-nl      | `https://ev               |
|                           |            | s.eu-nl.otc.t-systems.com |
|                           |            | /v3/$(tenant_id)s <https: |
|                           |            | //evs.eu-nl.otc.t-systems |
|                           |            | .com/v3/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| cloudeye                  | eu-de      | `https://ces.e            |
|                           |            | u-de.otc.t-systems.com/V1 |
|                           |            | .0/ <https://ces.eu-de.ot |
|                           |            | c.t-systems.com/V1.0/>`__ |
+---------------------------+------------+---------------------------+
| cloudeye                  | eu-nl      | `https://ces.e            |
|                           |            | u-nl.otc.t-systems.com/V1 |
|                           |            | .0/ <https://ces.eu-nl.ot |
|                           |            | c.t-systems.com/V1.0/>`__ |
+---------------------------+------------+---------------------------+
| containerengine           | eu-de      | `https://cce.eu-          |
|                           |            | de.otc.t-systems.com/api/ |
|                           |            | v1 <https://cce.eu-de.otc |
|                           |            | .t-systems.com/api/v1>`__ |
+---------------------------+------------+---------------------------+
| containerengine           | eu-nl      | `https://cce.eu-          |
|                           |            | nl.otc.t-systems.com/api/ |
|                           |            | v1 <https://cce.eu-nl.otc |
|                           |            | .t-systems.com/api/v1>`__ |
+---------------------------+------------+---------------------------+
| css                       | eu-de      | `https://css.eu           |
|                           |            | -de.otc.t-systems.com/v1. |
|                           |            | 0/$(tenant_id)s <https:// |
|                           |            | css.eu-de.otc.t-systems.c |
|                           |            | om/v1.0/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| css                       | eu-nl      | `https://css.eu           |
|                           |            | -nl.otc.t-systems.com/v1. |
|                           |            | 0/$(tenant_id)s <https:// |
|                           |            | css.eu-nl.otc.t-systems.c |
|                           |            | om/v1.0/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| cts                       | eu-de      | `https://cts.eu           |
|                           |            | -de.otc.t-systems.com/v1. |
|                           |            | 0/$(tenant_id)s <https:// |
|                           |            | cts.eu-de.otc.t-systems.c |
|                           |            | om/v1.0/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| cts                       | eu-nl      | `https://cts.eu           |
|                           |            | -nl.otc.t-systems.com/v1. |
|                           |            | 0/$(tenant_id)s <https:// |
|                           |            | cts.eu-nl.otc.t-systems.c |
|                           |            | om/v1.0/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| ctsv2                     | eu-de      | `https://cts.eu           |
|                           |            | -de.otc.t-systems.com/v2. |
|                           |            | 0/$(tenant_id)s <https:// |
|                           |            | cts.eu-de.otc.t-systems.c |
|                           |            | om/v2.0/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| ctsv2                     | eu-nl      | `https://cts.eu           |
|                           |            | -nl.otc.t-systems.com/v2. |
|                           |            | 0/$(tenant_id)s <https:// |
|                           |            | cts.eu-nl.otc.t-systems.c |
|                           |            | om/v2.0/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| data ingestion service    | eu-de      | `h                        |
|                           |            | ttps://dis.eu-de.otc.t-sy |
|                           |            | stems.com <https://dis.eu |
|                           |            | -de.otc.t-systems.com>`__ |
+---------------------------+------------+---------------------------+
| datawarehouseservice      | eu-de      | `h                        |
|                           |            | ttps://dws.eu-de.otc.t-sy |
|                           |            | stems.com <https://dws.eu |
|                           |            | -de.otc.t-systems.com>`__ |
+---------------------------+------------+---------------------------+
| dcsv1                     | eu-de      | `https://dcs.eu           |
|                           |            | -de.otc.t-systems.com/v1. |
|                           |            | 0/$(tenant_id)s <https:// |
|                           |            | dcs.eu-de.otc.t-systems.c |
|                           |            | om/v1.0/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| dcsv1                     | eu-nl      | `https://dcs.eu           |
|                           |            | -nl.otc.t-systems.com/v1. |
|                           |            | 0/$(tenant_id)s <https:// |
|                           |            | dcs.eu-nl.otc.t-systems.c |
|                           |            | om/v1.0/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| ddsv3                     | eu-de      | `https://dd               |
|                           |            | s.eu-de.otc.t-systems.com |
|                           |            | /v3/$(tenant_id)s <https: |
|                           |            | //dds.eu-de.otc.t-systems |
|                           |            | .com/v3/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| ddsv3                     | eu-nl      | `https://dd               |
|                           |            | s.eu-nl.otc.t-systems.com |
|                           |            | /v3/$(tenant_id)s <https: |
|                           |            | //dds.eu-nl.otc.t-systems |
|                           |            | .com/v3/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| deh                       | eu-de      | `https://deh.eu           |
|                           |            | -de.otc.t-systems.com/v1. |
|                           |            | 0/$(tenant_id)s <https:// |
|                           |            | deh.eu-de.otc.t-systems.c |
|                           |            | om/v1.0/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| deh                       | eu-nl      | `https://deh.eu           |
|                           |            | -nl.otc.t-systems.com/v1. |
|                           |            | 0/$(tenant_id)s <https:// |
|                           |            | deh.eu-nl.otc.t-systems.c |
|                           |            | om/v1.0/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| designate                 | eu-de      | `h                        |
|                           |            | ttps://dns.eu-de.otc.t-sy |
|                           |            | stems.com <https://dns.eu |
|                           |            | -de.otc.t-systems.com>`__ |
+---------------------------+------------+---------------------------+
| designate                 | eu-nl      | `h                        |
|                           |            | ttps://dns.eu-nl.otc.t-sy |
|                           |            | stems.com <https://dns.eu |
|                           |            | -nl.otc.t-systems.com>`__ |
+---------------------------+------------+---------------------------+
| direct-connect            | eu-de      | `https://dcaas.e          |
|                           |            | u-de.otc.t-systems.com/v2 |
|                           |            | .0 <https://dcaas.eu-de.o |
|                           |            | tc.t-systems.com/v2.0>`__ |
+---------------------------+------------+---------------------------+
| distributed cache service | eu-de      | `https://dcs.e            |
|                           |            | u-de.otc.t-systems.com/v1 |
|                           |            | .0/ <https://dcs.eu-de.ot |
|                           |            | c.t-systems.com/v1.0/>`__ |
+---------------------------+------------+---------------------------+
| distributed cache service | eu-nl      | `https://dcs.e            |
|                           |            | u-nl.otc.t-systems.com/v1 |
|                           |            | .0/ <https://dcs.eu-nl.ot |
|                           |            | c.t-systems.com/v1.0/>`__ |
+---------------------------+------------+---------------------------+
| distributedmessageservice | eu-de      | `https://dms              |
|                           |            | .eu-de.otc.t-systems.com/ |
|                           |            | v1.0 <https://dms.eu-de.o |
|                           |            | tc.t-systems.com/v1.0>`__ |
+---------------------------+------------+---------------------------+
| distributedmessageservice | eu-nl      | `https://dms              |
|                           |            | .eu-nl.otc.t-systems.com/ |
|                           |            | v1.0 <https://dms.eu-nl.o |
|                           |            | tc.t-systems.com/v1.0>`__ |
+---------------------------+------------+---------------------------+
| disv2                     | eu-de      | `https://di               |
|                           |            | s.eu-de.otc.t-systems.com |
|                           |            | /v2/$(tenant_id)s <https: |
|                           |            | //dis.eu-de.otc.t-systems |
|                           |            | .com/v2/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| dmsv1                     | eu-de      | `https://dms.eu           |
|                           |            | -de.otc.t-systems.com/v1. |
|                           |            | 0/$(tenant_id)s <https:// |
|                           |            | dms.eu-de.otc.t-systems.c |
|                           |            | om/v1.0/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| dmsv1                     | eu-nl      | `https://dms.eu           |
|                           |            | -nl.otc.t-systems.com/v1. |
|                           |            | 0/$(tenant_id)s <https:// |
|                           |            | dms.eu-nl.otc.t-systems.c |
|                           |            | om/v1.0/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| dwsv1                     | eu-de      | `https://dws.eu           |
|                           |            | -de.otc.t-systems.com/v1. |
|                           |            | 0/$(tenant_id)s <https:// |
|                           |            | dws.eu-de.otc.t-systems.c |
|                           |            | om/v1.0/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| ecs                       | eu-de      | `https://ec               |
|                           |            | s.eu-de.otc.t-systems.com |
|                           |            | /v1/$(tenant_id)s <https: |
|                           |            | //ecs.eu-de.otc.t-systems |
|                           |            | .com/v1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| ecs                       | eu-nl      | `https://ec               |
|                           |            | s.eu-nl.otc.t-systems.com |
|                           |            | /v1/$(tenant_id)s <https: |
|                           |            | //ecs.eu-nl.otc.t-systems |
|                           |            | .com/v1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| elbv1                     | eu-de      | `https://elb.eu           |
|                           |            | -de.otc.t-systems.com/v1. |
|                           |            | 0/$(tenant_id)s <https:// |
|                           |            | elb.eu-de.otc.t-systems.c |
|                           |            | om/v1.0/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| elbv3                     | eu-de      | `https://el               |
|                           |            | b.eu-de.otc.t-systems.com |
|                           |            | /v3/$(tenant_id)s <https: |
|                           |            | //elb.eu-de.otc.t-systems |
|                           |            | .com/v3/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| elbv3                     | eu-nl      | `https://el               |
|                           |            | b.eu-nl.otc.t-systems.com |
|                           |            | /v3/$(tenant_id)s <https: |
|                           |            | //elb.eu-nl.otc.t-systems |
|                           |            | .com/v3/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| evs                       | eu-de      | `https://ev               |
|                           |            | s.eu-de.otc.t-systems.com |
|                           |            | /v2/$(tenant_id)s <https: |
|                           |            | //evs.eu-de.otc.t-systems |
|                           |            | .com/v2/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| evs                       | eu-nl      | `https://ev               |
|                           |            | s.eu-nl.otc.t-systems.com |
|                           |            | /v2/$(tenant_id)s <https: |
|                           |            | //evs.eu-nl.otc.t-systems |
|                           |            | .com/v2/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| glance                    | eu-de      | `h                        |
|                           |            | ttps://ims.eu-de.otc.t-sy |
|                           |            | stems.com <https://ims.eu |
|                           |            | -de.otc.t-systems.com>`__ |
+---------------------------+------------+---------------------------+
| glance                    | eu-nl      | `h                        |
|                           |            | ttps://ims.eu-nl.otc.t-sy |
|                           |            | stems.com <https://ims.eu |
|                           |            | -nl.otc.t-systems.com>`__ |
+---------------------------+------------+---------------------------+
| heat                      | eu-de      | `https://rt               |
|                           |            | s.eu-de.otc.t-systems.com |
|                           |            | /v1/$(tenant_id)s <https: |
|                           |            | //rts.eu-de.otc.t-systems |
|                           |            | .com/v1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| heat                      | eu-nl      | `https://rt               |
|                           |            | s.eu-nl.otc.t-systems.com |
|                           |            | /v1/$(tenant_id)s <https: |
|                           |            | //rts.eu-nl.otc.t-systems |
|                           |            | .com/v1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| karbor                    | eu-de      | `https://csbs             |
|                           |            | .eu-de.otc.t-systems.com/ |
|                           |            | v1/$(tenant_id)s <https:/ |
|                           |            | /csbs.eu-de.otc.t-systems |
|                           |            | .com/v1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| key-management            | eu-de      | `https://kms.e            |
|                           |            | u-de.otc.t-systems.com/v1 |
|                           |            | .0/ <https://kms.eu-de.ot |
|                           |            | c.t-systems.com/v1.0/>`__ |
+---------------------------+------------+---------------------------+
| key-management            | eu-nl      | `https://kms.e            |
|                           |            | u-nl.otc.t-systems.com/v1 |
|                           |            | .0/ <https://kms.eu-nl.ot |
|                           |            | c.t-systems.com/v1.0/>`__ |
+---------------------------+------------+---------------------------+
| keystone                  | eu-de      | `https:/                  |
|                           |            | /iam.eu-de.otc.t-systems. |
|                           |            | com/v3 <https://iam.eu-de |
|                           |            | .otc.t-systems.com/v3>`__ |
+---------------------------+------------+---------------------------+
| keystone                  | eu-nl      | `https:/                  |
|                           |            | /iam.eu-nl.otc.t-systems. |
|                           |            | com/v3 <https://iam.eu-nl |
|                           |            | .otc.t-systems.com/v3>`__ |
+---------------------------+------------+---------------------------+
| kmsv1                     | eu-de      | `https://kms.eu           |
|                           |            | -de.otc.t-systems.com/v1. |
|                           |            | 0/$(tenant_id)s <https:// |
|                           |            | kms.eu-de.otc.t-systems.c |
|                           |            | om/v1.0/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| kmsv1                     | eu-nl      | `https://kms.eu           |
|                           |            | -nl.otc.t-systems.com/v1. |
|                           |            | 0/$(tenant_id)s <https:// |
|                           |            | kms.eu-nl.otc.t-systems.c |
|                           |            | om/v1.0/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| loadbalance               | eu-de      | `https://elb              |
|                           |            | .eu-de.otc.t-systems.com/ |
|                           |            | v1.0 <https://elb.eu-de.o |
|                           |            | tc.t-systems.com/v1.0>`__ |
+---------------------------+------------+---------------------------+
| loadbalance               | eu-nl      | `h                        |
|                           |            | ttps://elb.eu-nl.otc.t-sy |
|                           |            | stems.com <https://elb.eu |
|                           |            | -nl.otc.t-systems.com>`__ |
+---------------------------+------------+---------------------------+
| manilav2                  | eu-de      | `https://sf               |
|                           |            | s.eu-de.otc.t-systems.com |
|                           |            | /v2/$(tenant_id)s <https: |
|                           |            | //sfs.eu-de.otc.t-systems |
|                           |            | .com/v2/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| manilav2                  | eu-nl      | `https://sf               |
|                           |            | s.eu-nl.otc.t-systems.com |
|                           |            | /v2/$(tenant_id)s <https: |
|                           |            | //sfs.eu-nl.otc.t-systems |
|                           |            | .com/v2/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| mapreduce                 | eu-de      | `https://mrs              |
|                           |            | .eu-de.otc.t-systems.com/ |
|                           |            | v1.1 <https://mrs.eu-de.o |
|                           |            | tc.t-systems.com/v1.1>`__ |
+---------------------------+------------+---------------------------+
| modelarts                 | eu-de      | `https://modelarts.eu-d   |
|                           |            | e.otc.t-systems.com/v1/$( |
|                           |            | tenant_id)s <https://mode |
|                           |            | larts.eu-de.otc.t-systems |
|                           |            | .com/v1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| modelarts                 | eu-de      | `https://modelarts.eu-d   |
|                           |            | e.otc.t-systems.com/v2/$( |
|                           |            | tenant_id)s <https://mode |
|                           |            | larts.eu-de.otc.t-systems |
|                           |            | .com/v2/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| mrsv1                     | eu-de      | `https://mrs.eu           |
|                           |            | -de.otc.t-systems.com/v1. |
|                           |            | 1/$(tenant_id)s <https:// |
|                           |            | mrs.eu-de.otc.t-systems.c |
|                           |            | om/v1.1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| nat                       | eu-de      | `https://nat              |
|                           |            | .eu-de.otc.t-systems.com/ |
|                           |            | v2.0 <https://nat.eu-de.o |
|                           |            | tc.t-systems.com/v2.0>`__ |
+---------------------------+------------+---------------------------+
| nat                       | eu-nl      | `https://nat              |
|                           |            | .eu-nl.otc.t-systems.com/ |
|                           |            | v2.0 <https://nat.eu-nl.o |
|                           |            | tc.t-systems.com/v2.0>`__ |
+---------------------------+------------+---------------------------+
| neutron                   | eu-de      | `h                        |
|                           |            | ttps://vpc.eu-de.otc.t-sy |
|                           |            | stems.com <https://vpc.eu |
|                           |            | -de.otc.t-systems.com>`__ |
+---------------------------+------------+---------------------------+
| neutron                   | eu-nl      | `h                        |
|                           |            | ttps://vpc.eu-nl.otc.t-sy |
|                           |            | stems.com <https://vpc.eu |
|                           |            | -nl.otc.t-systems.com>`__ |
+---------------------------+------------+---------------------------+
| nova                      | eu-de      | `https://ecs.eu           |
|                           |            | -de.otc.t-systems.com/v2. |
|                           |            | 1/$(tenant_id)s <https:// |
|                           |            | ecs.eu-de.otc.t-systems.c |
|                           |            | om/v2.1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| nova                      | eu-nl      | `https://ecs.eu           |
|                           |            | -nl.otc.t-systems.com/v2. |
|                           |            | 1/$(tenant_id)s <https:// |
|                           |            | ecs.eu-nl.otc.t-systems.c |
|                           |            | om/v2.1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| objectstorage             | eu-de      | `h                        |
|                           |            | ttps://obs.eu-de.otc.t-sy |
|                           |            | stems.com <https://obs.eu |
|                           |            | -de.otc.t-systems.com>`__ |
+---------------------------+------------+---------------------------+
| objectstorage             | eu-nl      | `h                        |
|                           |            | ttps://obs.eu-nl.otc.t-sy |
|                           |            | stems.com <https://obs.eu |
|                           |            | -nl.otc.t-systems.com>`__ |
+---------------------------+------------+---------------------------+
| octavia                   | eu-nl      | `https://o                |
|                           |            | ctavia.eu-nl.otc.t-system |
|                           |            | s.com <https://octavia.eu |
|                           |            | -nl.otc.t-systems.com>`__ |
+---------------------------+------------+---------------------------+
| rdsv1                     | eu-de      | `https://rds.eu-de.       |
|                           |            | otc.t-systems.com/rds/v1/ |
|                           |            | $(tenant_id)s <https://rd |
|                           |            | s.eu-de.otc.t-systems.com |
|                           |            | /rds/v1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| rdsv1                     | eu-nl      | `https://rds.eu-nl.       |
|                           |            | otc.t-systems.com/rds/v1/ |
|                           |            | $(tenant_id)s <https://rd |
|                           |            | s.eu-nl.otc.t-systems.com |
|                           |            | /rds/v1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| rdsv3                     | eu-de      | `https://rd               |
|                           |            | s.eu-de.otc.t-systems.com |
|                           |            | /v3/$(tenant_id)s <https: |
|                           |            | //rds.eu-de.otc.t-systems |
|                           |            | .com/v3/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| rdsv3                     | eu-nl      | `https://rd               |
|                           |            | s.eu-nl.otc.t-systems.com |
|                           |            | /v3/$(tenant_id)s <https: |
|                           |            | //rds.eu-nl.otc.t-systems |
|                           |            | .com/v3/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| relationaldatabase        | eu-de      | `https://rds.eu-          |
|                           |            | de.otc.t-systems.com/rds/ |
|                           |            | v1 <https://rds.eu-de.otc |
|                           |            | .t-systems.com/rds/v1>`__ |
+---------------------------+------------+---------------------------+
| relationaldatabase        | eu-nl      | `https://rds.eu-          |
|                           |            | nl.otc.t-systems.com/rds/ |
|                           |            | v1 <https://rds.eu-nl.otc |
|                           |            | .t-systems.com/rds/v1>`__ |
+---------------------------+------------+---------------------------+
| sdrs                      | eu-de      | `https://sdrs             |
|                           |            | .eu-de.otc.t-systems.com/ |
|                           |            | v1/$(tenant_id)s <https:/ |
|                           |            | /sdrs.eu-de.otc.t-systems |
|                           |            | .com/v1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| sfs                       | eu-de      | `https://sf               |
|                           |            | s.eu-de.otc.t-systems.com |
|                           |            | /v2/$(tenant_id)s <https: |
|                           |            | //sfs.eu-de.otc.t-systems |
|                           |            | .com/v2/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| sfsturbo                  | eu-de      | `https://sfs-turbo.eu-d   |
|                           |            | e.otc.t-systems.com/v1/$( |
|                           |            | tenant_id)s <https://sfs- |
|                           |            | turbo.eu-de.otc.t-systems |
|                           |            | .com/v1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| sfsturbo                  | eu-nl      | `https://sfs-turbo.eu-n   |
|                           |            | l.otc.t-systems.com/v1/$( |
|                           |            | tenant_id)s <https://sfs- |
|                           |            | turbo.eu-nl.otc.t-systems |
|                           |            | .com/v1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| simplemessagenotification | eu-de      | `https://s                |
|                           |            | mn.eu-de.otc.t-systems.co |
|                           |            | m/v2/ <https://smn.eu-de. |
|                           |            | otc.t-systems.com/v2/>`__ |
+---------------------------+------------+---------------------------+
| simplemessagenotification | eu-nl      | `https://s                |
|                           |            | mn.eu-nl.otc.t-systems.co |
|                           |            | m/v2/ <https://smn.eu-nl. |
|                           |            | otc.t-systems.com/v2/>`__ |
+---------------------------+------------+---------------------------+
| smnv2                     | eu-de      | `https://sm               |
|                           |            | n.eu-de.otc.t-systems.com |
|                           |            | /v2/$(tenant_id)s <https: |
|                           |            | //smn.eu-de.otc.t-systems |
|                           |            | .com/v2/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| smnv2                     | eu-nl      | `https://sm               |
|                           |            | n.eu-nl.otc.t-systems.com |
|                           |            | /v2/$(tenant_id)s <https: |
|                           |            | //smn.eu-nl.otc.t-systems |
|                           |            | .com/v2/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| swift                     | eu-de      | `https://swift.eu-de.otc. |
|                           |            | t-systems.com/v1/AUTH_$(t |
|                           |            | enant_id)s <https://swift |
|                           |            | .eu-de.otc.t-systems.com/ |
|                           |            | v1/AUTH_$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| tag-management            | eu-de      | `https://tms              |
|                           |            | .eu-de.otc.t-systems.com/ |
|                           |            | v1.0 <https://tms.eu-de.o |
|                           |            | tc.t-systems.com/v1.0>`__ |
+---------------------------+------------+---------------------------+
| tag-management            | eu-nl      | `https://tms              |
|                           |            | .eu-nl.otc.t-systems.com/ |
|                           |            | v1.0 <https://tms.eu-nl.o |
|                           |            | tc.t-systems.com/v1.0>`__ |
+---------------------------+------------+---------------------------+
| trove                     | eu-de      | `https://rds              |
|                           |            | .eu-de.otc.t-systems.com/ |
|                           |            | v1.0 <https://rds.eu-de.o |
|                           |            | tc.t-systems.com/v1.0>`__ |
+---------------------------+------------+---------------------------+
| trove                     | eu-nl      | `https://rds              |
|                           |            | .eu-nl.otc.t-systems.com/ |
|                           |            | v1.0 <https://rds.eu-nl.o |
|                           |            | tc.t-systems.com/v1.0>`__ |
+---------------------------+------------+---------------------------+
| vbsv2                     | eu-de      | `https://vb               |
|                           |            | s.eu-de.otc.t-systems.com |
|                           |            | /v2/$(tenant_id)s <https: |
|                           |            | //vbs.eu-de.otc.t-systems |
|                           |            | .com/v2/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| volume-backup             | eu-de      | `https://v                |
|                           |            | bs.eu-de.otc.t-systems.co |
|                           |            | m/v2/ <https://vbs.eu-de. |
|                           |            | otc.t-systems.com/v2/>`__ |
+---------------------------+------------+---------------------------+
| vpc                       | eu-de      | `https://vp               |
|                           |            | c.eu-de.otc.t-systems.com |
|                           |            | /v1/$(tenant_id)s <https: |
|                           |            | //vpc.eu-de.otc.t-systems |
|                           |            | .com/v1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| vpc                       | eu-nl      | `https://vp               |
|                           |            | c.eu-nl.otc.t-systems.com |
|                           |            | /v1/$(tenant_id)s <https: |
|                           |            | //vpc.eu-nl.otc.t-systems |
|                           |            | .com/v1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| vpc2.0                    | eu-de      | `https://vpc.eu           |
|                           |            | -de.otc.t-systems.com/v2. |
|                           |            | 0/$(tenant_id)s <https:// |
|                           |            | vpc.eu-de.otc.t-systems.c |
|                           |            | om/v2.0/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| vpcep                     | eu-de      | `https://vpcep.           |
|                           |            | eu-de.otc.t-systems.com/v |
|                           |            | 1/$(tenant_id)s <https:// |
|                           |            | vpcep.eu-de.otc.t-systems |
|                           |            | .com/v1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| vpcep                     | eu-nl      | `https://vpcep.           |
|                           |            | eu-nl.otc.t-systems.com/v |
|                           |            | 1/$(tenant_id)s <https:// |
|                           |            | vpcep.eu-nl.otc.t-systems |
|                           |            | .com/v1/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+
| waf                       | eu-de      | `h                        |
|                           |            | ttps://waf.eu-de.otc.t-sy |
|                           |            | stems.com <https://waf.eu |
|                           |            | -de.otc.t-systems.com>`__ |
+---------------------------+------------+---------------------------+
| waf                       | eu-nl      | `h                        |
|                           |            | ttps://waf.eu-nl.otc.t-sy |
|                           |            | stems.com <https://waf.eu |
|                           |            | -nl.otc.t-systems.com>`__ |
+---------------------------+------------+---------------------------+
| workspace                 | eu-de      | `h                        |
|                           |            | ttps://workspace.eu-de.ot |
|                           |            | c.t-systems.com/v1.0/$(te |
|                           |            | nant_id)s <https://worksp |
|                           |            | ace.eu-de.otc.t-systems.c |
|                           |            | om/v1.0/$(tenant_id)s>`__ |
+---------------------------+------------+---------------------------+

We again recommend to not hardcode the IP addresses as we do reserve the
right to change them.

.. |image01| image:: /_static/images/image-factory-customer-information-windows-password.png
