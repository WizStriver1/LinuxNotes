# 查找windows的menuentry

可在以下文档中查看：
```
sudo cat /etc/grub2-efi.cfg
```
或
```
sudo cat /boot/efi/efi/grub.cfg
``` 

示例：

执行**sudo vim /etc/grub2-efi.cfg**命令，查找到如下文字：

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sdb2)' --class windows --class os $menuentry_id_option 'osprober-efi-B0DE-A77A' {
	insmod part_gpt
	insmod fat
	set root='hd1,gpt2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  B0DE-A77A
	else
	  search --no-floppy --fs-uuid --set=root B0DE-A77A
	fi
	chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
### END /etc/grub.d/30_os-prober ###
```

则windows的menuentry是”Windows Boot Manager (on /dev/sdb2)”


# 打开/boot/grub2/grubenv文件，将saved_entry的值改为windows的menuentry:

示例：

执行sudo vim /boot/grub2/grubenv命令：文件修改为如下

saved_entry=Windows Boot Manager (on /dev/sdb2)

重启电脑，就会发现已经将windows更改为默认启动项.
