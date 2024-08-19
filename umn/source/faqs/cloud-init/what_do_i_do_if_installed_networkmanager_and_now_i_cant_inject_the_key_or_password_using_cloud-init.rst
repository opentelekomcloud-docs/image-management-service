:original_name: en-us_topic_0113992021.html

.. _en-us_topic_0113992021:

What Do I Do If Installed NetworkManager and Now I Can't Inject the Key or Password Using Cloud-Init?
=====================================================================================================

Cause
-----

One likely possibility is that the version of Cloud-Init is incompatible with that of NetworkManager. In Debian 9.0 and later versions, NetworkManager is incompatible with Cloud-Init 0.7.9.

Solution
--------

Uninstall the current Cloud-Init and install Cloud-Init 0.7.6 or an earlier version.

For details about how to install Cloud-Init, see :ref:`Installing Cloud-Init <en-us_topic_0030730603>`.
