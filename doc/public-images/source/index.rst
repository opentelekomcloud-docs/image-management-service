====================================================
Image Management Service - Public Image Introduction
====================================================

Customer documentation for public images at OpenTelekomCloud
============================================================

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

+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| IP                   | DNS Name                            | Type of Service              | Notes                                                                    |
+======================+=====================================+==============================+==========================================================================+
| 100.125.4.25         |                                     | DNS                          | HA Setup                                                                 |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 100.125.129.199      |                                     | DNS                          | HA Setup                                                                 |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 100.125.4.28         | ntp01.eu-de.otc-service.com         | NTP                          | AZ1                                                                      |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 100.125.4.29         | ntp02.eu-de.otc-service.com         | NTP                          | AZ2                                                                      |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 100.125.0.15         | ntp01.eu-nl.otc-service.com         | NTP                          | AZ1                                                                      |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 100.125.0.16         | ntp02.eu-nl.otc-service.com         | NTP                          | AZ2                                                                      |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 198.19.33.237        | vendordata.eu-de.otc-service.com    | Vendordata OpenStack (HTTP)  | first boot provisioning                                                  |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 100.125.1.10         | vendordata.eu-nl.otc-service.com    | Vendordata OpenStack (HTTP)  | first boot provisioning                                                  |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 100.125.4.20         | smt.eu-de.otc-service.com           | Repo (HTTP)                  | openSUSE, SLES, EulerOS, OpenEuler, CentOS, Oracle, Fedora, Alma, Rocky  |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 100.125.1.15         | smt.eu-nl.otc-service.com           | Repo (HTTP)                  | openSUSE, SLES, EulerOS, OpenEuler, CentOS, Oracle, Fedora, Alma, Rocky  |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 198.19.61.228        | debmirror.eu-de.otc-service.com     | Repo (HTTP)                  | Debian, Ubuntu                                                           |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 100.125.1.11         | debmirror.eu-nl.otc-service.com     | Repo (HTTP)                  | Debian, Ubuntu                                                           |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 198.19.41.19         | rhui.eu-de.otc-service.com          | RHUI (HTTPS)                 | RedHat 6/7/8/9 Update Infra                                              |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 100.125.1.25         | rhui.eu-nl.otc-service.com          | RHUI (HTTPS)                 | RedHat 6/7/8/9 Update Infra                                              |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 198.19.55.230        | kms.eu-de.otc-service.com           | KMS                          | Windows activation                                                       |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 100.125.1.17         | kms.eu-nl.otc-service.com           | KMS                          | Windows activation                                                       |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 198.19.35.231        | wsus.eu-de.otc-service.com          | WSUS                         | Windows updates (WSUS)                                                   |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 100.125.1.18         | wsus.eu-nl.otc-service.com          | WSUS                         | Windows updates (WSUS)                                                   |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 198.19.34.77         | gpulicence01.eu-de.otc-service.com  | NLS                          | NVIDIA License Server                                                    |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 198.19.44.221        | gpulicence02.eu-de.otc-service.com  | NLS                          | NVIDIA License Server                                                    |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 100.125.1.27         | gpulicence01.eu-nl.otc-service.com  | NLS                          | NVIDIA License Server                                                    |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+
| 100.125.1.28         | gpulicence02.eu-nl.otc-service.com  | NLS                          | NVIDIA License Server                                                    |
+----------------------+-------------------------------------+------------------------------+--------------------------------------------------------------------------+


As part of that we recently migrated to new debmirrors (and also
vendordata servers => required at the first boot of an ECS/BMS server)
in a different IP address range.

.. warning::

   Currently there are two ip address blocks, which contain OTC
   services: 100.64.0.0/10 and 198.19.0.0/16. **Whitelisting** both blocks
   is sufficient for the foreseeable future, since we do not plan to use
   any addresses outside these ranges. Please do not whitelist single ip
   addresses out of these ranges, because it is possible that we migrate to
   different ip addresses within these ranges without any prior warning.

.. warning::

   Also please note that the other package repositories (rhui, smt,
   wsus/kms) and the Nvidia license servers are destined to be migrated to
   the 198.19.0.0/16 range.

Image types and naming convention
---------------------------------

On the Open Telekom Cloud platform the following public images are
provided.

Preview/Beta
~~~~~~~~~~~~

