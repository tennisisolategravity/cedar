# WebIndex 聚合导航

WebIndex 是一个面向技术调研、内容聚合与知识归档场景的轻量级外链资源汇总平台。该项目定位于为开发者、技术作者、数据分析师以及信息整理人员提供一套结构清晰、可扩展的 URL 资源管理方案，用于集中存储、分类展示和快速检索分散于多个内容源的文章链接。WebIndex 本身不存储任何正文内容，仅维护 URL 索引与元信息，通过目录化结构与纯文本可读性降低信息过载，提升跨源资料的复用效率。

## 功能概览

- **分级目录索引**：支持按领域、批次、来源域名等多维度对链接进行树状归类，便于按上下文查阅。
- **原始链接直出**：所有收录的 URL 均保持原始格式输出，不附加协议转换、域名规范化或追踪参数，确保引用路径的精确性。
- **批量导入与去重**：提供基于文本行的批量链接导入接口，自动识别重复条目并生成导入报告。
- **结构化元数据标注**：每条链接可附带来源域名、文章标识符、收录时间与自定义标签，支持后续过滤与排序。
- **静态站点生成适配**：项目输出为纯 Markdown 与静态 HTML，无需数据库或后端运行时，可无缝集成至 GitHub Pages、Vercel 或任何 Web 服务器。
- **多批次分档管理**：内置批次管理机制，当前为第 14/80 批次，支持批次切换与增量追加，便于长期维护大规模链接库。
- **全文检索接口**：提供基于域名和文章 ID 的模糊查询能力，支持在本地开发环境中快速定位特定资源。

## 应用场景

- **技术调研与文献归档**：研究人员在阅读技术博客、论文或新闻时，可将散落的 URL 统一收录至 WebIndex，按主题批次分类，后续撰写综述或报告时可直接引用目录结构。
- **内容聚合与 newsletter 素材库**：内容创作者可定期将各平台（如移动端资讯站、技术社区）的优质文章链接集中存放，作为周报或专题汇编的原始素材池。
- **团队知识库外链管理**：团队可将项目相关的参考资料、竞品分析、技术规范等外链通过 WebIndex 统一维护，避免浏览器书签散乱和链接失效问题，新成员可通过目录快速了解背景资料。
- **数据源追溯与审计**：数据分析师在处理第三方数据时，可将数据来源 URL 按批次录入，便于后续审计、复现或更新数据时快速回溯原始发布页。

## 快速开始

以下命令适用于 Linux / macOS / Windows（WSL 或 Git Bash）环境。

```bash
# 克隆仓库
git clone https://github.com/your-org/webindex.git
cd webindex

# 安装依赖（使用 Python 3.9+ 和 pip）
python -m venv venv
source venv/bin/activate      # Windows 请使用 venv\Scripts\activate
pip install -r requirements.txt

# 运行本地开发服务器
python app.py --port 8080
```

访问 `http://127.0.0.1:8080` 即可查看当前批次的链接列表与目录导航。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.9 - 3.12 | 核心运行环境，用于解析链接与生成静态页 |
| pip | 21.0+ | Python 包管理工具，用于安装依赖库 |
| Markdown | 3.4+ | 将 .md 源文件渲染为 HTML 内容 |
| Jinja2 | 3.1+ | 模板引擎，用于生成动态目录和分页 |
| click | 8.1+ | 命令行交互框架，支持导入、校验等管理命令 |
| watchdog | 3.0+ | 可选依赖，用于开发模式下的文件监视自动刷新 |
| Git | 2.30+ | 版本控制，用于克隆仓库和提交更新 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | /docs/user-guide.md | 如何添加链接、管理批次、生成静态站点？ |
| 管理员指南 | /docs/admin.md | 如何配置域名白名单、处理失效链接、备份索引？ |
| 开发者文档 | /docs/developer.md | 如何扩展元数据字段、自定义模板、编写插件？ |
| API 参考 | /docs/api.md | 本地开发服务器提供了哪些内部接口？如何通过脚本批量导入？ |
| 设计说明 | /docs/design.md | 链接去重策略、批次编号规则、目录树结构的设计依据是什么？ |

