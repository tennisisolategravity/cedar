# LinkMap 资源导航系统

LinkMap 是一个面向技术调研、内容聚合与知识管理场景的轻量化外链资源汇总平台。项目定位为技术团队、独立研究者与内容运营人员提供可自部署的 URL 资产化管理工具，通过结构化索引与分类标签体系，将分散的网页链接转化为可检索、可审计、可共享的知识资产。

本项目并非传统书签管理器或收藏夹工具，而是面向批次化、项目化资源采集场景设计的专业外链治理方案。LinkMap 为每一条资源提供稳定的本地缓存元数据字段，支持来源域名溯源、采集批次标记、内容摘要快照与访问状态监控，适用于需要长期维护大量外链引用关系的技术文档库、开源项目 README 资源附录、行业报告参考资料表等严肃写作场景。

目标用户包括：技术博客作者、开源项目维护者、科研助理、数据分析师、知识库管理员以及任何需要系统化管理数百级以上外链资源的专业人员。LinkMap 不依赖第三方云服务，所有数据存储于本地 SQLite 数据库与 YAML 索引文件中，确保数据主权与长期可维护性。

## 功能概览

**批次化资源导入** 支持批量粘贴 URL 列表，自动解析域名、路径与查询参数，生成唯一资源指纹，单次可处理 80 批次共计 250 条链接。

**域名源分类视图** 自动识别资源来源域名（如 map.read.usuhx.com 与 map.mobile.xqnqq.com），按域名分组展示资源分布，便于评估外部引用依赖结构。

**资源状态健康检查** 内置异步 HTTP 头探测机制，标记每个链接的可达性、响应状态码与内容类型，辅助清理失效引用。

**自定义标签与批注系统** 为每条资源附加项目标签（如“第63批”“技术文档”“数据源”）、重要性等级与简短批注，支持后续筛选与导出。

**全文检索与筛选器** 基于 URL 路径关键词、域名、批次号、标签组合进行快速筛选，支持正则表达式高级查询。

**结构化导出功能** 将资源列表导出为 Markdown 列表、CSV 表格或 YAML 索引文件，直接嵌入技术文档或项目报告。

**数据快照与版本追踪** 每次导入或修改操作自动生成时间戳快照，支持回滚至任意历史状态，避免资源列表误删或覆盖。

## 应用场景

**技术文档附录资源整理** 撰写开源项目 README 或技术白皮书时，需要引用大量外部参考资料。LinkMap 可将零散的 URL 按章节编号、标签分类，最终一键生成符合规范的外链附录，避免手动排版错误。

**行业竞品与市场调研** 市场分析人员每日收集竞品官网、新闻稿、产品页面链接，使用 LinkMap 的批次导入功能按采集日期分组，结合域名源视图快速识别信息来源分布，为调研报告提供可追溯的原始数据支撑。

**学术论文参考文献预管理** 研究人员在文献调研阶段积累数十至数百篇在线论文、数据集与工具页面。LinkMap 的批注系统可记录每篇文献的阅读状态、重要程度与核心摘要，在撰写论文时可直接导出为 BibTeX 或标准引用列表。

**开源项目依赖链梳理** 大型开源项目需要整理上下游依赖项目、镜像站点、文档镜像与社区论坛链接。LinkMap 的健康检查功能可定期扫描依赖链接是否仍有效，提前发现镜像失效或域名过期问题。

**内容聚合站点运营** 运营人员每日从多个来源采集新闻、博客、视频链接，通过 LinkMap 的标签系统区分不同内容栏目，结合导出功能生成每日更新播报或周报链接合集。

## 快速开始

以下命令将在本地克隆项目仓库、安装依赖并启动开发服务器。

```bash
git clone https://github.com/linkmap-org/linkmap-station.git
cd linkmap-station
pip install -r requirements.txt
python scripts/init_db.py
python app.py
```

