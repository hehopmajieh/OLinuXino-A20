Get linux-sunxi kernel :

 git clone https://github.com/linux-sunxi/linux-sunxi -b stage/sunxi-3.4
 cd linux-sunxi
Compile kernel

 wget https://raw.github.com/hehopmajieh/OLinuXino-A20/master/olinuxinoA20-3.4_defconfig -O arch/arm/configs/olinuxinoA20_defconfig
 make ARCH=arm olinuxinoA20_defconfig
 make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- -j4 uImage
 make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- -j4 INSTALL_MOD_PATH=out modules
 make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- -j4 INSTALL_MOD_PATH=out modules_install

1. Copy arc/arm/boot/uImage to your sdcard boot partition

cp -v arc/arm/boot/uImage /sdcard_part1_mount_point/.

2. Copy modules and firmware dirs to yur file system partition 

cp -aRv out/lib/modules/* /sdcard_part2_mount_point/lib/modules/.
