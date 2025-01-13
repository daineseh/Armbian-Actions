
# 简介
- 通过GitHub Actions构建armbian支持列表之外的rk33xx设备固件
- 此仓库仅提供armbian构建方法、思路；如出现固件不能用、外设不能用等等问题请自行寻找解决方法
- Armbian branch的stable选项必须要构建的板卡支持这两个分支才选择，否则会报错
- Armbian kernel：linux-dtb、linux-headers、linux-image、linux-libc-dev四个deb包
- Armbian源码https://github.com/armbian/build

## 仓库详情
- rk3399-main用来构建6.6内核，由于6.12 kernel的rk3399-opp被合并，不可用于6.12及以上内核构建
- stable：kernel-6.1；current：kernel-6.6；edge：kernel-6.12
- rk3399-beta分支是测试分支，主要用来验证dts/patch的可行性和6.12及以上内核
- rockchip64-current存放current（rockchip64-6.6）,edge（rockchip64-6.12）的patch/dts文件通过软链接让一份文件实现复用
- rockchip64-6.1存放stable（自定义内核分支，armbian没有这个分支，25.02以下默认为current-6.6）
- stable必须要在xxx.conf的KERNEL_TARGET选项添加stable

## yml工作流文件说明  
- build armbian all borad.yml：构建列表内所有设备armbian固件，不上传kernel headers文件
- build armbian customize board.yml：单独构建某设备armbian固件，不上传kernel headers文件
- build armbian kernel customize.yml：单独构建某设备armbian固件，将headers、image、dtb、libc-dev上传至[Armbian Kernel](https://github.com/Lemon1151/Armbian-Actions/releases/tag/Armbian_Kernel)标签
- build kernel boardfamily.yml只构建内核，将headers、image、dtb、libc-dev上传至[Armbian Kernel](https://github.com/Lemon1151/Armbian-Actions/releases/tag/Armbian_Kernel)标签
- build kernel customize.yml：单独构建armbian固件，只上传headers、image、dtb、libc-dev至[Armbian Kernel](https://github.com/Lemon1151/Armbian-Actions/releases/tag/Armbian_Kernel)标签

## Links  
- [armbian](https://github.com/armbian/build)
- [ophub](https://github.com/ophub/amlogic-s9xxx-armbian)
- [cm9vdA](https://github.com/cm9vdA/build-armbian)
- [Lollipop907](https://github.com/Lollipop907)
- [xiaomeng9597](https://github.com/xiaomeng9597/iStoreOS-For-RK33XX)
- [QXY716](https://github.com/QXY716/Fine3399-rk3399-armbian)