执行完成后，访问控制台输出的本地地址（默认 http://127.0.0.1:5000）即可进入 LinkMap 管理界面。首次启动将自动创建 SQLite 数据库文件与示例索引目录。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，用于后端 API 与命令行工具 |
| SQLite | 3.31 及以上 | 内嵌数据库，存储资源元数据与标签关系 |
| Flask | 2.2.x | Web 管理界面框架，提供 RESTful API |
| requests | 2.28.x | 用于资源健康检查的 HTTP 客户端 |
| PyYAML | 6.0 | 读写 YAML 索引文件，支持自定义序列化 |
| markdown | 3.4.x | 导出功能中将批注渲染为 Markdown 格式 |
| click | 8.1.x | 命令行交互工具，用于批量导入与维护操作 |
| pytest | 7.2.x | 单元测试框架（仅开发环境需要） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide/import.md | 如何批量导入 URL？如何配置批次标签？导入失败如何处理？ |
| 用户手册 | docs/user-guide/export.md | 支持哪些导出格式？如何自定义导出模板？能否只导出特定标签的资源？ |
| 运维指南 | docs/ops/health-check.md | 健康检查的频率如何配置？如何解读检查结果？怎样标记永久失效链接？ |
| 开发指南 | docs/dev/api-reference.md | 后端提供了哪些 API 端点？如何通过脚本调用资源查询接口？ |
| 开发指南 | docs/dev/database-schema.md | 数据库表结构是怎样的？如何扩展自定义字段？ |
| 配置说明 | docs/config/advanced-settings.md | 如何修改默认端口？怎样启用 HTTPS 本地证书？快照保留数量如何调整？ |
| 贡献指南 | CONTRIBUTING.md | 如何提交新功能？代码风格要求是什么？测试用例如何编写？ |

## 资源列表

