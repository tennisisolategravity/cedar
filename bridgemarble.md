# LinkMap 聚合导航系统

LinkMap 是一个面向技术调研、内容聚合与知识管理场景的轻量化外链资源导航系统。项目定位于帮助开发者、技术博主、数据分析师以及运维人员高效管理分散在多个内容源下的文章链接，通过集中式索引与分类标注机制，将零散的 URL 转化为可检索、可追溯、可分享的结构化知识资产。

本项目不依赖复杂前端框架，核心基于静态站点生成逻辑与纯文本索引机制，适配内网部署、个人知识库构建及团队协作场景。第 79/80 批次资源收录工作已完成，当前共计纳入 250 个外部链接，覆盖技术文档、行业资讯、地图服务与移动端应用参考等多个领域。

## 功能概览

**批量链接收录与去重校验**：支持从文本文件、CSV 或直接粘贴的 URL 列表中批量导入链接，自动完成协议归一化与重复项检测，确保索引库唯一性。

**多级分类标签系统**：允许用户为每条链接自定义一级分类、二级标签及权重评分，便于按主题域（如前端工程、后端架构、数据可视化）快速筛选。

**全文元数据提取**：对收录的 URL 进行标题、摘要、关键词及发布时间等元数据的自动抓取与解析，减少手动录入成本。

**静态索引生成器**：基于配置模板将链接库输出为纯静态 HTML/JSON 文件，支持离线浏览与内网发布，无需数据库依赖。

**快速检索与过滤**：提供关键词模糊匹配、域名过滤、收录时间范围筛选等多种查询方式，可在百毫秒内返回结果。

**数据导入导出**：支持 JSON、YAML 及 Markdown 表格格式的链接库导入导出，方便与外部工具链（如 Obsidian、Notion、Hugo）进行数据交换。

**访问状态监控**：周期性对已收录链接进行可用性探测，标记失效链接并生成异常报告，辅助链接库健康度维护。

## 应用场景

技术团队内部知识库建设：团队可将日常阅读的技术博客、官方文档、API 参考及故障处理案例链接统一收录至 LinkMap，按项目或技术栈分类，新成员入职时可快速获取体系化的学习路径。

运维与监控信息汇聚：运维人员可将不同云厂商状态页、监控大盘、日志查询工具及内部运维文档的入口集中管理，通过 LinkMap 的标签筛选功能快速跳转至目标页面，缩短故障排查时的导航路径。

自媒体与内容策展：技术博主或资讯编辑可利用 LinkMap 收集选题素材、竞品动态及行业报告，通过元数据提取功能批量获取文章发布时间与摘要，辅助内容日历规划与热点追踪。

离线环境下的资源镜像参考：在受限网络环境中，LinkMap 生成的静态索引文件可作为外部资源的描述性目录，配合本地缓存或内网镜像服务，为隔离环境提供可浏览的链接清单。

## 快速开始

以下命令演示了从克隆代码仓库到启动本地服务的完整流程。

```bash
git clone https://github.com/linkmap-org/linkmap-core.git
cd linkmap-core
pip install -r requirements.txt
python scripts/ingest.py --input ./samples/url_list_79.txt --output ./data/index.json
python server.py --port 8080
```

执行完成后，访问 http://localhost:8080 即可查看已收录的链接列表。如需自定义数据目录或调整抓取并发数，可参考 `config/default.yaml` 中的参数说明。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 及以上 | 核心运行环境，推荐使用 3.11 以获取更好性能 |
| Pip | 22.0 及以上 | 依赖包管理工具 |
| Requests | 2.31.0 | 处理 HTTP 请求与元数据抓取 |
| BeautifulSoup4 | 4.12.0 | 解析 HTML 文档提取标题与摘要 |
| PyYAML | 6.0 | 处理 YAML 格式的配置文件 |
| Jinja2 | 3.1.0 | 渲染静态 HTML 模板 |
| Pydantic | 2.0 及以上 | 数据模型校验与配置管理 |
| schedule | 1.2.0 | 可选依赖，用于周期性健康检查任务 |
| lxml | 4.9.0 | 可选依赖，提供更高效的 HTML 解析后端 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | /docs/user-guide/ingestion.md | 如何导入第一批链接？如何配置自动去重与分类规则？ |
| 运维指南 | /docs/ops/deployment.md | 支持哪些部署方式（本地、Docker、内网静态托管）？环境变量如何配置？ |
| 开发参考 | /docs/dev/api.md | 数据模型字段定义是什么？如何扩展自定义元数据提取器？ |
| 集成方案 | /docs/integration/obsidian.md | 如何将 LinkMap 索引与 Obsidian 或 Logseq 双向链接？ |
| 故障排查 | /docs/troubleshooting/common-issues.md | 抓取超时、SSL 证书错误、编码乱码等问题如何解决？ |

