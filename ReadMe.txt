1. Android buid 
  - Download original android source code (kitkat Version 4.4.2) from http://source.android.com                    
  - Untar opensource packages of VK810_android_KK.tar.gz into downloaded android source directory 
    a)$tar xvzf ./VK810_android_KK.tar.gz
  - And, merge the source into the android source code(Kitkat)
  - Run following scripts to build android                          
    a)$source build/envsetup.sh                                      
    b)$lunch 1
    c)$m -j4                                                                         
  - When you compile the android source code, you have to add google original prebuilt source(toolchain) 
    into the android folder 
  - After build, you can find output at out/target/product/generic   
  
2. Kernel Build 
  - Untar using follwing command at the original android source folder
    a)$tar -xzvf ./VK810_kernel_opensource.tar.gz
  - Set Path and Build
    a) cd kernel
	b) mkdir -p out
	c) export ARCH=arm
	d) export PATH=$PATH:tools/lz4demo
	e) export CROSS_COMPILE=$(pwd)/../prebuilts/gcc/linux-x86/arm/arm-eabi-4.6/bin/arm-eabi-
    f) make O=./out ARCH=arm altev-perf_defconfig
	g) make O=./out -j4
		* "-j4" : The number, 4, is the number of multiple jobs to be invoked simultaneously. 
		* lz4demo : More information can be found at "https://code.google.com/p/lz4/"
  - After build, you can find the build image(zImage) at out/arch/arm/boot/

3. how  to build chromium_lge (vendor\lge\external\chromium_lge),
   please refer to Buildme.txt at the folder mentioned above.