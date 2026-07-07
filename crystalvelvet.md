# LinkSphere 技术外链资源聚合站

LinkSphere 是一个面向开发者、技术研究人员与内容创作者的轻量级外链资源聚合与导航系统。该项目旨在解决技术资料分散、优质外链难以追溯、文章资源易失效等问题，通过结构化的文章链接收录机制，为技术社区提供一个可维护、可扩展的外部资源索引平台。

项目定位于中小型技术团队、个人知识管理爱好者以及开源文档维护者。用户可通过 LinkSphere 快速收录、分类和检索来自多个源站点的技术文章链接，并利用内置的元数据提取与状态检测能力，持续跟踪外链的有效性与内容变更。LinkSphere 不存储文章全文，仅保留链接、标题、来源站点与时间戳等索引信息，确保合规与轻量化。

第 9/80 批次资源导入工作已完成，当前批次共收录 250 个外链条目，覆盖两个主要源站域名。本批次资源主要涉及移动端技术文档、通用开发教程与系统运维类文章，后续批次将持续扩充源站覆盖范围。

## 功能概览

批量链接导入：支持通过文本列表或 CSV 文件批量导入外链 URL，系统自动解析域名、路径与文章 ID，并按来源站点分组存储。

来源站点管理：内置多源站点配置机制，当前已适配 mobile.xqnqq.com 与 read.usuhx.com 两个内容源，支持动态添加或禁用站点。

链接状态检测：定期发起 HEAD 请求验证外链可达性，标记失效链接并生成异常报告，辅助维护者清理或更新资源。

元数据提取：自动抓取目标页面的标题、概要描述及发布时间等基础元数据，填充索引库以提升检索体验。

标签与分类体系：允许用户为每条链接打标签，支持按标签、域名或导入批次进行筛选与聚合查询。

只读 API 接口：提供基于 RESTful 风格的只读查询接口，支持按 ID、域名、标签等条件分页获取链接列表，便于集成到其他系统。

导入导出兼容性：支持标准 JSON 与 Markdown 列表两种导出格式，便于迁移或生成静态文档站点。

## 应用场景

技术博客外部引用管理：技术博主可使用 LinkSphere 整理文末参考链接，将散落在各处的引用来源统一收录，并定期检查链接是否仍然有效，避免读者点击失效引用。

开源项目文档外链索引：开源项目的维护者可将项目文档中引用的外部教程、API 参考和社区讨论链接集中纳入 LinkSphere 管理，确保文档中的外部资源可追溯、可更新。

团队知识库资源聚合：企业内部技术团队可将日常阅读收藏的技术文章链接通过 LinkSphere 统一入库，配合标签体系按主题分类，形成团队共享的外部知识索引。

个人阅读列表备份与整理：技术爱好者可定期将阅读过的优质文章链接导入 LinkSphere，避免浏览器书签杂乱无章，同时利用元数据提取能力快速回忆文章主题。

## 快速开始

以下命令演示了如何从 GitHub 克隆项目、安装依赖并启动开发服务。

```bash
git clone https://github.com/linksphere/linksphere-core.git
cd linksphere-core
pip install -r requirements.txt
cp .env.example .env
# 编辑 .env 文件配置数据库连接与源站点参数
python manage.py migrate
python manage.py import_batch --file ./batches/batch_9_80.txt
python manage.py runserver
```

生产环境部署建议参考 `deploy/` 目录下的 Docker Compose 配置与 Nginx 示例文件。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10 及以上 | 核心运行环境，推荐使用 3.11 |
| PostgreSQL | 14.x 及以上 | 主数据库，用于存储链接索引与元数据 |
| Redis | 7.x 及以上 | 缓存与任务队列后端，用于状态检测任务调度 |
| Celery | 5.3.x | 异步任务框架，用于执行链接状态检测与元数据抓取 |
| httpx | 0.27.x | HTTP 客户端，用于发起外链请求，支持异步与超时控制 |
| beautifulsoup4 | 4.12.x | HTML 解析库，用于从目标页面提取标题与描述元数据 |
| python-dotenv | 1.0.x | 环境变量管理，用于加载 .env 配置文件 |
| psycopg2-binary | 2.9.x | PostgreSQL 适配器，生产环境建议使用二进制版本 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户指南 | docs/user_guide/ | 如何导入链接、如何查看状态报告、如何使用标签筛选 |
| 运维手册 | docs/ops/ | 如何部署生产环境、如何配置 Celery 工作进程、如何备份索引库 |
| API 参考 | docs/api/ | 提供哪些查询端点、请求参数格式、返回数据结构示例 |
| 批次管理 | docs/batch/ | 批次文件格式规范、导入命令用法、当前批次进度查询方法 |

