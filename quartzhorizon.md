# WebLink Collective Asset Manager

WebLink Collective Asset Manager 是一个面向技术内容聚合与外部链接治理的开源工具集，专为需要批量管理、校验、分类和归档大量外链资源的开发团队与内容运营者设计。该项目不依赖任何第三方云服务，完全基于本地文件系统与静态分析逻辑运行，适合作为技术博客、文档站、导航站或知识库的后台链接管理模块。

项目定位为“链接即数据”，将每一条外部 URL 视为可结构化处理的资产条目，提供去重、失效检测、域名聚类、协议归一化校验、批量导入导出等核心能力。目标用户包括开源文档维护者、技术内容运营人员、爬虫数据清洗工程师以及个人知识管理爱好者。

第 27/80 批次包含 250 个待处理资源链接，本批次数据源主要覆盖 mobile.xqnqq.com 与 read.usuhx.com 两个域名下的文章类页面。项目内置针对此类内容站点的链路抽取与元数据解析适配器。

## 功能概览

**批量链接导入解析** 支持从文本文件、CSV 或直接粘贴的 URL 列表中批量解析链接，自动识别协议头与域名结构。

**域名与路径聚类分析** 对导入的链接按二级域名、路径深度、文件类型进行分组统计，输出结构化摘要报告。

**HTTP 状态码存活检测** 并发发起 HEAD 请求验证链接可访问性，支持自定义超时与重试策略，标记异常链接。

**协议与格式归一化校验** 自动检测混合协议（http/https）及大小写不一致问题，生成归一化建议清单。

**黑名单与白名单过滤** 允许用户定义域名或路径正则规则，批量筛除广告、追踪或内部测试链接。

**标签化分类管理** 为每条链接添加自定义标签（如“文档”“博客”“API 参考”），支持多标签组合筛选。

**增量更新与批次追踪** 记录每批次导入的时间戳、来源与处理状态，支持多批次数据合并与差异比对。

**结构化数据导出** 支持将处理后的链接清单导出为 JSON、CSV 或 Markdown 表格格式，便于嵌入文档或报表。

## 应用场景

**技术文档站外链巡检** 技术博客或开源项目文档中常引用大量外部参考链接，随时间推移部分链接可能失效。项目维护者可定期运行本工具对文档源文件中的链接进行批量存活检测，自动生成失效链接报告，辅助文档更新。

**内容聚合导航站构建** 运营技术导航或资源推荐站点的编辑人员，可通过本工具统一管理待上线的 URL 清单，进行去重与分类标注，再导出为结构化数据供前端渲染，减少人工整理错误。

**爬虫数据清洗预处理** 数据采集工程师在爬取文章列表页后，得到大量原始 URL，其中可能混杂重复、无效或非目标域名的链接。使用本工具可快速完成清洗，输出干净的待抓取队列。

**个人知识库外链归档** 使用本地 Markdown 或 Org-mode 管理知识笔记的用户，可将散落在笔记中的外部链接提取汇总，通过本工具统一检查可用性并添加分类标签，构建个人外链索引库。

## 快速开始

以下指令适用于 Linux 与 macOS 环境，Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-collective/asset-manager.git

# 进入项目目录
cd asset-manager

# 安装 Python 依赖（建议使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 运行批量链接导入与检测（示例：处理当前批次的 raw_links.txt）
python cli.py import --input ./batches/batch_27_80.txt --output ./reports/batch_27_report.json

# 生成 Markdown 格式的链接清单
python cli.py export --input ./reports/batch_27_report.json --format markdown --output ./docs/batch_27_links.md
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 核心运行环境，建议使用 3.10 长期支持版本 |
| requests | 2.28.0 及以上 | 用于发送 HTTP 存活检测请求 |
| click | 8.1.0 及以上 | 提供命令行交互界面框架 |
| pydantic | 2.0.0 及以上 | 用于链接数据模型校验与序列化 |
| pytest | 7.0.0 及以上 | 单元测试与集成测试框架（仅开发依赖） |
| black | 23.0.0 及以上 | 代码格式化工具（仅开发依赖） |
| mypy | 1.0.0 及以上 | 静态类型检查（仅开发依赖） |

