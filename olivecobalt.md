# WebLink Corpus Project

WebLink Corpus Project 是一个面向技术文档检索、外链有效性监控与内容聚合场景的开源数据整理工具集。该项目旨在帮助开发者、运维人员与内容研究者系统性地采集、去重、分类并监控特定域名下的文章型资源链接，形成可长期维护的 URL 工作集。项目本身不依赖商业 API，所有核心功能基于 Python 标准库与轻量级第三方组件构建，适用于批量链接管理、变更检测与元数据提取等任务。

项目定位为技术资源链接的规范化处理流水线，而非通用爬虫框架。目标用户包括需要维护技术文档引用列表的文档工程师、负责外部资源合规审查的法务技术团队、以及搭建技术资讯聚合站点的个人开发者。当前批次处理第 7/80 批资源，覆盖 mobile.xqnqq.com 与 read.usuhx.com 两个域名的共计 250 个文章链接，后续批次将逐步扩展至更多技术内容源。

## 功能概览

**批量链接标准化**：自动补全协议头缺失的 URL，剔除片段标识与查询参数，统一输出为纯文章路径格式。

**域名白名单过滤**：仅处理预先配置的允许域名列表，拒绝非授权域名的导入，防止数据污染。

**增量去重机制**：基于 URL 完整路径与文章 ID 双重校验，避免同一资源在多次运行中被重复记录。

**状态码可观测性**：对每个链接执行 HEAD 请求，记录响应状态、重定向链与最终可达性，输出结构化日志。

**元数据提取存根**：从 HTML 标题标签与 meta description 中抽取文章标题与摘要，生成 CSV 元数据附表。

**定时任务集成示例**：提供 systemd timer 与 cron 配置片段，支持每日凌晨自动执行链接刷新与报告生成。

**导出格式多选**：支持输出为纯文本列表、JSON 数组、Markdown 表格以及 SQLite 数据库文件。

## 应用场景

技术文档团队定期校验外部引用链接的有效性，避免文档中出现死链或跳转异常页面。项目可配置为每周执行一次全量检查，生成失效链接报告并邮件通知责任人。

个人技术博客作者需要将散落在浏览器书签中的文章链接整理为可公开分享的资源集合。项目提供导入去重与分类打标功能，帮助快速生成干净的阅读清单。

合规审计人员需要批量获取指定域名下的所有文章 URL，用于人工抽检内容合规性。项目支持按域名导出完整链接列表，便于导入第三方审核平台。

运维自动化系统在部署前需要验证依赖的文档链接是否可访问，作为前置检查项之一。项目提供命令行退出码，可与 CI/CD 流程集成。

## 快速开始