## 资源列表

- http://map.mobile.xqnqq.com/Article/033965.shtml
- http://map.mobile.xqnqq.com/Article/6515.shtml
- http://map.read.usuhx.com/Article/9005.shtml
- http://map.read.usuhx.com/Article/7054750.shtml
- http://map.read.usuhx.com/Article/959929.shtml
- http://map.mobile.xqnqq.com/Article/8776.shtml
- http://map.read.usuhx.com/Article/131898.shtml
- http://map.read.usuhx.com/Article/900034.shtml
- http://map.read.usuhx.com/Article/4448572.shtml
- http://map.mobile.xqnqq.com/Article/15107.shtml
- http://map.mobile.xqnqq.com/Article/89091.shtml
- http://map.read.usuhx.com/Article/1811450.shtml
- http://map.read.usuhx.com/Article/07963.shtml
- http://map.mobile.xqnqq.com/Article/5106109.shtml
- http://map.read.usuhx.com/Article/993088.shtml
- http://map.mobile.xqnqq.com/Article/515642.shtml
- http://map.read.usuhx.com/Article/3236952.shtml
- http://map.read.usuhx.com/Article/712578.shtml
- http://map.read.usuhx.com/Article/57358.shtml
- http://map.mobile.xqnqq.com/Article/1739489.shtml
- http://map.read.usuhx.com/Article/0278.shtml
- http://map.mobile.xqnqq.com/Article/88949.shtml
- http://map.read.usuhx.com/Article/80233.shtml
- http://map.read.usuhx.com/Article/3006.shtml
- http://map.mobile.xqnqq.com/Article/034736.shtml
- http://map.read.usuhx.com/Article/06310.shtml
- http://map.mobile.xqnqq.com/Article/0772.shtml
- http://map.mobile.xqnqq.com/Article/7820460.shtml
- http://map.read.usuhx.com/Article/66221.shtml
- http://map.mobile.xqnqq.com/Article/404760.shtml
- http://map.mobile.xqnqq.com/Article/2568671.shtml
- http://map.mobile.xqnqq.com/Article/60168.shtml
- http://map.read.usuhx.com/Article/269684.shtml
- http://map.read.usuhx.com/Article/7720.shtml
- http://map.read.usuhx.com/Article/973483.shtml
- http://map.mobile.xqnqq.com/Article/5396.shtml
- http://map.read.usuhx.com/Article/73235.shtml
- http://map.mobile.xqnqq.com/Article/32473.shtml
- http://map.mobile.xqnqq.com/Article/36613.shtml
- http://map.mobile.xqnqq.com/Article/20348.shtml
- http://map.read.usuhx.com/Article/2917200.shtml
- http://map.mobile.xqnqq.com/Article/02364.shtml
- http://map.mobile.xqnqq.com/Article/056527.shtml
- http://map.mobile.xqnqq.com/Article/55396.shtml
- http://map.mobile.xqnqq.com/Article/13214.shtml
- http://map.read.usuhx.com/Article/12498.shtml
- http://map.read.usuhx.com/Article/717561.shtml
- http://map.mobile.xqnqq.com/Article/371790.shtml
- http://map.mobile.xqnqq.com/Article/70670.shtml
- http://map.read.usuhx.com/Article/8015688.shtml
- http://map.read.usuhx.com/Article/244560.shtml
- http://map.read.usuhx.com/Article/8532052.shtml
- http://map.mobile.xqnqq.com/Article/8294.shtml
- http://map.read.usuhx.com/Article/789822.shtml
- http://map.read.usuhx.com/Article/26941.shtml
- http://map.read.usuhx.com/Article/58211.shtml
- http://map.mobile.xqnqq.com/Article/256900.shtml
- http://map.mobile.xqnqq.com/Article/0658500.shtml
- http://map.read.usuhx.com/Article/451591.shtml
- http://map.read.usuhx.com/Article/8141.shtml
- http://map.read.usuhx.com/Article/179599.shtml
- http://map.read.usuhx.com/Article/6400814.shtml
- http://map.mobile.xqnqq.com/Article/459602.shtml
- http://map.read.usuhx.com/Article/9879.shtml
- http://map.read.usuhx.com/Article/2946129.shtml
- http://map.mobile.xqnqq.com/Article/85061.shtml
- http://map.mobile.xqnqq.com/Article/934688.shtml
- http://map.read.usuhx.com/Article/8736332.shtml
- http://map.read.usuhx.com/Article/6304325.shtml
- http://map.mobile.xqnqq.com/Article/620628.shtml
- http://map.read.usuhx.com/Article/70785.shtml
- http://map.mobile.xqnqq.com/Article/72707.shtml
- http://map.mobile.xqnqq.com/Article/31614.shtml
- http://map.read.usuhx.com/Article/9482.shtml
- http://map.mobile.xqnqq.com/Article/39991.shtml
- http://map.read.usuhx.com/Article/98248.shtml
- http://map.read.usuhx.com/Article/781021.shtml
- http://map.mobile.xqnqq.com/Article/998910.shtml
- http://map.read.usuhx.com/Article/9350.shtml
- http://map.read.usuhx.com/Article/009659.shtml
- http://map.read.usuhx.com/Article/5714.shtml
- http://map.read.usuhx.com/Article/893954.shtml
- http://map.read.usuhx.com/Article/9451.shtml
- http://map.mobile.xqnqq.com/Article/3715331.shtml
- http://map.mobile.xqnqq.com/Article/647744.shtml
- http://map.mobile.xqnqq.com/Article/2596143.shtml
- http://map.read.usuhx.com/Article/95531.shtml
- http://map.mobile.xqnqq.com/Article/9393107.shtml
- http://map.mobile.xqnqq.com/Article/0875062.shtml
- http://map.mobile.xqnqq.com/Article/4165.shtml
- http://map.mobile.xqnqq.com/Article/52754.shtml
- http://map.mobile.xqnqq.com/Article/871849.shtml
- http://map.read.usuhx.com/Article/220875.shtml
- http://map.mobile.xqnqq.com/Article/13307.shtml
- http://map.read.usuhx.com/Article/03797.shtml
- http://map.read.usuhx.com/Article/1659531.shtml
- http://map.read.usuhx.com/Article/7616207.shtml
- http://map.mobile.xqnqq.com/Article/541379.shtml
- http://map.mobile.xqnqq.com/Article/38257.shtml
- http://map.mobile.xqnqq.com/Article/0111207.shtml
- http://map.mobile.xqnqq.com/Article/0805.shtml
- http://map.read.usuhx.com/Article/45374.shtml
- http://map.read.usuhx.com/Article/4820621.shtml
- http://map.read.usuhx.com/Article/635140.shtml
- http://map.read.usuhx.com/Article/17133.shtml
- http://map.read.usuhx.com/Article/8889306.shtml
- http://map.read.usuhx.com/Article/530461.shtml
- http://map.read.usuhx.com/Article/307990.shtml
- http://map.mobile.xqnqq.com/Article/8015177.shtml
- http://map.read.usuhx.com/Article/977400.shtml
- http://map.mobile.xqnqq.com/Article/97978.shtml
- http://map.mobile.xqnqq.com/Article/1213.shtml
- http://map.mobile.xqnqq.com/Article/301193.shtml
- http://map.mobile.xqnqq.com/Article/7046.shtml
- http://map.read.usuhx.com/Article/883341.shtml
- http://map.mobile.xqnqq.com/Article/158463.shtml
- http://map.read.usuhx.com/Article/633573.shtml
- http://map.mobile.xqnqq.com/Article/834746.shtml
- http://map.mobile.xqnqq.com/Article/55504.shtml
- http://map.mobile.xqnqq.com/Article/90518.shtml
- http://map.mobile.xqnqq.com/Article/6248.shtml
- http://map.read.usuhx.com/Article/648484.shtml
- http://map.mobile.xqnqq.com/Article/7464956.shtml
- http://map.read.usuhx.com/Article/46599.shtml
- http://map.mobile.xqnqq.com/Article/1824441.shtml
- http://map.mobile.xqnqq.com/Article/9924849.shtml
- http://map.mobile.xqnqq.com/Article/1000.shtml
- http://map.mobile.xqnqq.com/Article/8164696.shtml
- http://map.read.usuhx.com/Article/5212.shtml
- http://map.mobile.xqnqq.com/Article/73693.shtml
- http://map.read.usuhx.com/Article/8429.shtml
- http://map.mobile.xqnqq.com/Article/0066132.shtml
- http://map.mobile.xqnqq.com/Article/530911.shtml
- http://map.mobile.xqnqq.com/Article/1737224.shtml
- http://map.read.usuhx.com/Article/074122.shtml
- http://map.mobile.xqnqq.com/Article/2861.shtml
- http://map.read.usuhx.com/Article/35689.shtml
- http://map.read.usuhx.com/Article/8715.shtml
- http://map.read.usuhx.com/Article/12761.shtml
- http://map.mobile.xqnqq.com/Article/037363.shtml
- http://map.read.usuhx.com/Article/8191.shtml
- http://map.mobile.xqnqq.com/Article/18397.shtml
- http://map.mobile.xqnqq.com/Article/8719.shtml
- http://map.read.usuhx.com/Article/3115204.shtml
- http://map.mobile.xqnqq.com/Article/89139.shtml
- http://map.read.usuhx.com/Article/0132606.shtml
- http://map.read.usuhx.com/Article/1155797.shtml
- http://map.mobile.xqnqq.com/Article/8436.shtml
- http://map.mobile.xqnqq.com/Article/9568.shtml
- http://map.read.usuhx.com/Article/61475.shtml
- http://map.read.usuhx.com/Article/6703.shtml
- http://map.mobile.xqnqq.com/Article/91615.shtml
- http://map.read.usuhx.com/Article/63793.shtml
- http://map.mobile.xqnqq.com/Article/73579.shtml
- http://map.read.usuhx.com/Article/73992.shtml
- http://map.read.usuhx.com/Article/7388584.shtml
- http://map.mobile.xqnqq.com/Article/2097.shtml
- http://map.read.usuhx.com/Article/6170.shtml
- http://map.read.usuhx.com/Article/117583.shtml
- http://map.read.usuhx.com/Article/5287.shtml
- http://map.read.usuhx.com/Article/075564.shtml
- http://map.mobile.xqnqq.com/Article/6371.shtml
- http://map.read.usuhx.com/Article/3555744.shtml
- http://map.read.usuhx.com/Article/8416.shtml
- http://map.read.usuhx.com/Article/3438.shtml
- http://map.mobile.xqnqq.com/Article/7986955.shtml
- http://map.read.usuhx.com/Article/95783.shtml
- http://map.mobile.xqnqq.com/Article/0264.shtml
- http://map.mobile.xqnqq.com/Article/1811.shtml
- http://map.read.usuhx.com/Article/4637030.shtml
- http://map.mobile.xqnqq.com/Article/1336.shtml
- http://map.mobile.xqnqq.com/Article/851711.shtml
- http://map.read.usuhx.com/Article/8107212.shtml
- http://map.mobile.xqnqq.com/Article/4357211.shtml
- http://map.mobile.xqnqq.com/Article/3742573.shtml
- http://map.mobile.xqnqq.com/Article/9666.shtml
- http://map.read.usuhx.com/Article/2753508.shtml
- http://map.mobile.xqnqq.com/Article/920527.shtml
- http://map.read.usuhx.com/Article/7651.shtml
- http://map.read.usuhx.com/Article/46368.shtml
- http://map.mobile.xqnqq.com/Article/4029988.shtml
- http://map.mobile.xqnqq.com/Article/1081.shtml
- http://map.read.usuhx.com/Article/57488.shtml
- http://map.read.usuhx.com/Article/357256.shtml
- http://map.read.usuhx.com/Article/021158.shtml
- http://map.mobile.xqnqq.com/Article/0473.shtml
- http://map.read.usuhx.com/Article/7496716.shtml
- http://map.read.usuhx.com/Article/56281.shtml
- http://map.read.usuhx.com/Article/7137.shtml
- http://map.mobile.xqnqq.com/Article/886876.shtml
- http://map.read.usuhx.com/Article/44997.shtml
- http://map.read.usuhx.com/Article/68350.shtml
- http://map.read.usuhx.com/Article/11608.shtml
- http://map.read.usuhx.com/Article/87256.shtml
- http://map.mobile.xqnqq.com/Article/25635.shtml
- http://map.read.usuhx.com/Article/59241.shtml
- http://map.read.usuhx.com/Article/0453158.shtml
- http://map.read.usuhx.com/Article/1275.shtml
- http://map.mobile.xqnqq.com/Article/56385.shtml
- http://map.read.usuhx.com/Article/9014219.shtml
- http://map.mobile.xqnqq.com/Article/9784960.shtml
- http://map.mobile.xqnqq.com/Article/55168.shtml
- http://map.read.usuhx.com/Article/152950.shtml
- http://map.mobile.xqnqq.com/Article/7757.shtml
- http://map.mobile.xqnqq.com/Article/2554.shtml
- http://map.mobile.xqnqq.com/Article/589064.shtml
- http://map.mobile.xqnqq.com/Article/424921.shtml
- http://map.read.usuhx.com/Article/939098.shtml
- http://map.read.usuhx.com/Article/4022.shtml
- http://map.read.usuhx.com/Article/00109.shtml
- http://map.read.usuhx.com/Article/97026.shtml
- http://map.read.usuhx.com/Article/1021.shtml
- http://map.mobile.xqnqq.com/Article/642322.shtml
- http://map.read.usuhx.com/Article/1366414.shtml
- http://map.mobile.xqnqq.com/Article/271303.shtml
- http://map.read.usuhx.com/Article/3700876.shtml
- http://map.read.usuhx.com/Article/20601.shtml
- http://map.mobile.xqnqq.com/Article/3248.shtml
- http://map.mobile.xqnqq.com/Article/7015.shtml
- http://map.mobile.xqnqq.com/Article/79957.shtml
- http://map.mobile.xqnqq.com/Article/3433005.shtml
- http://map.mobile.xqnqq.com/Article/121689.shtml
- http://map.read.usuhx.com/Article/81242.shtml
- http://map.read.usuhx.com/Article/6285.shtml
- http://map.mobile.xqnqq.com/Article/4879.shtml
- http://map.mobile.xqnqq.com/Article/276130.shtml
- http://map.read.usuhx.com/Article/6997977.shtml
- http://map.read.usuhx.com/Article/493944.shtml
- http://map.read.usuhx.com/Article/01530.shtml
- http://map.mobile.xqnqq.com/Article/94524.shtml
- http://map.read.usuhx.com/Article/12472.shtml
- http://map.mobile.xqnqq.com/Article/1178.shtml
- http://map.mobile.xqnqq.com/Article/716229.shtml
- http://map.read.usuhx.com/Article/548265.shtml
- http://map.mobile.xqnqq.com/Article/69449.shtml
- http://map.read.usuhx.com/Article/84515.shtml
- http://map.mobile.xqnqq.com/Article/659328.shtml
- http://map.read.usuhx.com/Article/002610.shtml
- http://map.read.usuhx.com/Article/2035.shtml
- http://map.read.usuhx.com/Article/751651.shtml
- http://map.read.usuhx.com/Article/97075.shtml
- http://map.mobile.xqnqq.com/Article/8585.shtml
- http://map.read.usuhx.com/Article/249413.shtml
- http://map.read.usuhx.com/Article/8689189.shtml
- http://map.mobile.xqnqq.com/Article/302125.shtml
- http://map.read.usuhx.com/Article/42847.shtml
- http://map.read.usuhx.com/Article/520864.shtml
- http://map.mobile.xqnqq.com/Article/1533245.shtml
- http://map.mobile.xqnqq.com/Article/1512094.shtml
- http://map.read.usuhx.com/Article/222623.shtml