## 资源列表

- http://www.mobile.xqnqq.com/Article/3925.shtml
- http://www.read.usuhx.com/Article/642729.shtml
- http://www.read.usuhx.com/Article/8137721.shtml
- http://www.read.usuhx.com/Article/3377343.shtml
- http://www.read.usuhx.com/Article/9549.shtml
- http://www.read.usuhx.com/Article/6320260.shtml
- http://www.read.usuhx.com/Article/53838.shtml
- http://www.mobile.xqnqq.com/Article/62119.shtml
- http://www.mobile.xqnqq.com/Article/18340.shtml
- http://www.mobile.xqnqq.com/Article/1027.shtml
- http://www.read.usuhx.com/Article/04404.shtml
- http://www.mobile.xqnqq.com/Article/3282408.shtml
- http://www.read.usuhx.com/Article/7755327.shtml
- http://www.read.usuhx.com/Article/472744.shtml
- http://www.read.usuhx.com/Article/11229.shtml
- http://www.mobile.xqnqq.com/Article/46094.shtml
- http://www.read.usuhx.com/Article/5419245.shtml
- http://www.mobile.xqnqq.com/Article/546183.shtml
- http://www.mobile.xqnqq.com/Article/1851.shtml
- http://www.read.usuhx.com/Article/58051.shtml
- http://www.read.usuhx.com/Article/984479.shtml
- http://www.read.usuhx.com/Article/8878.shtml
- http://www.mobile.xqnqq.com/Article/6860.shtml
- http://www.read.usuhx.com/Article/5566.shtml
- http://www.mobile.xqnqq.com/Article/26177.shtml
- http://www.mobile.xqnqq.com/Article/711534.shtml
- http://www.mobile.xqnqq.com/Article/14731.shtml
- http://www.mobile.xqnqq.com/Article/89210.shtml
- http://www.read.usuhx.com/Article/88086.shtml
- http://www.read.usuhx.com/Article/03134.shtml
- http://www.mobile.xqnqq.com/Article/5004.shtml
- http://www.mobile.xqnqq.com/Article/93140.shtml
- http://www.mobile.xqnqq.com/Article/7275.shtml
- http://www.read.usuhx.com/Article/01295.shtml
- http://www.mobile.xqnqq.com/Article/0629719.shtml
- http://www.mobile.xqnqq.com/Article/44893.shtml
- http://www.mobile.xqnqq.com/Article/5344.shtml
- http://www.mobile.xqnqq.com/Article/199451.shtml
- http://www.read.usuhx.com/Article/325264.shtml
- http://www.mobile.xqnqq.com/Article/657713.shtml
- http://www.mobile.xqnqq.com/Article/030507.shtml
- http://www.mobile.xqnqq.com/Article/4030.shtml
- http://www.read.usuhx.com/Article/60178.shtml
- http://www.mobile.xqnqq.com/Article/84448.shtml
- http://www.read.usuhx.com/Article/638498.shtml
- http://www.read.usuhx.com/Article/081922.shtml
- http://www.mobile.xqnqq.com/Article/95635.shtml
- http://www.read.usuhx.com/Article/8311589.shtml
- http://www.mobile.xqnqq.com/Article/2532263.shtml
- http://www.read.usuhx.com/Article/788056.shtml
- http://www.read.usuhx.com/Article/210463.shtml
- http://www.read.usuhx.com/Article/940850.shtml
- http://www.read.usuhx.com/Article/47804.shtml
- http://www.read.usuhx.com/Article/7483.shtml
- http://www.read.usuhx.com/Article/2428866.shtml
- http://www.mobile.xqnqq.com/Article/345763.shtml
- http://www.read.usuhx.com/Article/657205.shtml
- http://www.read.usuhx.com/Article/2824693.shtml
- http://www.read.usuhx.com/Article/31630.shtml
- http://www.read.usuhx.com/Article/717527.shtml
- http://www.mobile.xqnqq.com/Article/7384.shtml
- http://www.mobile.xqnqq.com/Article/1894.shtml
- http://www.mobile.xqnqq.com/Article/4913.shtml
- http://www.mobile.xqnqq.com/Article/2987.shtml
- http://www.read.usuhx.com/Article/173136.shtml
- http://www.mobile.xqnqq.com/Article/730052.shtml
- http://www.read.usuhx.com/Article/679246.shtml
- http://www.read.usuhx.com/Article/1622602.shtml
- http://www.read.usuhx.com/Article/58372.shtml
- http://www.read.usuhx.com/Article/891720.shtml
- http://www.read.usuhx.com/Article/708052.shtml
- http://www.mobile.xqnqq.com/Article/244054.shtml
- http://www.read.usuhx.com/Article/8743563.shtml
- http://www.read.usuhx.com/Article/6369316.shtml
- http://www.mobile.xqnqq.com/Article/179797.shtml
- http://www.read.usuhx.com/Article/9990232.shtml
- http://www.read.usuhx.com/Article/40746.shtml
- http://www.read.usuhx.com/Article/38457.shtml
- http://www.read.usuhx.com/Article/80731.shtml
- http://www.mobile.xqnqq.com/Article/26925.shtml
- http://www.mobile.xqnqq.com/Article/1142.shtml
- http://www.read.usuhx.com/Article/4747.shtml
- http://www.mobile.xqnqq.com/Article/125851.shtml
- http://www.read.usuhx.com/Article/5614949.shtml
- http://www.read.usuhx.com/Article/3173.shtml
- http://www.mobile.xqnqq.com/Article/09437.shtml
- http://www.mobile.xqnqq.com/Article/57439.shtml
- http://www.read.usuhx.com/Article/6972883.shtml
- http://www.read.usuhx.com/Article/22191.shtml
- http://www.mobile.xqnqq.com/Article/0118231.shtml
- http://www.mobile.xqnqq.com/Article/8677897.shtml
- http://www.mobile.xqnqq.com/Article/2146019.shtml
- http://www.mobile.xqnqq.com/Article/86281.shtml
- http://www.mobile.xqnqq.com/Article/27833.shtml
- http://www.read.usuhx.com/Article/681558.shtml
- http://www.read.usuhx.com/Article/015858.shtml
- http://www.read.usuhx.com/Article/562537.shtml
- http://www.mobile.xqnqq.com/Article/86285.shtml
- http://www.read.usuhx.com/Article/374976.shtml
- http://www.mobile.xqnqq.com/Article/6944076.shtml
- http://www.read.usuhx.com/Article/414873.shtml
- http://www.mobile.xqnqq.com/Article/7666734.shtml
- http://www.read.usuhx.com/Article/7834.shtml
- http://www.mobile.xqnqq.com/Article/8640903.shtml
- http://www.mobile.xqnqq.com/Article/4404.shtml
- http://www.read.usuhx.com/Article/836635.shtml
- http://www.mobile.xqnqq.com/Article/3239226.shtml
- http://www.mobile.xqnqq.com/Article/812720.shtml
- http://www.read.usuhx.com/Article/2226038.shtml
- http://www.mobile.xqnqq.com/Article/0408053.shtml
- http://www.mobile.xqnqq.com/Article/42977.shtml
- http://www.mobile.xqnqq.com/Article/153149.shtml
- http://www.mobile.xqnqq.com/Article/32043.shtml
- http://www.mobile.xqnqq.com/Article/5948.shtml
- http://www.read.usuhx.com/Article/417580.shtml
- http://www.read.usuhx.com/Article/4111.shtml
- http://www.mobile.xqnqq.com/Article/253991.shtml
- http://www.mobile.xqnqq.com/Article/05914.shtml
- http://www.read.usuhx.com/Article/9742.shtml
- http://www.mobile.xqnqq.com/Article/52685.shtml
- http://www.read.usuhx.com/Article/5686873.shtml
- http://www.mobile.xqnqq.com/Article/29488.shtml
- http://www.read.usuhx.com/Article/796916.shtml
- http://www.read.usuhx.com/Article/6636200.shtml
- http://www.mobile.xqnqq.com/Article/8859.shtml
- http://www.read.usuhx.com/Article/255287.shtml
- http://www.mobile.xqnqq.com/Article/6744.shtml
- http://www.read.usuhx.com/Article/5810618.shtml
- http://www.read.usuhx.com/Article/9545776.shtml
- http://www.read.usuhx.com/Article/3792713.shtml
- http://www.mobile.xqnqq.com/Article/6946.shtml
- http://www.mobile.xqnqq.com/Article/3272650.shtml
- http://www.read.usuhx.com/Article/649753.shtml
- http://www.mobile.xqnqq.com/Article/410932.shtml
- http://www.read.usuhx.com/Article/10008.shtml
- http://www.read.usuhx.com/Article/340198.shtml
- http://www.mobile.xqnqq.com/Article/9836.shtml
- http://www.mobile.xqnqq.com/Article/5642975.shtml
- http://www.mobile.xqnqq.com/Article/788903.shtml
- http://www.mobile.xqnqq.com/Article/109407.shtml
- http://www.read.usuhx.com/Article/957188.shtml
- http://www.mobile.xqnqq.com/Article/7037.shtml
- http://www.mobile.xqnqq.com/Article/73659.shtml
- http://www.mobile.xqnqq.com/Article/2051.shtml
- http://www.read.usuhx.com/Article/99060.shtml
- http://www.mobile.xqnqq.com/Article/8330.shtml
- http://www.read.usuhx.com/Article/39258.shtml
- http://www.read.usuhx.com/Article/0789515.shtml
- http://www.mobile.xqnqq.com/Article/056733.shtml
- http://www.read.usuhx.com/Article/3595515.shtml
- http://www.read.usuhx.com/Article/7257967.shtml
- http://www.read.usuhx.com/Article/1256.shtml
- http://www.read.usuhx.com/Article/728632.shtml
- http://www.read.usuhx.com/Article/6825.shtml
- http://www.mobile.xqnqq.com/Article/4356.shtml
- http://www.read.usuhx.com/Article/514087.shtml
- http://www.read.usuhx.com/Article/9271.shtml
- http://www.mobile.xqnqq.com/Article/641759.shtml
- http://www.read.usuhx.com/Article/27836.shtml
- http://www.mobile.xqnqq.com/Article/64693.shtml
- http://www.read.usuhx.com/Article/9481815.shtml
- http://www.read.usuhx.com/Article/221867.shtml
- http://www.mobile.xqnqq.com/Article/3098.shtml
- http://www.read.usuhx.com/Article/30440.shtml
- http://www.read.usuhx.com/Article/874820.shtml
- http://www.read.usuhx.com/Article/12955.shtml
- http://www.mobile.xqnqq.com/Article/410589.shtml
- http://www.read.usuhx.com/Article/8745.shtml
- http://www.read.usuhx.com/Article/9068.shtml
- http://www.mobile.xqnqq.com/Article/2404.shtml
- http://www.read.usuhx.com/Article/296639.shtml
- http://www.read.usuhx.com/Article/0150077.shtml
- http://www.read.usuhx.com/Article/8246332.shtml
- http://www.mobile.xqnqq.com/Article/8878999.shtml
- http://www.read.usuhx.com/Article/0958571.shtml
- http://www.mobile.xqnqq.com/Article/5274.shtml
- http://www.read.usuhx.com/Article/1074.shtml
- http://www.mobile.xqnqq.com/Article/45700.shtml
- http://www.mobile.xqnqq.com/Article/47479.shtml
- http://www.read.usuhx.com/Article/810800.shtml
- http://www.mobile.xqnqq.com/Article/8409488.shtml
- http://www.read.usuhx.com/Article/2554.shtml
- http://www.read.usuhx.com/Article/13415.shtml
- http://www.read.usuhx.com/Article/501880.shtml
- http://www.mobile.xqnqq.com/Article/1144361.shtml
- http://www.read.usuhx.com/Article/6730984.shtml
- http://www.mobile.xqnqq.com/Article/2933.shtml
- http://www.read.usuhx.com/Article/3048741.shtml
- http://www.mobile.xqnqq.com/Article/2010.shtml
- http://www.mobile.xqnqq.com/Article/67110.shtml
- http://www.mobile.xqnqq.com/Article/5333.shtml
- http://www.read.usuhx.com/Article/72386.shtml
- http://www.mobile.xqnqq.com/Article/609423.shtml
- http://www.read.usuhx.com/Article/0328.shtml
- http://www.read.usuhx.com/Article/51327.shtml
- http://www.read.usuhx.com/Article/2136924.shtml
- http://www.read.usuhx.com/Article/4470.shtml
- http://www.mobile.xqnqq.com/Article/28206.shtml
- http://www.mobile.xqnqq.com/Article/8148.shtml
- http://www.mobile.xqnqq.com/Article/52113.shtml
- http://www.mobile.xqnqq.com/Article/637917.shtml
- http://www.read.usuhx.com/Article/599947.shtml
- http://www.mobile.xqnqq.com/Article/92879.shtml
- http://www.read.usuhx.com/Article/9307.shtml
- http://www.mobile.xqnqq.com/Article/20901.shtml
- http://www.mobile.xqnqq.com/Article/8414.shtml
- http://www.mobile.xqnqq.com/Article/6973.shtml
- http://www.read.usuhx.com/Article/26231.shtml
- http://www.mobile.xqnqq.com/Article/16267.shtml
- http://www.mobile.xqnqq.com/Article/3944.shtml
- http://www.read.usuhx.com/Article/33538.shtml
- http://www.mobile.xqnqq.com/Article/1244.shtml
- http://www.mobile.xqnqq.com/Article/75753.shtml
- http://www.mobile.xqnqq.com/Article/0275130.shtml
- http://www.mobile.xqnqq.com/Article/405311.shtml
- http://www.mobile.xqnqq.com/Article/13894.shtml
- http://www.read.usuhx.com/Article/927894.shtml
- http://www.read.usuhx.com/Article/18036.shtml
- http://www.mobile.xqnqq.com/Article/158460.shtml
- http://www.read.usuhx.com/Article/8463821.shtml
- http://www.mobile.xqnqq.com/Article/72294.shtml
- http://www.mobile.xqnqq.com/Article/56762.shtml
- http://www.read.usuhx.com/Article/9575.shtml
- http://www.read.usuhx.com/Article/2813836.shtml
- http://www.mobile.xqnqq.com/Article/5388959.shtml
- http://www.mobile.xqnqq.com/Article/92510.shtml
- http://www.read.usuhx.com/Article/387990.shtml
- http://www.mobile.xqnqq.com/Article/7445.shtml
- http://www.mobile.xqnqq.com/Article/57503.shtml
- http://www.mobile.xqnqq.com/Article/470549.shtml
- http://www.read.usuhx.com/Article/238569.shtml
- http://www.mobile.xqnqq.com/Article/9361.shtml
- http://www.mobile.xqnqq.com/Article/7643.shtml
- http://www.read.usuhx.com/Article/9488585.shtml
- http://www.mobile.xqnqq.com/Article/8400.shtml
- http://www.read.usuhx.com/Article/577746.shtml
- http://www.mobile.xqnqq.com/Article/304620.shtml
- http://www.read.usuhx.com/Article/025855.shtml
- http://www.read.usuhx.com/Article/19194.shtml
- http://www.mobile.xqnqq.com/Article/9892.shtml
- http://www.read.usuhx.com/Article/5887.shtml
- http://www.mobile.xqnqq.com/Article/31299.shtml
- http://www.read.usuhx.com/Article/1359.shtml
- http://www.mobile.xqnqq.com/Article/9826216.shtml
- http://www.read.usuhx.com/Article/7160.shtml
- http://www.mobile.xqnqq.com/Article/505353.shtml
- http://www.read.usuhx.com/Article/4623244.shtml
- http://www.read.usuhx.com/Article/1718972.shtml
- http://www.read.usuhx.com/Article/8415.shtml
- http://www.read.usuhx.com/Article/0520685.shtml