```bash
git clone https://github.com/your-org/weblink-corpus.git
cd weblink-corpus
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python main.py --input ./sources/batch_07.txt --output ./reports/batch_07_result.json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，建议使用 3.10 长期支持版 |
| requests | 2.28.0 及以上 | HTTP 请求处理，用于链接状态检测 |
| beautifulsoup4 | 4.11.0 及以上 | HTML 解析，用于元数据提取 |
| lxml | 4.9.0 及以上 | 解析器后端，提高 beautifulsoup 处理速度 |
| pytest | 7.2.0 及以上 | 单元测试框架，仅开发环境需要 |
| black | 22.3.0 及以上 | 代码格式化工具，仅开发环境需要 |
| mypy | 0.990 及以上 | 静态类型检查，仅开发环境需要 |
| sqlite3 | 系统内置 | 数据库导出功能依赖，Python 标准库自带 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user_guide.md | 如何准备输入文件、调整并发数、配置日志级别 |
| 运维参考 | docs/operations.md | 如何部署定时任务、迁移数据库文件、备份报告 |
| 开发指南 | docs/development.md | 如何新增解析器、自定义导出格式、编写测试用例 |
| 设计说明 | docs/architecture.md | 整体模块划分、数据流转路径、扩展点设计 |

## 资源列表

- http://www.mobile.xqnqq.com/Article/1355.shtml
- http://www.mobile.xqnqq.com/Article/97704.shtml
- http://www.mobile.xqnqq.com/Article/4989.shtml
- http://www.read.usuhx.com/Article/0676533.shtml
- http://www.mobile.xqnqq.com/Article/1066983.shtml
- http://www.read.usuhx.com/Article/5190233.shtml
- http://www.read.usuhx.com/Article/4828314.shtml
- http://www.mobile.xqnqq.com/Article/95942.shtml
- http://www.mobile.xqnqq.com/Article/46705.shtml
- http://www.mobile.xqnqq.com/Article/2046077.shtml
- http://www.read.usuhx.com/Article/678034.shtml
- http://www.mobile.xqnqq.com/Article/5220.shtml
- http://www.read.usuhx.com/Article/10675.shtml
- http://www.mobile.xqnqq.com/Article/138585.shtml
- http://www.read.usuhx.com/Article/73755.shtml
- http://www.read.usuhx.com/Article/36729.shtml
- http://www.mobile.xqnqq.com/Article/63315.shtml
- http://www.read.usuhx.com/Article/7329706.shtml
- http://www.mobile.xqnqq.com/Article/91364.shtml
- http://www.mobile.xqnqq.com/Article/905534.shtml
- http://www.mobile.xqnqq.com/Article/521647.shtml
- http://www.mobile.xqnqq.com/Article/2418.shtml
- http://www.mobile.xqnqq.com/Article/87158.shtml
- http://www.read.usuhx.com/Article/6577.shtml
- http://www.mobile.xqnqq.com/Article/3380.shtml
- http://www.mobile.xqnqq.com/Article/034839.shtml
- http://www.read.usuhx.com/Article/6366.shtml
- http://www.read.usuhx.com/Article/248830.shtml
- http://www.read.usuhx.com/Article/8219.shtml
- http://www.read.usuhx.com/Article/04690.shtml
- http://www.read.usuhx.com/Article/4675176.shtml
- http://www.read.usuhx.com/Article/4620.shtml
- http://www.read.usuhx.com/Article/3305732.shtml
- http://www.read.usuhx.com/Article/59626.shtml
- http://www.read.usuhx.com/Article/5709181.shtml
- http://www.mobile.xqnqq.com/Article/555907.shtml
- http://www.read.usuhx.com/Article/0755944.shtml
- http://www.read.usuhx.com/Article/639129.shtml
- http://www.read.usuhx.com/Article/28237.shtml
- http://www.mobile.xqnqq.com/Article/383929.shtml
- http://www.mobile.xqnqq.com/Article/4351.shtml
- http://www.mobile.xqnqq.com/Article/6550.shtml
- http://www.read.usuhx.com/Article/1493250.shtml
- http://www.read.usuhx.com/Article/153004.shtml
- http://www.read.usuhx.com/Article/78399.shtml
- http://www.read.usuhx.com/Article/9241.shtml
- http://www.read.usuhx.com/Article/2547511.shtml
- http://www.read.usuhx.com/Article/07365.shtml
- http://www.mobile.xqnqq.com/Article/328035.shtml
- http://www.read.usuhx.com/Article/59793.shtml
- http://www.mobile.xqnqq.com/Article/2971119.shtml
- http://www.read.usuhx.com/Article/603121.shtml
- http://www.read.usuhx.com/Article/187156.shtml
- http://www.read.usuhx.com/Article/48453.shtml
- http://www.mobile.xqnqq.com/Article/2050.shtml
- http://www.read.usuhx.com/Article/89952.shtml
- http://www.read.usuhx.com/Article/7757.shtml
- http://www.read.usuhx.com/Article/69118.shtml
- http://www.read.usuhx.com/Article/1835969.shtml
- http://www.read.usuhx.com/Article/289803.shtml
- http://www.mobile.xqnqq.com/Article/128696.shtml
- http://www.read.usuhx.com/Article/4274138.shtml
- http://www.mobile.xqnqq.com/Article/9447.shtml
- http://www.read.usuhx.com/Article/90925.shtml
- http://www.mobile.xqnqq.com/Article/2130.shtml
- http://www.mobile.xqnqq.com/Article/8833.shtml
- http://www.read.usuhx.com/Article/2586949.shtml
- http://www.read.usuhx.com/Article/9401.shtml
- http://www.mobile.xqnqq.com/Article/17073.shtml
- http://www.mobile.xqnqq.com/Article/784523.shtml
- http://www.mobile.xqnqq.com/Article/8248544.shtml
- http://www.read.usuhx.com/Article/2068538.shtml
- http://www.read.usuhx.com/Article/632138.shtml
- http://www.mobile.xqnqq.com/Article/475240.shtml
- http://www.mobile.xqnqq.com/Article/3800.shtml
- http://www.mobile.xqnqq.com/Article/4255580.shtml
- http://www.read.usuhx.com/Article/040854.shtml
- http://www.mobile.xqnqq.com/Article/7669.shtml
- http://www.read.usuhx.com/Article/6828.shtml
- http://www.read.usuhx.com/Article/46491.shtml
- http://www.read.usuhx.com/Article/24913.shtml
- http://www.read.usuhx.com/Article/0262.shtml
- http://www.mobile.xqnqq.com/Article/8358.shtml
- http://www.mobile.xqnqq.com/Article/15049.shtml
- http://www.mobile.xqnqq.com/Article/496271.shtml
- http://www.read.usuhx.com/Article/7265.shtml
- http://www.mobile.xqnqq.com/Article/6032860.shtml
- http://www.mobile.xqnqq.com/Article/4187.shtml
- http://www.mobile.xqnqq.com/Article/6599.shtml
- http://www.read.usuhx.com/Article/1602774.shtml
- http://www.read.usuhx.com/Article/4428.shtml
- http://www.read.usuhx.com/Article/72356.shtml
- http://www.read.usuhx.com/Article/3362.shtml
- http://www.mobile.xqnqq.com/Article/3557.shtml
- http://www.mobile.xqnqq.com/Article/537649.shtml
- http://www.read.usuhx.com/Article/805420.shtml
- http://www.mobile.xqnqq.com/Article/2672.shtml
- http://www.read.usuhx.com/Article/5644.shtml
- http://www.read.usuhx.com/Article/596014.shtml
- http://www.mobile.xqnqq.com/Article/0320.shtml
- http://www.mobile.xqnqq.com/Article/5589.shtml
- http://www.read.usuhx.com/Article/1540326.shtml
- http://www.read.usuhx.com/Article/2034888.shtml
- http://www.read.usuhx.com/Article/90801.shtml
- http://www.mobile.xqnqq.com/Article/338541.shtml
- http://www.mobile.xqnqq.com/Article/5347851.shtml
- http://www.read.usuhx.com/Article/3674.shtml
- http://www.mobile.xqnqq.com/Article/0792469.shtml
- http://www.mobile.xqnqq.com/Article/4701754.shtml
- http://www.read.usuhx.com/Article/52111.shtml
- http://www.mobile.xqnqq.com/Article/3813967.shtml
- http://www.read.usuhx.com/Article/490909.shtml
- http://www.read.usuhx.com/Article/03372.shtml
- http://www.read.usuhx.com/Article/92734.shtml
- http://www.read.usuhx.com/Article/2789408.shtml
- http://www.read.usuhx.com/Article/22261.shtml
- http://www.mobile.xqnqq.com/Article/6377.shtml
- http://www.read.usuhx.com/Article/4387.shtml
- http://www.read.usuhx.com/Article/890419.shtml
- http://www.mobile.xqnqq.com/Article/090729.shtml
- http://www.mobile.xqnqq.com/Article/98021.shtml
- http://www.mobile.xqnqq.com/Article/528060.shtml
- http://www.mobile.xqnqq.com/Article/17532.shtml
- http://www.read.usuhx.com/Article/9757.shtml
- http://www.mobile.xqnqq.com/Article/75446.shtml
- http://www.mobile.xqnqq.com/Article/071122.shtml
- http://www.read.usuhx.com/Article/7199395.shtml
- http://www.read.usuhx.com/Article/531494.shtml
- http://www.read.usuhx.com/Article/60840.shtml
- http://www.mobile.xqnqq.com/Article/35555.shtml
- http://www.read.usuhx.com/Article/46762.shtml
- http://www.mobile.xqnqq.com/Article/6651355.shtml
- http://www.read.usuhx.com/Article/0844.shtml
- http://www.mobile.xqnqq.com/Article/355468.shtml
- http://www.read.usuhx.com/Article/0562.shtml
- http://www.read.usuhx.com/Article/60111.shtml
- http://www.read.usuhx.com/Article/3499097.shtml
- http://www.read.usuhx.com/Article/547992.shtml
- http://www.read.usuhx.com/Article/877799.shtml
- http://www.read.usuhx.com/Article/8671.shtml
- http://www.read.usuhx.com/Article/243010.shtml
- http://www.read.usuhx.com/Article/8950269.shtml
- http://www.read.usuhx.com/Article/4986.shtml
- http://www.mobile.xqnqq.com/Article/00250.shtml
- http://www.mobile.xqnqq.com/Article/7765048.shtml
- http://www.read.usuhx.com/Article/80151.shtml
- http://www.read.usuhx.com/Article/70455.shtml
- http://www.read.usuhx.com/Article/4442.shtml
- http://www.mobile.xqnqq.com/Article/1608.shtml
- http://www.mobile.xqnqq.com/Article/801930.shtml
- http://www.mobile.xqnqq.com/Article/7853.shtml
- http://www.read.usuhx.com/Article/40595.shtml
- http://www.mobile.xqnqq.com/Article/5901.shtml
- http://www.mobile.xqnqq.com/Article/6818833.shtml
- http://www.read.usuhx.com/Article/1215979.shtml
- http://www.read.usuhx.com/Article/198221.shtml
- http://www.mobile.xqnqq.com/Article/3578849.shtml
- http://www.mobile.xqnqq.com/Article/07008.shtml
- http://www.mobile.xqnqq.com/Article/134810.shtml
- http://www.read.usuhx.com/Article/29708.shtml
- http://www.read.usuhx.com/Article/4107.shtml
- http://www.read.usuhx.com/Article/1743017.shtml
- http://www.mobile.xqnqq.com/Article/18287.shtml
- http://www.mobile.xqnqq.com/Article/73428.shtml
- http://www.mobile.xqnqq.com/Article/46117.shtml
- http://www.mobile.xqnqq.com/Article/4334450.shtml
- http://www.mobile.xqnqq.com/Article/3460214.shtml
- http://www.mobile.xqnqq.com/Article/25372.shtml
- http://www.read.usuhx.com/Article/65902.shtml
- http://www.read.usuhx.com/Article/967706.shtml
- http://www.mobile.xqnqq.com/Article/28459.shtml
- http://www.mobile.xqnqq.com/Article/8250884.shtml
- http://www.read.usuhx.com/Article/652549.shtml
- http://www.read.usuhx.com/Article/0616.shtml
- http://www.mobile.xqnqq.com/Article/7388.shtml
- http://www.mobile.xqnqq.com/Article/97340.shtml
- http://www.read.usuhx.com/Article/4353.shtml
- http://www.read.usuhx.com/Article/539801.shtml
- http://www.mobile.xqnqq.com/Article/0819463.shtml
- http://www.read.usuhx.com/Article/8628.shtml
- http://www.mobile.xqnqq.com/Article/69058.shtml
- http://www.mobile.xqnqq.com/Article/6787.shtml
- http://www.read.usuhx.com/Article/428868.shtml
- http://www.read.usuhx.com/Article/246988.shtml
- http://www.read.usuhx.com/Article/94487.shtml
- http://www.read.usuhx.com/Article/049669.shtml
- http://www.mobile.xqnqq.com/Article/0509963.shtml
- http://www.read.usuhx.com/Article/2691827.shtml
- http://www.read.usuhx.com/Article/46819.shtml
- http://www.mobile.xqnqq.com/Article/242203.shtml
- http://www.read.usuhx.com/Article/3161.shtml
- http://www.mobile.xqnqq.com/Article/42993.shtml
- http://www.read.usuhx.com/Article/701188.shtml
- http://www.read.usuhx.com/Article/8674.shtml
- http://www.read.usuhx.com/Article/94931.shtml
- http://www.read.usuhx.com/Article/8165135.shtml
- http://www.mobile.xqnqq.com/Article/87678.shtml
- http://www.mobile.xqnqq.com/Article/4481.shtml
- http://www.mobile.xqnqq.com/Article/4586.shtml
- http://www.read.usuhx.com/Article/087733.shtml
- http://www.read.usuhx.com/Article/27450.shtml
- http://www.read.usuhx.com/Article/53040.shtml
- http://www.read.usuhx.com/Article/8568472.shtml
- http://www.read.usuhx.com/Article/17777.shtml
- http://www.mobile.xqnqq.com/Article/71973.shtml
- http://www.read.usuhx.com/Article/4136.shtml
- http://www.mobile.xqnqq.com/Article/02845.shtml
- http://www.read.usuhx.com/Article/91667.shtml
- http://www.mobile.xqnqq.com/Article/1902.shtml
- http://www.mobile.xqnqq.com/Article/511719.shtml
- http://www.read.usuhx.com/Article/013003.shtml
- http://www.read.usuhx.com/Article/8947607.shtml
- http://www.read.usuhx.com/Article/8361699.shtml
- http://www.read.usuhx.com/Article/2450938.shtml
- http://www.mobile.xqnqq.com/Article/699691.shtml
- http://www.mobile.xqnqq.com/Article/725302.shtml
- http://www.mobile.xqnqq.com/Article/74695.shtml
- http://www.read.usuhx.com/Article/6034.shtml
- http://www.read.usuhx.com/Article/2425985.shtml
- http://www.mobile.xqnqq.com/Article/0445.shtml
- http://www.read.usuhx.com/Article/425241.shtml
- http://www.read.usuhx.com/Article/033186.shtml
- http://www.mobile.xqnqq.com/Article/71142.shtml
- http://www.read.usuhx.com/Article/6768.shtml
- http://www.read.usuhx.com/Article/5070734.shtml
- http://www.mobile.xqnqq.com/Article/7370095.shtml
- http://www.read.usuhx.com/Article/758153.shtml
- http://www.read.usuhx.com/Article/0301821.shtml
- http://www.read.usuhx.com/Article/5654303.shtml
- http://www.read.usuhx.com/Article/474621.shtml
- http://www.read.usuhx.com/Article/2858963.shtml
- http://www.mobile.xqnqq.com/Article/19480.shtml
- http://www.read.usuhx.com/Article/1756955.shtml
- http://www.mobile.xqnqq.com/Article/5314359.shtml
- http://www.mobile.xqnqq.com/Article/8514900.shtml
- http://www.read.usuhx.com/Article/463307.shtml
- http://www.read.usuhx.com/Article/10664.shtml
- http://www.mobile.xqnqq.com/Article/925288.shtml
- http://www.mobile.xqnqq.com/Article/443435.shtml
- http://www.mobile.xqnqq.com/Article/2307120.shtml
- http://www.mobile.xqnqq.com/Article/9837.shtml
- http://www.read.usuhx.com/Article/51471.shtml
- http://www.mobile.xqnqq.com/Article/335829.shtml
- http://www.mobile.xqnqq.com/Article/1245020.shtml
- http://www.read.usuhx.com/Article/08166.shtml
- http://www.read.usuhx.com/Article/2372025.shtml
- http://www.mobile.xqnqq.com/Article/7117.shtml
- http://www.read.usuhx.com/Article/069605.shtml
- http://www.mobile.xqnqq.com/Article/3229128.shtml
- http://www.read.usuhx.com/Article/0039.shtml

## 项目结构

```
weblink-corpus/
├── main.py                         # 程序入口，解析命令行参数并调度核心流程
├── config/
│   ├── settings.py                 # 全局配置项：并发数、超时时间、重试策略
│   └── whitelist.txt               # 允许处理的域名列表，每行一个
├── core/
│   ├── loader.py                   # 文件加载器，支持 txt / csv / json 输入格式
│   ├── normalizer.py               # URL 规范化：去重、排序、补全协议头
│   ├── checker.py                  # 状态检测：并发 HEAD 请求与重定向跟踪
│   └── exporter.py                 # 导出模块：支持 json / csv / sqlite / markdown
├── parsers/
│   ├── html_parser.py              # 基于 beautifulsoup 的标题与描述提取
│   └── site_adapter.py             # 站点特异性适配器，处理不同域名下的 DOM 差异
├── utils/
│   ├── logger.py                   # 日志封装，支持文件与控制台双输出
│   ├── retry.py                    # 指数退避重试装饰器
│   └── hash_util.py                # URL 与文本的摘要计算，用于快速比对
├── tests/
│   ├── test_normalizer.py          # 规范化模块的单元测试
│   ├── test_checker.py             # 状态检测模块的单元测试
│   └── fixtures/                   # 测试用的样本数据目录
├── reports/                        # 默认输出目录，存放生成的报告文件
├── scripts/
│   ├── daily_check.sh              # 每日定时执行的包装脚本
│   └── migrate_db.py               # SQLite 数据库结构升级工具
├── requirements.txt                # 生产环境依赖清单
├── requirements-dev.txt            # 开发环境额外依赖
├── Dockerfile                      # 容器化构建文件，基于 python:3.10-slim
├── docker-compose.yml              # 本地测试用编排文件
└── README.md                       # 本文档
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库，并克隆到本地开发环境。确保使用 Python 3.10 及以上版本，并安装开发依赖 `pip install -r requirements-dev.txt`。

