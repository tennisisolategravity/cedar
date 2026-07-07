# WebLink Navigator

WebLink Navigator 是一个面向技术研究、内容聚合与知识工程场景的轻量级外链资源归集系统。该项目定位于解决分散于多个内容源、缺乏结构化组织的 URL 资源的统一收录、分类展示与可追溯访问问题。目标用户包括技术文档维护者、数据采集工程师、知识库管理员以及需要进行大规模外链审计与迁移的运维团队。

该项目不提供爬虫、索引或内容解析功能，专注于以人工可维护、机器可读的方式，对给定的外链集合进行规范化登记与可浏览化呈现。通过本项目提供的资源清单与目录结构，用户可快速定位特定批次的外链数据，并据此开展二次开发，例如链接可用性检测、元数据补全、访问频率统计或内容归档映射。

## 功能概览

- **外链清单化管理**：提供按批次、按来源域名的扁平化资源列表，支持人工审核与批量导出。
- **双源归集支持**：原生兼容 http://map.read.usuhx.com 与 http://map.mobile.xqnqq.com 两个内容源路径格式，保留原始 URL 参数与文件名。
- **批次元数据标识**：每个资源条目附带批次编号与来源标识，便于追踪数据收录阶段与责任归属。
- **纯静态目录树导航**：项目结构采用 ASCII 目录树描述，无需额外服务即可了解资源组织方式。
- **依赖清单透明化**：通过依赖表格明确列出运行环境所需的全部组件及其版本要求，降低部署门槛。
- **快速启动脚本**：提供从克隆到运行的三步 Shell 命令，适用于 Linux 与 macOS 开发环境。
- **文档分层导航**：将文档分为入门、运维、开发与 FAQ 四个层面，便于不同角色快速切入。
- **贡献流程标准化**：明确分支命名、提交规范与合并请求模板，保障协作质量。

## 应用场景

- **技术文档站外链审计**：技术团队在重构文档站点时，可利用本资源清单快速盘点所有引用的外部文章链接，逐一检查可用性与内容变更情况，避免文档中出现死链或失效引用。
- **数据采集任务配置校验**：数据工程师在配置采集任务前，可将待采集的 URL 清单导入本项目进行格式校验与去重，确认来源域名与路径模式符合预期，减少采集任务中的异常中断。
- **知识库资源导入前预处理**：知识库管理员在批量导入第三方文章链接前，通过本项目对 URL 进行规范化登记与分类标记，确保导入后的链接可在知识库内被正确索引与检索。
- **外链迁移与域名替换映射**：当内容源域名发生变更时，运维人员可基于本清单批量生成替换规则，测试新旧 URL 的映射关系，降低迁移过程中的遗漏风险。

## 快速开始

以下命令适用于 Linux 与 macOS 环境，请确保已安装 Git 与 Python 3.8 及以上版本。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/weblink-navigator.git
cd weblink-navigator

# 安装依赖（使用 pip 虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 运行资源校验脚本（验证所有 URL 格式）
python scripts/validate_urls.py --batch 68
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 或更高 | 运行校验与辅助脚本的核心解释器 |
| Git | 2.20 或更高 | 克隆仓库与版本管理 |
| pip | 20.0 或更高 | Python 包管理工具 |
| virtualenv | 可选 | 推荐用于创建隔离的 Python 环境 |
| pytest | 7.0 或更高 | 仅开发测试时需要，用于运行单元测试 |
| requests | 2.28 或更高 | 用于发送 HTTP 请求验证链接可达性 |
| pyyaml | 6.0 或更高 | 用于解析 YAML 格式的配置文件 |
| markdown | 3.4 或更高 | 用于生成文档预览（仅开发模式） |
| shellcheck | 0.8 或更高 | 用于检查 Shell 脚本语法（仅 CI 环境） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | docs/getting-started.md | 如何快速部署本项目、如何理解资源列表的组织方式、如何运行首个校验命令 |
| 运维手册 | docs/operations.md | 如何更新资源列表、如何添加新批次、如何执行链接健康检查、如何备份清单数据 |
| 开发参考 | docs/development.md | 如何扩展校验规则、如何编写新的 URL 处理脚本、如何提交代码变更与测试用例 |
| 常见问题 | docs/faq.md | 遇到 URL 格式报错怎么办、如何批量替换域名前缀、如何导出为 CSV 或 JSON 格式 |

