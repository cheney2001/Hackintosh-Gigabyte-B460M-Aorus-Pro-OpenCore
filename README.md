# Hackintosh-Gigabyte-B460M-Aorus-Pro-OpenCore
技嘉小雕B460M Aorus Pro ，10500 + Rx470

>  根据 OpenCore-Install-Guide CometLake 官方配置教程制作 

**小雕B460M Pro 官网更新了BIOS 可直接关闭CFG LOCK 版本号： `F5B`**

**此份EFI 需要你升级到F5B 并关闭 CFG LOCK 为Disable  ，使EFI 休眠完美**

*也可以不升级BIOS ，请看下面*  ⬇️

### 支持的macOS Version

* 10.15.* Catalina
* 10.16.* Big Sur

### 其他类似配置

* 相同的主板，对于10代U是通用的 
* 不同的主板PCH 同为B460也是通用的（可能声卡和网卡需要自定义一下）

### BIOS 设置

**根据官方教程 你需要在BIOS 如下设置（技嘉小雕B460M AORUS Pro 有的选项） ：**

**Disable**

- Fast Boot

- Secure Boot

- Serial/COM Port

- VT-d (can be enabled if you set [color=rgba(0, 0, 0, 0)][backcolor=rgba(27, 31, 35, 0.08)][size=0.85em]DisableIoMapper to YES)

- CSM

- CFG Lock 

**Enable**

- Above 4G decoding

- Hyper-Threading （默认开启的）

- EHCI/XHCI Hand-off

- OS type: Windows 8.1/10 UEFI Mode （设置为其他操作系统也可以）

- DVMT Pre-Allocated(iGPU Memory): 64MB ， （这里技嘉小雕的BIOS最小为128M ）

- SATA Mode: AHCI




### 配置客制

设置好了BIOS 后，如你有以下部分需求 ，请自行更改某些值，工具推荐使用 **ProperTree**

以下的手动配置有关的值等都在 **config.plist** 这个文件里



* 如果你只用核显作为显示 
  * 请将 `AAPL,ig-platform-id`  的值更改为 ： `07009B3E` 
* 如果你有免驱的A卡（就像我的RX470/570）等
  * 这部分 你啥也不用做



默认设置为 ，*核显计算模式* ，可支持硬件解码等加速

~~*如果你不喜欢我定制好的USB 口， 前2个 3.0 后就只有主板自带的3.0和2.0 等原生接口（Typec 我也定义好了）*~~

尝试定制USB Port 过，但始终不完美，用他人定制好的USBPort.kext 也是如此



### 关于部分设置

* **声卡ID 我已进行定制 ，无需在boot-args 中注入alcid**

* 默认开启SIP （建议开启 防止手贱）

**如果你的主板不想更新BIOS ，你可以搜索有关 CFG 的Key 的Boolean 值 将其修改为True 也可以成功进入系统（休眠效果未知）**

#### USB 3.0

已注入`USBInjectAll.kext` 驱动 ，并为最新版本，支持400系列

####  SMBIOS

你需要使用`iMac20,1` 或者 `iMac20,2`  这个也是官方推荐的cometLake 的推荐版本 

#### NVME 

`NVMEFix .kext  `如果你的NVME 异常的话就加一下 ，我的INTEL 760P无需添加这个Kext ，加了甚至会引导失败

#### iCloud

* 如果iCloud 那些总是登陆失败或者重启后掉线 ，请重新生成SMBIOS
* 如成功登陆，请第一时间**关闭查找我的电脑**

<img src="https://tva1.sinaimg.cn/large/008eGmZEgy1gmz068vi8oj30ga09t767.jpg" alt="WX20210119-145550"  />

![WX20210119-151354](https://tva1.sinaimg.cn/large/008eGmZEgy1gmz07m64m4j30g90a5dhc.jpg)

<img src="https://tva1.sinaimg.cn/large/008eGmZEgy1gmz06oxebnj30oo0gfjtz.jpg" alt="WechatIMG3" style="zoom: 67%;" />

![WechatIMG1](/Users/cheney/Desktop/EFI 制作发帖/WX20210119-153222.png)

![WechatIMG2](https://tva1.sinaimg.cn/large/008eGmZEgy1gmz08injr7j30ug0o5tdd.jpg)

![WechatIMG1](https://tva1.sinaimg.cn/large/008eGmZEgy1gmz08m8uhwj30ug0o5q7a.jpg)