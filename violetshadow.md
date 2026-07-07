# ResourceLink Aggregate Service

ResourceLink Aggregate Service 是一个面向技术文档工作者与数据采集工程师的开源外链资源归集与导航系统。该项目定位于将分散于多个内容源、不同域名与路径下的非结构化文章链接，按照统一的数据模型进行抓取、清洗、索引与展示，解决技术团队在维护外部知识库、做竞品内容分析或构建站点地图时面临的链接碎片化与元数据缺失问题。

目标用户包括运维工程师、爬虫开发人员、技术内容运营者以及需要批量处理外部引用链接的软件开发者。该项目本身不生产内容，而是通过可配置的采集调度器与轻量级 Web 界面，将原始 URL 资源转化为可检索、可标注、可导出的结构化外链资产。

## 功能概览

**多源异构链接采集**：支持从多个根域名路径并发拉取文章元数据，并针对每个源站维护独立的请求头与超时策略。

**自动去重与增量更新**：基于链接 URL 与文章标题的哈希指纹进行去重，并可按天或按小时粒度执行增量抓取任务，避免全量扫描导致的资源浪费。

**元数据智能抽取**：从目标页面中提取标题、发布时间、正文摘要、关键词以及内链数量，并自动补全缺失的发布日期字段。

**标签化分类管理**：支持用户自定义标签体系，可将采集到的链接按技术领域、内容类型或业务归属进行多级分类标记，支持批量打标签操作。

**全文检索与过滤**：内置倒排索引，支持按标题关键词、来源域名、日期范围、标签组合等条件进行复杂筛选，并输出 JSON 或 CSV 格式结果。

**导出与推送集成**：提供 RESTful API 与命令行导出工具，可将链接列表推送至 Kafka 队列、写入本地 Parquet 文件或直接同步至外部知识库系统。

## 应用场景

技术文档团队的外链资产盘点：在编写技术白皮书或 API 参考文档时，团队需要引用大量外部规范或案例文章。通过本系统可集中收集各部门提报的参考链接，并自动检测链接有效性及内容变更，确保文档引用的可溯源性。

爬虫任务的种子链接管理：数据采集工程师在启动大规模爬虫之前，通常需要准备一批高质量入口链接。本系统可作为种子链接的前置管理平台，对种子 URL 进行去重、分类与健康度检查，降低爬虫任务启动时的失败率。

竞品内容更新监控：市场分析人员可将竞品官方发布的文章链接批量录入本系统，系统定期回访并对比页面内容哈希变化，一旦发现更新即刻发送告警通知，帮助团队把握竞品动态。

企业内部知识库的外链统一入口：企业在搭建内部 Wiki 或 Confluence 时，各部门会引用大量外部站点资源。本系统提供统一的外链登记与审核流程，避免知识库中出现重复或失效的外部引用链接。

## 快速开始

以下命令演示了如何从代码仓库克隆项目、安装依赖并启动开发服务器。所有步骤均在 Linux 或 macOS 环境下验证通过。

```bash
# 克隆代码仓库
git clone https://github.com/example/resourcelink-aggregate.git
cd resourcelink-aggregate

# 安装 Python 依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化配置文件并执行数据库迁移
cp config/example.yaml config/local.yaml
python scripts/migrate_db.py --config config/local.yaml

# 启动开发调试服务
python app.py --host 127.0.0.1 --port 8080 --debug
```

## 安装要求

本项目基于 Python 3.9 以上版本构建，所有后端依赖项均通过 pip 进行管理。生产环境建议配合 PostgreSQL 与 Redis 使用，开发环境可使用 SQLite 作为替代数据库。

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 至 3.11 | 核心运行环境，低于 3.9 版本将不支持类型注解语法 |
| PostgreSQL | 12.0 及以上 | 生产环境默认关系型数据库，用于存储链接元数据与用户标签 |
| Redis | 6.0 及以上 | 分布式锁与任务队列缓存，用于协调多实例调度器 |
| Requests | 2.28.0 及以上 | HTTP 请求库，用于执行所有外链抓取任务 |
| BeautifulSoup4 | 4.11.0 及以上 | HTML 解析器，负责从页面中抽取结构化内容 |
| SQLAlchemy | 2.0.0 及以上 | ORM 框架，统一管理数据库连接池与模型映射 |
| PyYAML | 6.0 及以上 | 配置文件解析器，用于加载本地与全局 YAML 配置 |
| Pytest | 7.0 及以上 | 单元测试框架，仅开发与测试环境需要安装 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide/quick-start.md | 如何配置第一个采集源、如何执行手动抓取、如何查看采集结果 |
| 运维部署 | docs/ops/deployment-prod.md | 如何使用 Docker Compose 或 Kubernetes 部署高可用集群 |
| 开发者指南 | docs/dev/contribution.md | 如何编写新的解析器扩展、如何修改数据模型、如何运行单元测试 |
| API 参考 | docs/api/endpoints.md | 每一个 RESTful 接口的请求参数、响应格式与错误码说明 |