These are free self-managed images, which have been build within the 
T-Systems OTC Image Factory and not yet ready for GA. It is intended 
to test the customer's requirements for later live operation and to 
improve performance. They have received some general OTC related settings 
and basic hardening.

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

Preview/Beta
~~~~~~~~~~~~

Password login: Only possible on the console. Default user is ``linux``.
A random password is generated during ECS creation. The Password is
shown on the noVNC console. SSH login: With default user ``linux``. For
Ubuntu related images only SSH login with user ``ubuntu`` will work.

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
shown on the noVNC console. SSH login: With default user ``linux``. For
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

.. note::

   Important: Do not override bootcmd in ``user_data`` nor disable
   ``vendor_data`` if you need working update repositories in your VM
   created from public images in OTC!

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

Timezone: UTC 

Keyboard: en_US

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

+----------------------------+---------+----------------------------------------------------------------------+
| service                    | region  | endpoint                                                             |
+============================+=========+======================================================================+
| anti-ddos                  | eu-de   | https://antiddos.eu-de.otc.t-systems.com/v1/$(tenant_id)s            |
+----------------------------+---------+----------------------------------------------------------------------+
| anti-ddos                  | eu-nl   | https://antiddos.eu-nl.otc.t-systems.com/v1/$(tenant_id)s            |
+----------------------------+---------+----------------------------------------------------------------------+
| antiddos                   | eu-de   | https://antiddos.eu-de.otc.t-systems.com/v1/                         |
+----------------------------+---------+----------------------------------------------------------------------+
| antiddos                   | eu-nl   | https://antiddos.eu-nl.otc.t-systems.com/v1/                         |
+----------------------------+---------+----------------------------------------------------------------------+
| asv1                       | eu-de   | https://as.eu-de.otc.t-systems.com/autoscaling-api/v1/$(tenant_id)s  |
+----------------------------+---------+----------------------------------------------------------------------+
| asv1                       | eu-nl   | https://as.eu-nl.otc.t-systems.com/autoscaling-api/v1/$(tenant_id)s  |
+----------------------------+---------+----------------------------------------------------------------------+
| autoscaling                | eu-de   | https://as.eu-de.otc.t-systems.com/autoscaling-api/v1                |
+----------------------------+---------+----------------------------------------------------------------------+
| autoscaling                | eu-nl   | https://as.eu-nl.otc.t-systems.com/autoscaling-api/v1                |
+----------------------------+---------+----------------------------------------------------------------------+
| bms                        | eu-de   | https://bms.eu-de.otc.t-systems.com/v1/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| cbr                        | eu-de   | https://cbr.eu-de.otc.t-systems.com/v3/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| cbr                        | eu-nl   | https://cbr.eu-nl.otc.t-systems.com/v3/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| ccev2.0                    | eu-de   | https://cce.eu-de.otc.t-systems.com                                  |
+----------------------------+---------+----------------------------------------------------------------------+
| ccev2.0                    | eu-nl   | https://cce.eu-nl.otc.t-systems.com                                  |
+----------------------------+---------+----------------------------------------------------------------------+
| cesv1                      | eu-de   | https://ces.eu-de.otc.t-systems.com/V1.0/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| cesv1                      | eu-nl   | https://ces.eu-nl.otc.t-systems.com/V1.0/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| cinder                     | eu-de   | https://evs.eu-de.otc.t-systems.com/v2/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| cinder                     | eu-nl   | https://evs.eu-nl.otc.t-systems.com/v2/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| cinderv2                   | eu-de   | https://evs.eu-de.otc.t-systems.com/v2/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| cinderv2                   | eu-nl   | https://evs.eu-nl.otc.t-systems.com/v2/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| cinderv3                   | eu-de   | https://evs.eu-de.otc.t-systems.com/v3/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| cinderv3                   | eu-nl   | https://evs.eu-nl.otc.t-systems.com/v3/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| cloudeye                   | eu-de   | https://ces.eu-de.otc.t-systems.com/V1.0/                            |
+----------------------------+---------+----------------------------------------------------------------------+
| cloudeye                   | eu-nl   | https://ces.eu-nl.otc.t-systems.com/V1.0/                            |
+----------------------------+---------+----------------------------------------------------------------------+
| containerengine            | eu-de   | https://cce.eu-de.otc.t-systems.com/api/v1                           |
+----------------------------+---------+----------------------------------------------------------------------+
| containerengine            | eu-nl   | https://cce.eu-nl.otc.t-systems.com/api/v1                           |
+----------------------------+---------+----------------------------------------------------------------------+
| css                        | eu-de   | https://css.eu-de.otc.t-systems.com/v1.0/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| css                        | eu-nl   | https://css.eu-nl.otc.t-systems.com/v1.0/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| cts                        | eu-de   | https://cts.eu-de.otc.t-systems.com/v1.0/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| cts                        | eu-nl   | https://cts.eu-nl.otc.t-systems.com/v1.0/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| ctsv2                      | eu-de   | https://cts.eu-de.otc.t-systems.com/v2.0/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| ctsv2                      | eu-nl   | https://cts.eu-nl.otc.t-systems.com/v2.0/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| data ingestion service     | eu-de   | https://dis.eu-de.otc.t-systems.com                                  |
+----------------------------+---------+----------------------------------------------------------------------+
| datawarehouseservice       | eu-de   | https://dws.eu-de.otc.t-systems.com                                  |
+----------------------------+---------+----------------------------------------------------------------------+
| dcsv1                      | eu-de   | https://dcs.eu-de.otc.t-systems.com/v1.0/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| dcsv1                      | eu-nl   | https://dcs.eu-nl.otc.t-systems.com/v1.0/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| ddsv3                      | eu-de   | https://dds.eu-de.otc.t-systems.com/v3/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| ddsv3                      | eu-nl   | https://dds.eu-nl.otc.t-systems.com/v3/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| deh                        | eu-de   | https://deh.eu-de.otc.t-systems.com/v1.0/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| deh                        | eu-nl   | https://deh.eu-nl.otc.t-systems.com/v1.0/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| designate                  | eu-de   | https://dns.eu-de.otc.t-systems.com                                  |
+----------------------------+---------+----------------------------------------------------------------------+
| designate                  | eu-nl   | https://dns.eu-nl.otc.t-systems.com                                  |
+----------------------------+---------+----------------------------------------------------------------------+
| direct-connect             | eu-de   | https://dcaas.eu-de.otc.t-systems.com/v2.0                           |
+----------------------------+---------+----------------------------------------------------------------------+
| distributed cache service  | eu-de   | https://dcs.eu-de.otc.t-systems.com/v1.0/                            |
+----------------------------+---------+----------------------------------------------------------------------+
| distributed cache service  | eu-nl   | https://dcs.eu-nl.otc.t-systems.com/v1.0/                            |
+----------------------------+---------+----------------------------------------------------------------------+
| distributedmessageservice  | eu-de   | https://dms.eu-de.otc.t-systems.com/v1.0                             |
+----------------------------+---------+----------------------------------------------------------------------+
| distributedmessageservice  | eu-nl   | https://dms.eu-nl.otc.t-systems.com/v1.0                             |
+----------------------------+---------+----------------------------------------------------------------------+
| disv2                      | eu-de   | https://dis.eu-de.otc.t-systems.com/v2/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| dmsv1                      | eu-de   | https://dms.eu-de.otc.t-systems.com/v1.0/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| dmsv1                      | eu-nl   | https://dms.eu-nl.otc.t-systems.com/v1.0/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| dwsv1                      | eu-de   | https://dws.eu-de.otc.t-systems.com/v1.0/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| ecs                        | eu-de   | https://ecs.eu-de.otc.t-systems.com/v1/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| ecs                        | eu-nl   | https://ecs.eu-nl.otc.t-systems.com/v1/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| elbv1                      | eu-de   | https://elb.eu-de.otc.t-systems.com/v1.0/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| elbv3                      | eu-de   | https://elb.eu-de.otc.t-systems.com/v3/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| elbv3                      | eu-nl   | https://elb.eu-nl.otc.t-systems.com/v3/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| evs                        | eu-de   | https://evs.eu-de.otc.t-systems.com/v2/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| evs                        | eu-nl   | https://evs.eu-nl.otc.t-systems.com/v2/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| glance                     | eu-de   | https://ims.eu-de.otc.t-systems.com                                  |
+----------------------------+---------+----------------------------------------------------------------------+
| glance                     | eu-nl   | https://ims.eu-nl.otc.t-systems.com                                  |
+----------------------------+---------+----------------------------------------------------------------------+
| heat                       | eu-de   | https://rts.eu-de.otc.t-systems.com/v1/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| heat                       | eu-nl   | https://rts.eu-nl.otc.t-systems.com/v1/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| karbor                     | eu-de   | https://csbs.eu-de.otc.t-systems.com/v1/$(tenant_id)s                |
+----------------------------+---------+----------------------------------------------------------------------+
| key-management             | eu-de   | https://kms.eu-de.otc.t-systems.com/v1.0/                            |
+----------------------------+---------+----------------------------------------------------------------------+
| key-management             | eu-nl   | https://kms.eu-nl.otc.t-systems.com/v1.0/                            |
+----------------------------+---------+----------------------------------------------------------------------+
| keystone                   | eu-de   | https://iam.eu-de.otc.t-systems.com/v3                               |
+----------------------------+---------+----------------------------------------------------------------------+
| keystone                   | eu-nl   | https://iam.eu-nl.otc.t-systems.com/v3                               |
+----------------------------+---------+----------------------------------------------------------------------+
| kmsv1                      | eu-de   | https://kms.eu-de.otc.t-systems.com/v1.0/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| kmsv1                      | eu-nl   | https://kms.eu-nl.otc.t-systems.com/v1.0/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| loadbalance                | eu-de   | https://elb.eu-de.otc.t-systems.com/v1.0                             |
+----------------------------+---------+----------------------------------------------------------------------+
| loadbalance                | eu-nl   | https://elb.eu-nl.otc.t-systems.com                                  |
+----------------------------+---------+----------------------------------------------------------------------+
| manilav2                   | eu-de   | https://sfs.eu-de.otc.t-systems.com/v2/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| manilav2                   | eu-nl   | https://sfs.eu-nl.otc.t-systems.com/v2/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| mapreduce                  | eu-de   | https://mrs.eu-de.otc.t-systems.com/v1.1                             |
+----------------------------+---------+----------------------------------------------------------------------+
| modelarts                  | eu-de   | https://modelarts.eu-de.otc.t-systems.com/v1/$(tenant_id)s           |
+----------------------------+---------+----------------------------------------------------------------------+
| modelarts                  | eu-de   | https://modelarts.eu-de.otc.t-systems.com/v2/$(tenant_id)s           |
+----------------------------+---------+----------------------------------------------------------------------+
| mrsv1                      | eu-de   | https://mrs.eu-de.otc.t-systems.com/v1.1/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| nat                        | eu-de   | https://nat.eu-de.otc.t-systems.com/v2.0                             |
+----------------------------+---------+----------------------------------------------------------------------+
| nat                        | eu-nl   | https://nat.eu-nl.otc.t-systems.com/v2.0                             |
+----------------------------+---------+----------------------------------------------------------------------+
| neutron                    | eu-de   | https://vpc.eu-de.otc.t-systems.com                                  |
+----------------------------+---------+----------------------------------------------------------------------+
| neutron                    | eu-nl   | https://vpc.eu-nl.otc.t-systems.com                                  |
+----------------------------+---------+----------------------------------------------------------------------+
| nova                       | eu-de   | https://ecs.eu-de.otc.t-systems.com/v2.1/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| nova                       | eu-nl   | https://ecs.eu-nl.otc.t-systems.com/v2.1/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| objectstorage              | eu-de   | https://obs.eu-de.otc.t-systems.com                                  |
+----------------------------+---------+----------------------------------------------------------------------+
| objectstorage              | eu-nl   | https://obs.eu-nl.otc.t-systems.com                                  |
+----------------------------+---------+----------------------------------------------------------------------+
| octavia                    | eu-nl   | https://octavia.eu-nl.otc.t-systems.com                              |
+----------------------------+---------+----------------------------------------------------------------------+
| rdsv1                      | eu-de   | https://rds.eu-de.otc.t-systems.com/rds/v1/$(tenant_id)s             |
+----------------------------+---------+----------------------------------------------------------------------+
| rdsv1                      | eu-nl   | https://rds.eu-nl.otc.t-systems.com/rds/v1/$(tenant_id)s             |
+----------------------------+---------+----------------------------------------------------------------------+
| rdsv3                      | eu-de   | https://rds.eu-de.otc.t-systems.com/v3/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| rdsv3                      | eu-nl   | https://rds.eu-nl.otc.t-systems.com/v3/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| relationaldatabase         | eu-de   | https://rds.eu-de.otc.t-systems.com/rds/v1                           |
+----------------------------+---------+----------------------------------------------------------------------+
| relationaldatabase         | eu-nl   | https://rds.eu-nl.otc.t-systems.com/rds/v1                           |
+----------------------------+---------+----------------------------------------------------------------------+
| sdrs                       | eu-de   | https://sdrs.eu-de.otc.t-systems.com/v1/$(tenant_id)s                |
+----------------------------+---------+----------------------------------------------------------------------+
| sfs                        | eu-de   | https://sfs.eu-de.otc.t-systems.com/v2/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| sfsturbo                   | eu-de   | https://sfs-turbo.eu-de.otc.t-systems.com/v1/$(tenant_id)s           |
+----------------------------+---------+----------------------------------------------------------------------+
| sfsturbo                   | eu-nl   | https://sfs-turbo.eu-nl.otc.t-systems.com/v1/$(tenant_id)s           |
+----------------------------+---------+----------------------------------------------------------------------+
| simplemessagenotification  | eu-de   | https://smn.eu-de.otc.t-systems.com/v2/                              |
+----------------------------+---------+----------------------------------------------------------------------+
| simplemessagenotification  | eu-nl   | https://smn.eu-nl.otc.t-systems.com/v2/                              |
+----------------------------+---------+----------------------------------------------------------------------+
| smnv2                      | eu-de   | https://smn.eu-de.otc.t-systems.com/v2/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| smnv2                      | eu-nl   | https://smn.eu-nl.otc.t-systems.com/v2/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| swift                      | eu-de   | https://swift.eu-de.otc.t-systems.com/v1/AUTH_$(tenant_id)s          |
+----------------------------+---------+----------------------------------------------------------------------+
| tag-management             | eu-de   | https://tms.eu-de.otc.t-systems.com/v1.0                             |
+----------------------------+---------+----------------------------------------------------------------------+
| tag-management             | eu-nl   | https://tms.eu-nl.otc.t-systems.com/v1.0                             |
+----------------------------+---------+----------------------------------------------------------------------+
| trove                      | eu-de   | https://rds.eu-de.otc.t-systems.com/v1.0                             |
+----------------------------+---------+----------------------------------------------------------------------+
| trove                      | eu-nl   | https://rds.eu-nl.otc.t-systems.com/v1.0                             |
+----------------------------+---------+----------------------------------------------------------------------+
| vbsv2                      | eu-de   | https://vbs.eu-de.otc.t-systems.com/v2/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| volume-backup              | eu-de   | https://vbs.eu-de.otc.t-systems.com/v2/                              |
+----------------------------+---------+----------------------------------------------------------------------+
| vpc                        | eu-de   | https://vpc.eu-de.otc.t-systems.com/v1/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| vpc                        | eu-nl   | https://vpc.eu-nl.otc.t-systems.com/v1/$(tenant_id)s                 |
+----------------------------+---------+----------------------------------------------------------------------+
| vpc2.0                     | eu-de   | https://vpc.eu-de.otc.t-systems.com/v2.0/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| vpcep                      | eu-de   | https://vpcep.eu-de.otc.t-systems.com/v1/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| vpcep                      | eu-nl   | https://vpcep.eu-nl.otc.t-systems.com/v1/$(tenant_id)s               |
+----------------------------+---------+----------------------------------------------------------------------+
| waf                        | eu-de   | https://waf.eu-de.otc.t-systems.com                                  |
+----------------------------+---------+----------------------------------------------------------------------+
| waf                        | eu-nl   | https://waf.eu-nl.otc.t-systems.com                                  |
+----------------------------+---------+----------------------------------------------------------------------+
| workspace                  | eu-de   | https://workspace.eu-de.otc.t-systems.com/v1.0/$(tenant_id)s         |
+----------------------------+---------+----------------------------------------------------------------------+

We again recommend to not hardcode the IP addresses as we do reserve the
right to change them.

.. |image01| image:: /_static/images/image-factory-customer-information-windows-password.png