## 项目结构

```
linkmap-core/
├── config/                                  # 全局配置与环境变量
│   ├── default.yaml                         # 默认配置项（端口、超时、抓取并发数）
│   └── schema.json                          # 配置字段的 JSON Schema 校验文件
├── data/                                    # 数据存储目录（运行时生成）
│   ├── index.json                           # 主索引库，包含所有链接元数据
│   ├── health_report.json                   # 链接健康检查结果缓存
│   └── snapshots/                           # 历史索引快照，按日期归档
├── docs/                                    # 完整项目文档
│   ├── user-guide/                          # 用户使用手册
│   ├── ops/                                 # 部署与运维文档
│   ├── dev/                                 # 开发者文档与 API 参考
│   └── integration/                         # 第三方工具集成指南
├── scripts/                                 # 命令行工具与辅助脚本
│   ├── ingest.py                            # 核心导入脚本，支持多种输入格式
│   ├── export.py                            # 导出为 JSON/YAML/Markdown
│   ├── health_check.py                      # 链接可用性检测任务
│   └── dedup.py                             # 独立去重工具，可手动触发
├── src/                                     # 核心源码包
│   ├── models/                              # Pydantic 数据模型定义
│   │   ├── link.py                          # LinkEntry 与 LinkCollection 模型
│   │   └── config.py                        # 配置加载与校验模型
│   ├── parsers/                             # 元数据提取器实现
│   │   ├── html_parser.py                   # 基于 BeautifulSoup 的通用解析
│   │   └── custom_rules.py                  # 针对特定站点的自定义解析规则
│   ├── engines/                             # 检索与过滤引擎
│   │   ├── search.py                        # 关键词匹配与模糊查询实现
│   │   └── filter.py                        # 多条件组合过滤逻辑
│   └── generators/                          # 静态输出生成器
│       ├── html_generator.py                # Jinja2 模板渲染器
│       └── json_generator.py                # 结构化 JSON 导出
├── templates/                               # 静态站点 HTML 模板文件
│   ├── base.html                            # 基础页面骨架
│   ├── index.html                           # 链接列表页模板
│   └── detail.html                          # 单条链接详情页模板
├── tests/                                   # 单元测试与集成测试
│   ├── test_parsers.py                      # 解析器功能测试
│   ├── test_engines.py                      # 检索引擎性能测试
│   └── fixtures/                            # 测试用固定样本数据
├── requirements.txt                         # 生产环境依赖清单
├── requirements-dev.txt                     # 开发环境额外依赖（测试、代码检查）
├── server.py                                # 本地开发服务器入口
└── README.md                                # 项目说明文档（本文件）
```

