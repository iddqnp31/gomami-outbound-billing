# GoMami出站流量计费到底怎么算？单向计费、超量限速、入站免费这些坑你搞懂了吗——附全系套餐流量配置与省钱姿势全表

做跨境业务、跑数据同步、搭海外节点的人，最怕的不是服务器性能不够，而是月底一看账单——流量超了，钱没了。**GoMami出站流量计费**这件事，最近在圈子里被问得特别多。有人听说它是单向计费，有人担心超量会停机，还有人搞不清"出站"和"入站"到底哪个算钱。今天就把这件事彻底掰开揉碎讲清楚，顺便把 GoMami（圈内人爱叫"狗妈"）全系套餐的流量配置、超量处理、省钱优惠码一次性整理给你。

## 一、先搞懂：GoMami出站流量计费的核心规则

很多人搜"GoMami出站流量计费"时，其实心里装着好几个疑问。我直接把官方文档和实测信息里最关键的几条规则拎出来，你一看就明白。

**规则一：只算出站，入站完全免费。**

这是 GoMami 最显性的一个特点。官方 FAQ 里写得很直接——"GoMami 只对出站流量计费，入站流量完全免费"。换句话说，你从外面往服务器里传文件、拉镜像、做数据备份回灌，这些**入站方向**的流量，一个字节都不计入账单。只有服务器主动往外发数据（出站/Outbound）才消耗套餐里的流量额度。

**规则二：流量超量不会停机，会限速到 20 KB/s。**

这也是很多人最关心的一点。GoMami 的策略是：套餐流量跑满之后，带宽会被**降速到 20 KB/s**，一直到下一个计费周期开始才恢复。不会直接停机，也不会自动扣超额费用。这个处理方式对建站用户比较友好——站点还能访问，只是慢得像回到了拨号时代，至少不会突然打不开让用户以为你跑路了。

**规则三：流量是单向统计，标注的额度就是出站可用量。**

你在套餐表里看到的"1TB""2TB""5TB"这些数字，指的就是出站流量额度，不是入站+出站的总和。这点和搬瓦工那种双向计费的模式不一样，别拿别的厂商的双向逻辑套进来。

> 简单总结一句话：**入站随便用，出站按额度算，超了不停机只降速。**

## 二、为什么"单向计费"这件事值得单独拎出来说

你可能觉得，单向计费不就是少算一半嘛，有啥好讲的？真到自己用的时候你会发现，这个规则的实际影响比想象中大得多。

**场景一：数据同步与备份回灌。** 比如你用 GoMami 的香港节点做海外业务，每天要把国内的数据库快照同步上去。同步方向是"国内→服务器"，属于入站，**不计费**。这意味着你可以放心地做大文件传输、定期备份回灌，不用心疼流量。

**场景二：CDN 回源。** 如果你拿 GoMami 当源站，用户访问经过 CDN 回源拉数据，这个方向是出站，**要算流量**。所以做内容分发场景时，得把回源流量预估进去。

**场景三：下载站、网盘类业务。** 用户从服务器下载文件，全是出站方向，**吃流量最狠**。这类业务选套餐时，流量额度要比 CPU、内存更优先考虑。

**场景四：代理、中转类用途。** 这类场景下出站和入站都不小，但 GoMami 只算出站那一半，等于变相帮你省了一半流量成本。这也是为什么圈内做中转的人对 GoMami 的单向计费评价很高。

## 三、超量之后怎么办：限速、加购、换套餐三条路

流量跑满被降到 20 KB/s，确实难受。GoMami 给了你三个选择，不用干等到下个月。

**第一条路：等。** 限速到 20 KB/s 撑到下个计费周期，自动恢复。适合流量超得不多、业务能忍的场景。

**第二条路：买流量包。** 官方文档里提到，GoMami 支持"购买流量包——按需加购流量，无需升级套餐"。也就是说你不用为了多几 TB 流量去换更贵的套餐，直接加购就行。Forge 独立服务器系列的超出部分按 **$0.06/GB** 计费，VPS 系列的加购价格以工单咨询为准。

**第三条路：升级套餐。** 如果你的业务长期处于流量紧张状态，那不如直接升级到更高流量的套餐，比反复买流量包划算。GoMami 支持套餐变更，多数情况下不需要重新部署服务器。

## 四、全系套餐流量配置一览：从入门到旗舰

下面这张表是 GoMami 官网目前展示的**全部在售套餐**，按系列整理，重点标注了出站流量额度和带宽，方便你按"流量需求"来选。所有购买链接都带 AFF 参数，直接点就能进对应套餐的下单页。

### 香港节点（HKG）

**HKG Turin 系列（AMD EPYC 9575F / Zen 5 / 5.0GHz / PCIe Gen5 + DDR5）**

