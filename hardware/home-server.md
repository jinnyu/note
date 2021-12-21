# 私有服务器

## 服务器硬件

### 已有设备

| 部件         | 品牌   | 型号                | 备注             |
| :----------- | :----- | :------------------ | :--------------- |
| CPU          | AMD    | Ryzen 5 1600        |                  |
| 主板         | 微星   | X470 Gaming Pro MAX |                  |
| 内存         | 七彩虹 | DDR4 2666 8G * 2    | 超至3200Mhz      |
| 内存         | 七彩虹 | DDR4 2666 8G * 2    | 超至3200Mhz      |
| SSD          | 英特尔 | 傲腾 16G            | 系统盘           |
| SSD          | 三星   | 850 EVO 250G        | 软件盘           |
| SSD          | HPE    | PM1723b 3.84T       | 存储盘 U2转PCI-E |
| HDD          | 东芝   | P300 3T * 4         | 存储盘 (ZFS)     |
| 万兆光纤网卡 | 迈洛思 | Connect-X3          |                  |
| 电源         | 讯景   | XFX 550             |                  |
| 机箱         | AY     | 4U 工控机箱         |                  |
| UPS          | 施耐德 | BK650M2-CH          |                  |

### 待购设备

- [ ] 购买新硬盘
  - [ ] HDD 企业级 8T/12T * 4
  - [ ] SSD 1T/2T * 2 (已购镁光M600 * 1)
  - [ ] ~~SSD 三星/英特尔 250G * 2~~
- [ ] NAS机箱 (含背板)
- [ ] 拆机阵列卡 (HBA)
- [ ] 1U服务器电源 + 转ATX模块


## 服务器软件

### 服务

1. 内网穿透

   - frp
   - lanproxy (考察阶段 2021-12-20)

2. 代码托管

   - Gitea

3. 远程下载

   - aria2

4. 开发环境

   - jdk (graalvm/openjdk)
   - maven
   - mysql
   - postgres
   - redis
   - nacos
   - rocketmq
   - grafana
   - loki
   - jenkins
   - sonarqube

5. Web服务

   - nginx
   - ~~虚拟局域网~~

6. 文件分享

  内网 - `Samba` 配合万兆网卡实现高速读取文件  
  公网 - `FileBrowser` 私有文件外链
