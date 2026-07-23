## Hi there, I'm 田星雨 (doggytian) 👋

**后台开发工程师** · 专注 **C++ / 高并发服务 / AI 编程工具链**

- 🔭 日常：大规模在线服务的架构设计、性能优化与稳定性建设
- 🌱 在学：内核旁路网络（DPDK / io_uring）、市场微结构与做市策略、tick-to-trade 延迟分解
- 🛠️ 在折腾：Vibe Coding、AI Agent Skill 的开发与发布
- 💬 可以聊：C++ 高并发、缓存架构、服务降本提效、AI 辅助开发
- 📫 联系我：xingyutian2023@163.com

---

### 🧰 技术栈

![C++](https://img.shields.io/badge/C++-00599C?style=flat-square&logo=cplusplus&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![Kafka](https://img.shields.io/badge/Kafka-231F20?style=flat-square&logo=apachekafka&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)

**方向关键词**：高并发服务 · 缓存架构 · 分布式中间件 · 可观测性 · 性能调优 · AI 编程工具链

---

### 📌 精选项目

#### ⚡ [MiniTrader — 从零实现的低延迟交易系统](https://github.com/doggytian/MiniTrader)

[![CI](https://github.com/doggytian/MiniTrader/actions/workflows/ci.yml/badge.svg)](https://github.com/doggytian/MiniTrader/actions/workflows/ci.yml)

用现代 C++20 从零构建的高性能撮合系统，完整实现从行情接收到策略决策到风控落单的全链路，
专注于演示量化交易场景下的低延迟系统设计原则。

- **Lock-free SPSC 队列**：`memory_order_acquire/release` 极简内存屏障，`std::byte[]`
  替换 C++23 废弃的 `aligned_storage_t`，push/pop 往返 **2.1 ns**
- **O(1) 撮合簿**：平坦数组按价格索引（无红黑树 pointer chasing），O(1) `cancel_order`
  via `unordered_map<id → list::iterator>`，单级 add **43 ns**、cancel **24 ns**
- **完整数据流**：`MarketTick → SPSCQueue → TradingEngine → RiskGate → OrderBook → FillCallback → Strategy`，稳态全路径 **65 ns**，含双边下单 **735 ns**
- **做市策略 Demo**：`SpreadStrategy` 双边报价，成交后撤销对侧、自动重报；含自成交检测
- **延迟分位数**（10 万次采样）：P50 **83 ns** · P90 **84 ns** · P99 **125 ns** · P99.9 **167 ns**
- **工程化**：GitHub Actions CI（Ubuntu + macOS）、Google Benchmark、per-tick 延迟计时、一键脚本

> 技术栈：C++20 · CMake · Google Test · Google Benchmark。
> 📄 [README](https://github.com/doggytian/MiniTrader/blob/main/README.md)

#### 🗺️ [RoadLens — 车道级地理空间数据可视化与质检工作台](https://github.com/doggytian/RoadLens)

[![CI](https://github.com/doggytian/RoadLens/actions/workflows/ci.yml/badge.svg)](https://github.com/doggytian/RoadLens/actions/workflows/ci.yml)

一个完全自包含、可本地运行的 Web 工具，用于**车道级 / 道路级地理空间数据的可视化分析
与质量检查**。数据全部来自公开来源（OpenStreetMap）或合成随机几何，依赖均为开源库，
**不含任何专有代码、数据或内部服务**。

- **可视化交互**：Leaflet 地图叠加 RoadCorridor / Lane / ReferenceLink，支持点选 / 框选、
  属性面板、图层样式自定义与经纬度跳转
- **8 类质检**：基于 `shapely` 实现走廊宽度、缓冲断裂、中心线覆盖、压盖、菱形拓扑、
  几何有效性、参考绑定、参考拓扑，结果以 GeoJSON 分类着色叠加
- **米制精度**：几何计算统一投影到以 tile 中心为原点的方位等距平面，公里级尺度误差极小
- **工程化配套**：Flask + shapely + pyproj 后端，多用户工作区隔离、LRU 缓存与后台清理；
  含单元测试 / GitHub Actions CI / Docker 容器化部署

> 技术栈：Python · Flask · shapely · pyproj · Leaflet（原生 ES6，无前端框架）。
> 📄 [README](https://github.com/doggytian/RoadLens/blob/main/README.md)

---

### 📊 GitHub Stats

![doggytian's GitHub stats](https://github-readme-stats.vercel.app/api?username=doggytian&show_icons=true&theme=default&hide_border=true&count_private=true)

![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=doggytian&layout=compact&theme=default&hide_border=true)