- http://map.read.usuhx.com/Article/5382.shtml
- http://map.read.usuhx.com/Article/3598110.shtml
- http://map.mobile.xqnqq.com/Article/5369.shtml
- http://map.read.usuhx.com/Article/792869.shtml
- http://map.mobile.xqnqq.com/Article/097705.shtml
- http://map.mobile.xqnqq.com/Article/87546.shtml
- http://map.read.usuhx.com/Article/962987.shtml
- http://map.mobile.xqnqq.com/Article/28287.shtml
- http://map.read.usuhx.com/Article/56994.shtml
- http://map.read.usuhx.com/Article/592694.shtml
- http://map.read.usuhx.com/Article/6571.shtml
- http://map.mobile.xqnqq.com/Article/563125.shtml
- http://map.mobile.xqnqq.com/Article/8053151.shtml
- http://map.mobile.xqnqq.com/Article/1224.shtml
- http://map.mobile.xqnqq.com/Article/165423.shtml
- http://map.mobile.xqnqq.com/Article/1913919.shtml
- http://map.mobile.xqnqq.com/Article/23264.shtml
- http://map.mobile.xqnqq.com/Article/3128684.shtml
- http://map.mobile.xqnqq.com/Article/9883034.shtml
- http://map.mobile.xqnqq.com/Article/82143.shtml
- http://map.read.usuhx.com/Article/9116.shtml
- http://map.mobile.xqnqq.com/Article/222384.shtml
- http://map.read.usuhx.com/Article/4967968.shtml
- http://map.mobile.xqnqq.com/Article/4931.shtml
- http://map.mobile.xqnqq.com/Article/377864.shtml
- http://map.read.usuhx.com/Article/56081.shtml
- http://map.read.usuhx.com/Article/5707.shtml
- http://map.mobile.xqnqq.com/Article/6327948.shtml
- http://map.mobile.xqnqq.com/Article/065060.shtml
- http://map.mobile.xqnqq.com/Article/697421.shtml
- http://map.read.usuhx.com/Article/49764.shtml
- http://map.mobile.xqnqq.com/Article/962147.shtml
- http://map.mobile.xqnqq.com/Article/4445.shtml
- http://map.mobile.xqnqq.com/Article/8818839.shtml
- http://map.mobile.xqnqq.com/Article/2971.shtml
- http://map.mobile.xqnqq.com/Article/3476440.shtml
- http://map.read.usuhx.com/Article/9412808.shtml
- http://map.mobile.xqnqq.com/Article/7304021.shtml
- http://map.mobile.xqnqq.com/Article/278014.shtml
- http://map.mobile.xqnqq.com/Article/0912046.shtml
- http://map.read.usuhx.com/Article/355103.shtml
- http://map.mobile.xqnqq.com/Article/3507043.shtml
- http://map.mobile.xqnqq.com/Article/9456927.shtml
- http://map.mobile.xqnqq.com/Article/86702.shtml
- http://map.read.usuhx.com/Article/8209.shtml
- http://map.mobile.xqnqq.com/Article/9958162.shtml
- http://map.mobile.xqnqq.com/Article/461531.shtml
- http://map.mobile.xqnqq.com/Article/351888.shtml
- http://map.read.usuhx.com/Article/837704.shtml
- http://map.read.usuhx.com/Article/518792.shtml
- http://map.read.usuhx.com/Article/720757.shtml
- http://map.read.usuhx.com/Article/99531.shtml
- http://map.mobile.xqnqq.com/Article/216180.shtml
- http://map.read.usuhx.com/Article/355039.shtml
- http://map.mobile.xqnqq.com/Article/3734893.shtml
- http://map.mobile.xqnqq.com/Article/85477.shtml
- http://map.mobile.xqnqq.com/Article/335056.shtml
- http://map.read.usuhx.com/Article/898355.shtml
- http://map.mobile.xqnqq.com/Article/747701.shtml
- http://map.mobile.xqnqq.com/Article/1743.shtml
- http://map.mobile.xqnqq.com/Article/99002.shtml
- http://map.mobile.xqnqq.com/Article/31536.shtml
- http://map.read.usuhx.com/Article/380138.shtml
- http://map.mobile.xqnqq.com/Article/93490.shtml
- http://map.read.usuhx.com/Article/233951.shtml
- http://map.read.usuhx.com/Article/5296089.shtml
- http://map.mobile.xqnqq.com/Article/35543.shtml
- http://map.mobile.xqnqq.com/Article/704851.shtml
- http://map.read.usuhx.com/Article/4943022.shtml
- http://map.mobile.xqnqq.com/Article/6911.shtml
- http://map.read.usuhx.com/Article/4937.shtml
- http://map.mobile.xqnqq.com/Article/3469.shtml
- http://map.read.usuhx.com/Article/74932.shtml
- http://map.read.usuhx.com/Article/06216.shtml
- http://map.read.usuhx.com/Article/9214.shtml
- http://map.read.usuhx.com/Article/81898.shtml
- http://map.mobile.xqnqq.com/Article/5446725.shtml
- http://map.read.usuhx.com/Article/0555726.shtml
- http://map.mobile.xqnqq.com/Article/021274.shtml
- http://map.mobile.xqnqq.com/Article/126323.shtml
- http://map.read.usuhx.com/Article/83341.shtml
- http://map.mobile.xqnqq.com/Article/9750949.shtml
- http://map.mobile.xqnqq.com/Article/07504.shtml
- http://map.mobile.xqnqq.com/Article/588509.shtml
- http://map.read.usuhx.com/Article/284816.shtml
- http://map.read.usuhx.com/Article/00587.shtml
- http://map.mobile.xqnqq.com/Article/773178.shtml
- http://map.mobile.xqnqq.com/Article/3604154.shtml
- http://map.read.usuhx.com/Article/88939.shtml
- http://map.read.usuhx.com/Article/06289.shtml
- http://map.read.usuhx.com/Article/741534.shtml
- http://map.read.usuhx.com/Article/75005.shtml
- http://map.mobile.xqnqq.com/Article/46136.shtml
- http://map.read.usuhx.com/Article/058592.shtml
- http://map.read.usuhx.com/Article/52108.shtml
- http://map.read.usuhx.com/Article/78682.shtml
- http://map.mobile.xqnqq.com/Article/552057.shtml
- http://map.mobile.xqnqq.com/Article/671793.shtml
- http://map.read.usuhx.com/Article/029256.shtml
- http://map.mobile.xqnqq.com/Article/8145.shtml
- http://map.mobile.xqnqq.com/Article/23568.shtml
- http://map.read.usuhx.com/Article/973736.shtml
- http://map.read.usuhx.com/Article/86219.shtml
- http://map.mobile.xqnqq.com/Article/7703.shtml
- http://map.read.usuhx.com/Article/8643.shtml
- http://map.read.usuhx.com/Article/4791951.shtml
- http://map.read.usuhx.com/Article/6534.shtml
- http://map.mobile.xqnqq.com/Article/556660.shtml
- http://map.mobile.xqnqq.com/Article/5432372.shtml
- http://map.read.usuhx.com/Article/865079.shtml
- http://map.mobile.xqnqq.com/Article/15315.shtml
- http://map.mobile.xqnqq.com/Article/271720.shtml
- http://map.read.usuhx.com/Article/6847342.shtml
- http://map.read.usuhx.com/Article/458989.shtml
- http://map.read.usuhx.com/Article/2287149.shtml
- http://map.mobile.xqnqq.com/Article/80637.shtml
- http://map.mobile.xqnqq.com/Article/0324.shtml
- http://map.mobile.xqnqq.com/Article/93666.shtml
- http://map.mobile.xqnqq.com/Article/73972.shtml
- http://map.mobile.xqnqq.com/Article/3261.shtml
- http://map.read.usuhx.com/Article/9858434.shtml
- http://map.mobile.xqnqq.com/Article/717609.shtml
- http://map.mobile.xqnqq.com/Article/98339.shtml
- http://map.mobile.xqnqq.com/Article/250675.shtml
- http://map.mobile.xqnqq.com/Article/1287120.shtml
- http://map.mobile.xqnqq.com/Article/2172887.shtml
- http://map.mobile.xqnqq.com/Article/25597.shtml
- http://map.mobile.xqnqq.com/Article/5840.shtml
- http://map.read.usuhx.com/Article/33551.shtml
- http://map.read.usuhx.com/Article/2599623.shtml
- http://map.mobile.xqnqq.com/Article/2709111.shtml
- http://map.mobile.xqnqq.com/Article/67922.shtml
- http://map.mobile.xqnqq.com/Article/8799.shtml
- http://map.read.usuhx.com/Article/1796570.shtml
- http://map.mobile.xqnqq.com/Article/091617.shtml
- http://map.mobile.xqnqq.com/Article/6768725.shtml
- http://map.read.usuhx.com/Article/151224.shtml
- http://map.mobile.xqnqq.com/Article/98215.shtml
- http://map.read.usuhx.com/Article/25641.shtml
- http://map.read.usuhx.com/Article/96054.shtml
- http://map.mobile.xqnqq.com/Article/0686667.shtml
- http://map.mobile.xqnqq.com/Article/968659.shtml
- http://map.read.usuhx.com/Article/1086.shtml
- http://map.read.usuhx.com/Article/584013.shtml
- http://map.mobile.xqnqq.com/Article/2630.shtml
- http://map.mobile.xqnqq.com/Article/8401951.shtml
- http://map.read.usuhx.com/Article/2704.shtml
- http://map.mobile.xqnqq.com/Article/29408.shtml
- http://map.read.usuhx.com/Article/412053.shtml
- http://map.read.usuhx.com/Article/0413909.shtml
- http://map.mobile.xqnqq.com/Article/812844.shtml
- http://map.read.usuhx.com/Article/2543.shtml
- http://map.read.usuhx.com/Article/8215022.shtml
- http://map.mobile.xqnqq.com/Article/530381.shtml
- http://map.mobile.xqnqq.com/Article/4161.shtml
- http://map.mobile.xqnqq.com/Article/4066.shtml
- http://map.mobile.xqnqq.com/Article/4398.shtml
- http://map.read.usuhx.com/Article/2803734.shtml
- http://map.read.usuhx.com/Article/1337356.shtml
- http://map.read.usuhx.com/Article/0258646.shtml
- http://map.mobile.xqnqq.com/Article/36253.shtml
- http://map.read.usuhx.com/Article/26010.shtml
- http://map.read.usuhx.com/Article/602695.shtml
- http://map.read.usuhx.com/Article/7021.shtml
- http://map.read.usuhx.com/Article/139586.shtml
- http://map.read.usuhx.com/Article/4421.shtml
- http://map.mobile.xqnqq.com/Article/8936620.shtml
- http://map.mobile.xqnqq.com/Article/8100.shtml
- http://map.mobile.xqnqq.com/Article/7376.shtml
- http://map.mobile.xqnqq.com/Article/13274.shtml
- http://map.mobile.xqnqq.com/Article/0551.shtml
- http://map.mobile.xqnqq.com/Article/217937.shtml
- http://map.read.usuhx.com/Article/9132.shtml
- http://map.read.usuhx.com/Article/222037.shtml
- http://map.read.usuhx.com/Article/3105.shtml
- http://map.read.usuhx.com/Article/030682.shtml
- http://map.mobile.xqnqq.com/Article/387247.shtml
- http://map.mobile.xqnqq.com/Article/1824.shtml
- http://map.read.usuhx.com/Article/89096.shtml
- http://map.mobile.xqnqq.com/Article/6424362.shtml
- http://map.read.usuhx.com/Article/1211.shtml
- http://map.mobile.xqnqq.com/Article/996517.shtml
- http://map.mobile.xqnqq.com/Article/137197.shtml
- http://map.read.usuhx.com/Article/796180.shtml
- http://map.read.usuhx.com/Article/14814.shtml
- http://map.read.usuhx.com/Article/0564243.shtml
- http://map.read.usuhx.com/Article/1603.shtml
- http://map.mobile.xqnqq.com/Article/30588.shtml
- http://map.mobile.xqnqq.com/Article/1222731.shtml
- http://map.mobile.xqnqq.com/Article/561253.shtml
- http://map.mobile.xqnqq.com/Article/5849.shtml
- http://map.mobile.xqnqq.com/Article/4608.shtml
- http://map.mobile.xqnqq.com/Article/5769.shtml
- http://map.read.usuhx.com/Article/8647362.shtml
- http://map.mobile.xqnqq.com/Article/0912600.shtml
- http://map.read.usuhx.com/Article/86709.shtml
- http://map.read.usuhx.com/Article/85912.shtml
- http://map.read.usuhx.com/Article/6321.shtml
- http://map.read.usuhx.com/Article/9652.shtml
- http://map.mobile.xqnqq.com/Article/409254.shtml
- http://map.read.usuhx.com/Article/602902.shtml
- http://map.read.usuhx.com/Article/4860.shtml
- http://map.mobile.xqnqq.com/Article/35706.shtml
- http://map.mobile.xqnqq.com/Article/897737.shtml
- http://map.mobile.xqnqq.com/Article/069629.shtml
- http://map.read.usuhx.com/Article/4691.shtml
- http://map.read.usuhx.com/Article/26881.shtml
- http://map.mobile.xqnqq.com/Article/85474.shtml
- http://map.read.usuhx.com/Article/0203.shtml
- http://map.mobile.xqnqq.com/Article/4216.shtml
- http://map.mobile.xqnqq.com/Article/321869.shtml
- http://map.mobile.xqnqq.com/Article/80145.shtml
- http://map.read.usuhx.com/Article/1676.shtml
- http://map.mobile.xqnqq.com/Article/2922078.shtml
- http://map.mobile.xqnqq.com/Article/954661.shtml
- http://map.mobile.xqnqq.com/Article/6119378.shtml
- http://map.read.usuhx.com/Article/71429.shtml
- http://map.mobile.xqnqq.com/Article/2202.shtml
- http://map.mobile.xqnqq.com/Article/69430.shtml
- http://map.read.usuhx.com/Article/5662.shtml
- http://map.mobile.xqnqq.com/Article/870378.shtml
- http://map.read.usuhx.com/Article/46248.shtml
- http://map.mobile.xqnqq.com/Article/9295732.shtml
- http://map.mobile.xqnqq.com/Article/2762.shtml
- http://map.mobile.xqnqq.com/Article/816612.shtml
- http://map.read.usuhx.com/Article/2691.shtml
- http://map.mobile.xqnqq.com/Article/123029.shtml
- http://map.mobile.xqnqq.com/Article/5276668.shtml
- http://map.read.usuhx.com/Article/0934845.shtml
- http://map.mobile.xqnqq.com/Article/3351.shtml
- http://map.mobile.xqnqq.com/Article/8416.shtml
- http://map.read.usuhx.com/Article/4054.shtml
- http://map.mobile.xqnqq.com/Article/3958078.shtml
- http://map.mobile.xqnqq.com/Article/0352592.shtml
- http://map.mobile.xqnqq.com/Article/31651.shtml
- http://map.read.usuhx.com/Article/3059.shtml
- http://map.read.usuhx.com/Article/5719159.shtml
- http://map.read.usuhx.com/Article/7316.shtml
- http://map.mobile.xqnqq.com/Article/317200.shtml
- http://map.read.usuhx.com/Article/60051.shtml
- http://map.mobile.xqnqq.com/Article/721368.shtml
- http://map.read.usuhx.com/Article/788522.shtml
- http://map.read.usuhx.com/Article/790637.shtml
- http://map.read.usuhx.com/Article/183796.shtml
- http://map.read.usuhx.com/Article/46874.shtml
- http://map.mobile.xqnqq.com/Article/0442661.shtml
- http://map.mobile.xqnqq.com/Article/65685.shtml
- http://map.read.usuhx.com/Article/96798.shtml
- http://map.read.usuhx.com/Article/2862.shtml
- http://map.mobile.xqnqq.com/Article/1610109.shtml

