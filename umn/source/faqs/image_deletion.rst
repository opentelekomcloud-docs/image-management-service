:original_name: en-us_topic_0032326546.html

.. _en-us_topic_0032326546:

Image Deletion
==============

Will a Private Image Be Automatically Deleted If I Delete the ECS Used to Create the Image?
-------------------------------------------------------------------------------------------

No. Private images created using ECSs are stored in OBS buckets. Deleting the ECS used to create a private image does not affect the image.

Can I Delete an Image I Shared with Others If My Image Quota Becomes Insufficient?
----------------------------------------------------------------------------------

Yes. You can delete a shared image without requiring any operation by image recipients. After you delete the image, the image recipients cannot use it any longer. Inform the image recipients to back up their data before you delete the image.

How Do I Delete a Shared Image? Does the Deletion Affect an ECS or EVS Disk Created from It?
--------------------------------------------------------------------------------------------

Reject this image on the **Images Shared with Me** tab page. This does not affect an ECS or EVS disk created from it.
