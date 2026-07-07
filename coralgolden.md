# LinkVault Resource Aggregator

LinkVault is a curated, high-performance external resource aggregation and navigation system designed for developers, researchers, and content curators who need to manage, categorize, and distribute large volumes of unstructured web links. The project addresses the fundamental challenge of link rot, domain fragmentation, and manual cataloging by providing a lightweight, schema-agnostic ingestion pipeline that normalizes heterogeneous URL sources into a queryable, taggable, and exportable dataset. Target users include open-source documentation maintainers, data pipeline engineers, and academic reference collectors who routinely handle link collections exceeding 200 entries per batch.

The system implements a multi-threaded metadata fetcher, a deduplication engine based on normalized domain and path signatures, and a static site generator that renders the link corpus into a navigable HTML dashboard. LinkVault does not store full-page content but retains HTTP response headers, status codes, content-type declarations, and last-modified timestamps to enable automated health checks. The current release supports batch processing of up to 500 links per run, with incremental update capabilities for subsequent crawls. The project is written in Python 3.10+ and uses SQLite as the default storage backend, with optional PostgreSQL support for larger deployments.

## 功能概览

- **Bulk URL Ingestion Pipeline** – Accepts plain-text lists, CSV exports, and markdown-embedded URLs; performs automatic protocol normalization and trailing-slash removal while preserving the original URL string for display purposes.
- **Domain-Signature Deduplication** – Computes a SHA-256 fingerprint for each URL based on the registered domain, path depth, and query parameter keys to identify near-duplicates without full string matching.
- **Health Status Probing** – Issues conditional GET requests with configurable timeouts and user-agent rotation; records HTTP status codes, response times, and content-length values for each resource.
- **Tag-Based Classification Engine** – Allows users to attach hierarchical tags (e.g., "docs/api", "tutorials/networking", "references/security") to individual entries via a CLI interactive mode or a YAML batch mapping file.
- **Static Site Compiler** – Generates a responsive HTML index page with client-side filtering, search-by-domain, and sort-by-status columns; outputs zero-dependency CSS and JavaScript bundles.
- **Export Adapters** – Supports JSON, CSV, and markdown-table export formats; includes a GitHub-Flavored Markdown (GFM) renderer that produces the exact list format shown in this README.
- **Batch Lifecycle Management** – Tracks each import batch with a unique batch ID, timestamp, source file checksum, and total count; enables rollback or re-import of previous batches.
- **Periodic Refresh Scheduler** – Integrates with cron or systemd timers to automatically re-probe all stored URLs at defined intervals and log status changes.

## 应用场景

- **Open-Source Documentation Maintenance** – A project maintainer receives a list of 250 reference links from community contributors. LinkVault ingests the list, filters out broken or redirected URLs, and generates a "resources.md" file that is committed directly to the docs folder of the project repository. The health check ensures that only active references are published in the next release.
- **Academic Literature Aggregation** – A research assistant collects 200+ supplementary material URLs from conference proceedings. LinkVault tags each entry by research track (e.g., NLP, computer vision, robotics), exports a CSV for import into Zotero, and produces a static HTML page for internal lab sharing without requiring a database server.
- **Data Pipeline Sanity Testing** – A data engineer maintains a configuration file that references external schema registries and API endpoint documentation. LinkVault runs as a pre-deployment hook to validate that all external URIs are resolvable and return the expected content-type before the application container starts.
- **Content Migration Audit** – A website migration team needs to verify that 300+ legacy article URLs from an old domain (mobile.xqnqq.com) redirect correctly to new domain paths. LinkVault captures the redirect chain and generates a redirect-map report that highlights non-200 responses and circular references.
- **Personal Bookmark Hygiene** – An individual user with years of accumulated browser bookmarks exports them as HTML, passes the file through LinkVault, and receives a cleaned, deduplicated, and categorized markdown list that can be published as a personal knowledge-base index.

## 快速开始