## 资源列表

- http://www.mobile.xqnqq.com/Article/680515.shtml
- http://www.mobile.xqnqq.com/Article/11370.shtml
- http://www.read.usuhx.com/Article/0484162.shtml
- http://www.mobile.xqnqq.com/Article/50846.shtml
- http://www.read.usuhx.com/Article/49059.shtml
- http://www.read.usuhx.com/Article/3625648.shtml
- http://www.read.usuhx.com/Article/42668.shtml
- http://www.read.usuhx.com/Article/41065.shtml
- http://www.mobile.xqnqq.com/Article/83506.shtml
- http://www.mobile.xqnqq.com/Article/2792299.shtml
- http://www.read.usuhx.com/Article/702031.shtml
- http://www.mobile.xqnqq.com/Article/975932.shtml
- http://www.mobile.xqnqq.com/Article/653403.shtml
- http://www.mobile.xqnqq.com/Article/935450.shtml
- http://www.mobile.xqnqq.com/Article/3441654.shtml
- http://www.read.usuhx.com/Article/89922.shtml
- http://www.read.usuhx.com/Article/6976.shtml
- http://www.mobile.xqnqq.com/Article/7079370.shtml
- http://www.mobile.xqnqq.com/Article/7039.shtml
- http://www.read.usuhx.com/Article/56523.shtml
- http://www.mobile.xqnqq.com/Article/5225.shtml
- http://www.read.usuhx.com/Article/0032.shtml
- http://www.mobile.xqnqq.com/Article/2728236.shtml
- http://www.read.usuhx.com/Article/8751215.shtml
- http://www.read.usuhx.com/Article/0156642.shtml
- http://www.read.usuhx.com/Article/654455.shtml
- http://www.read.usuhx.com/Article/6763585.shtml
- http://www.read.usuhx.com/Article/73817.shtml
- http://www.read.usuhx.com/Article/5634.shtml
- http://www.read.usuhx.com/Article/1439.shtml
- http://www.read.usuhx.com/Article/0398871.shtml
- http://www.read.usuhx.com/Article/46815.shtml
- http://www.read.usuhx.com/Article/06163.shtml
- http://www.mobile.xqnqq.com/Article/9386.shtml
- http://www.mobile.xqnqq.com/Article/0643.shtml
- http://www.mobile.xqnqq.com/Article/3605.shtml
- http://www.mobile.xqnqq.com/Article/2851.shtml
- http://www.read.usuhx.com/Article/011565.shtml
- http://www.read.usuhx.com/Article/207171.shtml
- http://www.mobile.xqnqq.com/Article/2133231.shtml
- http://www.read.usuhx.com/Article/0860.shtml
- http://www.read.usuhx.com/Article/44155.shtml
- http://www.mobile.xqnqq.com/Article/93092.shtml
- http://www.mobile.xqnqq.com/Article/197417.shtml
- http://www.read.usuhx.com/Article/14792.shtml
- http://www.read.usuhx.com/Article/2277.shtml
- http://www.mobile.xqnqq.com/Article/78098.shtml
- http://www.read.usuhx.com/Article/729259.shtml
- http://www.read.usuhx.com/Article/39432.shtml
- http://www.read.usuhx.com/Article/0564.shtml
- http://www.read.usuhx.com/Article/829445.shtml
- http://www.read.usuhx.com/Article/9368204.shtml
- http://www.mobile.xqnqq.com/Article/656756.shtml
- http://www.mobile.xqnqq.com/Article/66894.shtml
- http://www.mobile.xqnqq.com/Article/0465.shtml
- http://www.read.usuhx.com/Article/0793.shtml
- http://www.mobile.xqnqq.com/Article/40188.shtml
- http://www.read.usuhx.com/Article/7038.shtml
- http://www.mobile.xqnqq.com/Article/0905.shtml
- http://www.mobile.xqnqq.com/Article/1387820.shtml
- http://www.mobile.xqnqq.com/Article/49809.shtml
- http://www.read.usuhx.com/Article/577876.shtml
- http://www.read.usuhx.com/Article/0034353.shtml
- http://www.mobile.xqnqq.com/Article/18919.shtml
- http://www.read.usuhx.com/Article/197802.shtml
- http://www.mobile.xqnqq.com/Article/509415.shtml
- http://www.read.usuhx.com/Article/746506.shtml
- http://www.mobile.xqnqq.com/Article/2837606.shtml
- http://www.read.usuhx.com/Article/97787.shtml
- http://www.read.usuhx.com/Article/415449.shtml
- http://www.read.usuhx.com/Article/2689.shtml
- http://www.mobile.xqnqq.com/Article/6054.shtml
- http://www.read.usuhx.com/Article/885875.shtml
- http://www.read.usuhx.com/Article/378989.shtml
- http://www.mobile.xqnqq.com/Article/5077.shtml
- http://www.mobile.xqnqq.com/Article/5191214.shtml
- http://www.read.usuhx.com/Article/4626.shtml
- http://www.read.usuhx.com/Article/8063658.shtml
- http://www.read.usuhx.com/Article/8002.shtml
- http://www.mobile.xqnqq.com/Article/2540820.shtml
- http://www.mobile.xqnqq.com/Article/0212592.shtml
- http://www.mobile.xqnqq.com/Article/6129835.shtml
- http://www.read.usuhx.com/Article/56104.shtml
- http://www.read.usuhx.com/Article/2570053.shtml
- http://www.mobile.xqnqq.com/Article/051994.shtml
- http://www.read.usuhx.com/Article/58302.shtml
- http://www.mobile.xqnqq.com/Article/2852.shtml
- http://www.mobile.xqnqq.com/Article/80206.shtml
- http://www.mobile.xqnqq.com/Article/361992.shtml
- http://www.read.usuhx.com/Article/637974.shtml
- http://www.mobile.xqnqq.com/Article/4929304.shtml
- http://www.read.usuhx.com/Article/55944.shtml
- http://www.read.usuhx.com/Article/691189.shtml
- http://www.mobile.xqnqq.com/Article/4982.shtml
- http://www.read.usuhx.com/Article/0244.shtml
- http://www.read.usuhx.com/Article/1695936.shtml
- http://www.read.usuhx.com/Article/9246.shtml
- http://www.mobile.xqnqq.com/Article/952954.shtml
- http://www.read.usuhx.com/Article/52959.shtml
- http://www.mobile.xqnqq.com/Article/60920.shtml
- http://www.read.usuhx.com/Article/279040.shtml
- http://www.read.usuhx.com/Article/820535.shtml
- http://www.mobile.xqnqq.com/Article/047120.shtml
- http://www.mobile.xqnqq.com/Article/4762.shtml
- http://www.mobile.xqnqq.com/Article/30095.shtml
- http://www.read.usuhx.com/Article/49906.shtml
- http://www.mobile.xqnqq.com/Article/91941.shtml
- http://www.mobile.xqnqq.com/Article/84333.shtml
- http://www.read.usuhx.com/Article/397021.shtml
- http://www.mobile.xqnqq.com/Article/41901.shtml
- http://www.read.usuhx.com/Article/698913.shtml
- http://www.read.usuhx.com/Article/837624.shtml
- http://www.read.usuhx.com/Article/7752420.shtml
- http://www.mobile.xqnqq.com/Article/4500.shtml
- http://www.mobile.xqnqq.com/Article/67333.shtml
- http://www.read.usuhx.com/Article/418926.shtml
- http://www.mobile.xqnqq.com/Article/21842.shtml
- http://www.mobile.xqnqq.com/Article/6878357.shtml
- http://www.mobile.xqnqq.com/Article/61071.shtml
- http://www.read.usuhx.com/Article/286107.shtml
- http://www.read.usuhx.com/Article/64039.shtml
- http://www.read.usuhx.com/Article/4457730.shtml
- http://www.read.usuhx.com/Article/722750.shtml
- http://www.mobile.xqnqq.com/Article/130039.shtml
- http://www.read.usuhx.com/Article/5570351.shtml
- http://www.mobile.xqnqq.com/Article/9474845.shtml
- http://www.read.usuhx.com/Article/201257.shtml
- http://www.mobile.xqnqq.com/Article/306246.shtml
- http://www.mobile.xqnqq.com/Article/4052640.shtml
- http://www.read.usuhx.com/Article/08416.shtml
- http://www.mobile.xqnqq.com/Article/3280981.shtml
- http://www.read.usuhx.com/Article/9904.shtml
- http://www.mobile.xqnqq.com/Article/019547.shtml
- http://www.mobile.xqnqq.com/Article/695668.shtml
- http://www.mobile.xqnqq.com/Article/72650.shtml
- http://www.read.usuhx.com/Article/9008612.shtml
- http://www.read.usuhx.com/Article/0789735.shtml
- http://www.read.usuhx.com/Article/5625375.shtml
- http://www.read.usuhx.com/Article/53095.shtml
- http://www.read.usuhx.com/Article/01509.shtml
- http://www.mobile.xqnqq.com/Article/4308.shtml
- http://www.mobile.xqnqq.com/Article/7867776.shtml
- http://www.mobile.xqnqq.com/Article/9928.shtml
- http://www.mobile.xqnqq.com/Article/561505.shtml
- http://www.read.usuhx.com/Article/2619.shtml
- http://www.mobile.xqnqq.com/Article/2925.shtml
- http://www.read.usuhx.com/Article/612019.shtml
- http://www.mobile.xqnqq.com/Article/3412383.shtml
- http://www.mobile.xqnqq.com/Article/2710.shtml
- http://www.read.usuhx.com/Article/1505296.shtml
- http://www.mobile.xqnqq.com/Article/0812.shtml
- http://www.mobile.xqnqq.com/Article/6686301.shtml
- http://www.mobile.xqnqq.com/Article/7483.shtml
- http://www.read.usuhx.com/Article/1808.shtml
- http://www.read.usuhx.com/Article/942755.shtml
- http://www.mobile.xqnqq.com/Article/5081779.shtml
- http://www.read.usuhx.com/Article/22598.shtml
- http://www.mobile.xqnqq.com/Article/62530.shtml
- http://www.read.usuhx.com/Article/6476936.shtml
- http://www.read.usuhx.com/Article/0978.shtml
- http://www.mobile.xqnqq.com/Article/7713989.shtml
- http://www.mobile.xqnqq.com/Article/488774.shtml
- http://www.read.usuhx.com/Article/07693.shtml
- http://www.mobile.xqnqq.com/Article/17025.shtml
- http://www.mobile.xqnqq.com/Article/5532302.shtml
- http://www.read.usuhx.com/Article/022225.shtml
- http://www.read.usuhx.com/Article/80914.shtml
- http://www.mobile.xqnqq.com/Article/4544.shtml
- http://www.read.usuhx.com/Article/764672.shtml
- http://www.mobile.xqnqq.com/Article/50987.shtml
- http://www.mobile.xqnqq.com/Article/79408.shtml
- http://www.read.usuhx.com/Article/11012.shtml
- http://www.mobile.xqnqq.com/Article/3511272.shtml
- http://www.mobile.xqnqq.com/Article/9577.shtml
- http://www.read.usuhx.com/Article/05437.shtml
- http://www.mobile.xqnqq.com/Article/2621.shtml
- http://www.read.usuhx.com/Article/248180.shtml
- http://www.read.usuhx.com/Article/4758.shtml
- http://www.mobile.xqnqq.com/Article/732980.shtml
- http://www.read.usuhx.com/Article/51241.shtml
- http://www.mobile.xqnqq.com/Article/9954.shtml
- http://www.mobile.xqnqq.com/Article/1728910.shtml
- http://www.mobile.xqnqq.com/Article/799083.shtml
- http://www.read.usuhx.com/Article/6771654.shtml
- http://www.read.usuhx.com/Article/770700.shtml
- http://www.read.usuhx.com/Article/3819.shtml
- http://www.mobile.xqnqq.com/Article/0000.shtml
- http://www.read.usuhx.com/Article/0432.shtml
- http://www.read.usuhx.com/Article/580424.shtml
- http://www.mobile.xqnqq.com/Article/8659.shtml
- http://www.mobile.xqnqq.com/Article/256789.shtml
- http://www.mobile.xqnqq.com/Article/7566.shtml
- http://www.mobile.xqnqq.com/Article/229470.shtml
- http://www.mobile.xqnqq.com/Article/515698.shtml
- http://www.read.usuhx.com/Article/3712.shtml
- http://www.mobile.xqnqq.com/Article/2531.shtml
- http://www.read.usuhx.com/Article/9542.shtml
- http://www.mobile.xqnqq.com/Article/44707.shtml
- http://www.mobile.xqnqq.com/Article/0083.shtml
- http://www.read.usuhx.com/Article/9092955.shtml
- http://www.mobile.xqnqq.com/Article/8661537.shtml
- http://www.read.usuhx.com/Article/975525.shtml
- http://www.mobile.xqnqq.com/Article/571835.shtml
- http://www.read.usuhx.com/Article/7587.shtml
- http://www.mobile.xqnqq.com/Article/600700.shtml
- http://www.mobile.xqnqq.com/Article/91945.shtml
- http://www.read.usuhx.com/Article/139174.shtml
- http://www.mobile.xqnqq.com/Article/4218277.shtml
- http://www.read.usuhx.com/Article/5018460.shtml
- http://www.read.usuhx.com/Article/8924.shtml
- http://www.mobile.xqnqq.com/Article/66410.shtml
- http://www.read.usuhx.com/Article/155964.shtml
- http://www.mobile.xqnqq.com/Article/5122.shtml
- http://www.mobile.xqnqq.com/Article/8315781.shtml
- http://www.mobile.xqnqq.com/Article/7344.shtml
- http://www.mobile.xqnqq.com/Article/6367.shtml
- http://www.mobile.xqnqq.com/Article/045538.shtml
- http://www.mobile.xqnqq.com/Article/7542.shtml
- http://www.read.usuhx.com/Article/71648.shtml
- http://www.mobile.xqnqq.com/Article/111476.shtml
- http://www.mobile.xqnqq.com/Article/0884675.shtml
- http://www.read.usuhx.com/Article/9309.shtml
- http://www.read.usuhx.com/Article/902087.shtml
- http://www.read.usuhx.com/Article/1563397.shtml
- http://www.read.usuhx.com/Article/853209.shtml
- http://www.read.usuhx.com/Article/27591.shtml
- http://www.read.usuhx.com/Article/9204.shtml
- http://www.read.usuhx.com/Article/363780.shtml
- http://www.read.usuhx.com/Article/5789.shtml
- http://www.mobile.xqnqq.com/Article/01270.shtml
- http://www.read.usuhx.com/Article/6532565.shtml
- http://www.mobile.xqnqq.com/Article/54219.shtml
- http://www.read.usuhx.com/Article/3679317.shtml
- http://www.mobile.xqnqq.com/Article/87138.shtml
- http://www.read.usuhx.com/Article/0585743.shtml
- http://www.mobile.xqnqq.com/Article/3016970.shtml
- http://www.mobile.xqnqq.com/Article/2979565.shtml
- http://www.read.usuhx.com/Article/0870603.shtml
- http://www.mobile.xqnqq.com/Article/8729.shtml
- http://www.mobile.xqnqq.com/Article/331562.shtml
- http://www.read.usuhx.com/Article/7799.shtml
- http://www.mobile.xqnqq.com/Article/5244958.shtml
- http://www.read.usuhx.com/Article/8335.shtml
- http://www.read.usuhx.com/Article/281405.shtml
- http://www.mobile.xqnqq.com/Article/842851.shtml
- http://www.mobile.xqnqq.com/Article/27605.shtml
- http://www.mobile.xqnqq.com/Article/6432.shtml
- http://www.read.usuhx.com/Article/4281209.shtml
- http://www.mobile.xqnqq.com/Article/804614.shtml
- http://www.mobile.xqnqq.com/Article/9819.shtml

