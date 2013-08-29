In premilinary release we use cubieboard2 kernel,
i do not recommend using this kernel.
Keep in mind that you need to have installed toolchain /ex. linaro/
Instructions to build kernel from source :
/From cuibieboard2 repo/ 

 curl https://raw.github.com/cubieboard/git-repo/stable/repo > ~/bin/repo
 chmod +x ~/bin/repo
 mkdir test_build && cd test_build
 repo init --no-repo-verify -u git://github.com/cubieboard2/manifests -b cb2 -m test.xml
 wget https://raw.github.com/hehopmajieh/OLinuXino-A20/master/olinuxinoA20_defconfig -O arch/arm/configs/olinuxinoA20_defconfig
 make ARCH=arm olinuxinoA20_defconfig
 make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- -j4 uImage
 make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- -j4 INSTALL_MOD_PATH=out modules
 make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- -j4 INSTALL_MOD_PATH=out modules_install

1. Copy arc/arm/boot/uImage to your sdcard boot partition

cp -v arc/arm/boot/uImage /sdcard_part1_mount_point/.

2. Copy modules and firmware dirs to yur file system partition 

cp -aRv out/lib/modules/* /sdcard_part2_mount_point/lib/modules/
