## 流程

1、在`recipes-support/aml-img-packer/aml-img-packer-native_1.0.bbappend`配方，把创维自定义镜像`conf配置`拷贝到`build\tmp\deploy\images\mesonsc2-lib64-hp45l-ah221-ui`目录下，供生成自定义镜像使用。

conf配置格式如下

```bash
# cat aml_upgrade_package_ab_dr_ota.conf

#This file define how pack aml_upgrade_package image

[LIST_NORMAL]
#partition images, don't need verfiy
file="u-boot.bin.usb.signed"        main_type= "USB"            sub_type="DDR"
file="u-boot.bin.usb.signed"        main_type= "USB"            sub_type="UBOOT"
file="u-boot.bin.sd.bin.signed"     main_type="UBOOT"           sub_type="aml_sdc_burn"
file="platform.conf"                main_type= "conf"           sub_type="platform"
file="aml_sdc_burn.ini"             main_type="ini"             sub_type="aml_sdc_burn"
file="dtb.img"                      main_type="dtb"             sub_type="meson1"
file="usb_flow.aml"                 main_type="aml"             sub_type="usb_flow"

[LIST_VERIFY]
#partition images needed verify

#if you want download userdata image, uncomment below line
#file="userdata.img"     main_type="PARTITION"      sub_type="data"

file="boot.img"             main_type="PARTITION"      sub_type="boot_a"
file="rootfs.ext4.img2simg" main_type="PARTITION"      sub_type="system_a"
file="vendor.ext4.img2simg" main_type="PARTITION"       sub_type="vendor_a"
file="dtb.img"              main_type="PARTITION"      sub_type="_aml_dtb"
file="recovery.img"         main_type="PARTITION"      sub_type="recovery"
```

具体里面的语法什么意思待研究

2、在`recipes-core\images\skyworth-generic-mediaclient-image.bb`配方里，里面的`do_aml_pack`任务会使用相关的可执行程序`aml_image_v2_packer_new`根据配置生成`img镜像`，就能通过`AML Burn Tool V2工具`进行烧录了。

![abc](http://note.youdao.com/yws/api/personal/file/WEBb2749bd5ab5ec2e2e7b61e47f9158389?method=download&shareKey=a4048e157b3ea9a84581ce1a7019d676)
![abc](http://note.youdao.com/yws/api/personal/file/WEBb2749bd5ab5ec2e2e7b61e47f9158389?method=download&shareKey=a4048e157b3ea9a84581ce1a7019d676)