操作系统兼容性：Linux（内核 4.0+）、macOS 10.15+、Windows 10/11（需启用 UTF-8 支持）。生产环境建议使用 Debian 11 或 Ubuntu 20.04 LTS。

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | docs/getting-started.md | 如何快速安装并完成第一批链接的导入与检测？ |
| 命令参考 | docs/cli-reference.md | 所有命令行子命令、参数选项与使用示例有哪些？ |
| 数据模型 | docs/data-models.md | 链接资产的数据结构定义、字段说明与存储格式是怎样的？ |
| 适配器开发 | docs/adapter-guide.md | 如何为新的内容站点编写自定义链接解析适配器？ |
| 批次管理 | docs/batch-management.md | 如何管理多批次数据、合并结果以及追踪变更历史？ |
| 性能调优 | docs/performance-tuning.md | 在大规模链接（万级以上）场景下如何优化检测速度与资源占用？ |

## 资源列表

- http://www.mobile.xqnqq.com/Article/2421764.shtml
- http://www.read.usuhx.com/Article/4602.shtml
- http://www.read.usuhx.com/Article/5738460.shtml
- http://www.mobile.xqnqq.com/Article/4057717.shtml
- http://www.mobile.xqnqq.com/Article/1641.shtml
- http://www.read.usuhx.com/Article/96104.shtml
- http://www.mobile.xqnqq.com/Article/59235.shtml
- http://www.mobile.xqnqq.com/Article/769051.shtml
- http://www.mobile.xqnqq.com/Article/9937.shtml
- http://www.read.usuhx.com/Article/201815.shtml
- http://www.read.usuhx.com/Article/5154782.shtml
- http://www.mobile.xqnqq.com/Article/18723.shtml
- http://www.read.usuhx.com/Article/3413.shtml
- http://www.mobile.xqnqq.com/Article/908396.shtml
- http://www.mobile.xqnqq.com/Article/4305.shtml
- http://www.mobile.xqnqq.com/Article/809415.shtml
- http://www.read.usuhx.com/Article/48837.shtml
- http://www.read.usuhx.com/Article/6756.shtml
- http://www.mobile.xqnqq.com/Article/8036335.shtml
- http://www.read.usuhx.com/Article/5030830.shtml
- http://www.mobile.xqnqq.com/Article/8290.shtml
- http://www.mobile.xqnqq.com/Article/285994.shtml
- http://www.read.usuhx.com/Article/285667.shtml
- http://www.read.usuhx.com/Article/3584.shtml
- http://www.read.usuhx.com/Article/880712.shtml
- http://www.read.usuhx.com/Article/328045.shtml
- http://www.mobile.xqnqq.com/Article/279354.shtml
- http://www.mobile.xqnqq.com/Article/8893340.shtml
- http://www.mobile.xqnqq.com/Article/044460.shtml
- http://www.mobile.xqnqq.com/Article/26857.shtml
- http://www.read.usuhx.com/Article/1425178.shtml
- http://www.read.usuhx.com/Article/6179.shtml
- http://www.mobile.xqnqq.com/Article/0618584.shtml
- http://www.read.usuhx.com/Article/24862.shtml
- http://www.read.usuhx.com/Article/464862.shtml
- http://www.mobile.xqnqq.com/Article/36128.shtml
- http://www.mobile.xqnqq.com/Article/49277.shtml
- http://www.mobile.xqnqq.com/Article/044993.shtml
- http://www.mobile.xqnqq.com/Article/6988039.shtml
- http://www.read.usuhx.com/Article/4103.shtml
- http://www.read.usuhx.com/Article/2343958.shtml
- http://www.mobile.xqnqq.com/Article/371224.shtml
- http://www.mobile.xqnqq.com/Article/2118380.shtml
- http://www.mobile.xqnqq.com/Article/6239.shtml
- http://www.mobile.xqnqq.com/Article/644309.shtml
- http://www.read.usuhx.com/Article/10348.shtml
- http://www.read.usuhx.com/Article/057328.shtml
- http://www.read.usuhx.com/Article/459976.shtml
- http://www.mobile.xqnqq.com/Article/540782.shtml
- http://www.read.usuhx.com/Article/64960.shtml
- http://www.read.usuhx.com/Article/4082.shtml
- http://www.mobile.xqnqq.com/Article/32390.shtml
- http://www.mobile.xqnqq.com/Article/1141422.shtml
- http://www.mobile.xqnqq.com/Article/444229.shtml
- http://www.mobile.xqnqq.com/Article/828424.shtml
- http://www.mobile.xqnqq.com/Article/39298.shtml
- http://www.mobile.xqnqq.com/Article/2518.shtml
- http://www.mobile.xqnqq.com/Article/570669.shtml
- http://www.mobile.xqnqq.com/Article/5563.shtml
- http://www.mobile.xqnqq.com/Article/9474.shtml
- http://www.read.usuhx.com/Article/09039.shtml
- http://www.mobile.xqnqq.com/Article/4171165.shtml
- http://www.mobile.xqnqq.com/Article/5341120.shtml
- http://www.mobile.xqnqq.com/Article/1315.shtml
- http://www.read.usuhx.com/Article/6692952.shtml
- http://www.read.usuhx.com/Article/06642.shtml
- http://www.read.usuhx.com/Article/457435.shtml
- http://www.mobile.xqnqq.com/Article/5474513.shtml
- http://www.read.usuhx.com/Article/6092711.shtml
- http://www.read.usuhx.com/Article/314785.shtml
- http://www.read.usuhx.com/Article/2211772.shtml
- http://www.mobile.xqnqq.com/Article/688444.shtml
- http://www.read.usuhx.com/Article/330677.shtml
- http://www.mobile.xqnqq.com/Article/21982.shtml
- http://www.mobile.xqnqq.com/Article/04255.shtml
- http://www.read.usuhx.com/Article/82430.shtml
- http://www.read.usuhx.com/Article/04434.shtml
- http://www.read.usuhx.com/Article/064322.shtml
- http://www.read.usuhx.com/Article/5902280.shtml
- http://www.mobile.xqnqq.com/Article/3038901.shtml
- http://www.mobile.xqnqq.com/Article/0550.shtml
- http://www.read.usuhx.com/Article/8996.shtml
- http://www.read.usuhx.com/Article/59971.shtml
- http://www.mobile.xqnqq.com/Article/5004883.shtml
- http://www.mobile.xqnqq.com/Article/3674.shtml
- http://www.read.usuhx.com/Article/395923.shtml
- http://www.read.usuhx.com/Article/148341.shtml
- http://www.mobile.xqnqq.com/Article/7223.shtml
- http://www.read.usuhx.com/Article/71384.shtml
- http://www.mobile.xqnqq.com/Article/79072.shtml
- http://www.mobile.xqnqq.com/Article/5523125.shtml
- http://www.read.usuhx.com/Article/874082.shtml
- http://www.read.usuhx.com/Article/919929.shtml
- http://www.mobile.xqnqq.com/Article/1700983.shtml
- http://www.mobile.xqnqq.com/Article/3524.shtml
- http://www.read.usuhx.com/Article/993812.shtml
- http://www.mobile.xqnqq.com/Article/02663.shtml
- http://www.read.usuhx.com/Article/42893.shtml
- http://www.mobile.xqnqq.com/Article/03756.shtml
- http://www.mobile.xqnqq.com/Article/49959.shtml
- http://www.mobile.xqnqq.com/Article/15540.shtml
- http://www.read.usuhx.com/Article/40849.shtml
- http://www.mobile.xqnqq.com/Article/5343.shtml
- http://www.read.usuhx.com/Article/770597.shtml
- http://www.read.usuhx.com/Article/28654.shtml
- http://www.read.usuhx.com/Article/60109.shtml
- http://www.read.usuhx.com/Article/531877.shtml
- http://www.read.usuhx.com/Article/4862441.shtml
- http://www.read.usuhx.com/Article/254196.shtml
- http://www.read.usuhx.com/Article/0724114.shtml
- http://www.read.usuhx.com/Article/30903.shtml
- http://www.mobile.xqnqq.com/Article/84017.shtml
- http://www.mobile.xqnqq.com/Article/7775.shtml
- http://www.read.usuhx.com/Article/093581.shtml
- http://www.read.usuhx.com/Article/7316090.shtml
- http://www.read.usuhx.com/Article/6644935.shtml
- http://www.mobile.xqnqq.com/Article/99565.shtml
- http://www.mobile.xqnqq.com/Article/2635.shtml
- http://www.mobile.xqnqq.com/Article/05525.shtml
- http://www.mobile.xqnqq.com/Article/285099.shtml
- http://www.mobile.xqnqq.com/Article/89815.shtml
- http://www.read.usuhx.com/Article/453030.shtml
- http://www.mobile.xqnqq.com/Article/41333.shtml
- http://www.mobile.xqnqq.com/Article/2631645.shtml
- http://www.read.usuhx.com/Article/8078371.shtml
- http://www.read.usuhx.com/Article/0239303.shtml
- http://www.read.usuhx.com/Article/0207554.shtml
- http://www.mobile.xqnqq.com/Article/8811481.shtml
- http://www.mobile.xqnqq.com/Article/532351.shtml
- http://www.read.usuhx.com/Article/55481.shtml
- http://www.read.usuhx.com/Article/87444.shtml
- http://www.read.usuhx.com/Article/145159.shtml
- http://www.mobile.xqnqq.com/Article/6410416.shtml
- http://www.read.usuhx.com/Article/5415.shtml
- http://www.read.usuhx.com/Article/58747.shtml
- http://www.mobile.xqnqq.com/Article/4883.shtml
- http://www.read.usuhx.com/Article/341407.shtml
- http://www.mobile.xqnqq.com/Article/6354.shtml
- http://www.read.usuhx.com/Article/32167.shtml
- http://www.read.usuhx.com/Article/436320.shtml
- http://www.mobile.xqnqq.com/Article/0636.shtml
- http://www.read.usuhx.com/Article/4851369.shtml
- http://www.read.usuhx.com/Article/1831.shtml
- http://www.mobile.xqnqq.com/Article/46690.shtml
- http://www.read.usuhx.com/Article/219173.shtml
- http://www.mobile.xqnqq.com/Article/84330.shtml
- http://www.read.usuhx.com/Article/3010.shtml
- http://www.read.usuhx.com/Article/7583.shtml
- http://www.mobile.xqnqq.com/Article/87464.shtml
- http://www.mobile.xqnqq.com/Article/0005.shtml
- http://www.mobile.xqnqq.com/Article/236826.shtml
- http://www.mobile.xqnqq.com/Article/2783.shtml
- http://www.read.usuhx.com/Article/3057.shtml
- http://www.read.usuhx.com/Article/0397394.shtml
- http://www.mobile.xqnqq.com/Article/16617.shtml
- http://www.mobile.xqnqq.com/Article/842379.shtml
- http://www.read.usuhx.com/Article/54564.shtml
- http://www.read.usuhx.com/Article/73203.shtml
- http://www.read.usuhx.com/Article/672801.shtml
- http://www.read.usuhx.com/Article/51802.shtml
- http://www.read.usuhx.com/Article/6920909.shtml
- http://www.mobile.xqnqq.com/Article/7508319.shtml
- http://www.read.usuhx.com/Article/29092.shtml
- http://www.mobile.xqnqq.com/Article/5970372.shtml
- http://www.mobile.xqnqq.com/Article/7400.shtml
- http://www.read.usuhx.com/Article/72907.shtml
- http://www.read.usuhx.com/Article/9484589.shtml
- http://www.read.usuhx.com/Article/7342.shtml
- http://www.read.usuhx.com/Article/50488.shtml
- http://www.read.usuhx.com/Article/891271.shtml
- http://www.read.usuhx.com/Article/55332.shtml
- http://www.read.usuhx.com/Article/49928.shtml
- http://www.mobile.xqnqq.com/Article/81097.shtml
- http://www.read.usuhx.com/Article/891897.shtml
- http://www.mobile.xqnqq.com/Article/92899.shtml
- http://www.mobile.xqnqq.com/Article/3432.shtml
- http://www.mobile.xqnqq.com/Article/4694047.shtml
- http://www.mobile.xqnqq.com/Article/6369878.shtml
- http://www.read.usuhx.com/Article/73690.shtml
- http://www.mobile.xqnqq.com/Article/601086.shtml
- http://www.mobile.xqnqq.com/Article/0157.shtml
- http://www.read.usuhx.com/Article/199235.shtml
- http://www.mobile.xqnqq.com/Article/1755.shtml
- http://www.mobile.xqnqq.com/Article/615849.shtml
- http://www.read.usuhx.com/Article/424114.shtml
- http://www.read.usuhx.com/Article/013461.shtml
- http://www.mobile.xqnqq.com/Article/118467.shtml
- http://www.mobile.xqnqq.com/Article/2318.shtml
- http://www.mobile.xqnqq.com/Article/5257211.shtml
- http://www.read.usuhx.com/Article/5269.shtml
- http://www.mobile.xqnqq.com/Article/56585.shtml
- http://www.read.usuhx.com/Article/8358819.shtml
- http://www.read.usuhx.com/Article/0784.shtml
- http://www.mobile.xqnqq.com/Article/815616.shtml
- http://www.read.usuhx.com/Article/724551.shtml
- http://www.read.usuhx.com/Article/37353.shtml
- http://www.mobile.xqnqq.com/Article/8480.shtml
- http://www.mobile.xqnqq.com/Article/66237.shtml
- http://www.read.usuhx.com/Article/47842.shtml
- http://www.read.usuhx.com/Article/45861.shtml
- http://www.mobile.xqnqq.com/Article/808672.shtml
- http://www.read.usuhx.com/Article/302280.shtml
- http://www.mobile.xqnqq.com/Article/057156.shtml
- http://www.read.usuhx.com/Article/8560.shtml
- http://www.mobile.xqnqq.com/Article/834922.shtml
- http://www.mobile.xqnqq.com/Article/7148567.shtml
- http://www.mobile.xqnqq.com/Article/75973.shtml
- http://www.mobile.xqnqq.com/Article/15644.shtml
- http://www.read.usuhx.com/Article/89457.shtml
- http://www.mobile.xqnqq.com/Article/80220.shtml
- http://www.mobile.xqnqq.com/Article/95473.shtml
- http://www.read.usuhx.com/Article/5039266.shtml
- http://www.mobile.xqnqq.com/Article/55542.shtml
- http://www.read.usuhx.com/Article/0633629.shtml
- http://www.mobile.xqnqq.com/Article/214283.shtml
- http://www.mobile.xqnqq.com/Article/63221.shtml
- http://www.mobile.xqnqq.com/Article/7109117.shtml
- http://www.mobile.xqnqq.com/Article/026904.shtml
- http://www.mobile.xqnqq.com/Article/029715.shtml
- http://www.mobile.xqnqq.com/Article/831286.shtml
- http://www.mobile.xqnqq.com/Article/489427.shtml
- http://www.mobile.xqnqq.com/Article/2732.shtml
- http://www.mobile.xqnqq.com/Article/7810.shtml
- http://www.mobile.xqnqq.com/Article/45290.shtml
- http://www.read.usuhx.com/Article/57600.shtml
- http://www.read.usuhx.com/Article/4735.shtml
- http://www.read.usuhx.com/Article/9075930.shtml
- http://www.mobile.xqnqq.com/Article/522549.shtml
- http://www.mobile.xqnqq.com/Article/6124.shtml
- http://www.mobile.xqnqq.com/Article/279417.shtml
- http://www.read.usuhx.com/Article/847295.shtml
- http://www.mobile.xqnqq.com/Article/3226.shtml
- http://www.mobile.xqnqq.com/Article/870482.shtml
- http://www.mobile.xqnqq.com/Article/750645.shtml
- http://www.read.usuhx.com/Article/0130.shtml
- http://www.mobile.xqnqq.com/Article/90272.shtml
- http://www.read.usuhx.com/Article/10999.shtml
- http://www.mobile.xqnqq.com/Article/160264.shtml
- http://www.mobile.xqnqq.com/Article/9617.shtml
- http://www.mobile.xqnqq.com/Article/037811.shtml
- http://www.read.usuhx.com/Article/75500.shtml
- http://www.mobile.xqnqq.com/Article/387937.shtml
- http://www.mobile.xqnqq.com/Article/9610380.shtml
- http://www.mobile.xqnqq.com/Article/3838.shtml
- http://www.read.usuhx.com/Article/3646355.shtml
- http://www.mobile.xqnqq.com/Article/5645439.shtml
- http://www.mobile.xqnqq.com/Article/380088.shtml
- http://www.read.usuhx.com/Article/443774.shtml
- http://www.mobile.xqnqq.com/Article/6348840.shtml
- http://www.mobile.xqnqq.com/Article/6751.shtml