```bash
# Clone the repository from the upstream source
git clone https://github.com/your-org/linkvault.git
cd linkvault

# Create a virtual environment and install dependencies
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install --upgrade pip
pip install -r requirements.txt

# Run the initial ingestion with a sample link list
python linkvault.py ingest --input samples/links_80.txt --batch-id 5 --format plain

# Generate the static HTML dashboard
python linkvault.py compile --batch 5 --output docs/index.html

# Start the local development server to preview the dashboard
python -m http.server 8000 --directory docs
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|----------|----------|------|
| Python | 3.10.0 或更高 | 核心运行时；类型提示与模式匹配特性依赖 3.10+ |
| SQLite | 3.35.0 或更高 | 内置存储引擎；支持 JSON 扩展和 R*Tree 索引优化 |
| requests | 2.28.0 或更高 | HTTP 会话管理与连接池；处理重定向和超时重试策略 |
| pyyaml | 6.0 或更高 | 解析 YAML 格式的标签映射文件和批量配置清单 |
| beautifulsoup4 | 4.11.0 或更高 | 可选依赖；用于从 HTML 页面中提取标题和元描述作为预览摘要 |
| lxml | 4.9.0 或更高 | XML/HTML 解析加速器；与 beautifulsoup4 配合使用时提升性能 |
| pytest | 7.2.0 或更高 | 开发依赖；运行单元测试与集成测试套件 |
| black | 22.10.0 或更高 | 开发依赖；代码格式化工具，保持提交风格一致 |
| pre-commit | 2.20.0 或更高 | 开发依赖；Git 提交钩子管理器，自动执行 lint 与格式检查 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user-guide/ingestion.md | 如何准备输入文件？支持哪些格式？如何处理编码问题？批量导入的并发参数如何调整？ |
| 用户手册 | docs/user-guide/tagging.md | 标签系统的命名规范是什么？如何批量应用标签？标签能否嵌套或继承？ |
| 运维参考 | docs/operations/health-checks.md | 健康探测的默认超时和重试次数是多少？如何自定义 User-Agent？日志存储在什么位置？ |
| 运维参考 | docs/operations/export-formats.md | 导出文件的字段映射关系是什么？JSON 和 CSV 的 schema 是否稳定？如何集成到 CI/CD 管道？ |
| 开发者指南 | docs/development/architecture.md | 数据流在各模块之间如何传递？存储层的抽象接口如何扩展？新增导出格式需要实现哪些方法？ |
| 开发者指南 | docs/development/testing.md | 如何模拟外部 HTTP 服务进行单元测试？测试覆盖率要求是多少？如何为新增功能编写集成测试？ |
| 运维参考 | docs/operations/scheduling.md | 如何配置 systemd timer 或 cron job 实现自动刷新？刷新结果如何通知管理员？ |

## 资源列表

- http://www.mobile.xqnqq.com/Article/147082.shtml
- http://www.read.usuhx.com/Article/464370.shtml
- http://www.mobile.xqnqq.com/Article/73735.shtml
- http://www.read.usuhx.com/Article/3540.shtml
- http://www.read.usuhx.com/Article/000352.shtml
- http://www.mobile.xqnqq.com/Article/98129.shtml
- http://www.read.usuhx.com/Article/917960.shtml
- http://www.mobile.xqnqq.com/Article/40945.shtml
- http://www.read.usuhx.com/Article/645322.shtml
- http://www.read.usuhx.com/Article/651946.shtml
- http://www.read.usuhx.com/Article/28471.shtml
- http://www.mobile.xqnqq.com/Article/654755.shtml
- http://www.mobile.xqnqq.com/Article/35084.shtml
- http://www.mobile.xqnqq.com/Article/6615820.shtml
- http://www.read.usuhx.com/Article/28811.shtml
- http://www.read.usuhx.com/Article/7039.shtml
- http://www.read.usuhx.com/Article/92857.shtml
- http://www.read.usuhx.com/Article/5843.shtml
- http://www.read.usuhx.com/Article/99881.shtml
- http://www.mobile.xqnqq.com/Article/8601560.shtml
- http://www.read.usuhx.com/Article/10250.shtml
- http://www.read.usuhx.com/Article/98194.shtml
- http://www.read.usuhx.com/Article/385299.shtml
- http://www.mobile.xqnqq.com/Article/7695.shtml
- http://www.mobile.xqnqq.com/Article/17365.shtml
- http://www.read.usuhx.com/Article/6054821.shtml
- http://www.read.usuhx.com/Article/13999.shtml
- http://www.mobile.xqnqq.com/Article/245755.shtml
- http://www.read.usuhx.com/Article/2359.shtml
- http://www.mobile.xqnqq.com/Article/771117.shtml
- http://www.mobile.xqnqq.com/Article/7966.shtml
- http://www.mobile.xqnqq.com/Article/157312.shtml
- http://www.read.usuhx.com/Article/3460136.shtml
- http://www.read.usuhx.com/Article/375265.shtml
- http://www.mobile.xqnqq.com/Article/7007.shtml
- http://www.mobile.xqnqq.com/Article/40265.shtml
- http://www.mobile.xqnqq.com/Article/1660711.shtml
- http://www.read.usuhx.com/Article/5532.shtml
- http://www.mobile.xqnqq.com/Article/824758.shtml
- http://www.read.usuhx.com/Article/63574.shtml
- http://www.mobile.xqnqq.com/Article/5794410.shtml
- http://www.read.usuhx.com/Article/25820.shtml
- http://www.read.usuhx.com/Article/20286.shtml
- http://www.mobile.xqnqq.com/Article/3485517.shtml
- http://www.read.usuhx.com/Article/7564609.shtml
- http://www.mobile.xqnqq.com/Article/168592.shtml
- http://www.mobile.xqnqq.com/Article/3011112.shtml
- http://www.read.usuhx.com/Article/3960.shtml
- http://www.read.usuhx.com/Article/6844.shtml
- http://www.read.usuhx.com/Article/46970.shtml
- http://www.mobile.xqnqq.com/Article/308070.shtml
- http://www.read.usuhx.com/Article/38737.shtml
- http://www.mobile.xqnqq.com/Article/4946.shtml
- http://www.read.usuhx.com/Article/76147.shtml
- http://www.read.usuhx.com/Article/6654.shtml
- http://www.read.usuhx.com/Article/8195.shtml
- http://www.read.usuhx.com/Article/2182.shtml
- http://www.read.usuhx.com/Article/603804.shtml
- http://www.mobile.xqnqq.com/Article/1916.shtml
- http://www.read.usuhx.com/Article/30625.shtml
- http://www.read.usuhx.com/Article/0700.shtml
- http://www.read.usuhx.com/Article/0707.shtml
- http://www.mobile.xqnqq.com/Article/076240.shtml
- http://www.mobile.xqnqq.com/Article/4250693.shtml
- http://www.read.usuhx.com/Article/24339.shtml
- http://www.mobile.xqnqq.com/Article/494716.shtml
- http://www.read.usuhx.com/Article/542584.shtml
- http://www.read.usuhx.com/Article/32431.shtml
- http://www.mobile.xqnqq.com/Article/647933.shtml
- http://www.mobile.xqnqq.com/Article/51330.shtml
- http://www.mobile.xqnqq.com/Article/7443248.shtml
- http://www.mobile.xqnqq.com/Article/0540.shtml
- http://www.read.usuhx.com/Article/7553.shtml
- http://www.mobile.xqnqq.com/Article/0412.shtml
- http://www.read.usuhx.com/Article/3963060.shtml
- http://www.mobile.xqnqq.com/Article/2341.shtml
- http://www.mobile.xqnqq.com/Article/9953062.shtml
- http://www.read.usuhx.com/Article/3403408.shtml
- http://www.read.usuhx.com/Article/0456518.shtml
- http://www.mobile.xqnqq.com/Article/63060.shtml
- http://www.mobile.xqnqq.com/Article/758958.shtml
- http://www.read.usuhx.com/Article/7288.shtml
- http://www.read.usuhx.com/Article/857849.shtml
- http://www.mobile.xqnqq.com/Article/36796.shtml
- http://www.mobile.xqnqq.com/Article/72909.shtml
- http://www.mobile.xqnqq.com/Article/54561.shtml
- http://www.mobile.xqnqq.com/Article/0752.shtml
- http://www.mobile.xqnqq.com/Article/026007.shtml
- http://www.mobile.xqnqq.com/Article/431210.shtml
- http://www.read.usuhx.com/Article/4520178.shtml
- http://www.mobile.xqnqq.com/Article/982178.shtml
- http://www.mobile.xqnqq.com/Article/6669882.shtml
- http://www.read.usuhx.com/Article/8787.shtml
- http://www.read.usuhx.com/Article/0215847.shtml
- http://www.mobile.xqnqq.com/Article/75488.shtml
- http://www.mobile.xqnqq.com/Article/299255.shtml
- http://www.read.usuhx.com/Article/3849650.shtml
- http://www.read.usuhx.com/Article/276064.shtml
- http://www.read.usuhx.com/Article/2394.shtml
- http://www.mobile.xqnqq.com/Article/14971.shtml
- http://www.read.usuhx.com/Article/2627.shtml
- http://www.mobile.xqnqq.com/Article/9856912.shtml
- http://www.read.usuhx.com/Article/1243273.shtml
- http://www.mobile.xqnqq.com/Article/1796.shtml
- http://www.mobile.xqnqq.com/Article/7825094.shtml
- http://www.read.usuhx.com/Article/81307.shtml
- http://www.read.usuhx.com/Article/7298925.shtml
- http://www.read.usuhx.com/Article/8495.shtml
- http://www.mobile.xqnqq.com/Article/6312.shtml
- http://www.mobile.xqnqq.com/Article/738595.shtml
- http://www.mobile.xqnqq.com/Article/4104857.shtml
- http://www.mobile.xqnqq.com/Article/28484.shtml
- http://www.read.usuhx.com/Article/4490096.shtml
- http://www.mobile.xqnqq.com/Article/68948.shtml
- http://www.mobile.xqnqq.com/Article/538420.shtml
- http://www.mobile.xqnqq.com/Article/116474.shtml
- http://www.mobile.xqnqq.com/Article/0375808.shtml
- http://www.read.usuhx.com/Article/8255802.shtml
- http://www.read.usuhx.com/Article/45298.shtml
- http://www.read.usuhx.com/Article/7681.shtml
- http://www.mobile.xqnqq.com/Article/4333.shtml
- http://www.read.usuhx.com/Article/66227.shtml
- http://www.read.usuhx.com/Article/1707.shtml
- http://www.read.usuhx.com/Article/49760.shtml
- http://www.read.usuhx.com/Article/878112.shtml
- http://www.read.usuhx.com/Article/249751.shtml
- http://www.read.usuhx.com/Article/8211.shtml
- http://www.read.usuhx.com/Article/897035.shtml
- http://www.read.usuhx.com/Article/7322541.shtml
- http://www.mobile.xqnqq.com/Article/16753.shtml
- http://www.mobile.xqnqq.com/Article/467713.shtml
- http://www.read.usuhx.com/Article/38719.shtml
- http://www.mobile.xqnqq.com/Article/3820.shtml
- http://www.mobile.xqnqq.com/Article/687508.shtml
- http://www.mobile.xqnqq.com/Article/28333.shtml
- http://www.read.usuhx.com/Article/168120.shtml
- http://www.read.usuhx.com/Article/665427.shtml
- http://www.read.usuhx.com/Article/9694842.shtml
- http://www.mobile.xqnqq.com/Article/11388.shtml
- http://www.read.usuhx.com/Article/03977.shtml
- http://www.mobile.xqnqq.com/Article/33644.shtml
- http://www.read.usuhx.com/Article/1954572.shtml
- http://www.mobile.xqnqq.com/Article/922355.shtml
- http://www.mobile.xqnqq.com/Article/5913.shtml
- http://www.mobile.xqnqq.com/Article/8648.shtml
- http://www.read.usuhx.com/Article/6371.shtml
- http://www.mobile.xqnqq.com/Article/4537.shtml
- http://www.mobile.xqnqq.com/Article/98407.shtml
- http://www.read.usuhx.com/Article/724342.shtml
- http://www.mobile.xqnqq.com/Article/57490.shtml
- http://www.read.usuhx.com/Article/591974.shtml
- http://www.mobile.xqnqq.com/Article/1014.shtml
- http://www.mobile.xqnqq.com/Article/3429.shtml
- http://www.mobile.xqnqq.com/Article/528984.shtml
- http://www.mobile.xqnqq.com/Article/88011.shtml
- http://www.read.usuhx.com/Article/152634.shtml
- http://www.read.usuhx.com/Article/1983.shtml
- http://www.mobile.xqnqq.com/Article/5001676.shtml
- http://www.read.usuhx.com/Article/11507.shtml
- http://www.mobile.xqnqq.com/Article/84575.shtml
- http://www.read.usuhx.com/Article/7094.shtml
- http://www.mobile.xqnqq.com/Article/2232839.shtml
- http://www.mobile.xqnqq.com/Article/1566297.shtml
- http://www.read.usuhx.com/Article/1592035.shtml
- http://www.read.usuhx.com/Article/2794488.shtml
- http://www.read.usuhx.com/Article/2601.shtml
- http://www.read.usuhx.com/Article/1564518.shtml
- http://www.mobile.xqnqq.com/Article/927556.shtml
- http://www.read.usuhx.com/Article/488215.shtml
- http://www.mobile.xqnqq.com/Article/00546.shtml
- http://www.read.usuhx.com/Article/7949.shtml
- http://www.read.usuhx.com/Article/663341.shtml
- http://www.mobile.xqnqq.com/Article/9920174.shtml
- http://www.mobile.xqnqq.com/Article/1534.shtml
- http://www.read.usuhx.com/Article/3898567.shtml
- http://www.read.usuhx.com/Article/6660.shtml
- http://www.mobile.xqnqq.com/Article/4050511.shtml
- http://www.read.usuhx.com/Article/5414.shtml
- http://www.mobile.xqnqq.com/Article/7334.shtml
- http://www.mobile.xqnqq.com/Article/212023.shtml
- http://www.read.usuhx.com/Article/3708425.shtml
- http://www.read.usuhx.com/Article/9030.shtml
- http://www.mobile.xqnqq.com/Article/788526.shtml
- http://www.read.usuhx.com/Article/368448.shtml
- http://www.read.usuhx.com/Article/46255.shtml
- http://www.mobile.xqnqq.com/Article/3634.shtml
- http://www.mobile.xqnqq.com/Article/1394.shtml
- http://www.read.usuhx.com/Article/797168.shtml
- http://www.mobile.xqnqq.com/Article/504868.shtml
- http://www.read.usuhx.com/Article/2308662.shtml
- http://www.read.usuhx.com/Article/8053.shtml
- http://www.mobile.xqnqq.com/Article/147642.shtml
- http://www.read.usuhx.com/Article/809796.shtml
- http://www.mobile.xqnqq.com/Article/0819.shtml
- http://www.read.usuhx.com/Article/2362438.shtml
- http://www.mobile.xqnqq.com/Article/0058.shtml
- http://www.mobile.xqnqq.com/Article/5671397.shtml
- http://www.mobile.xqnqq.com/Article/8548467.shtml
- http://www.read.usuhx.com/Article/60653.shtml
- http://www.read.usuhx.com/Article/814760.shtml
- http://www.mobile.xqnqq.com/Article/369211.shtml
- http://www.mobile.xqnqq.com/Article/931137.shtml
- http://www.mobile.xqnqq.com/Article/447351.shtml
- http://www.mobile.xqnqq.com/Article/98956.shtml
- http://www.read.usuhx.com/Article/877459.shtml
- http://www.mobile.xqnqq.com/Article/6293.shtml
- http://www.mobile.xqnqq.com/Article/6249030.shtml
- http://www.mobile.xqnqq.com/Article/61475.shtml
- http://www.read.usuhx.com/Article/3838.shtml
- http://www.read.usuhx.com/Article/256087.shtml
- http://www.mobile.xqnqq.com/Article/86815.shtml
- http://www.mobile.xqnqq.com/Article/77938.shtml
- http://www.mobile.xqnqq.com/Article/61483.shtml
- http://www.mobile.xqnqq.com/Article/5811.shtml
- http://www.read.usuhx.com/Article/740862.shtml
- http://www.mobile.xqnqq.com/Article/4908.shtml
- http://www.read.usuhx.com/Article/6553256.shtml
- http://www.read.usuhx.com/Article/1761137.shtml
- http://www.read.usuhx.com/Article/8446424.shtml
- http://www.mobile.xqnqq.com/Article/1618.shtml
- http://www.mobile.xqnqq.com/Article/5299186.shtml
- http://www.read.usuhx.com/Article/0931210.shtml
- http://www.mobile.xqnqq.com/Article/0678701.shtml
- http://www.mobile.xqnqq.com/Article/18991.shtml
- http://www.read.usuhx.com/Article/5344342.shtml
- http://www.mobile.xqnqq.com/Article/4820267.shtml
- http://www.read.usuhx.com/Article/3285.shtml
- http://www.read.usuhx.com/Article/2517.shtml
- http://www.read.usuhx.com/Article/939491.shtml
- http://www.read.usuhx.com/Article/4199723.shtml
- http://www.read.usuhx.com/Article/9806.shtml
- http://www.mobile.xqnqq.com/Article/67317.shtml
- http://www.mobile.xqnqq.com/Article/2128.shtml
- http://www.mobile.xqnqq.com/Article/0519985.shtml
- http://www.read.usuhx.com/Article/7669.shtml
- http://www.mobile.xqnqq.com/Article/054668.shtml
- http://www.read.usuhx.com/Article/052637.shtml
- http://www.read.usuhx.com/Article/104177.shtml
- http://www.read.usuhx.com/Article/9725922.shtml
- http://www.mobile.xqnqq.com/Article/7927353.shtml
- http://www.mobile.xqnqq.com/Article/0415.shtml
- http://www.mobile.xqnqq.com/Article/31849.shtml
- http://www.mobile.xqnqq.com/Article/34141.shtml
- http://www.read.usuhx.com/Article/4214461.shtml
- http://www.read.usuhx.com/Article/2607823.shtml
- http://www.read.usuhx.com/Article/9012.shtml
- http://www.mobile.xqnqq.com/Article/8641521.shtml
- http://www.read.usuhx.com/Article/9237.shtml
- http://www.read.usuhx.com/Article/508439.shtml
- http://www.read.usuhx.com/Article/21388.shtml

## 项目结构

```
linkvault/
├── src/                                 # 核心应用包
│   ├── core/                           # 数据模型与存储抽象层
│   │   ├── models.py                  # SQLAlchemy ORM 定义：Batch, Resource, Tag, ProbeHistory
│   │   ├── database.py                # 连接池管理，迁移脚本入口，会话生命周期控制
│   │   └── repository.py              # 仓储模式实现：增删改查与批量 upsert 操作
│   ├── ingestion/                      # 导入管道模块
│   │   ├── parser.py                  # 文本解析器：自动识别纯文本、CSV、HTML 中的 URL 提取
│   │   ├── normalizer.py              # URL 规范化：去除片段标识、排序查询参数、生成指纹
│   │   └── loader.py                  # 并发加载器：使用 ThreadPoolExecutor 实现可配置并发度
│   ├── probe/                          # 健康探测引擎
│   │   ├── client.py                  # 封装 requests.Session，配置重试策略与超时参数
│   │   ├── checker.py                 # 逐个执行探测任务，记录状态码、响应头、elapsed 时间
│   │   └── scheduler.py               # APScheduler 集成，支持 interval 和 cron 触发器
│   ├── compiler/                       # 静态站点生成器
│   │   ├── renderer.py                # Jinja2 模板渲染器，加载 HTML 布局与 CSS 变量
│   │   ├── exporter.py                # 导出适配器：JSON, CSV, GFM 三种格式的具体实现
│   │   └── assets/                    # 前端资源文件（CSS 样式表，JavaScript 过滤逻辑）
│   │       ├── style.css
│   │       └── filter.js
│   ├── cli/                            # 命令行接口命令定义
│   │   ├── main.py                    # Click 应用入口，注册子命令组
│   │   ├── ingest_cmd.py              # 处理 ingest 子命令的参数解析与流程编排
│   │   └── compile_cmd.py             # 处理 compile 与 export 子命令
│   └── utils/                          # 通用工具函数
│       ├── logging.py                 # 日志配置：按级别输出到控制台与文件轮转
│       ├── validators.py              # URL 格式校验，域名黑名单过滤
│       └── file_helpers.py            # 文件读写辅助，确保目录存在与权限检查
├── tests/                              # 测试套件
│   ├── unit/                          # 单元测试，覆盖 models, normalizer, checker
│   ├── integration/                   # 集成测试，使用临时 SQLite 数据库与模拟 HTTP 服务
│   └── fixtures/                      # 测试数据：示例输入文件与预期输出结果
├── docs/                               # 用户手册与 API 参考
│   ├── user-guide/                    # 面向最终用户的操作指引
│   └── development/                   # 面向贡献者的架构说明与编码规范
├── scripts/                            # 运维辅助脚本
│   ├── backup_db.sh                   # 定时备份 SQLite 文件到指定目录
│   └── migration_generate.py          # 自动生成 Alembic 迁移脚本
├── config/                             # 配置文件模板
│   ├── default.yaml                   # 默认参数：并发数、超时阈值、重试策略
│   └── production.yaml                # 生产环境覆盖配置，含 PostgreSQL 连接串
├── requirements.txt                    # 运行时依赖清单，固定版本范围
├── pyproject.toml                      # 项目元数据，构建配置与 black/isort 设置
└── README.md                           # 本文件
```

## 贡献指南

1. 阅读开发者指南中的架构概述和编码规范文档（位于 docs/development/architecture.md），了解模块边界、依赖注入模式以及异常处理约定。所有新增功能需保持与现有抽象层的一致性。

2. 在 GitHub 仓库中创建一个新的 issue 描述您希望修复的问题或新增的功能，等待维护者确认后再开始编码，以避免重复劳动或偏离项目路线图。对于简单文档修正，可直接提交拉取请求。

3. 克隆代码库，创建以功能名称命名的分支（例如 feature/add-export-format）。确保本地环境中已安装 pre-commit 钩子，以便提交时自动运行 black 格式化、isort 导入排序和 flake8 静态检查。

4. 编写或更新对应的单元测试和集成测试，确保代码覆盖率不低于当前主干分支的基准值（当前为 92%）。所有测试必须通过 `pytest tests/` 命令完整运行，且不产生警告或跳过项。

5. 提交拉取请求时，请在描述中引用关联的 issue 编号，并附上手动测试的截图或命令行输出日志。维护者将在 5 个工作日内进行审查，可能需要您根据反馈进行修改。合并后您的贡献将被列入下一版本的发布说明。

## 常见问题

**问：LinkVault 是否会存储被引用页面的完整 HTML 内容？是否会侵犯版权？**

答：LinkVault 默认仅存储 HTTP 响应元数据（状态码、内容类型、内容长度、最后修改时间戳）以及用户手动添加的标签和备注。系统不会自动爬取或存储页面正文内容。用户可以选择启用可选的标题提取功能，该功能仅解析 HTML 的 title 标签，不保存 DOM 树或任何文本内容。关于版权合规性，建议用户在导入外部链接时遵守目标网站的 robots.txt 规则，并合理设置请求间隔。

**问：如何处理导入列表中包含重复 URL 或同一资源的不同变体？**

答：系统在导入阶段会执行两级去重策略。第一级是精确字符串匹配，直接剔除完全相同的 URL。第二级是规范化指纹去重，系统会提取注册域名、路径深度和查询参数键的排序组合，计算 SHA-256 指纹，若指纹重复则保留首次出现的条目，并在日志中记录后续重复项的位置和重定向关系。用户可以通过 `--dedup strict` 或 `--dedup loose` 参数调整去重灵敏度。

**问：静态生成的 HTML 页面能否支持离线浏览？链接点击后是否会造成跨域问题？**

答：生成的 HTML 页面是完全自包含的，所有 CSS 和 JavaScript 都内联在单个文件中，不依赖任何外部 CDN 资源，因此可以在本地文件系统或内网环境中直接打开。页面中的链接使用标准的 `<a href="...">` 标签，点击后会在当前窗口或新标签页（由用户浏览器设置决定）打开原始目标 URL，不经过任何中间代理或重定向服务，因此不会引入跨域脚本问题。由于页面是静态的，搜索和过滤功能完全在客户端内存中执行，不发送任何数据到外部服务器。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