## 资源列表

- http://map.read.usuhx.com/Article/7210166.shtml
- http://map.mobile.xqnqq.com/Article/60859.shtml
- http://map.mobile.xqnqq.com/Article/8307620.shtml
- http://map.read.usuhx.com/Article/474838.shtml
- http://map.mobile.xqnqq.com/Article/7767.shtml
- http://map.mobile.xqnqq.com/Article/5482835.shtml
- http://map.read.usuhx.com/Article/159959.shtml
- http://map.mobile.xqnqq.com/Article/8948.shtml
- http://map.read.usuhx.com/Article/118953.shtml
- http://map.read.usuhx.com/Article/653041.shtml
- http://map.mobile.xqnqq.com/Article/6582512.shtml
- http://map.read.usuhx.com/Article/33529.shtml
- http://map.read.usuhx.com/Article/91284.shtml
- http://map.mobile.xqnqq.com/Article/9598.shtml
- http://map.read.usuhx.com/Article/010766.shtml
- http://map.mobile.xqnqq.com/Article/7886.shtml
- http://map.read.usuhx.com/Article/744642.shtml
- http://map.read.usuhx.com/Article/1097340.shtml
- http://map.read.usuhx.com/Article/5549217.shtml
- http://map.mobile.xqnqq.com/Article/90402.shtml
- http://map.read.usuhx.com/Article/164800.shtml
- http://map.mobile.xqnqq.com/Article/250044.shtml
- http://map.mobile.xqnqq.com/Article/061369.shtml
- http://map.mobile.xqnqq.com/Article/923946.shtml
- http://map.mobile.xqnqq.com/Article/932298.shtml
- http://map.mobile.xqnqq.com/Article/9693.shtml
- http://map.read.usuhx.com/Article/338712.shtml
- http://map.read.usuhx.com/Article/69897.shtml
- http://map.read.usuhx.com/Article/122775.shtml
- http://map.mobile.xqnqq.com/Article/3379.shtml
- http://map.read.usuhx.com/Article/1326.shtml
- http://map.read.usuhx.com/Article/8957.shtml
- http://map.mobile.xqnqq.com/Article/9110852.shtml
- http://map.read.usuhx.com/Article/29379.shtml
- http://map.mobile.xqnqq.com/Article/3135495.shtml
- http://map.mobile.xqnqq.com/Article/10407.shtml
- http://map.mobile.xqnqq.com/Article/62746.shtml
- http://map.mobile.xqnqq.com/Article/02244.shtml
- http://map.mobile.xqnqq.com/Article/9669.shtml
- http://map.read.usuhx.com/Article/4432154.shtml
- http://map.read.usuhx.com/Article/3512247.shtml
- http://map.read.usuhx.com/Article/47658.shtml
- http://map.read.usuhx.com/Article/3462.shtml
- http://map.mobile.xqnqq.com/Article/5317.shtml
- http://map.read.usuhx.com/Article/6871783.shtml
- http://map.read.usuhx.com/Article/056771.shtml
- http://map.read.usuhx.com/Article/819952.shtml
- http://map.mobile.xqnqq.com/Article/281774.shtml
- http://map.read.usuhx.com/Article/0080.shtml
- http://map.mobile.xqnqq.com/Article/2134801.shtml
- http://map.mobile.xqnqq.com/Article/86513.shtml
- http://map.mobile.xqnqq.com/Article/936730.shtml
- http://map.mobile.xqnqq.com/Article/381705.shtml
- http://map.mobile.xqnqq.com/Article/1171316.shtml
- http://map.mobile.xqnqq.com/Article/7564.shtml
- http://map.mobile.xqnqq.com/Article/3400.shtml
- http://map.mobile.xqnqq.com/Article/7276897.shtml
- http://map.read.usuhx.com/Article/2813018.shtml
- http://map.mobile.xqnqq.com/Article/468989.shtml
- http://map.mobile.xqnqq.com/Article/8381.shtml
- http://map.mobile.xqnqq.com/Article/86169.shtml
- http://map.read.usuhx.com/Article/588530.shtml
- http://map.mobile.xqnqq.com/Article/550590.shtml
- http://map.read.usuhx.com/Article/4997.shtml
- http://map.mobile.xqnqq.com/Article/7089.shtml
- http://map.mobile.xqnqq.com/Article/511751.shtml
- http://map.read.usuhx.com/Article/1160.shtml
- http://map.read.usuhx.com/Article/9110.shtml
- http://map.mobile.xqnqq.com/Article/01471.shtml
- http://map.read.usuhx.com/Article/217148.shtml
- http://map.mobile.xqnqq.com/Article/760342.shtml
- http://map.mobile.xqnqq.com/Article/0065179.shtml
- http://map.read.usuhx.com/Article/64384.shtml
- http://map.mobile.xqnqq.com/Article/13911.shtml
- http://map.mobile.xqnqq.com/Article/809638.shtml
- http://map.mobile.xqnqq.com/Article/4309457.shtml
- http://map.read.usuhx.com/Article/3326139.shtml
- http://map.mobile.xqnqq.com/Article/633571.shtml
- http://map.read.usuhx.com/Article/6092.shtml
- http://map.read.usuhx.com/Article/2399498.shtml
- http://map.read.usuhx.com/Article/21700.shtml
- http://map.read.usuhx.com/Article/75393.shtml
- http://map.read.usuhx.com/Article/70406.shtml
- http://map.read.usuhx.com/Article/9416904.shtml
- http://map.read.usuhx.com/Article/1578746.shtml
- http://map.read.usuhx.com/Article/83167.shtml
- http://map.mobile.xqnqq.com/Article/3970.shtml
- http://map.mobile.xqnqq.com/Article/4721261.shtml
- http://map.mobile.xqnqq.com/Article/4032.shtml
- http://map.mobile.xqnqq.com/Article/88160.shtml
- http://map.mobile.xqnqq.com/Article/635743.shtml
- http://map.read.usuhx.com/Article/499575.shtml
- http://map.read.usuhx.com/Article/8357.shtml
- http://map.read.usuhx.com/Article/2559263.shtml
- http://map.mobile.xqnqq.com/Article/4080740.shtml
- http://map.mobile.xqnqq.com/Article/2296811.shtml
- http://map.mobile.xqnqq.com/Article/67017.shtml
- http://map.mobile.xqnqq.com/Article/700379.shtml
- http://map.mobile.xqnqq.com/Article/7175420.shtml
- http://map.mobile.xqnqq.com/Article/7394.shtml
- http://map.read.usuhx.com/Article/9864.shtml
- http://map.mobile.xqnqq.com/Article/01489.shtml
- http://map.read.usuhx.com/Article/23163.shtml
- http://map.mobile.xqnqq.com/Article/38140.shtml
- http://map.read.usuhx.com/Article/5535.shtml
- http://map.read.usuhx.com/Article/27106.shtml
- http://map.read.usuhx.com/Article/5082091.shtml
- http://map.mobile.xqnqq.com/Article/717531.shtml
- http://map.mobile.xqnqq.com/Article/848693.shtml
- http://map.mobile.xqnqq.com/Article/571077.shtml
- http://map.mobile.xqnqq.com/Article/3282.shtml
- http://map.read.usuhx.com/Article/254579.shtml
- http://map.read.usuhx.com/Article/455562.shtml
- http://map.mobile.xqnqq.com/Article/85170.shtml
- http://map.mobile.xqnqq.com/Article/87583.shtml
- http://map.read.usuhx.com/Article/86982.shtml
- http://map.read.usuhx.com/Article/0358315.shtml
- http://map.read.usuhx.com/Article/323910.shtml
- http://map.read.usuhx.com/Article/69180.shtml
- http://map.read.usuhx.com/Article/85467.shtml
- http://map.mobile.xqnqq.com/Article/4514.shtml
- http://map.mobile.xqnqq.com/Article/2503.shtml
- http://map.mobile.xqnqq.com/Article/58571.shtml
- http://map.mobile.xqnqq.com/Article/14486.shtml
- http://map.read.usuhx.com/Article/7775171.shtml
- http://map.mobile.xqnqq.com/Article/3635.shtml
- http://map.read.usuhx.com/Article/683692.shtml
- http://map.read.usuhx.com/Article/373695.shtml
- http://map.mobile.xqnqq.com/Article/25587.shtml
- http://map.mobile.xqnqq.com/Article/8820.shtml
- http://map.mobile.xqnqq.com/Article/392227.shtml
- http://map.mobile.xqnqq.com/Article/2589.shtml
- http://map.read.usuhx.com/Article/72204.shtml
- http://map.read.usuhx.com/Article/073324.shtml
- http://map.mobile.xqnqq.com/Article/1422600.shtml
- http://map.read.usuhx.com/Article/356414.shtml
- http://map.read.usuhx.com/Article/2559.shtml
- http://map.mobile.xqnqq.com/Article/6802105.shtml
- http://map.mobile.xqnqq.com/Article/21256.shtml
- http://map.mobile.xqnqq.com/Article/2940998.shtml
- http://map.read.usuhx.com/Article/816790.shtml
- http://map.mobile.xqnqq.com/Article/67408.shtml
- http://map.read.usuhx.com/Article/56482.shtml
- http://map.mobile.xqnqq.com/Article/96480.shtml
- http://map.read.usuhx.com/Article/63916.shtml
- http://map.mobile.xqnqq.com/Article/7915812.shtml
- http://map.read.usuhx.com/Article/39387.shtml
- http://map.read.usuhx.com/Article/2118042.shtml
- http://map.read.usuhx.com/Article/12795.shtml
- http://map.mobile.xqnqq.com/Article/42542.shtml
- http://map.mobile.xqnqq.com/Article/7733406.shtml
- http://map.read.usuhx.com/Article/0833.shtml
- http://map.read.usuhx.com/Article/04684.shtml
- http://map.read.usuhx.com/Article/52066.shtml
- http://map.mobile.xqnqq.com/Article/53932.shtml
- http://map.read.usuhx.com/Article/67047.shtml
- http://map.read.usuhx.com/Article/0203816.shtml
- http://map.mobile.xqnqq.com/Article/884615.shtml
- http://map.read.usuhx.com/Article/253242.shtml
- http://map.mobile.xqnqq.com/Article/111069.shtml
- http://map.read.usuhx.com/Article/28235.shtml
- http://map.read.usuhx.com/Article/564937.shtml
- http://map.mobile.xqnqq.com/Article/5167.shtml
- http://map.read.usuhx.com/Article/7944.shtml
- http://map.mobile.xqnqq.com/Article/822636.shtml
- http://map.read.usuhx.com/Article/077521.shtml
- http://map.mobile.xqnqq.com/Article/89413.shtml
- http://map.mobile.xqnqq.com/Article/7293367.shtml
- http://map.read.usuhx.com/Article/5958754.shtml
- http://map.mobile.xqnqq.com/Article/05965.shtml
- http://map.read.usuhx.com/Article/577451.shtml
- http://map.read.usuhx.com/Article/754351.shtml
- http://map.read.usuhx.com/Article/039787.shtml
- http://map.mobile.xqnqq.com/Article/7559859.shtml
- http://map.read.usuhx.com/Article/062218.shtml
- http://map.read.usuhx.com/Article/8823589.shtml
- http://map.read.usuhx.com/Article/0040.shtml
- http://map.read.usuhx.com/Article/64822.shtml
- http://map.mobile.xqnqq.com/Article/0558.shtml
- http://map.mobile.xqnqq.com/Article/56798.shtml
- http://map.mobile.xqnqq.com/Article/1987.shtml
- http://map.mobile.xqnqq.com/Article/0443205.shtml
- http://map.mobile.xqnqq.com/Article/1491088.shtml
- http://map.read.usuhx.com/Article/42133.shtml
- http://map.read.usuhx.com/Article/2038.shtml
- http://map.read.usuhx.com/Article/4583935.shtml
- http://map.read.usuhx.com/Article/5583902.shtml
- http://map.mobile.xqnqq.com/Article/0084.shtml
- http://map.mobile.xqnqq.com/Article/144681.shtml
- http://map.read.usuhx.com/Article/221760.shtml
- http://map.read.usuhx.com/Article/9138.shtml
- http://map.mobile.xqnqq.com/Article/059402.shtml
- http://map.mobile.xqnqq.com/Article/1006.shtml
- http://map.mobile.xqnqq.com/Article/8158913.shtml
- http://map.read.usuhx.com/Article/877985.shtml
- http://map.read.usuhx.com/Article/03895.shtml
- http://map.read.usuhx.com/Article/9103.shtml
- http://map.read.usuhx.com/Article/7985.shtml
- http://map.read.usuhx.com/Article/6438977.shtml
- http://map.mobile.xqnqq.com/Article/1252.shtml
- http://map.mobile.xqnqq.com/Article/2357.shtml
- http://map.read.usuhx.com/Article/62413.shtml
- http://map.mobile.xqnqq.com/Article/796774.shtml
- http://map.read.usuhx.com/Article/54687.shtml
- http://map.mobile.xqnqq.com/Article/083819.shtml
- http://map.mobile.xqnqq.com/Article/8125.shtml
- http://map.mobile.xqnqq.com/Article/165603.shtml
- http://map.mobile.xqnqq.com/Article/6746.shtml
- http://map.read.usuhx.com/Article/1520046.shtml
- http://map.read.usuhx.com/Article/889226.shtml
- http://map.read.usuhx.com/Article/7466227.shtml
- http://map.read.usuhx.com/Article/3503.shtml
- http://map.mobile.xqnqq.com/Article/5571.shtml
- http://map.read.usuhx.com/Article/8984623.shtml
- http://map.mobile.xqnqq.com/Article/1028410.shtml
- http://map.mobile.xqnqq.com/Article/1090002.shtml
- http://map.read.usuhx.com/Article/128405.shtml
- http://map.mobile.xqnqq.com/Article/487217.shtml
- http://map.mobile.xqnqq.com/Article/83268.shtml
- http://map.read.usuhx.com/Article/1404356.shtml
- http://map.mobile.xqnqq.com/Article/963459.shtml
- http://map.read.usuhx.com/Article/424996.shtml
- http://map.read.usuhx.com/Article/2292701.shtml
- http://map.read.usuhx.com/Article/528206.shtml
- http://map.read.usuhx.com/Article/10137.shtml
- http://map.read.usuhx.com/Article/589950.shtml
- http://map.read.usuhx.com/Article/519820.shtml
- http://map.mobile.xqnqq.com/Article/3602.shtml
- http://map.mobile.xqnqq.com/Article/893795.shtml
- http://map.mobile.xqnqq.com/Article/2261312.shtml
- http://map.mobile.xqnqq.com/Article/945384.shtml
- http://map.mobile.xqnqq.com/Article/79994.shtml
- http://map.mobile.xqnqq.com/Article/588697.shtml
- http://map.read.usuhx.com/Article/0448681.shtml
- http://map.read.usuhx.com/Article/8897768.shtml
- http://map.read.usuhx.com/Article/94887.shtml
- http://map.mobile.xqnqq.com/Article/339832.shtml
- http://map.mobile.xqnqq.com/Article/026234.shtml
- http://map.mobile.xqnqq.com/Article/93659.shtml
- http://map.mobile.xqnqq.com/Article/317476.shtml
- http://map.read.usuhx.com/Article/6585795.shtml
- http://map.read.usuhx.com/Article/28766.shtml
- http://map.read.usuhx.com/Article/75797.shtml
- http://map.mobile.xqnqq.com/Article/4710.shtml
- http://map.mobile.xqnqq.com/Article/7811.shtml
- http://map.mobile.xqnqq.com/Article/0706.shtml
- http://map.read.usuhx.com/Article/2470.shtml
- http://map.mobile.xqnqq.com/Article/21767.shtml
- http://map.mobile.xqnqq.com/Article/7297705.shtml
- http://map.mobile.xqnqq.com/Article/11804.shtml

