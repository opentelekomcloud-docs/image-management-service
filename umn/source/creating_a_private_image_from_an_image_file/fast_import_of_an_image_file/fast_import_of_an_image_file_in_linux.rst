:original_name: en-us_topic_0133773660.html

.. _en-us_topic_0133773660:

Fast Import of an Image File in Linux
=====================================

Scenarios
---------

This section describes how to convert the format of a large image file on a Linux server and then quickly import it to the cloud platform. You are advised to use an EulerOS ECS for converting image file formats and generating bitmap files.

In Linux, you are advised to use **qemu-img-hw** to convert image formats.

Prerequisites
-------------

-  The image file has been initially configured as instructed in :ref:`Table 2 <en-us_topic_0000002183615189__table1182513010515>` based on the OS in the image file.

-  You have created an ECS running EulerOS on the management console and bound an EIP to the ECS.
-  An OBS bucket has been created on the management console.

Procedure
---------

#. Upload an image file.

   -  If the image file is uploaded from a Linux PC, run the **scp** command.

      For example, to upload **image01.qcow2** to the **/usr/** directory of the ECS, run the following command:

      **scp /var/image01.qcow2 root@**\ *xxx.xxx.xx.xxx*\ **:/usr/**

      *xxx.xxx.xx.xxx* indicates the EIP bound to the ECS.

   -  If the image file is uploaded from a Windows PC, use a file transfer tool, such as WinSCP, to upload the image file.

#. Obtain the fast import tool package, upload it to the ECS, and then decompress the package.

   Contact the administrator to obtain the fast import tool.

#. Use **qemu-img-hw** to convert the image format.

   a. Go to the directory where **qemu-img-hw** is stored, for example, **/usr/quick-import-tools/qemu-img-hw**.

      **cd /usr/quick-import-tools/qemu-img-hw**

   b. Run the following command to make **qemu-img-hw** executable:

      **chmod +x qemu-img-hw**

   c. Execute **qemu-img-hw** to convert the image file format to ZVHD2 (recommended) or RAW.

      Command format:

      **./qemu-img-hw convert -p -O** *{target-image-format}* *{source-image-file}* *{target-image-file}*

      For example, run the following command to convert an **image01.qcow2** file to an **image01.zvhd2** file:

      **./qemu-img-hw convert -p -O zvhd2 image01.qcow2 image01.zvhd2**

      -  If the image file is converted to the ZVHD2 format, go to :ref:`5 <en-us_topic_0133773660__li12136151722>`.
      -  If the image file is converted to the RAW format, go to :ref:`4 <en-us_topic_0133773660__li1683153619217>`.

#. .. _en-us_topic_0133773660__li1683153619217:

   Use **CreateMF.jar** to generate a bitmap file.

   a. Ensure that JDK has been installed on the ECS.

      Run the following commands to check whether JDK is installed:

      **source /etc/profile**

      **java -version**

      If a Java version is displayed, JDK has been installed.

   b. Run the following command to enter the directory where **CreateMF.jar** is stored:

      **cd /usr/quick-import-tools/createMF**

   c. Run the following command to generate a bitmap file:

      **java -jar CreateMF.jar** */<original-RAW-file-path>/<generated-.mf-file-path>*

      Example:

      **java -jar CreateMF.jar image01.raw image01.mf**

      .. caution::

         -  The generated .mf bitmap file must have the same prefix as the RAW image file. For example, if the image file name is **image01.raw**, the generated bitmap file name is **image01.mf**.

#. .. _en-us_topic_0133773660__li12136151722:

   Use **s3cmd** to upload the file(s) to an OBS bucket.

   a. Install **s3cmd** on the ECS.

      If **s3cmd** has been installed, skip this step.

      #. Run the following command to install setuptools:

         **yum** **install** **python-setuptools**

      #. Run the following command to install wget:

         **yum install wget**

      #. Run the following commands to obtain the **s3cmd** software package:

         **wget https://github.com/s3tools/s3cmd/archive/master.zip**

         **mv master.zip s3cmd-master.zip**

      #. Run the following commands to install **s3cmd**:

         **unzip s3cmd-master.zip**

         **cd s3cmd-master**

         **python setup.py install**

   b. Configure **s3cmd**.

      Run the following command to configure **s3cmd**:

      .. code-block::

         s3cmd --configure
         Access Key: Enter an AK.
         Secret Key: Enter an SK.
         Default Region: Enter the region where the bucket is located.
         S3 Endpoint: Refer to the OBS endpoint.
         DNS-style bucket+hostname:port template for accessing a bucket: Enter a server address with a bucket name, for example, mybucket.obs.myclouds.com.
         Encryption password: Press Enter.
         Path to GPG program: Press Enter.
         Use HTTPS protocol: Specifies whether to use HTTPS. The value can be Yes or No.
         HTTP Proxy server name: Specifies the proxy address used to connect the cloud from an external network. (If you do not need it, press Enter.)
         HTTP Proxy server port: Specifies the proxy port used to connect to the cloud from an external network (If you do not need it, press Enter.)
         Test access with supplied credentials? y
         (If "Success. Your access key and secret key worked fine :-)" is displayed, the connection is successful.)
         Save settings? y (Specifies whether to save the configurations. If you enter y, the configuration will be saved.)

      .. note::

         The configurations will be stored in **/root/.s3cfg**. If you want to modify these configurations, run the **s3cmd --configure** command to configure the parameters or run the **vi .s3cfg** command to edit the **.s3cfg** file.

   c. Run the following command to upload the ZVHD2 image file (or the RAW image file and its bitmap file) to an OBS bucket.

      .. code-block::

         s3cmd put image01.zvhd2 s3://mybucket/

      .. caution::

         The .mf bitmap file must be in the same OBS bucket as the RAW image file.

