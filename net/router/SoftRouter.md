# 软路由

### 背景

家中老AMD平台神奇的复活了... 之前买的G3258空闲出来了, 闲着也是闲着...

### 配置

| 部件          | 品牌       | 型号                             | 购买价格 | 产品链接                                                                                                                       | 说明                                                          |
| :------------ | :--------- | :------------------------------- | :------- | :----------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------ |
| ~~CPU~~       | ~~Intel~~  | ~~Pentium G3258 (20周年纪念版)~~ | ~~469~~  | ~~[链接](https://www.intel.cn/content/www/cn/zh/products/processors/pentium/g3258.html)~~                                      | ~~[购买链接](https://item.jd.com/1166116.html)~~              |
| CPU           | Intel      | Core i7 4702HQ                   | 550      | [链接](https://ark.intel.com/content/www/cn/zh/ark/products/75118/intel-core-i7-4702hq-processor-6m-cache-up-to-3-20-ghz.html) | [购买链接](https://item.taobao.com/item.htm?id=561914181308)  |
| ~~主板~~      | ~~Asrock~~ | ~~Fatal1ty B85 Killer~~          | ~~539~~  | ~~[链接](http://www.asrockchina.com.cn/MB/Intel/Fatal1ty%20B85%20Killer/index.cn.asp)~~                                        | ~~[购买链接](https://item.jd.com/1023241.html)~~              |
| 主板          | MSI        | B85-G43 Gaming                   | 599      | [链接](https://cn.msi.com/Motherboard/B85-G43-GAMING.html)                                                                     | [购买链接](https://item.jd.com/953798.html)                   |
| 内存          | G.Skill    | DDR3 1333 4G * 2                 | 0        | [链接](https://www.gskill.com/tw/product/203/225/1532315176/F3-10666CL9D-8GBRLRipjawsDDR3-1333MHz-CL9-9-9-1.50V8GB-(2x4GB))    | 朋友送的                                                      |
| 内存          | Samsung    | DDR3 1600 4G * 2                 | 165      | [链接](https://www.samsung.com/semiconductor/cn/dram/module/M391B5173EB0-YK0)                                                  | 闲鱼 山寨条                                                   |
| SSD           | Kodak      | X100 120G                        | 131      | [链接](http://kodakflash.com.cn/product/c/x--0007)                                                                             | [购买链接](https://item.jd.com/100001967519.html)             |
| 板载网卡      | Killer     | E2200                            | 0        | 未找到介绍 附官网[链接](https://www.killernetworking.com)                                                                      | -                                                             |
| PCI-E有线网卡 | Intel      | I350 T4V2                        | 233.24   | [链接](https://ark.intel.com/content/www/cn/zh/ark/products/84805/intel-ethernet-server-adapter-i350-t4v2.html)                | [购买链接](https://item.taobao.com/item.htm?id=556165663722)  |
| PCI-E无线网卡 | Intel      | 9260 AC                          | 65.21    | [链接](https://ark.intel.com/content/www/cn/zh/ark/products/99445/intel-wireless-ac-9260.html)                                 | [购买链接](https://item.taobao.com/item.htm?id=565776272616)  |
| 电源          | Antec      | VP300                            | 144      | [链接](http://www.antec.com.cn/index.php?m=content&c=index&a=show&catid=45&id=75)                                              | [购买链接](https://detail.tmall.com/item.htm?id=567496242245) |
| 机箱          | DIY        | 开放式机架                       | 97.02    | [链接](https://item.taobao.com/item.htm?id=585430613332)                                                                       | [购买链接](https://item.taobao.com/item.htm?id=585430613332)  |

### 系统选择

因为之前用的是`R8000`(仍在服役), 对软件中心比较有好感, 所以目前的选择是`LEDE x86`.

### 架设方案

|        平台         |    日期    |           架构            |                状态                |
| :-----------------: | :--------: | :-----------------------: | :--------------------------------: |
| Windows Server 2019 | 2019-02-27 | 物理机 -> Hyper-v -> LEDE | 安装成功, 运行正常. (已切换至ESXi) |
|        ESXi         | 2910-04-05 |  物理机 -> ESXi -> LEDE   |        安装成功, 运行正常.         |

### 折腾历程

> 2019-??

放弃软路由, 原因有几点...  
1 整体功耗较高.  
2 研究不透彻, 要学的东西比较多. (虚拟化平台, 虚拟化硬件直通, 网络协议等等)  
3 挂了个2T的硬盘, 由于长时间不关机, 导致通电时间暴增.  

所以暂时放弃了, 等后期有需要的时候再考虑上软路由.

> 2019-04-27  

3月底的时候发现了一个比较不错的魔改CPU `英特尔® 酷睿™ i7-4702HQ 处理器`  
4C8T 3.2Ghz睿频 HD4600核显 支持 `VT-x` (下面会说为什么必须要这个功能)

Q 为什么要换CPU?  
A 首先 3258 (TDP 53W) 超频后功耗较大, 即使待机状态下 整机也有45W左右的样子, 差不多一天一度电.  
   &emsp;虽说 4702 (TDP 37W) 功耗和那些低压U的功耗比不了, 但至少是满血的4C8T, 方便多开虚拟机.  
   &emsp;之前有在 `Windows Server 2019` 上尝试虚拟化别的服务, 但是运行起来相当卡, 内网用远程桌面都会掉,  
   &emsp;其次 3258 不支持 `VT-x`, 不支持 `VT-x` 就没办法直通硬件设备到虚拟机上, 性能上会差不少.  
   &emsp;(性能比较 : 物理设备 > 直通设备 > 虚拟设备 , 部分支持较好的设备性能接近物理设备的直接表现)  

Q 为什么要换虚拟化平台?  
A `Windows Server 2019` 占用空间太大了, 大概在15G左右(桌面体验版).  
  &emsp;不能直通硬件? (不清楚Win上的直通)

> 2019-02-28  

待解决问题  
 * ~~`AP`设置模式问题.(在`LEDE`中无法看到`AP`的IP, 但`AP`功能正常.)~~  
 * ~~固定其他设备IP~~  
 * 插件配置  
 * `NAS`和`Linux`服务架设  

> 2019-02-27  

经过一天的思考, 现在已成功装好`LEDE`系统, 并正常使用!  
简单记录下怎么配置系统  
PS : 我有两块网卡, 所以不是单臂路由, 安装难度会小很多.  
1. 物理机安装网卡并安装驱动  
2. 在`Hyper-v`中添加虚拟网卡  
   - 创建`LAN`口虚拟网卡(`Intel`), 类型为外部, 绑定到外置网卡上. (我这里创建了4个, 每个对应一个网口. 不知道对不对, 有待研究.)  
   - 创建`WAN`口虚拟网卡(`Killer`), 类型为外部, 绑定到板载网卡上.  
3. 创建`LEDE`虚拟机
   - 虚拟机代数选择第二代 (`UEFI`固件)  
   - 网络连接暂时不选择  
   - 磁盘选择转换为`Hyper-v`之后的镜像地址 [转换工具](https://www.starwindsoftware.com/starwind-v2v-converter#download)  
   - 扩展磁盘空间  
4. 修改虚拟机设置
   - 添加网卡 注意 : 这里要先添加`LAN`口网卡, 最后再添加`WAN`口网卡, 不知道什么原因, 有待研究.  
   - 修改所有网卡设置, 点开网卡前边的`+`, 在高级设置中勾选`启用MAC地址欺骗`.  
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
  * ~~固定宿主机IP~~  
  * ~~插件安装~~  
  * `NFS`挂载宿主机硬盘  
 
> 2019-02-26
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
- 在不关闭光猫`DHCP`的情况下能否做到网卡之间的连通
- 如何分配物理网卡和虚拟网卡之间的关系

~~头痛中...~~  