2. 新建功能分支，分支命名采用 `feature/` 或 `fix/` 前缀加简要描述，例如 `feature/add-json-export`。所有代码提交前需运行 `black` 格式化与 `mypy` 类型检查。

3. 编写或更新单元测试，覆盖新增功能或修复的缺陷。测试用例需放置在 `tests/` 目录下，并确保 `pytest` 全部通过。

4. 更新文档，包括本 README 中的功能概览或配置项说明，以及 `docs/` 下对应的用户手册或开发指南。

5. 提交 pull request 到主分支，描述中需明确说明变更内容、影响范围以及测试结果。等待维护者 code review 并通过后合并。

## 常见问题

**问：程序运行时报错 "ImportError: No module named lxml"，应如何处理？**

答：lxml 为可选解析器后端，但强烈建议安装以获得更好的解析性能。若系统缺少编译依赖，可执行 `pip install lxml` 前先安装系统级 libxml2 与 libxslt 开发包。在 Debian 系系统上为 `apt-get install libxml2-dev libxslt1-dev`，在 RHEL 系上为 `yum install libxml2-devel libxslt-devel`。

**问：如何自定义超时时间和重试次数以应对网络不稳定环境？**

答：可在 `config/settings.py` 中修改 `REQUEST_TIMEOUT`（默认 10 秒）和 `MAX_RETRIES`（默认 3 次）变量。也可以通过命令行参数 `--timeout` 和 `--retries` 临时覆盖，具体用法参考 `python main.py --help`。

**问：输入文件支持哪些编码格式？**

答：程序默认以 UTF-8 编码读取输入文件，同时自动检测 BOM 头并兼容 UTF-8-SIG 格式。若处理 GBK 或 GB2312 编码的文件，请先使用 `iconv` 或 `chardet` 转换为 UTF-8，或修改 `config/settings.py` 中的 `INPUT_ENCODING` 配置项。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