## 项目结构

```
webindex/
├── app.py                      # 开发服务器入口，提供路由与模板渲染
├── requirements.txt            # Python 依赖清单
├── config.yaml                 # 站点配置：端口、批次号、域名白名单等
├── manager.py                  # 命令行管理工具：导入、去重、校验
├── data/
│   ├── batches/                # 各批次数据目录
│   │   ├── batch_14/           # 当前批次（第14批）
│   │   │   ├── links.txt       # 纯文本链接列表，一行一个URL
│   │   │   └── metadata.json   # 批次元信息（收录时间、来源统计）
│   │   └── batch_13/           # 历史批次（归档）
│   └── index.db                # SQLite 本地索引（用于快速检索）
├── docs/
│   ├── user-guide.md           # 用户手册
│   ├── admin.md                # 管理员指南
│   ├── developer.md            # 开发者文档
│   ├── api.md                  # 本地接口参考
│   └── design.md               # 设计说明
├── templates/
│   ├── base.html               # 基础 HTML 模板
│   ├── index.html              # 首页目录视图
│   └── batch.html              # 单批次详情视图
├── static/
│   ├── style.css               # 默认样式表
│   └── script.js               # 前端检索与过滤逻辑
├── tests/
│   ├── test_import.py          # 导入功能单元测试
│   └── test_dedup.py           # 去重算法测试
└── README.md                   # 项目说明文档（本文件）
```