## 项目结构

```
asset-manager/
├── cli.py                      # 命令行入口，注册所有子命令
├── requirements.txt            # 生产环境依赖清单
├── pyproject.toml              # 项目元数据与构建配置
├── README.md                   # 项目说明文档（本文件）
├── LICENSE                     # MIT 许可证文本
├── .gitignore                  # Git 版本控制忽略规则
│
├── src/                        # 核心源代码目录
│   ├── __init__.py             # 包初始化
│   ├── models/                 # 数据模型层
│   │   ├── __init__.py
│   │   ├── link.py             # Link 实体类定义（URL、状态、标签）
│   │   └── batch.py            # Batch 批次元数据模型
│   ├── parsers/                # 链接解析适配器
│   │   ├── __init__.py
│   │   ├── base.py             # 抽象解析器基类
│   │   └── article_site.py     # 针对 xqnqq 与 usuhx 类站点的解析器
│   ├── checkers/               # 链接检测模块
│   │   ├── __init__.py
│   │   ├── http_checker.py     # HTTP 存活检测实现
│   │   └── protocol_normalizer.py  # 协议归一化工具
│   ├── exporters/              # 导出格式支持
│   │   ├── __init__.py
│   │   ├── json_exporter.py
│   │   ├── csv_exporter.py
│   │   └── markdown_exporter.py
│   └── utils/                  # 通用工具函数
│       ├── __init__.py
│       ├── file_io.py          # 文件读写辅助
│       └── concurrency.py      # 并发请求控制
│
├── tests/                      # 测试套件
│   ├── unit/                   # 单元测试
│   └── integration/            # 集成测试
│
├── docs/                       # 文档目录（详见文档导航）
│   ├── getting-started.md
│   ├── cli-reference.md
│   ├── data-models.md
│   ├── adapter-guide.md
│   ├── batch-management.md
│   └── performance-tuning.md
│
├── batches/                    # 批次数据存放目录
│   └── batch_27_80.txt         # 第 27/80 批原始链接列表
│
└── reports/                    # 处理报告输出目录
    └── batch_27_report.json    # 第 27 批次检测报告示例
```