## 贡献指南

1. 查阅 Issue 列表与项目看板，确认当前迭代周期内的待办事项，选择未被认领的任务或提出新的改进建议。对于新增功能或较大重构，建议先通过 Issue 与维护者讨论方案可行性。

2. 派生项目仓库至个人账户，在派生副本中创建功能分支，分支命名规范为 `feature/功能简述` 或 `fix/问题编号`。提交代码前请运行 `make lint` 与 `make test` 确保代码风格一致且现有测试用例全部通过。

3. 针对新增的 URL 解析规则或检索功能，需要在 `tests/` 目录下补充对应的测试用例，覆盖正常路径与边界异常情形。测试覆盖率不低于 85%。

4. 提交 Pull Request 至主仓库的 `main` 分支，PR 描述中请明确关联对应的 Issue 编号，列出主要变更点、测试结果以及用户文档是否需要同步更新的说明。

5. 维护者会在 3 个工作日内进行 Code Review，必要时会提出修改意见。合并后代码将自动触发 CI 流水线，构建并更新演示站点。

## 常见问题

**问：导入大量链接时出现超时或抓取失败，如何优化？**

答：建议调整 `config/default.yaml` 中的 `fetch_timeout` 参数（单位秒）和 `concurrency_limit` 并发数。对于网络环境较差的情况，可将超时设为 15 秒，并发数降至 3。此外，可通过 `--retry` 参数启用失败重试机制，最多重试 3 次。如果目标站点存在反爬策略，可考虑在配置中启用自定义 User-Agent 轮换。

**问：静态生成的 HTML 页面能否直接部署到 Nginx 或对象存储？**

答：可以。执行 `python scripts/export.py --format html --output ./dist` 后，`dist/` 目录下即为完全静态的 HTML、CSS 与 JavaScript 文件。无需额外后端服务，可直接托管至任意静态文件服务器、CDN 或云存储桶。检索功能在前端内存中完成，适合中小规模链接库（5000 条以内）。

**问：如何将 LinkMap 与现有的 Wiki 或笔记系统联动？**

答：推荐使用 JSON 导出功能。执行 `python scripts/export.py --format json --output ./export.json` 后，可编写简单脚本将数据同步至 Obsidian 的 CSV 插件、Notion 的 API 或 Logseq 的 EDN 导入功能。同时，项目提供了 `integration/` 目录下的示例脚本，展示了如何将索引数据转换为 Markdown 反链列表。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