| 套餐 | vCPU | 内存 | NVMe SSD | 出站流量 | 带宽 | 月付价格 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Turin Mini | 2 | 4GB | 100GB | 1TB | 2Gbps | $69 | [立即购买](https://gomami.io/aff.php?aff=415&pid=14) |
| Turin Air | 4 | 8GB | 140GB | 2TB | 2Gbps | $129 | [立即购买](https://gomami.io/aff.php?aff=415&pid=15) |
| Turin Pro | 6 | 16GB | 180GB | 5TB | 5Gbps | $299 | [立即购买](https://gomami.io/aff.php?aff=415&pid=16) |
| Turin Ultra | 12 | 32GB | 220GB | 10TB | 5Gbps | $599 | [立即购买](https://gomami.io/aff.php?aff=415&pid=22) |

**HKG Peak X5 系列（AMD Ryzen 9 9950X / 5.7GHz Boost / 支持 Windows）**

| 套餐 | vCPU | 内存 | NVMe SSD | 出站流量 | 带宽 | 月付价格 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Peak X5 Mini | 2 | 4GB | 40GB | 1TB | 2Gbps | $69 | [立即购买](https://gomami.io/aff.php?aff=415&pid=hkgpeakx5mini) |
| Peak X5 Air | 4 | 8GB | 60GB | 2TB | 2Gbps | $99 | [立即购买](https://gomami.io/aff.php?aff=415&pid=hkgpeakx5air) |
| Peak X5 Pro | 6 | 16GB | 80GB | 5TB | 5Gbps | $199 | [立即购买](https://gomami.io/aff.php?aff=415&pid=hkgpeakx5pro) |

**HKG Pulse 系列（AMD EPYC 7763 / 3.5GHz / 入门主力）**

| 套餐 | vCPU | 内存 | NVMe SSD | 出站流量 | 带宽 | 月付价格 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Pulse Nano | 2 | 2GB | 40GB | 500GB | 1Gbps | $49 | [立即购买](https://gomami.io/aff.php?aff=415&pid=26) |
| Pulse Mini | 2 | 4GB | 60GB | 1TB | 1Gbps | $59 | [立即购买](https://gomami.io/aff.php?aff=415&pid=4) |
| Pulse Air | 4 | 8GB | 80GB | 2TB | 1Gbps | $119 | [立即购买](https://gomami.io/aff.php?aff=415&pid=5) |
| Pulse Pro | 8 | 16GB | 100GB | 5TB | 3Gbps | $269 | [立即购买](https://gomami.io/aff.php?aff=415&pid=6) |
| Pulse Ultra | 16 | 32GB | 300GB | 10TB | 5Gbps | $499 | [立即购买](https://gomami.io/aff.php?aff=415&pid=25) |

**HKG Forge 独立服务器系列（AMD EPYC 7663 / 56核112线程 / 资源独占）**

| 套餐 | CPU | 内存 | NVMe SSD | 出站流量 | 带宽 | 月付价格 | 安装费 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Forge Mini | EPYC 7663 56核 | 128GB | 960GB | 10TB | 2Gbps | $399 | $68 | [立即购买](https://gomami.io/aff.php?aff=415&pid=9) |
| Forge Air | EPYC 7663 56核 | 256GB | 4TB | 20TB | 2Gbps | $699 | $68 | [立即购买](https://gomami.io/aff.php?aff=415&pid=20) |

> Forge 系列超出套餐流量后按 **$0.06/GB** 计费，不会直接降速，适合流量波动大的业务。

### 日本节点（JPN）

**JPN Pulse 系列（AMD EPYC 7773X / 7K83 / 3.5GHz）**

| 套餐 | vCPU | 内存 | NVMe SSD | 出站流量 | 带宽 | 月付价格 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Pulse Nano | 2 | 2GB | 40GB | 500GB | 1Gbps | $29 | [立即购买](https://gomami.io/aff.php?aff=415&pid=13) |
| Pulse Mini | 2 | 4GB | 40GB | 1TB | 1.5Gbps | $49 | [立即购买](https://gomami.io/aff.php?aff=415&pid=10) |
| Pulse Air | 4 | 8GB | 80GB | 2TB | 1Gbps | $89 | [立即购买](https://gomami.io/aff.php?aff=415&pid=11) |
| Pulse Pro | 8 | 16GB | 100GB | 5TB | 3Gbps | $169 | [立即购买](https://gomami.io/aff.php?aff=415&pid=12) |
| Pulse Ultra | 12 | 32GB | 300GB | 10TB | 3Gbps | $338 | [立即购买](https://gomami.io/aff.php?aff=415&pid=24) |

### 新加坡节点（SIN）

**SIN Pulse 系列（AMD EPYC 7773X / 7K83 / 3.5GHz）**

| 套餐 | vCPU | 内存 | NVMe SSD | 出站流量 | 带宽 | 月付价格 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Pulse Nano | 2 | 2GB | 40GB | 500GB | 1Gbps | $29 | [立即购买](https://gomami.io/aff.php?aff=415&pid=21) |
| Pulse Mini | 2 | 4GB | 60GB | 1TB | 1Gbps | $49 | [立即购买](https://gomami.io/aff.php?aff=415&pid=17) |
| Pulse Air | 4 | 8GB | 80GB | 2TB | 1Gbps | $89 | [立即购买](https://gomami.io/aff.php?aff=415&pid=18) |
| Pulse Pro | 8 | 16GB | 100GB | 5TB | 3Gbps | $169 | [立即购买](https://gomami.io/aff.php?aff=415&pid=19) |
| Pulse Ultra | 12 | 32GB | 300GB | 10TB | 5Gbps | $338 | [立即购买](https://gomami.io/aff.php?aff=415&pid=23) |

### 美国洛杉矶节点（LAX）

**LAX Pulse 系列（AMD EPYC 7K62 / 3.3GHz / CN2 GIA + AS9929 + CMIN2 三网双程精品）**

| 套餐 | vCPU | 内存 | NVMe SSD | 出站流量 | 带宽 | 月付价格 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Pulse Nano | 2 | 2GB | 40GB | 1TB | 1Gbps | $29 | [立即购买](https://gomami.io/aff.php?aff=415&pid=27) |
| Pulse Mini | 2 | 4GB | 60GB | 2TB | 1Gbps | $59 | [立即购买](https://gomami.io/aff.php?aff=415&pid=28) |
| Pulse Air | 4 | 8GB | 80GB | 4TB | 2Gbps | $129 | [立即购买](https://gomami.io/aff.php?aff=415&pid=29) |
| Pulse Pro | 6 | 16GB | 100GB | 8TB | 3Gbps | $259 | [立即购买](https://gomami.io/aff.php?aff=415&pid=30) |
| Pulse Ultra | 12 | 32GB | 300GB | 15TB | 5Gbps | $599 | [立即购买](https://gomami.io/aff.php?aff=415&pid=31) |
| Pulse Titan | 12 | 32GB | 600GB | 30TB | 10Gbps | $999 | [立即购买](https://gomami.io/aff.php?aff=415&pid=32) |

> 注意看 LAX Pulse 的流量配置——同样是 Nano，LAX 给到 1TB 出站，比香港 Pulse Nano 的 500GB 翻了一倍。如果你的业务出站流量大、又需要美西落地，LAX Pulse 的流量性价比明显更高。

## 五、按"出站流量需求"挑套餐：四个典型场景

光看表格可能还是有点抽象，下面按几种常见需求场景，给你直接对应到具体套餐。

**场景一：个人建站 / 轻量博客（出站 < 1TB/月）。** 选 👉 [HKG Pulse Mini](https://gomami.io/aff.php?aff=415&pid=4) 或 👉 [JPN Pulse Mini](https://gomami.io/aff.php?aff=415&pid=10)，1TB 出站够用，价格分别是 $59/月和 $49/月。日本节点更便宜，香港节点延迟更低（<30ms vs <50ms），按你受众所在地选。

**场景二：跨境电商 / 多站点运营（出站 2-5TB/月）。** 选 👉 [HKG Turin Air](https://gomami.io/aff.php?aff=415&pid=15) 或 👉 [LAX Pulse Air](https://gomami.io/aff.php?aff=415&pid=29)。前者 2TB 出站 + Zen 5 高频 CPU + PCIe Gen5，建站 IO 强；后者 4TB 出站，流量更宽裕，适合面向北美用户的店铺。

**场景三：内容分发 / 下载类业务（出站 8TB+/月）。** 直接看 👉 [LAX Pulse Pro](https://gomami.io/aff.php?aff=415&pid=30)（8TB）或 👉 [LAX Pulse Ultra](https://gomami.io/aff.php?aff=415&pid=31)（15TB）。流量大户首选 LAX，单价最划算。如果对延迟敏感，👉 [HKG Pulse Ultra](https://gomami.io/aff.php?aff=415&pid=25) 给到 10TB 出站 + 5Gbps 带宽，香港延迟优势明显。

**场景四：数据库 / 大内存服务（出站不是瓶颈，要的是资源独占）。** 选 👉 [HKG Forge Mini](https://gomami.io/aff.php?aff=415&pid=9)，128GB 内存 + 56 核 + 10TB 出站，超出部分按 $0.06/GB 计费，不会降速，适合 MySQL/PostgreSQL/Elasticsearch 这类对内存和 IO 敏感的服务。

## 六、省钱姿势：优惠码与计费周期怎么搭最划算

聊完流量，再说说怎么把账单压下来。GoMami 的优惠码体系分两类，一类是全系通用，一类是节点/系列专属。

**全系通用码：`GOMAMI365`**

这是覆盖面最广的码，**全系产品年付 8 折循环优惠**。所谓"循环"，就是续费时同样按 8 折算，不是首年便宜、续费原价的套路。年付下单时在结账页填入即可生效。按这个码算，HKG Pulse Mini 从 $49/月 降到 $39.2/月，Turin Pro 从 $199/月 降到 $159.2/月，一年下来能省几百美元。

**节点/系列专属码**

| 优惠码 | 适用范围 | 折扣 | 计费周期 |
| --- | --- | --- | --- |
| `Hi,LAX` | LAX Pulse 全系 | 8 折 | 月付 |
| `Hello Japan` | JPN Pulse 全系 | 8.5 折 | 月付 |
| `Hi,Turin-M80` | HKG Turin | 8 折 | 月付 |
| `Hi,Turin-Q75` | HKG Turin | 7.5 折 | 季付 |
| `Hi,Turin-Y70` | HKG Turin | 7 折 | 年付 |
| `Hi,SIN-M80` | SIN Pulse | 8 折 | 月付 |
| `Hi,SIN-Q75` | SIN Pulse | 7.5 折 | 季付 |
| `Hi,SIN-Y70` | SIN Pulse | 7 折 | 年付 |

**怎么搭最省？** 一个简单原则：**月付用专属码试水，长期用年付 `GOMAMI365` 锁价。** 比如 HKG Turin，月付先用 `Hi,Turin-M80` 试一个月看体验，满意了第二年转年付 + `Hi,Turin-Y70` 直接 7 折，比 `GOMAMI365` 的 8 折还狠。SIN Pulse 同理，年付 `Hi,SIN-Y70` 比 `GOMAMI365` 多省 10%。Peak X5 和 LAX Pulse 没有专属年付码，就用 `GOMAMI365` 8 折。

> 所有优惠码都可以在 👉 [GoMami 结账页](https://bit.ly/Gomami) 的"Apply Promo Code"栏填入验证。

## 七、几个高频疑问，一次说清

**Q1：GoMami 出站流量到底怎么统计？是按 95 计费还是按总量？**
按总量计费，统计的是计费周期内累计的出站字节数，不是 95th percentile 那种峰值计费。所以不用担心某个瞬间带宽跑满被多算钱。

**Q2：流量超量会被停机吗？**
不会。降到 20 KB/s 继续跑，到下个周期自动恢复。Forge 独立服务器例外，超量后按 $0.06/GB 计费，不降速。

**Q3：入站流量真的完全不计费？包括大文件上传？**
是的，入站方向不计费，无论文件多大。这也是 GoMami 单向计费的核心优势，备份、同步、镜像拉取都放心用。

**Q4：能不能加购流量包，不升级套餐？**
可以。官方文档明确支持"购买流量包——按需加购流量，无需升级套餐"。具体价格通过工单或 support@gomami.io 咨询。

**Q5：套餐之间能换吗？换的时候要重装吗？**
支持套餐变更，多数情况下不需要重新部署服务器，控制面板里操作即可。但降配可能有数据风险，建议先备份。

**Q6：有试用吗？**
有。全系套餐支持 **24 小时无风险退款**，下单后 24 小时内不满意可全额退。等于给你一天时间实测延迟、带宽、出站流量统计是否准确。

## 八、写在最后：搞懂计费规则，比挑最贵的套餐更重要

回到最开始那个问题——**GoMami出站流量计费**到底怎么算？现在你应该清楚了：入站免费、出站按额度、超量降速不停机、可加购可升级。这套规则的核心好处是**对下载、同步、备份类场景天然友好**，因为大头流量往往在入站方向，而 GoMami 这部分一分不收。

挑套餐的时候，别只盯着 CPU 和内存看。先估一下自己业务的出站流量峰值和均值，再对照上面的流量配置表选档位。流量买大了浪费，买小了被限速到 20 KB/s 那种窒息感，谁试谁知道。

最后给个直接建议：如果你是第一次接触 GoMami，先用 👉 [HKG Pulse Mini](https://gomami.io/aff.php?aff=415&pid=4) 或 👉 [JPN Pulse Nano](https://gomami.io/aff.php?aff=415&pid=13) 这种入门档试水，配上 24 小时退款政策，实测一下出站流量统计、晚高峰带宽、到大陆的延迟，再决定要不要上 Turin 或 Forge 这种高配。毕竟，再好的套餐，也得跑起来顺手才算数。