## 贡献指南

1. 查阅 issue 列表或新建 issue 描述您希望修复的问题或新增的功能，等待维护者确认避免重复工作。

2. Fork 项目仓库并在本地创建特性分支（feature/your-feature-name 或 fix/your-bug-fix），确保分支基于最新的 main 分支。

3. 编写代码并补充对应的单元测试（位于 tests/ 目录下），测试覆盖率不低于 85%，同时使用 black 与 mypy 进行代码格式与类型检查。

4. 提交代码前运行完整测试套件（pytest tests/）确保所有现有测试通过，并更新相关文档（如 CLI 参考或适配器指南）以反映您的变更。

5. 发起 Pull Request 至 main 分支，在 PR 描述中清晰说明变更内容、影响范围以及测试结果摘要，等待代码审查。

## 常见问题

**Q: 检测大量链接时出现超时或连接错误怎么办？**

A: 可调整并发线程数（--workers 参数）与单次超时时间（--timeout 参数）。对于网络不稳定环境，建议降低并发数并增加超时阈值。同时可启用 --retry 参数开启自动重试机制，默认重试 3 次。若目标站点有反爬策略，可考虑增加请求间隔（--delay 参数）。

**Q: 如何处理一批链接中包含不同协议（http 与 https）的情况？**

A: 工具默认开启协议归一化校验，在检测报告中会标注协议不一致的链接条目。用户可通过 --normalize-protocol 选项将检测目标统一转换为 https（或保留原始协议）。对于仅支持 http 的站点，建议在配置文件中通过白名单规则排除归一化。

**Q: 是否可以集成到 CI/CD 流程中自动运行？**

A: 可以。cli.py 支持非交互模式运行，所有参数均可通过命令行传递，返回码在检测到失效链接时非零，便于 CI 系统捕获。建议在 Git 仓库的 pre-commit hook 或 GitHub Actions 中配置定期执行，并将报告归档为构建产物。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
