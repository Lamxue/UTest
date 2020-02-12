

# 镜像上传

## 操作步骤

1、将镜像上传至UFile。因镜像容量通常较大，需要使用客户端或SDK上传。[查看说明](/storage_cdn/ufile/tools)
**注意，请将镜像添加至公开存储空间。**

2、请选择 控制台 -\> 云主机 -\> 镜像，点击“镜像上传”

3、输入镜像相关信息。选择“确定”，开始导入。

4、导入进度可在镜像列表中查询。镜像状态变为“可用”后，即可创建主机。

备注：部分地域暂不支持镜像上传。如希望上传到此类地域，请先在北京二上传镜像，完毕后提工单迁移镜像到目标地域。

## 操作须知

### Linux镜像

系统：基于CentOS、Redhat、Ubuntu、OpenSUSE、SUSE发行版的镜像。支持32位和64位。（暂不支持Debian和Gentoo，若希望导入此类镜像，请咨询技术支持）

支持镜像格式：raw、vhd、qcow2、vmdk

文件系统类型：使用 MBR 分区的ext3或ext4文件系统（不支持GPT分区）

系统盘大小：建议不超过50G

驱动：必须安装虚拟化平台KVM的virtio驱动

内核限制：建议采用原生内核，如果修改内核可能会导致导入失败；若镜像为Redhat，需要用户自行购买license。

其他限制：仅支持系统盘镜像，不支持数据盘。

### Windows镜像

操作系统：Microsoft Windows Server 2008/2012；支持32位/64位系统，支持激活

支持镜像格式：raw、vhd、qcow2、vmdk

文件系统类型：使用 MBR 分区的NTFS文件系统（不支持GPT分区）

系统盘大小：建议不超过50G。

驱动：若镜像自带virtio驱动，会以virtio启动；若镜像不带此驱动，会以IDE启动。

其他限制：仅支持系统盘镜像，不支持数据盘。

### 其他镜像

当您的镜像不在UCloud支持的镜像范围内时，可以选择上传为“其他”类型镜像。

![](/images/guide/image/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7_2018-09-07_%E4%B8%8B%E5%8D%882.18.03.png)

其他镜像有以下限制：

- 默认不带任何初始化。因此创建主机/重装主机时的密码设置、网络设置、SSH安装、NTP配置、Yum源配置等初始化步骤均不会生效。需要用户通过控制台登陆功能，自助配置。请参照“手动初始化步骤”。
- 控制台修改密码功能无法生效。

手动初始化步骤：

- 在上传前，镜像内部须开启DHCP，自动获取内网IP。 
- 通过控制台上传镜像，并通过此镜像创建主机。
- 在控制台，通过云主机登录功能进入虚机内部。 
- 设置密码。 
- 配置NTP，Yum源。（可选） 
- 安装SSH。（可选）