## 项目结构

```
linkmap-station/
├── app/                                # 主应用包
│   ├── __init__.py                     # Flask 工厂函数与扩展初始化
│   ├── routes/                         # 路由蓝图目录
│   │   ├── import.py                   # 批量导入接口，处理 URL 解析与去重
│   │   ├── export.py                   # 导出接口，支持 Markdown/CSV/YAML
│   │   ├── health.py                   # 健康检查接口，异步探测链接状态
│   │   └── query.py                    # 检索与筛选接口，支持标签和关键词
│   ├── models/                         # 数据模型与 ORM 映射
│   │   ├── resource.py                 # Resource 实体，对应 resources 表
│   │   ├── batch.py                    # Batch 实体，记录导入批次信息
│   │   └── tag.py                      # Tag 实体，资源标签关联表
│   ├── services/                       # 业务逻辑层
│   │   ├── parser.py                   # URL 解析服务，提取域名、路径、参数
│   │   ├── fingerprint.py              # 资源指纹生成器，基于规范化 URL 计算 SHA256
│   │   └── snapshot.py                 # 快照管理服务，创建与恢复历史版本
│   ├── static/                         # 前端静态资源
│   │   ├── css/                        # 样式文件（Bootstrap 定制主题）
│   │   └── js/                         # 交互脚本（筛选器、健康检查进度条）
│   └── templates/                      # Jinja2 模板
│       ├── index.html                  # 资源列表主页，含筛选与分页
│       ├── import.html                 # 批量导入页面，提供文本域与批次表单
│       └── detail.html                 # 单条资源详情页，显示完整元数据
├── scripts/                            # 运维与工具脚本
│   ├── init_db.py                      # 初始化 SQLite 数据库，创建表结构
│   ├── migrate_v1_to_v2.py             # 数据库迁移脚本（版本升级用）
│   └── batch_import_cli.py             # 命令行批量导入工具，支持 CSV 文件输入
├── tests/                              # 单元测试与集成测试
│   ├── test_parser.py                  # URL 解析服务测试用例
│   ├── test_fingerprint.py             # 指纹生成算法测试
│   └── test_routes.py                  # Flask 路由端点测试（使用 pytest）
├── data/                               # 数据存储目录（运行时生成）
│   ├── linkmap.db                      # SQLite 主数据库文件
│   ├── snapshots/                      # 快照历史存档（JSON 格式）
│   └── exports/                        # 导出文件临时存放目录
├── docs/                               # 项目文档（详见文档导航）
│   ├── user-guide/                     # 用户手册
│   ├── ops/                            # 运维指南
│   └── dev/                            # 开发指南
├── config.py                           # 应用配置（环境变量、默认参数）
├── requirements.txt                    # Python 依赖清单
├── setup.py                            # 打包与分发配置
└── README.md                           # 本文件
```

