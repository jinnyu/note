# 软路由

### 背景

家中老AMD平台神器的复活了... 之前买的G3258空闲出来了, 闲着也是闲着...

### 配置

| 部件 | 品牌 | 型号 | 价格 | 链接 | 
| :------: | :------: | :------: | :------: | :------: |
| CPU | Intel | Pentium G3258 | 469 | https://item.jd.com/1166116.html |
| 主板 | Asrock | 玩家至尊 B85 杀手版 主板 | 539 | https://item.jd.com/1023241.html |
| 内存 | G.Skill | DDR3 1333 4G * 2 | 0 (朋友送的) | http://www.gskill.com/tw/product/f3-10666cl9s-4gbrl |
| SSD | Kodak | 柯达X100 128G | 131 | https://item.jd.com/100001967519.html |
| 网卡 | Intel | I350T4V2 | 233.24 | https://item.taobao.com/item.htm?id=556165663722 |
| 电源 | Antec | VP300 额定300W | 144 | https://detail.tmall.com/item.htm?id=567496242245 |
| 机箱 | DIY | 开放式机架 | 97.02 | https://item.taobao.com/item.htm?id=585430613332 |

### 系统选择

因为之前用的是R8000(仍在服役), 对软件中心比较有好感, 所以目前的选择是`LEDE x86`

### 架设方案

| 平台 | 架构 |
| :-----: | :-----: |
| ESXi | 暂未尝试 |
| Hyper-v | 尝试中 |

### 折腾历程

初步想法 :  
物理机 安装 Windows Server 2019
在Server中利用`Hyper-v`虚拟出`LEDE`
但是暂时没有尝试出对的安装...  
当前难点是  
> 记录日期 : 2019-02-26
- 在不关闭光猫DHCP的情况下能否做到网卡之间的连通
- 如何分配网卡和虚拟网卡之间的关系

头痛中...