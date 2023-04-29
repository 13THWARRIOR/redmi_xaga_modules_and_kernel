# gki_xaga_modules_and_kernel
This repository is for xaga kernel and module for gki compilation. 

How to compile gki kernel and get modules from vendor kernel :
- clone android common kernel 12 from aosp - > repo init -u https://android.googlesource.com/kernel/manifest -b common-android12-5.10 
- clone this repository into redmi folder under the root directory of aosp common kernel directory structure
- use this command to compile the kernel and get boot.img and vendor modules:
  SKIP_MRPROPER=1 SKIP_IF_VERSION_MATCHES=1 GKI_BUILD_CONFIG=common/build.config.gki.aarch64 BUILD_CONFIG=redmi/xaga/kernel-5.10/build.config.xaga KERNEL_BINARY=Image.gz AVB_SIGN_BOOT_IMG=1 AVB_BOOT_PARTITION_SIZE=65536000 AVB_BOOT_KEY=./tools/mkbootimg/gki/testdata/testkey_rsa2048.pem AVB_BOOT_ALGORITHM=SHA256_RSA2048 BUILD_BOOT_IMG=1 SKIP_VENDOR_BOOT=1 BOOT_IMAGE_HEADER_VERSION=4 GKI_RAMDISK_PREBUILT_BINARY=./prebuilts/boot-artifacts/gki/ramdisk KERNEL_CMDLINE="" MKBOOTIMG_EXTRA_ARGS="--os_patch_level 2023-05 --os_version 12.0.0" PAGE_SIZE=4096 LTO=thin CC=clang build/build.sh
- i will not be covering how to create vendor_boot.img for the time being 