## 项目结构

```
weblink-navigator/
├── data/                                  # 资源数据存储目录
│   ├── batches/                           # 按批次组织的资源清单
│   │   ├── batch_068.json                 # 第68批资源元数据（含收录时间、来源域）
│   │   └── batch_069.json                 # 第69批资源清单模板
│   ├── schemas/                           # JSON Schema 校验定义
│   │   └── url_entry.schema.json          # 单个 URL 条目的校验规则
│   └── manifests/                         # 全量资源清单聚合文件
│       └── full_manifest.lock             # 所有批次的锁定清单，用于去重校验
├── scripts/                               # 运维与工具脚本
│   ├── validate_urls.py                   # URL 格式校验脚本（支持批量与单条模式）
│   ├── check_reachability.py              # 链接可达性检测脚本（基于 requests）
│   ├── export_csv.py                      # 将资源清单导出为 CSV 格式
│   └── batch_import.sh                    # 批量导入新 URL 的 Shell 辅助脚本
├── tests/                                 # 单元测试与集成测试
│   ├── test_validate.py                   # validate_urls 的测试用例
│   ├── test_export.py                     # 导出功能的测试用例
│   └── fixtures/                          # 测试用的固定数据样本
│       └── sample_urls.txt
├── docs/                                  # 项目文档
│   ├── getting-started.md                 # 入门指南
│   ├── operations.md                      # 运维手册
│   ├── development.md                     # 开发参考
│   └── faq.md                             # 常见问题
├── config/                                # 项目配置文件
│   ├── settings.yaml                      # 全局设置（超时时间、重试次数、输出路径）
│   └── allowed_domains.yaml               # 允许收录的域名白名单
├── .github/                               # GitHub 协作配置
│   └── workflows/                         # CI 流水线定义
│       └── validate_on_push.yml           # 每次推送时自动执行 URL 校验
├── requirements.txt                       # Python 运行时依赖列表
├── Makefile                               # 常用任务快捷命令（如 make test、make lint）
└── README.md                              # 项目主文档（本文件）
```