## 贡献指南

**提交 Issue 报告缺陷或建议** 在 GitHub Issues 页面选择对应模板，描述复现步骤、期望行为与实际行为，附带操作系统版本、Python 版本与相关日志片段。

**Fork 仓库并创建功能分支** 将主仓库 Fork 至个人账户，使用 `git checkout -b feature/your-feature-name` 创建新分支，避免在主分支上直接修改。

**遵循代码风格与测试规范** 所有 Python 代码须通过 `flake8` 与 `pylint` 基础检查，新增功能须附带对应的 `pytest` 测试用例，确保覆盖率不低于 80%。

**编写或更新文档** 若修改涉及用户可见功能，须同步更新 `docs/` 目录下对应手册，并在 PR 描述中标注文档变更位置。

**提交 Pull Request 并等待审核** 推送分支后发起 PR，填写变更摘要、测试结果与截图（如涉及 UI 变动）。PR 至少需要一位维护者批准后方可合并。

## 常见问题

**Q：导入大量 URL 时页面响应缓慢或超时怎么办？**

A：LinkMap 默认使用同步请求处理导入，单次建议不超过 500 条 URL。若需导入更大规模资源，请使用命令行工具 `scripts/batch_import_cli.py --file links.csv --batch "第64批"`，该工具不受 Web 超时限制，并支持断点续传。导入完成后可在 Web 界面刷新查看。

**Q：健康检查显示大量链接状态为 UNREACHABLE，但浏览器中可以正常访问？**

A：LinkMap 的健康检查模块默认使用 requests 库的默认超时设置（3 秒）且不跟随 JavaScript 重定向。若目标网站需要较长时间响应或依赖客户端渲染，可将健康检查超时参数在 `config.py` 中调大（如 `HEALTH_CHECK_TIMEOUT = 10`）。同时，部分网站会拦截非浏览器 User-Agent，可在配置中修改 `HEALTH_CHECK_UA` 为常见浏览器标识。

**Q：如何将 LinkMap 中的资源列表迁移到另一台服务器？**

A：直接复制 `data/linkmap.db` 数据库文件与 `data/snapshots/` 目录下的快照文件夹至新服务器相同路径即可。若需要跨版本迁移，请先运行 `scripts/migrate_v1_to_v2.py` 检查数据库版本一致性。所有数据均存储于本地，不依赖外部云服务，因此迁移过程仅涉及文件拷贝。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
