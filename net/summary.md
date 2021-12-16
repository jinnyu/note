# 网络设备

## 总体需求

1. 路由设备
   - 内网穿透
   - 自定义内网DNS
   - 反追踪 + 去广告
   - ~~特殊需求~~

2. 交换设备
   - 必选 电口 4个以上(含) 2.5G (10G最好)
   - 必选 光口 4个以上(含) 10G
   - 可选 POE供电

3. 无线设备
   - WIFI 6E
   - 无缝漫游

## 设备清单

| 购买情况 | 类型           | 名称                           | 价格                     | 配置 / 接口                                             | 供电     | 官网信息                                                                     | 其他信息                                                             |
| :------- | :------------- | :----------------------------- | :----------------------- | :------------------------------------------------------ | :------- | :--------------------------------------------------------------------------- | :------------------------------------------------------------------- |
| 已购     | 软路由         | 固耐普工控软由器               | 淘宝 588                 | J3455 / 8G DDR3L<br>128G mSATA / 4 * 1G RJ45            | DC       | -                                                                            | 准系统                                                               |
| 待选     | 交换机         | Mikrotik CRS312-4C+8XG-RM      | 1688 3580                | 4 * 10G SFP+ / 8 * 10G RJ45 (其中4个为光电复用)         | 220V     | [官网信息](https://mikrotik.com/product/crs312_4c_8xg_rm)                    | [KoolShare开箱](https://www.koolcenter.com/thread/176287)            |
| 待选     | 交换机         | 兮克 SKS7300-8GPY4CGS          | 淘宝 1399 / 拼多多 1199  | 4 * 10G SFP+ / 8 * 2.5G                                 | 220V     | [官网信息](https://www.seekswan.com/xksupport/Sks7300.htm)                   | -                                                                    |
| 待选     | 交换机         | 普联 TL-R5408PE-AC             | 淘宝 839                 | 4 * 2.5G RJ45 (POE) / 4 * 1G RJ45 (POE) / 内置AC        | 220V     | [官网信息](https://www.tp-link.com.cn/product_1972.html)                     | [acwifi拆解](https://www.acwifi.net/17663.html)                      |
| 待选     | 无线控制器     | 普联 TL-AC100 (V4.0)           | 淘宝 199 / 闲鱼 175      | 5 * 100M RJ45                                           | DC       | [官网信息](https://www.tp-link.com.cn/product_347.html)                      | [acwifi拆解](https://www.acwifi.net/17772.html)                      |
| 待选     | 无线接入点     | 普联 TL-XAP5407GC-PoE/DC易展版 | 1688 840                 | 1 * 2.5G RJ45                                           | DC / POE | [官网信息](https://www.tp-link.com.cn/product_1846.html)                     | [acwifi拆解](https://www.acwifi.net/16413.html) / DC电源线需自行购买 |
| 待选     | 万兆光转电模块 | 鸿章安防                       | 淘宝 235                 | SFP+ 转 RJ45                                            | -        | [官网信息](http://www.fangyuhe.com/product/10g/20211001/11.html)             | -                                                                    |
| 待选     | 配件           | DC 电源                        | 淘宝 25+                 | 5.5 * 2.1 mm                                            | DC 输出  | -                                                                            | -                                                                    |
| 待选     | 配件           | 猫头鹰 4020风扇                | 淘宝 110 三方 / 119 官方 | 40 * 20 mm / PWM                                        | 4pin     | [官网信息](https://noctua.at/cn/nf-a4x20-pwm)                                | 为 Mikrotik CRS312-4C+8XG-RM 降噪 需求4个                            |
| 出局     | 交换机         | ~~普联 TL-R6812TP-AC~~         | 闲鱼 1530                | 8 * 10G SFP+ / 4 * 1G RJ45 (POE) / 内置AC               | 220V     | [官网信息](https://www.tp-link.com.cn/product_1974.html)                     | [CHH讨论](https://www.chiphell.com/thread-2350359-1-1.html)          |
| 出局     | 交换机         | ~~普联 TL-ST5008F~~            | 淘宝 819 / 闲鱼 700      | 8 * 10G SPF+                                            | 220V     | [官网信息](https://www.tp-link.com.cn/product_1649.html)                     | [CHH开箱](https://www.chiphell.com/thread-2244916-1-1.html)          |
| 出局     | 交换机         | ~~网件 MS510TXUP~~             | 价格较贵                 | 2 * 10G SFP+ / 4 * 10G RJ45 (POE) / 4 * 2.5G RJ45 (POE) | 220V     | [官网信息](https://www.netgear.com/business/wired/switches/smart/ms510txup/) | -                                                                    |
| 出局     | 交换机         | ~~网件 MS510TXM~~              | 价格较贵                 | 2 * 10G SFP+ / 4 * 10G RJ45 / 4 * 2.5G RJ45             | 220V     | [官网信息](https://www.netgear.com/business/wired/switches/smart/ms510txm/)  | -                                                                    |
