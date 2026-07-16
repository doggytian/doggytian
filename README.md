## Hi there, I'm 田星雨 (doggytian) 👋

**后台开发工程师** · 专注 **C++ / 高并发服务 / AI 编程工具链**

- 🔭 日常：大规模在线服务的架构设计、性能优化与稳定性建设
- 🌱 在学：LLM 推理优化（vLLM / KV Cache / PagedAttention）、AI Infra
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

#### 🚀 [CppTrader — 无锁订单网关优化](https://github.com/doggytian/CppTrader/tree/feature/lockfree-order-gateway)

在开源撮合引擎 [CppTrader](https://github.com/chronoxor/CppTrader) 上，设计并实现
「网络线程 → 撮合线程」的**无锁 SPSC 交接前端**，对照 mutex + condition_variable
基线做量化评测。

- **无锁交接**：基于 SPSC 环形队列的单生产者-单消费者交接，替代锁 + 条件变量唤醒
- **背压量化**：引入在途上限（in-flight limit）保持队列浅水位，测得的是纯 hand-off
  开销而非排队延迟
- **分位数分析**：逐命令采集 `dequeue_ts - enqueue_ts`，输出 min/mean/p50/p90/p99/p999/max
- **实测**（12.6 万条命令）：p50 **23.75µs vs 231.7µs（≈9.8×）**，
  p99 **53.9µs vs 774µs（≈14.4× 尾延迟改善）**，端到端 **≈9.6× 提速**

> 我的贡献：对照基准设计 + 集成 + 背压量化 + 分位数分析；底层 `SPSCRingQueue`
> 由 CppCommon 提供。📄 [中文文档](https://github.com/doggytian/CppTrader/blob/feature/lockfree-order-gateway/documents/LOCKFREE_ORDER_GATEWAY.zh-CN.md)
> · [English](https://github.com/doggytian/CppTrader/blob/feature/lockfree-order-gateway/documents/LOCKFREE_ORDER_GATEWAY.md)

#### 🗺️ [RoadLens — 车道级地理空间数据可视化与质检工作台](https://github.com/doggytian/RoadLens)

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
