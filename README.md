# Nucintosh
NUC8ixBEy 黑苹果（Catalina）

## 导航
* [安装](#安装)
* [完善](#完善)
* [升级](#升级)
* [补充](#补充)
* [致谢](#致谢)
  
## 安装
+ 将 BIOS 升级到最新版本 (0089) -> 加载默认 BIOS 配置 (F9) -> 修改并保存以下项目 (F10)
```
Devices -> USB -> Port Device Charging Mode -> off
Devices -> USB -> USB Legacy -> Disabled
Security -> Thunderbolt Security Level -> Legacy Mode
Power -> Wake on LAN from S4/S5: Stay Off
Boot -> Boot Configuration -> Network Boot -> Disable
Boot -> Secure Boot -> Disable
```
+ [下载](https://blog.daliansky.net/) macOS Catalina 镜像
+ 使用 [balenaEtcher](https://www.balena.io/etcher/) 制作启动U盘
+ 使用 [ProperTree](https://github.com/corpnewt/ProperTree) 编辑 config.plist 并修改以下内容
```
PlatformInfo -> Generic -> MLB
PlatformInfo -> Generic -> ROM
PlatformInfo -> Generic -> SystemSerialNumber
PlatformInfo -> Generic -> SystemUUID
```
使用 [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) 生成三码。ROM 值填入网卡MAC地址。
+ 将此 EFI 文件夹复制至启动U盘的 EFI 分区
+ 清除 NVRAM
+ **安装 macOS**

## 安装之后
+ 运行 ```sudo diskutil mount disk0s1``` 挂载硬盘 EFI 分区
+ Disable NVMeFix.kext if you don't have an NVMe drive
+ 将启动U盘的 EFI 文件夹复制至硬盘的 EFI 分区
+ 运行 ```sudo trimforce enable``` 开启 TRIM

修改 ```config.plist``` 以获得更好的启动体验：
+ 去掉 ```boot-args``` 中的 ```-v``` 选项以关闭啰嗦模式
+ 将 ```ShowPicker``` 设为 ```false``` 以隐藏启动项菜单（在启动时按住 *alt* 键以显示 OpenCore 菜单）

## 升级
将当前 MLB/ROM/SystemSerialNumber/SystemUUID 值复制至新 EFI 即可。

## 补充
+ 读卡器/红外接收器不工作或未测试。

## 致谢
+ https://github.com/acidanthera
+ https://github.com/OpenIntelWireless
+ https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html
+ https://github.com/osy
+ https://github.com/Rashed97/Intel-NUC-DSDT-Patch/commit/47476815b52f8e4c97e8f85df158c9ab1b6ecedd
+ https://github.com/honglov3/NUC8I7BEH
+ https://github.com/sarkrui/NUC8i7BEH-Hackintosh-Build
+ https://github.com/mbarbierato/Intel-NUC8i3BEH
+ https://github.com/zearp/Nucintosh
+ ……