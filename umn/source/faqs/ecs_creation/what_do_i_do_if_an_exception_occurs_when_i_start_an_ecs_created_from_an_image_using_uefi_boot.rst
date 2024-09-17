:original_name: en-us_topic_0161870891.html

.. _en-us_topic_0161870891:

What Do I Do If an Exception Occurs When I Start an ECS Created from an Image Using UEFI Boot?
==============================================================================================

Symptom
-------

An ECS created from a private image booting to UEFI cannot start.

Possible Causes
---------------

The image is configured for UEFI boot, but the uefi attribute was not added to the image.

Solution
--------

#. Delete the ECS that failed to start.

#. Call the API to update the image attributes and change the value of **hw_firmware_type** to **uefi**.

   API URI: PATCH /v2/cloudimages/{*image_id*}

   For details about how to call the API, see "Updating Image Information" in *Image Management Service API Reference*.

#. Use the updated image to create an ECS.
