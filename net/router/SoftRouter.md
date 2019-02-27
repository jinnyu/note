# 软路由

### 背景

家中老AMD平台神奇的复活了... 之前买的G3258空闲出来了, 闲着也是闲着...

### 配置

| 部件 | 品牌 | 型号 | 购买价格 | 产品链接 |购买链接 |
| :------: | :------: | :------: | :------: | :------: | :------: |
| CPU | Intel | Pentium G3258 (20周年纪念版) | 469 | [链接](https://www.intel.cn/content/www/cn/zh/products/network-io/ethernet/gigabit-adapters/server-i350-t4v2.html) | [链接](https://item.jd.com/1166116.html) |
| 主板 | Asrock | Fatal1ty B85 Killer | 539 | [链接](http://www.asrockchina.com.cn/MB/Intel/Fatal1ty%20B85%20Killer/index.cn.asp) | [链接](https://item.jd.com/1023241.html) |
| 内存 | G.Skill | DDR3 1333 4G * 2 | 0<br>(朋友送的) | [链接](http://www.gskill.com/tw/product/f3-10666cl9s-4gbxl-) |  |
| SSD | Kodak | 柯达X100 128G | 131 | [链接](http://kodakflash.com.cn/product/c/x--0007) | [链接](https://item.jd.com/100001967519.html) |
| 板载网卡 | Killer | E2200 |   | [链接](https://www.killernetworking.com) <br>(没找到E2200的介绍, 附官网链接) |  |
| 外置网卡 | Intel | I350T4V2 | 233.24 | [链接](https://www.intel.cn/content/www/cn/zh/products/network-io/ethernet/gigabit-adapters/server-i350-t4v2.html) | [链接](https://item.taobao.com/item.htm?id=556165663722) |
| 电源 | Antec | VP300 (额定300W) | 144 | [链接](http://www.antec.com.cn/index.php?m=content&c=index&a=show&catid=45&id=75) | [链接](https://detail.tmall.com/item.htm?id=567496242245) |
| 机箱 | DIY | 开放式机架 | 97.02 | [链接](https://item.taobao.com/item.htm?id=585430613332) | [链接](https://item.taobao.com/item.htm?id=585430613332) |

### 系统选择

因为之前用的是`R8000`(仍在服役), 对软件中心比较有好感, 所以目前的选择是`LEDE x86`.

### 架设方案

| 平台 | 架构 | 状态 |
| :-----: | :-----: | :-----: |
| ESXi | 物理机 | 暂未尝试 |
| Hyper-v | 物理机 => Hyper-v => LEDE | ~~尝试中~~<br>2019-02-27 安装成功, 运行正常. |

### 折腾历程

为什么要用虚拟机去装`LEDE`?  

- 硬件资源比较不错, 比市面上的工控机要强不少.  
  CPU : `Pentium G3258`本身支持超频, 配合特定的`BIOS`可以实现. 目前稳定超到4.2Ghz, 电压为1.3V.  
  主板 : ATX B85大板 扩展性强 (空间不是问题, ITX党可以退下了.)
- `EXSi`**不支持**`Killer`网卡.  
- 可以用来虚拟化别的系统来提供服务. (`NAS`, `Linux`, `TimeMachine` 等)
- 在客厅当`HTPC`.

初步想法 :  
物理机 安装 `Windows Server 2019`
在`Server`中利用`Hyper-v`虚拟出`LEDE`.  

~~但是暂时没有尝试出对的配置...~~  
~~当前难点是~~  

> 2019-02-26
- 在不关闭光猫`DHCP`的情况下能否做到网卡之间的连通
- 如何分配物理网卡和虚拟网卡之间的关系

~~头痛中...~~  

> 2019-02-27  
- 经过一天的思考, 现在已成功装好`LEDE`系统, 并正常使用!  
  简单记录下怎么配置系统  
  PS : 我有两块网卡, 所以不是单臂路由, 安装难度会小很多.
    1. 物理机安装网卡并安装驱动
    2. 在`Hyper-v`中添加虚拟网卡
       * 创建`LAN`口虚拟网卡(`Intel`), 类型为外部, 绑定到外置网卡上. (我这里创建了4个, 每个对应一个网口. 不知道对不对, 有待研究.)  
       * 创建`WAN`口虚拟网卡(`Killer`), 类型为外部, 绑定到板载网卡上.  
    3. 创建`LEDE`虚拟机
       * 虚拟机代数选择第二代 (`UEFI`固件)  
       * 网络连接暂时不选择  
       * 磁盘选择转换为`Hyper-v`之后的镜像地址 转换工具 [StarWind V2V Image Converter](https://www.starwindsoftware.com/starwind-v2v-converter#download)  
       * 扩展磁盘空间  
    4. 修改虚拟机设置
       * 添加网卡 注意 : 这里要先添加`LAN`口网卡, 最后再添加`WAN`口网卡, 不知道什么原因, 有待研究.  
       * 修改所有网卡设置, 点开网卡前边的`+`, 在高级设置中勾选`启动MAC地址欺骗`.  
    5. 开机启动  
    6. 随便将一个设备插到`LAN`口上, 来保证`LEDE`将外接网卡当做`LAN`口看待.  
    7. 修改`LAN`口默认IP. `LEDE`默认`LAN`口IP为`192.168.1.1`, 这个地址有可能别的设备的网段有冲突, 所以最好更改下, 我这里用的是`10.0.0.1`.
    
       ```shell
       vi /etc/config/network
       ```

       按`i`, 进入编辑模式  
       修改`LAN`口的`192.168.1.1`为`10.0.0.1`  
       按`ESC`退出编辑模式  
       按`:wq` + 回车 保存修改  

    8. 重启虚拟机, 让`LEDE`接管虚拟网卡.  
    9. 将`WAN`口插上有网络的网线.  
    10. 正常情况下宿主机应该就可以上网了.
- 待解决问题  
  * 固定`LAN`口IP地址  
  * 固定宿主机IP  
  * 插件安装  
  * `NFS`挂载宿主机硬盘  

