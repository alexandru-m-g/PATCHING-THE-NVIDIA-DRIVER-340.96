PATCHING THE NVIDIA DRIVER 340.96
=================================

After updating my linux machine ( Opensuse Tumbleweed ) to the latest kernel 4.6.2 ( from 4.5 ) my Nvidia driver refused to build. Apparently some interface changes in the new kernel broke the driver. 

Managed to create a small patch to fix the issues.

The following websites helped in building the patch below that works for me:
  *  `get_user_pages() <https://devtalk.nvidia.com/default/topic/936310/nvidia-drivers-do-not-install-with-kernel-4-6/>`_ problem
  *  `page_cache_release() <https://github.com/manjaro/packages-extra/issues/68>`_ problem
  *  `VM_FAULT_MINOR <https://devtalk.nvidia.com/default/topic/926824/364-12-won-t-compile-against-latest-git-tree-patches-for-4-6-0-rc1-included-/>`_ problem 
  
Building the nvidia driver with the patch
-----------------------------------------

First download the **nvidia.patch** file from this repo. Then run:

.. code:: bash

   ./NVIDIA-Linux-x86_64-340.96.run --apply-patch nvidia.patch
   
This will create another archived executable with the name ending in *_custom.run*. Running this executable should successfully build and install the nvidia driver.

NOTES
-----
The nvidia driver was downloaded from the official `nvidia website <http://www.nvidia.com/object/unix.html>`_

If you need to play more with the sources of the driver you can unpack them with:

.. code:: bash

   ./NVIDIA-Linux-x86_64-340.96.run -x
   
