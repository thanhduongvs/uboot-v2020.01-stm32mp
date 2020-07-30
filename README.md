# u-bootW
https://wiki.dh-electronics.com/index.php/Avenger96#Downloads
https://www.digikey.com/eewiki/display/linuxonarm/STM32MP1
https://wiki.st.com/stm32mpu/wiki/U-Boot_-_How_to_debug
https://wiki.st.com/stm32mpu/wiki/How_to_configure_U-Boot_for_your_board
https://gitlab.com/unicorn_team/yocto-open-rex/-/blob/master/02.%20Starting/lesson.md
https://octavosystems.com/app_notes/stm32mp1-cubemx-tutorial-for-osd32mp15x/
https://wiki.st.com/stm32mpu/wiki/U-Boot_overview
https://github.com/STMicroelectronics/u-boot/blob/v2020.01-stm32mp/doc/board/st/stm32mp1.rst
https://www.kernel.org/doc/Documentation/devicetree/bindings/pinctrl/pinctrl-bindings.txt
git clone https://github.com/STMicroelectronics/u-boot.git
	arch/arm/dts/Makefile
export CROSS_COMPILE=arm-linux-gnueabihf-
export ARCH=arm
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- distclean
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- stm32mp15_kmtek_basic_defconfig
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- DEVICE_TREE=osd32mp157c_kmtek all -j8
make -j8

make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- distclean
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- stm32mp15_basic_defconfig
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- DEVICE_TREE=stm32mp157c-dk2 all

make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- distclean
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- stm32mp15_dhcom_basic_defconfig
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- DEVICE_TREE=stm32mp15xx-dhcom-pdk2 all -j8

make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- stm32mp1_dk2_config

uboot-v2020.01-stm32mp

stm32mp157c-kmtek-octavo

ARM Cross Compiler: GCC
cd toolchain
wget -c https://releases.linaro.org/components/toolchain/binaries/6.5-2018.12/arm-linux-gnueabihf/gcc-linaro-6.5.0-2018.12-x86_64_arm-linux-gnueabihf.tar.xz
tar xf gcc-linaro-6.5.0-2018.12-x86_64_arm-linux-gnueabihf.tar.xz
vim ~/.bashrc
export PATH=$PATH:~/toolchain/gcc-linaro-6.5.0-2018.12-x86_64_arm-linux-gnueabihf/bin
source ~/.bashrc

git clone https://github.com/thanhduongvs/uboot-v2020.01-stm32mp.git
cd uboot-v2020.01-stm32mp
export CROSS_COMPILE=arm-linux-gnueabihf-
export ARCH=arm
export DEVICE_TREE=stm32mp157c-kmtek-octavo
export KBUILD_OUTPUT=./build
make distclean
make stm32mp15_basic_defconfig
make all -j8