## 项目结构

```
linksphere-core/
├── src/
│   ├── core/                         # 核心配置与全局常量
│   │   ├── settings.py               # Django 项目配置，包含数据库、缓存与 Celery 设置
│   │   └── constants.py              # 状态码、超时阈值、默认分页大小等常量定义
│   ├── links/                        # 链接管理主应用
│   │   ├── models.py                 # Link, SourceSite, Tag, BatchRecord 等数据模型
│   │   ├── services/                 # 业务逻辑层
│   │   │   ├── importer.py           # 批量导入服务，支持文本列表与 CSV 解析
│   │   │   ├── checker.py            # 链接状态检测服务，基于 httpx 异步并发
│   │   │   └── extractor.py          # 元数据提取服务，基于 beautifulsoup4
│   │   ├── tasks.py                  # Celery 异步任务定义（检测、抓取、清理）
│   │   └── admin.py                  # Django Admin 后台管理配置
│   ├── api/                          # RESTful 只读 API 视图与序列化器
│   │   ├── views.py                  # 按域名、标签、批次查询的接口视图
│   │   └── serializers.py            # Link 与 BatchRecord 的序列化定义
│   └── utils/                        # 通用工具函数
│       ├── http.py                   # 自定义 httpx 客户端封装，含重试与超时策略
│       └── parser.py                 # URL 解析辅助函数，提取域名与文章 ID
├── tests/                            # 单元测试与集成测试
│   ├── test_importer.py
│   ├── test_checker.py
│   └── test_api.py
├── docs/                             # 完整文档目录，对应文档导航表格
├── deploy/                           # 生产环境部署配置
│   ├── docker-compose.yml
│   ├── nginx/
│   └── supervisor/
├── batches/                          # 批次导入文件存档
│   └── batch_9_80.txt                # 第 9/80 批次原始链接列表
├── requirements.txt                  # Python 依赖清单
├── .env.example                      # 环境变量模板
├── manage.py                         # Django 管理入口
└── README.md                         # 本文件
```