#. Register a private image.

   You can register a private image using the converted ZVHD2 or RAW file on the console or using an API.

   Method 1: Register a private image on the console.

   a. Log in to the management console.

      #. Under **Computing**, click **Image Management Service**. The IMS console is displayed.

   b. In the upper right corner, click **Create Image**.

   c. In the **Image Type and Source** area, select **Import Image** for **Type** and then select **System disk image** or **Data disk image** for **Image Type**.

   d. Select the bucket storing the ZVHD2 or RAW image file and then select the image file.

   e. Select **Enable Fast Create**, and select the sentence following **Image File Preparation**.


      .. figure:: /_static/images/en-us_image_0210228327.png
         :alt: **Figure 1** Fast import of an image file

         **Figure 1** Fast import of an image file

   f. Set parameters as prompted.

      For details about the parameters, see :ref:`Registering an Image File as a Private Image <en-us_topic_0030713193>`.

      .. caution::

         -  The OS must be the same as that in the image file.

         -  The system disk capacity must be greater than that specified in the image file.

            Run the following command to check the system disk capacity in the image file:

            **qemu-img-hw** **info** *test.zvhd2*

   Method 2: Register a private image using an API.

   The API is POST /v2/cloudimages/quickimport/action.

   For details about how to call this API, see "Importing an Image File Quickly" in *Image Management Service API Reference*.

Appendix 1: Common qemu-img-hw Commands
---------------------------------------

-  Convert the format of the image file.

   .. code-block::

      qemu-img-hw convert -p -O {target-image-format} {source-image-file} {target-image-file}

   The parameters are described as follows:

   **-p**: indicates the conversion progress.

   The part following **-O** (which must be in upper case) consists of the target image format, source image file, and target image file.

   For example, run the following command to convert a QCOW2 image file to a ZVHD2 file:

   .. code-block::

      qemu-img-hw convert -p -O zvhd2 test.qcow2 test.zvhd2

-  Query image file information.

   .. code-block::

      qemu-img-hw info {image-file}

   Example:

   .. code-block::

      qemu-img-hw info test.zvhd2

-  View help information.

   .. code-block::

      qemu-img-hw -help

Appendix 2: Common qemu-img-hw Errors
-------------------------------------

-  Symptom:

   The following information is displayed when you run the **qemu-img-hw** command:

   .. code-block::

      ./qemu-img-hw: /lib64/libc.so.6: version `GLIBC_2.14' not found (required by ./qemu-img-hw)

   Solution:

   Run the **strings /lib64/libc.so.6 \| grep GLIBC** command to check the GLIBC version. If the version is too early, install the latest version. Run the following commands in sequence:

   .. code-block::

      wget http://ftp.gnu.org/gnu/glibc/glibc-2.15.tar.gz
      wget http://ftp.gnu.org/gnu/glibc/glibc-ports-2.15.tar.gz
      tar -xvf glibc-2.15.tar.gz
      tar -xvf glibc-ports-2.15.tar.gz
      mv glibc-ports-2.15 glibc-2.15/ports
      mkdir glibc-build-2.15
      cd glibc-build-2.15
      ../glibc-2.15/configure --prefix=/usr --disable-profile --enable-add-ons --with-headers=/usr/include --with-binutils=/usr/bin

   .. note::

      If "configure: error: no acceptable C compiler found in $PATH" is displayed, run the **yum -y install gcc** command.

   .. code-block::

      make
      make install

-  Symptom:

   The following information is displayed when you run the **qemu-img-hw** command:

   .. code-block::

      ./qemu-img-hw: error while loading shared libraries: libaio.so.1: cannot open shared object file: No such file or directory

   Solution:

   Run the following command:

   .. code-block::

      yum install libaio

-  Symptom:

   The following information is displayed when you run the **qemu-img-hw** command:

   .. code-block::

      ./qemu-img-hw: error while loading shared libraries: libcrypto.so.10: cannot open shared object file: No such file or directory

   Solution: Run **openssl version** to check whether the OpenSSL version is later than 1.0. If yes, install OpenSSL 1.0.

   Run the following commands to install OpenSSL 1.0:

   .. code-block::

      wget https://github.com/openssl/openssl/releases/download/OpenSSL_1_0_2k/openssl-1.0.2k.tar.gz
      tar -xvf openssl-1.0.2k.tar.gz
      cd openssl-1.0.2k
      ./config -d shared --prefix=/tmp/openssl (custom installation directory)
      make
      make install
      cp /tmp/openssl/lib/libcrypto.so.1.0.0 /usr/lib64/libcrypto.so.10

   Delete the **/usr/lib64/libcrypto.so.10** file if you no longer need it.