## 资源列表

- http://map.mobile.xqnqq.com/Article/3347735.shtml
- http://map.read.usuhx.com/Article/9957.shtml
- http://map.read.usuhx.com/Article/3643655.shtml
- http://map.read.usuhx.com/Article/47808.shtml
- http://map.mobile.xqnqq.com/Article/403917.shtml
- http://map.mobile.xqnqq.com/Article/2764.shtml
- http://map.mobile.xqnqq.com/Article/899062.shtml
- http://map.read.usuhx.com/Article/8392.shtml
- http://map.read.usuhx.com/Article/1727299.shtml
- http://map.read.usuhx.com/Article/7863.shtml
- http://map.mobile.xqnqq.com/Article/2468.shtml
- http://map.mobile.xqnqq.com/Article/202675.shtml
- http://map.mobile.xqnqq.com/Article/9310.shtml
- http://map.mobile.xqnqq.com/Article/3823.shtml
- http://map.mobile.xqnqq.com/Article/3290396.shtml
- http://map.read.usuhx.com/Article/932887.shtml
- http://map.mobile.xqnqq.com/Article/04125.shtml
- http://map.read.usuhx.com/Article/567514.shtml
- http://map.read.usuhx.com/Article/0391.shtml
- http://map.read.usuhx.com/Article/8080829.shtml
- http://map.mobile.xqnqq.com/Article/3580.shtml
- http://map.read.usuhx.com/Article/7644.shtml
- http://map.read.usuhx.com/Article/51662.shtml
- http://map.mobile.xqnqq.com/Article/4078206.shtml
- http://map.mobile.xqnqq.com/Article/72101.shtml
- http://map.read.usuhx.com/Article/335109.shtml
- http://map.mobile.xqnqq.com/Article/0687.shtml
- http://map.mobile.xqnqq.com/Article/4190649.shtml
- http://map.read.usuhx.com/Article/504328.shtml
- http://map.mobile.xqnqq.com/Article/42802.shtml
- http://map.read.usuhx.com/Article/29859.shtml
- http://map.read.usuhx.com/Article/91554.shtml
- http://map.mobile.xqnqq.com/Article/9410255.shtml
- http://map.read.usuhx.com/Article/0533.shtml
- http://map.mobile.xqnqq.com/Article/6511916.shtml
- http://map.mobile.xqnqq.com/Article/782406.shtml
- http://map.read.usuhx.com/Article/18030.shtml
- http://map.read.usuhx.com/Article/4104.shtml
- http://map.read.usuhx.com/Article/50605.shtml
- http://map.mobile.xqnqq.com/Article/5460.shtml
- http://map.read.usuhx.com/Article/208430.shtml
- http://map.mobile.xqnqq.com/Article/47432.shtml
- http://map.read.usuhx.com/Article/4350.shtml
- http://map.mobile.xqnqq.com/Article/4120313.shtml
- http://map.read.usuhx.com/Article/724503.shtml
- http://map.read.usuhx.com/Article/449729.shtml
- http://map.read.usuhx.com/Article/5828.shtml
- http://map.read.usuhx.com/Article/659487.shtml
- http://map.read.usuhx.com/Article/9708263.shtml
- http://map.mobile.xqnqq.com/Article/7820.shtml
- http://map.mobile.xqnqq.com/Article/566511.shtml
- http://map.mobile.xqnqq.com/Article/420416.shtml
- http://map.mobile.xqnqq.com/Article/8760.shtml
- http://map.read.usuhx.com/Article/2969.shtml
- http://map.read.usuhx.com/Article/3270.shtml
- http://map.mobile.xqnqq.com/Article/840741.shtml
- http://map.read.usuhx.com/Article/88156.shtml
- http://map.read.usuhx.com/Article/4530028.shtml
- http://map.read.usuhx.com/Article/10486.shtml
- http://map.mobile.xqnqq.com/Article/0939.shtml
- http://map.mobile.xqnqq.com/Article/4927395.shtml
- http://map.read.usuhx.com/Article/5667.shtml
- http://map.mobile.xqnqq.com/Article/8566.shtml
- http://map.mobile.xqnqq.com/Article/5110652.shtml
- http://map.mobile.xqnqq.com/Article/75959.shtml
- http://map.read.usuhx.com/Article/237688.shtml
- http://map.read.usuhx.com/Article/34245.shtml
- http://map.mobile.xqnqq.com/Article/90024.shtml
- http://map.mobile.xqnqq.com/Article/4780.shtml
- http://map.mobile.xqnqq.com/Article/374402.shtml
- http://map.mobile.xqnqq.com/Article/6016.shtml
- http://map.read.usuhx.com/Article/7332.shtml
- http://map.read.usuhx.com/Article/2819110.shtml
- http://map.mobile.xqnqq.com/Article/2018729.shtml
- http://map.mobile.xqnqq.com/Article/2770319.shtml
- http://map.read.usuhx.com/Article/54748.shtml
- http://map.read.usuhx.com/Article/962759.shtml
- http://map.mobile.xqnqq.com/Article/2128585.shtml
- http://map.mobile.xqnqq.com/Article/177775.shtml
- http://map.mobile.xqnqq.com/Article/8042480.shtml
- http://map.mobile.xqnqq.com/Article/7187708.shtml
- http://map.read.usuhx.com/Article/861658.shtml
- http://map.mobile.xqnqq.com/Article/401343.shtml
- http://map.mobile.xqnqq.com/Article/351911.shtml
- http://map.mobile.xqnqq.com/Article/409075.shtml
- http://map.read.usuhx.com/Article/9331100.shtml
- http://map.mobile.xqnqq.com/Article/571166.shtml
- http://map.read.usuhx.com/Article/805558.shtml
- http://map.read.usuhx.com/Article/6763.shtml
- http://map.read.usuhx.com/Article/35417.shtml
- http://map.read.usuhx.com/Article/7219.shtml
- http://map.read.usuhx.com/Article/955641.shtml
- http://map.read.usuhx.com/Article/2351429.shtml
- http://map.mobile.xqnqq.com/Article/88816.shtml
- http://map.read.usuhx.com/Article/712238.shtml
- http://map.mobile.xqnqq.com/Article/14532.shtml
- http://map.read.usuhx.com/Article/6155.shtml
- http://map.read.usuhx.com/Article/7937.shtml
- http://map.mobile.xqnqq.com/Article/979376.shtml
- http://map.mobile.xqnqq.com/Article/08812.shtml
- http://map.read.usuhx.com/Article/310205.shtml
- http://map.mobile.xqnqq.com/Article/4625185.shtml
- http://map.mobile.xqnqq.com/Article/125112.shtml
- http://map.mobile.xqnqq.com/Article/495764.shtml
- http://map.mobile.xqnqq.com/Article/34819.shtml
- http://map.read.usuhx.com/Article/5753.shtml
- http://map.read.usuhx.com/Article/7252268.shtml
- http://map.read.usuhx.com/Article/3320011.shtml
- http://map.mobile.xqnqq.com/Article/40257.shtml
- http://map.mobile.xqnqq.com/Article/2671.shtml
- http://map.read.usuhx.com/Article/044227.shtml
- http://map.read.usuhx.com/Article/1836046.shtml
- http://map.mobile.xqnqq.com/Article/653773.shtml
- http://map.read.usuhx.com/Article/9463.shtml
- http://map.mobile.xqnqq.com/Article/37490.shtml
- http://map.mobile.xqnqq.com/Article/9174.shtml
- http://map.read.usuhx.com/Article/2678.shtml
- http://map.mobile.xqnqq.com/Article/4300.shtml
- http://map.read.usuhx.com/Article/405315.shtml
- http://map.read.usuhx.com/Article/88075.shtml
- http://map.read.usuhx.com/Article/6704.shtml
- http://map.mobile.xqnqq.com/Article/0274.shtml
- http://map.read.usuhx.com/Article/7295496.shtml
- http://map.mobile.xqnqq.com/Article/8121.shtml
- http://map.mobile.xqnqq.com/Article/0263.shtml
- http://map.read.usuhx.com/Article/3731.shtml
- http://map.read.usuhx.com/Article/0837012.shtml
- http://map.read.usuhx.com/Article/4129.shtml
- http://map.read.usuhx.com/Article/69705.shtml
- http://map.mobile.xqnqq.com/Article/8676198.shtml
- http://map.mobile.xqnqq.com/Article/5189.shtml
- http://map.mobile.xqnqq.com/Article/371915.shtml
- http://map.mobile.xqnqq.com/Article/079932.shtml
- http://map.mobile.xqnqq.com/Article/750557.shtml
- http://map.mobile.xqnqq.com/Article/1054.shtml
- http://map.read.usuhx.com/Article/8922439.shtml
- http://map.mobile.xqnqq.com/Article/62314.shtml
- http://map.mobile.xqnqq.com/Article/7844889.shtml
- http://map.read.usuhx.com/Article/4734.shtml
- http://map.read.usuhx.com/Article/831998.shtml
- http://map.read.usuhx.com/Article/745342.shtml
- http://map.read.usuhx.com/Article/1408.shtml
- http://map.read.usuhx.com/Article/0698833.shtml
- http://map.read.usuhx.com/Article/1294.shtml
- http://map.read.usuhx.com/Article/358317.shtml
- http://map.mobile.xqnqq.com/Article/34091.shtml
- http://map.read.usuhx.com/Article/4182.shtml
- http://map.read.usuhx.com/Article/37271.shtml
- http://map.read.usuhx.com/Article/516075.shtml
- http://map.mobile.xqnqq.com/Article/0770124.shtml
- http://map.mobile.xqnqq.com/Article/516096.shtml
- http://map.read.usuhx.com/Article/084253.shtml
- http://map.read.usuhx.com/Article/7291.shtml
- http://map.read.usuhx.com/Article/8141582.shtml
- http://map.read.usuhx.com/Article/0123880.shtml
- http://map.read.usuhx.com/Article/90018.shtml
- http://map.mobile.xqnqq.com/Article/708673.shtml
- http://map.mobile.xqnqq.com/Article/6175195.shtml
- http://map.mobile.xqnqq.com/Article/1562011.shtml
- http://map.read.usuhx.com/Article/166634.shtml
- http://map.read.usuhx.com/Article/684720.shtml
- http://map.mobile.xqnqq.com/Article/865673.shtml
- http://map.mobile.xqnqq.com/Article/8798.shtml
- http://map.mobile.xqnqq.com/Article/8491.shtml
- http://map.mobile.xqnqq.com/Article/64553.shtml
- http://map.mobile.xqnqq.com/Article/6520.shtml
- http://map.mobile.xqnqq.com/Article/98020.shtml
- http://map.read.usuhx.com/Article/414166.shtml
- http://map.mobile.xqnqq.com/Article/806313.shtml
- http://map.mobile.xqnqq.com/Article/7219.shtml
- http://map.read.usuhx.com/Article/029923.shtml
- http://map.read.usuhx.com/Article/70893.shtml
- http://map.mobile.xqnqq.com/Article/9161005.shtml
- http://map.read.usuhx.com/Article/10788.shtml
- http://map.read.usuhx.com/Article/44954.shtml
- http://map.mobile.xqnqq.com/Article/7586644.shtml
- http://map.mobile.xqnqq.com/Article/0230.shtml
- http://map.mobile.xqnqq.com/Article/1501136.shtml
- http://map.read.usuhx.com/Article/963754.shtml
- http://map.read.usuhx.com/Article/4130.shtml
- http://map.read.usuhx.com/Article/49048.shtml
- http://map.mobile.xqnqq.com/Article/152582.shtml
- http://map.read.usuhx.com/Article/35422.shtml
- http://map.mobile.xqnqq.com/Article/1214.shtml
- http://map.mobile.xqnqq.com/Article/87897.shtml
- http://map.read.usuhx.com/Article/6850508.shtml
- http://map.read.usuhx.com/Article/391250.shtml
- http://map.read.usuhx.com/Article/00504.shtml
- http://map.read.usuhx.com/Article/787329.shtml
- http://map.mobile.xqnqq.com/Article/78465.shtml
- http://map.read.usuhx.com/Article/9313334.shtml
- http://map.mobile.xqnqq.com/Article/18111.shtml
- http://map.mobile.xqnqq.com/Article/5970.shtml
- http://map.mobile.xqnqq.com/Article/1327.shtml
- http://map.read.usuhx.com/Article/9495585.shtml
- http://map.read.usuhx.com/Article/594546.shtml
- http://map.mobile.xqnqq.com/Article/8128664.shtml
- http://map.mobile.xqnqq.com/Article/44514.shtml
- http://map.read.usuhx.com/Article/80034.shtml
- http://map.mobile.xqnqq.com/Article/1370.shtml
- http://map.mobile.xqnqq.com/Article/3972126.shtml
- http://map.read.usuhx.com/Article/9797907.shtml
- http://map.read.usuhx.com/Article/7277255.shtml
- http://map.read.usuhx.com/Article/864800.shtml
- http://map.read.usuhx.com/Article/166949.shtml
- http://map.read.usuhx.com/Article/36634.shtml
- http://map.mobile.xqnqq.com/Article/18165.shtml
- http://map.read.usuhx.com/Article/6950.shtml
- http://map.mobile.xqnqq.com/Article/897890.shtml
- http://map.mobile.xqnqq.com/Article/207621.shtml
- http://map.mobile.xqnqq.com/Article/7396027.shtml
- http://map.mobile.xqnqq.com/Article/9900101.shtml
- http://map.mobile.xqnqq.com/Article/398536.shtml
- http://map.read.usuhx.com/Article/5648.shtml
- http://map.read.usuhx.com/Article/17948.shtml
- http://map.read.usuhx.com/Article/0006.shtml
- http://map.read.usuhx.com/Article/3966.shtml
- http://map.read.usuhx.com/Article/0996.shtml
- http://map.read.usuhx.com/Article/568676.shtml
- http://map.read.usuhx.com/Article/39539.shtml
- http://map.mobile.xqnqq.com/Article/592999.shtml
- http://map.read.usuhx.com/Article/4162.shtml
- http://map.read.usuhx.com/Article/3689.shtml
- http://map.mobile.xqnqq.com/Article/8454.shtml
- http://map.mobile.xqnqq.com/Article/7612.shtml
- http://map.read.usuhx.com/Article/9533285.shtml
- http://map.read.usuhx.com/Article/60366.shtml
- http://map.read.usuhx.com/Article/2897516.shtml
- http://map.read.usuhx.com/Article/96251.shtml
- http://map.mobile.xqnqq.com/Article/075799.shtml
- http://map.read.usuhx.com/Article/8438129.shtml
- http://map.read.usuhx.com/Article/224331.shtml
- http://map.read.usuhx.com/Article/2731.shtml
- http://map.mobile.xqnqq.com/Article/6291812.shtml
- http://map.read.usuhx.com/Article/8089843.shtml
- http://map.read.usuhx.com/Article/8856.shtml
- http://map.mobile.xqnqq.com/Article/3693455.shtml
- http://map.read.usuhx.com/Article/3178101.shtml
- http://map.read.usuhx.com/Article/56280.shtml
- http://map.mobile.xqnqq.com/Article/69521.shtml
- http://map.mobile.xqnqq.com/Article/7987.shtml
- http://map.read.usuhx.com/Article/063525.shtml
- http://map.mobile.xqnqq.com/Article/83910.shtml
- http://map.read.usuhx.com/Article/7660.shtml
- http://map.mobile.xqnqq.com/Article/74570.shtml
- http://map.mobile.xqnqq.com/Article/4775450.shtml
- http://map.mobile.xqnqq.com/Article/543455.shtml
- http://map.mobile.xqnqq.com/Article/5900.shtml
- http://map.read.usuhx.com/Article/680074.shtml
- http://map.mobile.xqnqq.com/Article/460696.shtml

