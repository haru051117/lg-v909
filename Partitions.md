
# Partition Layout #

---

This article will describe the G Slate's partition layout as best we know at the moment. As we learn more, the document will be updated.

## Fastboot Partition Layout ##

---

```
0 /tmp ramdisk (null) (null) 0
1 /system ext4 /dev/block/mmcblk0p1 (null) 0
2 /cache ext4 /dev/block/mmcblk0p2 (null) 0
3 /misc emmc /dev/block/mmcblk0p3 (null) 0
4 /data ext4 /dev/block/mmcblk0p4 (null) 0
5 /recovery emmc /dev/block/mmcblk0p5 (null) 0
6 /boot emmc /dev/block/mmcblk0p6 (null) 0
7 /radio emmc /dev/block/mmcblk0p9 (null) 0
8 /oemboot emmc /dev/block/mmcblk0p10 (null) 0
```

## APX Partition Layout ##

---

```

[device]
type=hsmmc
instance=3

[partition]
name=BCT
id=2
type=boot_config_table
allocation_policy=sequential
filesystem_type=basic
size=3145728
file_system_attribute=0
partition_attribute=0
allocation_attribute=8
percent_reserved=0

[partition]
name=PT
id=3
type=partition_table
allocation_policy=sequential
filesystem_type=basic
size=524288
file_system_attribute=0
partition_attribute=0
allocation_attribute=8
percent_reserved=0

[partition]
name=EBT
id=4
type=bootloader
allocation_policy=sequential
filesystem_type=basic
size=5242880
file_system_attribute=0
partition_attribute=0
allocation_attribute=8
percent_reserved=0
filename=bootloader.bin

[partition]
name=NIC
id=5
type=data
allocation_policy=sequential
filesystem_type=basic
size=1048576
file_system_attribute=0
partition_attribute=0
allocation_attribute=8
percent_reserved=0
filename=part5_nic.img

[partition]
name=RED
id=6
type=data
allocation_policy=sequential
filesystem_type=basic
size=5242880
file_system_attribute=0
partition_attribute=0
allocation_attribute=8
percent_reserved=0
filename=part6_red.img

[partition]
name=GP1
id=7
type=GP1
allocation_policy=sequential
filesystem_type=basic
size=1048576
file_system_attribute=0
partition_attribute=0
allocation_attribute=8
percent_reserved=0

[partition]
name=APP
id=8
type=data
allocation_policy=sequential
filesystem_type=basic
size=419430400
file_system_attribute=0
partition_attribute=0
allocation_attribute=8
percent_reserved=0
filename=system.img

[partition]
name=CAC
id=9
type=data
allocation_policy=sequential
filesystem_type=ext3
size=419430400
file_system_attribute=0
partition_attribute=0
allocation_attribute=8
percent_reserved=0

[partition]
name=MSC
id=10
type=data
allocation_policy=sequential
filesystem_type=ext3
size=4194304
file_system_attribute=0
partition_attribute=0
allocation_attribute=8
percent_reserved=0

[partition]
name=UDA
id=11
type=data
allocation_policy=sequential
filesystem_type=ext3
size=124256256
file_system_attribute=0
partition_attribute=0
allocation_attribute=0x808
percent_reserved=0

[partition]
name=SOS
id=12
type=data
allocation_policy=sequential
filesystem_type=basic
size=5242880
file_system_attribute=0
partition_attribute=0
allocation_attribute=8
percent_reserved=0
filename=part12_sos.img

[partition]
name=LNX
id=13
type=data
allocation_policy=sequential
filesystem_type=basic
size=5242880
file_system_attribute=0
partition_attribute=0
allocation_attribute=8
percent_reserved=0
filename=part13_lnx.img

[partition]
name=LGE
id=14
type=data
allocation_policy=sequential
filesystem_type=basic
size=2097152
file_system_attribute=0
partition_attribute=0
allocation_attribute=8
percent_reserved=0
filename=part14_lge.img

[partition]
name=MFT
id=15
type=data
allocation_policy=sequential
filesystem_type=basic
size=4194304
file_system_attribute=0
partition_attribute=0
allocation_attribute=8
percent_reserved=0
filename=part15_mft.img

[partition]
name=CPI
id=16
type=data
allocation_policy=sequential
filesystem_type=basic
size=100663296
file_system_attribute=0
partition_attribute=0
allocation_attribute=8
percent_reserved=0
filename=part16_cpi.img

[partition]
name=BLI
id=17
type=data
allocation_policy=sequential
filesystem_type=basic
size=5242880
file_system_attribute=0
partition_attribute=0
allocation_attribute=8
percent_reserved=0
filename=part17_bli.img

[partition]
name=GPT
id=18
type=GPT
allocation_policy=sequential
filesystem_type=basic
size=0xFFFFFFFFFFFFFFFF
file_system_attribute=0
partition_attribute=0
allocation_attribute=8
percent_reserved=0
```

## Kernel partition map ##

---


| **device name**| **block size**	| **byte size**	| **comment** |
|:---------------|:---------------|:--------------|:------------|
| --		           |		              | 16252928+	    | NV p2-p7 probably not visible in linux |
| --		           |		              | 16252928+	    | NV p7 GP1 type GP1 -- this seems to be a marker: anything after that is visible to linux, before it all is invisible |
| _mmcblk0_	     | _31256576_	    | _32006733824_	|             |
| mmcblk0p1	     | 409600	        | 419430400	    | NV p8 APP   |
| mmcblk0p2	     | 409600	        | 419430400	    | NV p9 CAC? ext3 |
| mmcblk0p3	     | 4096		         | 4194304	      | NV p10 MSC? ext3 |
| mmcblk0p4	     | 30300160	      | 31027363840	  | NV p11 UDA? |
| mmcblk0p5	     | 5120		         | 5242880	      | NV p12 SOS  |
| mmcblk0p6	     | 5120		         | 5242880	      | NV p13 LNX  |
| mmcblk0p7	     | 2048		         | 2097152	      | NV p14 LGE  |
| mmcblk0p8	     | 4096		         | 4194304	      | NV p15 MFT  |
| mmcblk0p9	     | 98304	         | 100663296	    | NV p16 CPI  |
| mmcblk0p10	    | 5120		         | 5242880	      | NV p17 BLI  |
| --		           | --		           | --		          | NV p18 GPT - EFI partition table; probably visible in linux (tail of mmcblk0), this is where linux takes the partitioning info from |

Partitioned total: 31243264 blocks