## 贡献指南

1. 复刻仓库至个人账号，并在本地创建功能分支（例如 `feat/batch-15-import`），确保分支命名语义化。
2. 在 `data/batches/` 下按批次格式添加新的链接文件或更新现有批次，保持每行一个 URL 的纯文本格式，并同步更新对应 `metadata.json` 中的统计字段。
3. 运行 `python manager.py validate` 校验新增链接的格式合法性（协议、域名、路径结构），运行 `python manager.py dedup` 确保无重复条目。
4. 为新增功能或修复编写对应的单元测试（位于 `tests/` 目录），确保测试覆盖率达到现有标准。
5. 提交 Pull Request 至主仓库的 `main` 分支，在 PR 描述中说明变更内容、影响范围以及测试结果，等待维护者审阅。

## 常见问题

**问：项目是否支持自动抓取链接标题或摘要？**  
答：当前版本不主动抓取任何外部页面内容，仅维护 URL 本身及其元数据。这是为了保持轻量、避免法律风险并保证运行速度。用户可通过自定义标签字段手动补充说明。

**问：如何迁移或备份已有的链接数据？**  
答：所有链接数据以纯文本和 JSON 格式存储在 `data/` 目录下，直接复制该目录即可完成完整迁移。建议定期使用 `manager.py export` 命令生成全量 CSV 导出作为额外备份。

**问：部署到生产环境时是否需要数据库？**  
答：不需要。WebIndex 默认使用文件系统存储和 SQLite 本地索引，无需额外部署数据库服务。对于大规模使用（超过 10 万条链接），可配置外部 MySQL/PostgreSQL，详情参见 `config.yaml` 中的注释。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