## 项目结构

项目采用分层架构设计，核心采集引擎位于 `core` 包中，Web 层与数据访问层严格分离。具体目录结构及职责说明如下所示。

```
resourcelink-aggregate/
├── app.py                           # 应用主入口，初始化 Flask 与调度器
├── config/
│   ├── default.yaml                 # 默认配置项，包含超时、并发数、日志级别
│   └── local.yaml                   # 本地覆盖配置，不提交至版本库
├── core/                            # 核心采集与处理模块
│   ├── __init__.py
│   ├── fetcher.py                   # 异步 HTTP 抓取器，含重试与代理逻辑
│   ├── parser.py                    # 基于 BeautifulSoup4 的元数据解析器
│   ├── dedup.py                     # 布隆过滤器与哈希去重实现
│   └── scheduler.py                 # APScheduler 定时任务编排器
├── models/                          # 数据模型与 ORM 映射
│   ├── __init__.py
│   ├── base.py                      # SQLAlchemy 基类与数据库连接工厂
│   ├── link.py                      # Link 实体，包含 URL、标题、摘要、哈希
│   └── tag.py                       # Tag 实体及 Link-Tag 多对多关联表
├── web/                             # Web 界面与 REST API
│   ├── __init__.py
│   ├── routes/                      # 路由蓝图
│   │   ├── index.py                 # 主页与仪表盘
│   │   ├── links.py                 # 链接列表、筛选、导出接口
│   │   └── tasks.py                 # 手动触发采集任务与管理后台
│   └── templates/                   # Jinja2 模板文件
│       ├── base.html
│       └── link_table.html
├── scripts/                         # 运维与工具脚本
│   ├── migrate_db.py                # 数据库迁移与初始化
│   ├── export_csv.py                # 命令行导出工具
│   └── seed_data.py                 # 测试数据填充脚本
├── tests/                           # 单元测试与集成测试
│   ├── test_fetcher.py
│   ├── test_parser.py
│   └── conftest.py                  # pytest 固定装置配置
├── requirements.txt                 # 生产环境依赖清单
├── requirements-dev.txt             # 开发与测试额外依赖
└── README.md                        # 项目说明文档（本文件）
```