## 贡献指南

我们欢迎并鼓励社区贡献，无论您是提交代码、完善文档还是反馈问题，都请遵循以下流程。

1. 查阅问题跟踪器：访问 GitHub Issues 页面，查找标记为 good-first-issue 或 help-wanted 的待办事项，避免重复工作。
2. 派生仓库并创建特性分支：从主分支派生个人副本，新建分支命名格式为 feature/简述改动内容，例如 feature/add-timeout-config。
3. 编写或更新测试用例：任何新增功能或修复均需提供对应的单元测试，确保测试覆盖率达到 80% 以上。
4. 提交拉取请求：在 PR 描述中详细说明改动目的、实现方式及测试结果，并关联相关的 Issue 编号。PR 需经过至少一名维护者审核。
5. 文档同步更新：若改动涉及用户可见功能或配置变更，必须同步更新 docs/ 目录下的对应文档，并补充 CHANGELOG 条目。

## 常见问题

Q：导入批次链接时，系统是否会立即检测所有链接的状态？

A：不会。导入操作仅将链接写入索引库，并记录批次信息。链接状态检测由 Celery 定时任务调度执行，默认每 24 小时运行一次全量检测。您也可以手动触发检测任务：python manage.py run_checker --batch batch_9_80。

Q：部分源站链接返回 403 或超时，是否会导致导入失败？

A：不会。导入阶段仅做 URL 格式校验与去重检查，不发起对外请求。链接可达性问题统一由状态检测阶段处理，并在报告中标注为异常。您可以根据报告决定是否保留或移除异常链接。

Q：如何迁移 LinkSphere 到新的服务器？

A：迁移需要同步传输数据库转储文件、批次存档目录以及 .env 配置文件。在新服务器上部署相同版本的代码与环境依赖后，执行 python manage.py loaddata links.json 恢复索引数据，并重新配置 Celery 定时任务即可。详细的迁移步骤请参考 docs/ops/migration.md。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