## 贡献指南

1. **分支命名与创建**：从 main 分支切出 feature/ 或 fix/ 前缀的新分支，例如 feature/add-batch-70 或 fix/url-format-error。分支名称应简洁描述本次变更的内容。
2. **资源列表更新流程**：若需新增或修改资源列表，请编辑 data/batches/ 下对应的批次 JSON 文件，确保每个 URL 对象包含 "url"、"source_domain"、"recorded_at" 三个字段。提交前运行 scripts/validate_urls.py 进行本地校验。
3. **代码变更提交规范**：提交信息应遵循 "类型: 简短描述" 的格式，类型包括 feat、fix、docs、chore、test 等。例如 "feat: add reachability check retry mechanism"。提交前确保通过所有单元测试（pytest tests/）。
4. **合并请求描述要求**：提交 Pull Request 时，需在描述中说明变更动机、影响范围以及测试结果。若涉及资源列表变动，请附上校验脚本的输出日志。至少需要一名项目维护者审核通过后方可合并。
5. **文档同步更新**：任何影响使用方式或配置项的变更，必须同步更新 docs/ 下对应的文档章节。新增脚本或配置项时，需在 README 的项目结构部分补充说明。

## 常见问题

**Q: 为什么资源列表中的 URL 包含数字编号，这些编号是否有实际含义？**

A: 这些编号为原始内容源系统的文章标识符，本项目仅做原样收录，不解析其业务含义。编号用于保证每个 URL 在源系统内的唯一性，便于后续追溯与去重。本项目不依赖编号连续性，也不对编号进行校验或补全。

**Q: 如何批量检查资源列表中的链接是否仍然可访问？**

A: 项目提供了 scripts/check_reachability.py 脚本，可发送 HEAD 或 GET 请求验证链接状态。建议在低峰时段运行，并设置合理的超时（默认 5 秒）与重试次数（默认 2 次），以避免对源服务器造成压力。运行示例：python scripts/check_reachability.py --batch 68 --timeout 3 --retry 1。

**Q: 项目支持添加新的来源域名吗？**

A: 支持。请在 config/allowed_domains.yaml 中添加新域名的正则表达式或精确匹配规则，然后运行校验脚本验证格式。注意新增域名需要经过项目维护者审核，以确保资源来源的合规性与稳定性。若需临时添加而不修改白名单，可使用 --allow-any-domain 参数绕过校验，但该模式不建议在生产环境使用。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