## 贡献指南

我们欢迎任何形式的贡献，包括但不限于新增解析器适配、性能优化、文档改进与缺陷修复。请遵循以下流程提交您的变更。

1. 在 GitHub 上 fork 本仓库，并基于 `main` 分支创建您的特性分支，分支命名建议采用 `feat/` 或 `fix/` 前缀，例如 `feat/add-xpath-parser`。

2. 在本地环境运行单元测试套件，确保所有现有用例均通过。若新增功能，请在 `tests/` 目录下补充相应的测试代码，并确保测试覆盖率不低于百分之八十。

3. 更新项目文档，包括但不限于配置文件说明、API 接口示例以及本 README 中涉及功能变更的章节。所有文档变更需与代码提交保持在同一 PR 内。

4. 提交代码前执行代码风格检查工具，本项目采用 Black 作为 Python 代码格式化工具，使用 Flake8 进行静态检查。提交信息应遵循 Conventional Commits 规范，格式为 `<type>(<scope>): <subject>`。

5. 通过 Pull Request 提交变更，并在描述中清楚说明该 PR 解决的具体问题或实现的功能。等待至少一位维护者进行代码审查，并配合修改直至审查通过。

## 常见问题

**Q: 采集过程中出现大量超时或连接拒绝错误，应如何调整配置？**

A: 此类错误通常由目标站点限制并发请求或网络延迟引起。建议在 `config/local.yaml` 中降低 `fetcher.concurrency` 参数值，并适当增大 `fetcher.timeout` 超时阈值。同时可开启 `fetcher.retry.enabled` 选项，配置最多三次重试，每次重试间隔建议设置为指数退避策略。若目标站点位于境外，可考虑配置代理池。

**Q: 系统是否支持增量采集，如何避免每次启动任务时重复抓取全部链接？**

A: 支持增量采集。系统在首次运行时会为每一个已采集的链接记录 `last_fetched_at` 时间戳和内容哈希。在调度器配置中，可将 `scheduler.mode` 设为 `incremental`，并设置 `scheduler.interval_hours` 为 24 或更小值。每次增量任务仅拉取最近更新日期大于上次采集时间的文章，同时对于哈希不变的页面直接跳过正文解析流程，显著减少处理开销。若需强制全量刷新，可在 API 调用时传入 `force=true` 参数。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
