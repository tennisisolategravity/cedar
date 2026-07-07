# WebIndexer

WebIndexer 是一个面向技术调研、内容聚合与批量外链管理的静态站点生成工具。该项目定位于帮助开发者、技术文档撰写者及运维人员快速构建一个结构清晰、可检索、可分类的 URL 资源导航站，特别适用于处理大批量（百级至万级）外链数据的整理与展示。WebIndexer 本身不依赖数据库或后端服务，所有资源列表在构建时生成静态 HTML 与 Markdown 索引文件，可直接部署至任意 HTTP 服务器或对象存储服务。

## 功能概览

**批量 URL 导入与清洗**：支持从纯文本文件、CSV 或直接粘贴的 URL 列表中自动识别并提取有效链接，自动去除重复项、规范化空白字符。

**多层级分类索引**：支持基于 URL 中的域名、路径关键字或用户自定义标签生成两级分类目录，每个分类自动生成独立的索引页面。

**可配置的元数据提取**：在构建过程中可对每个 URL 发起 HEAD 请求以获取 Content-Type 与最后修改时间，可选地截取页面标题（通过正则或简单 HTML 解析）作为链接描述。

**纯静态输出**：构建产物全部为 HTML、CSS 与 Markdown 文件，不依赖任何运行时环境，可直接通过浏览器访问，也支持通过 Markdown 渲染器查看资源列表。

**灵活的模板覆盖机制**：用户可自定义首页模板、分类页模板以及列表项的渲染方式，内置默认模板基于响应式设计，适配桌面与移动端。

**增量构建与缓存**：支持将已提取的元数据缓存至本地 JSON 文件，后续构建仅处理新增或变更的 URL，显著提升大型资源列表的构建速度。

**链接可用性检查**：集成可选的链接可达性检测模块，构建时可输出失效链接报告，便于维护者及时清理或更新资源。

## 应用场景

**技术文档站的外链附录**：适用于开源项目文档站需要统一管理参考链接、引用文章或相关工具列表的场景。WebIndexer 可生成一个独立的外链附录页面，与 MkDocs、VuePress 等项目集成。

**数据调研与采集结果的预览**：数据采集工程师完成一批 URL 采集后，可使用 WebIndexer 快速生成带分类和基础元数据的预览站，便于团队内部评审或交付给业务方查看。

**运维监控仪表盘的补充视图**：运维团队可将内部监控系统、日志面板、工单系统等内部工具的访问链接通过 WebIndexer 统一编目，生成一个团队内部使用的工具导航页，减少书签管理的混乱。

**个人知识库的链接书架**：知识管理爱好者可将长期积累的阅读列表、参考文章按主题整理，通过 WebIndexer 生成可检索的静态书架页面，支持按时间或分类排序。

## 快速开始

以下步骤适用于 Linux / macOS / Windows WSL 环境，需提前安装 Git 与 Node.js 18 以上版本。

```bash
# 克隆项目仓库
git clone https://github.com/webindexer/webindexer.git
cd webindexer

# 安装项目依赖
npm install

# 执行构建：默认从 data/urls.txt 读取 URL 列表，输出至 dist/ 目录
npm run build

# 启动本地预览服务（默认监听 http://localhost:8080）
npm run serve
```

如需使用自定义输入文件或修改输出路径，可通过命令行参数指定：

```bash
npm run build -- --input ./my-links.txt --output ./my-site --cache ./cache.json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或更高 | 运行时环境，用于执行构建脚本与本地服务 |
| npm | 9.x 或更高 | 包管理器，用于安装项目依赖 |
| Git | 2.30 或更高 | 版本控制工具，用于克隆仓库与获取更新 |
| 网络连接 | 可选 | 仅在启用元数据提取或链接检查时需要对外发起 HTTP 请求 |
| 磁盘空间 | 至少 50 MB | 用于存放源码、依赖及构建产物，实际需求随资源列表规模增长 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户指南 | docs/user-guide/installation.md | 如何在不同操作系统上安装 WebIndexer 及其依赖 |
| 用户指南 | docs/user-guide/configuration.md | 如何配置输入源、分类规则、输出格式与缓存策略 |
| 开发指南 | docs/developer-guide/architecture.md | 项目的模块划分、构建流程的核心抽象与扩展接口 |
| 开发指南 | docs/developer-guide/template-system.md | 如何编写自定义模板、覆盖默认渲染逻辑及使用内置模板函数 |

## 资源列表

- http://www.read.usuhx.com/Article/7684199.shtml
- http://www.read.usuhx.com/Article/467014.shtml
- http://www.mobile.xqnqq.com/Article/27012.shtml
- http://www.mobile.xqnqq.com/Article/4307703.shtml
- http://www.mobile.xqnqq.com/Article/9191741.shtml
- http://www.read.usuhx.com/Article/098307.shtml
- http://www.mobile.xqnqq.com/Article/5922017.shtml
- http://www.read.usuhx.com/Article/69257.shtml
- http://www.mobile.xqnqq.com/Article/755909.shtml
- http://www.mobile.xqnqq.com/Article/4272.shtml
- http://www.mobile.xqnqq.com/Article/2785309.shtml
- http://www.mobile.xqnqq.com/Article/6816.shtml
- http://www.mobile.xqnqq.com/Article/3121537.shtml
- http://www.mobile.xqnqq.com/Article/6709379.shtml
- http://www.mobile.xqnqq.com/Article/28176.shtml
- http://www.mobile.xqnqq.com/Article/73574.shtml
- http://www.mobile.xqnqq.com/Article/7929.shtml
- http://www.read.usuhx.com/Article/08310.shtml
- http://www.read.usuhx.com/Article/8675402.shtml
- http://www.mobile.xqnqq.com/Article/46154.shtml
- http://www.read.usuhx.com/Article/7310570.shtml
- http://www.read.usuhx.com/Article/0151.shtml
- http://www.mobile.xqnqq.com/Article/102112.shtml
- http://www.mobile.xqnqq.com/Article/1571.shtml
- http://www.mobile.xqnqq.com/Article/676914.shtml
- http://www.read.usuhx.com/Article/1794.shtml
- http://www.mobile.xqnqq.com/Article/417314.shtml
- http://www.mobile.xqnqq.com/Article/705285.shtml
- http://www.read.usuhx.com/Article/97546.shtml
- http://www.mobile.xqnqq.com/Article/1735840.shtml
- http://www.mobile.xqnqq.com/Article/4917720.shtml
- http://www.mobile.xqnqq.com/Article/709602.shtml
- http://www.mobile.xqnqq.com/Article/8942615.shtml
- http://www.mobile.xqnqq.com/Article/203286.shtml
- http://www.read.usuhx.com/Article/6414622.shtml
- http://www.read.usuhx.com/Article/99003.shtml
- http://www.read.usuhx.com/Article/0748.shtml
- http://www.read.usuhx.com/Article/989548.shtml
- http://www.read.usuhx.com/Article/398714.shtml
- http://www.mobile.xqnqq.com/Article/0747840.shtml
- http://www.read.usuhx.com/Article/1166.shtml
- http://www.mobile.xqnqq.com/Article/33484.shtml
- http://www.read.usuhx.com/Article/911412.shtml
- http://www.read.usuhx.com/Article/60404.shtml
- http://www.mobile.xqnqq.com/Article/70779.shtml
- http://www.read.usuhx.com/Article/35274.shtml
- http://www.read.usuhx.com/Article/8279714.shtml
- http://www.mobile.xqnqq.com/Article/912690.shtml
- http://www.read.usuhx.com/Article/4080.shtml
- http://www.mobile.xqnqq.com/Article/90941.shtml
- http://www.read.usuhx.com/Article/20655.shtml
- http://www.read.usuhx.com/Article/8642.shtml
- http://www.read.usuhx.com/Article/4532698.shtml
- http://www.read.usuhx.com/Article/4724.shtml
- http://www.mobile.xqnqq.com/Article/667802.shtml
- http://www.mobile.xqnqq.com/Article/3399.shtml
- http://www.read.usuhx.com/Article/647997.shtml
- http://www.read.usuhx.com/Article/3990737.shtml
- http://www.read.usuhx.com/Article/084393.shtml
- http://www.mobile.xqnqq.com/Article/850186.shtml
- http://www.mobile.xqnqq.com/Article/67460.shtml
- http://www.read.usuhx.com/Article/875732.shtml
- http://www.read.usuhx.com/Article/8391.shtml
- http://www.read.usuhx.com/Article/3085.shtml
- http://www.read.usuhx.com/Article/7576.shtml
- http://www.read.usuhx.com/Article/3432848.shtml
- http://www.read.usuhx.com/Article/60425.shtml
- http://www.read.usuhx.com/Article/337738.shtml
- http://www.read.usuhx.com/Article/924784.shtml
- http://www.read.usuhx.com/Article/0320.shtml
- http://www.mobile.xqnqq.com/Article/451103.shtml
- http://www.read.usuhx.com/Article/30534.shtml
- http://www.read.usuhx.com/Article/497524.shtml
- http://www.mobile.xqnqq.com/Article/1210.shtml
- http://www.read.usuhx.com/Article/9653660.shtml
- http://www.read.usuhx.com/Article/4771.shtml
- http://www.mobile.xqnqq.com/Article/575406.shtml
- http://www.read.usuhx.com/Article/846097.shtml
- http://www.mobile.xqnqq.com/Article/36819.shtml
- http://www.read.usuhx.com/Article/344154.shtml
- http://www.read.usuhx.com/Article/204457.shtml
- http://www.read.usuhx.com/Article/852191.shtml
- http://www.read.usuhx.com/Article/4283.shtml
- http://www.read.usuhx.com/Article/2582.shtml
- http://www.read.usuhx.com/Article/12867.shtml
- http://www.mobile.xqnqq.com/Article/36363.shtml
- http://www.read.usuhx.com/Article/699832.shtml
- http://www.read.usuhx.com/Article/0581891.shtml
- http://www.mobile.xqnqq.com/Article/9000.shtml
- http://www.mobile.xqnqq.com/Article/11527.shtml
- http://www.read.usuhx.com/Article/0327239.shtml
- http://www.read.usuhx.com/Article/0760.shtml
- http://www.mobile.xqnqq.com/Article/20722.shtml
- http://www.mobile.xqnqq.com/Article/890341.shtml
- http://www.read.usuhx.com/Article/4290228.shtml
- http://www.read.usuhx.com/Article/0849249.shtml
- http://www.mobile.xqnqq.com/Article/2214.shtml
- http://www.read.usuhx.com/Article/3231693.shtml
- http://www.read.usuhx.com/Article/7727.shtml
- http://www.read.usuhx.com/Article/38297.shtml
- http://www.read.usuhx.com/Article/15138.shtml
- http://www.mobile.xqnqq.com/Article/80156.shtml
- http://www.read.usuhx.com/Article/264044.shtml
- http://www.mobile.xqnqq.com/Article/6143.shtml
- http://www.mobile.xqnqq.com/Article/92234.shtml
- http://www.mobile.xqnqq.com/Article/1969976.shtml
- http://www.mobile.xqnqq.com/Article/6132110.shtml
- http://www.mobile.xqnqq.com/Article/95497.shtml
- http://www.read.usuhx.com/Article/7886755.shtml
- http://www.read.usuhx.com/Article/27388.shtml
- http://www.read.usuhx.com/Article/7147.shtml
- http://www.mobile.xqnqq.com/Article/980230.shtml
- http://www.mobile.xqnqq.com/Article/50605.shtml
- http://www.read.usuhx.com/Article/0346.shtml
- http://www.read.usuhx.com/Article/28316.shtml
- http://www.mobile.xqnqq.com/Article/36907.shtml
- http://www.read.usuhx.com/Article/4959911.shtml
- http://www.mobile.xqnqq.com/Article/4083.shtml
- http://www.read.usuhx.com/Article/19181.shtml
- http://www.read.usuhx.com/Article/367528.shtml
- http://www.mobile.xqnqq.com/Article/0500458.shtml
- http://www.mobile.xqnqq.com/Article/2754.shtml
- http://www.mobile.xqnqq.com/Article/6105718.shtml
- http://www.read.usuhx.com/Article/57213.shtml
- http://www.read.usuhx.com/Article/748975.shtml
- http://www.mobile.xqnqq.com/Article/104570.shtml
- http://www.mobile.xqnqq.com/Article/16272.shtml
- http://www.mobile.xqnqq.com/Article/13516.shtml
- http://www.read.usuhx.com/Article/293565.shtml
- http://www.mobile.xqnqq.com/Article/533957.shtml
- http://www.read.usuhx.com/Article/1637485.shtml
- http://www.read.usuhx.com/Article/6053.shtml
- http://www.mobile.xqnqq.com/Article/6557.shtml
- http://www.mobile.xqnqq.com/Article/595813.shtml
- http://www.read.usuhx.com/Article/3394.shtml
- http://www.mobile.xqnqq.com/Article/015879.shtml
- http://www.read.usuhx.com/Article/9918492.shtml
- http://www.read.usuhx.com/Article/0873675.shtml
- http://www.read.usuhx.com/Article/40439.shtml
- http://www.read.usuhx.com/Article/4156644.shtml
- http://www.mobile.xqnqq.com/Article/5023639.shtml
- http://www.mobile.xqnqq.com/Article/3108.shtml
- http://www.read.usuhx.com/Article/9727109.shtml
- http://www.read.usuhx.com/Article/39701.shtml
- http://www.mobile.xqnqq.com/Article/15757.shtml
- http://www.read.usuhx.com/Article/06928.shtml
- http://www.mobile.xqnqq.com/Article/57815.shtml
- http://www.read.usuhx.com/Article/90361.shtml
- http://www.read.usuhx.com/Article/1913539.shtml
- http://www.mobile.xqnqq.com/Article/2379.shtml
- http://www.read.usuhx.com/Article/46357.shtml
- http://www.mobile.xqnqq.com/Article/15867.shtml
- http://www.mobile.xqnqq.com/Article/170332.shtml
- http://www.read.usuhx.com/Article/132432.shtml
- http://www.mobile.xqnqq.com/Article/7173.shtml
- http://www.mobile.xqnqq.com/Article/564337.shtml
- http://www.mobile.xqnqq.com/Article/248019.shtml
- http://www.read.usuhx.com/Article/70752.shtml
- http://www.mobile.xqnqq.com/Article/916883.shtml
- http://www.mobile.xqnqq.com/Article/013344.shtml
- http://www.read.usuhx.com/Article/50496.shtml
- http://www.mobile.xqnqq.com/Article/4253.shtml
- http://www.read.usuhx.com/Article/3214201.shtml
- http://www.read.usuhx.com/Article/93612.shtml
- http://www.read.usuhx.com/Article/021937.shtml
- http://www.mobile.xqnqq.com/Article/077552.shtml
- http://www.mobile.xqnqq.com/Article/3702152.shtml
- http://www.mobile.xqnqq.com/Article/847214.shtml
- http://www.read.usuhx.com/Article/81506.shtml
- http://www.read.usuhx.com/Article/45754.shtml
- http://www.mobile.xqnqq.com/Article/622812.shtml
- http://www.mobile.xqnqq.com/Article/5294209.shtml
- http://www.read.usuhx.com/Article/1799838.shtml
- http://www.read.usuhx.com/Article/0310874.shtml
- http://www.mobile.xqnqq.com/Article/3015078.shtml
- http://www.mobile.xqnqq.com/Article/4966877.shtml
- http://www.mobile.xqnqq.com/Article/6224030.shtml
- http://www.mobile.xqnqq.com/Article/9772.shtml
- http://www.read.usuhx.com/Article/8538847.shtml
- http://www.mobile.xqnqq.com/Article/268025.shtml
- http://www.read.usuhx.com/Article/8342934.shtml
- http://www.read.usuhx.com/Article/22617.shtml
- http://www.mobile.xqnqq.com/Article/34658.shtml
- http://www.mobile.xqnqq.com/Article/9199.shtml
- http://www.mobile.xqnqq.com/Article/2580.shtml
- http://www.mobile.xqnqq.com/Article/5125753.shtml
- http://www.read.usuhx.com/Article/9890.shtml
- http://www.mobile.xqnqq.com/Article/4379.shtml
- http://www.read.usuhx.com/Article/6224201.shtml
- http://www.mobile.xqnqq.com/Article/0799446.shtml
- http://www.read.usuhx.com/Article/9086493.shtml
- http://www.mobile.xqnqq.com/Article/1557.shtml
- http://www.mobile.xqnqq.com/Article/8754.shtml
- http://www.read.usuhx.com/Article/45468.shtml
- http://www.read.usuhx.com/Article/817189.shtml
- http://www.mobile.xqnqq.com/Article/6297.shtml
- http://www.mobile.xqnqq.com/Article/001505.shtml
- http://www.mobile.xqnqq.com/Article/9651951.shtml
- http://www.mobile.xqnqq.com/Article/6037984.shtml
- http://www.read.usuhx.com/Article/539116.shtml
- http://www.read.usuhx.com/Article/77737.shtml
- http://www.read.usuhx.com/Article/0011.shtml
- http://www.read.usuhx.com/Article/3847.shtml
- http://www.mobile.xqnqq.com/Article/050923.shtml
- http://www.mobile.xqnqq.com/Article/01052.shtml
- http://www.read.usuhx.com/Article/104170.shtml
- http://www.read.usuhx.com/Article/01522.shtml
- http://www.mobile.xqnqq.com/Article/21186.shtml
- http://www.read.usuhx.com/Article/3603022.shtml
- http://www.mobile.xqnqq.com/Article/6241.shtml
- http://www.read.usuhx.com/Article/5848.shtml
- http://www.mobile.xqnqq.com/Article/1643155.shtml
- http://www.mobile.xqnqq.com/Article/17345.shtml
- http://www.read.usuhx.com/Article/6473599.shtml
- http://www.mobile.xqnqq.com/Article/9061.shtml
- http://www.mobile.xqnqq.com/Article/1788.shtml
- http://www.mobile.xqnqq.com/Article/59757.shtml
- http://www.mobile.xqnqq.com/Article/377203.shtml
- http://www.mobile.xqnqq.com/Article/2793.shtml
- http://www.read.usuhx.com/Article/99354.shtml
- http://www.mobile.xqnqq.com/Article/5689104.shtml
- http://www.mobile.xqnqq.com/Article/0914944.shtml
- http://www.mobile.xqnqq.com/Article/721272.shtml
- http://www.mobile.xqnqq.com/Article/5859046.shtml
- http://www.read.usuhx.com/Article/981647.shtml
- http://www.mobile.xqnqq.com/Article/0418000.shtml
- http://www.read.usuhx.com/Article/410834.shtml
- http://www.mobile.xqnqq.com/Article/74707.shtml
- http://www.mobile.xqnqq.com/Article/81285.shtml
- http://www.mobile.xqnqq.com/Article/25753.shtml
- http://www.mobile.xqnqq.com/Article/1770.shtml
- http://www.mobile.xqnqq.com/Article/392216.shtml
- http://www.mobile.xqnqq.com/Article/00327.shtml
- http://www.mobile.xqnqq.com/Article/467073.shtml
- http://www.mobile.xqnqq.com/Article/41817.shtml
- http://www.mobile.xqnqq.com/Article/603137.shtml
- http://www.read.usuhx.com/Article/1196.shtml
- http://www.mobile.xqnqq.com/Article/6999536.shtml
- http://www.read.usuhx.com/Article/597896.shtml
- http://www.mobile.xqnqq.com/Article/78288.shtml
- http://www.read.usuhx.com/Article/3830280.shtml
- http://www.mobile.xqnqq.com/Article/6343597.shtml
- http://www.read.usuhx.com/Article/0345541.shtml
- http://www.mobile.xqnqq.com/Article/6259674.shtml
- http://www.mobile.xqnqq.com/Article/213335.shtml
- http://www.mobile.xqnqq.com/Article/7236809.shtml
- http://www.mobile.xqnqq.com/Article/9185903.shtml
- http://www.mobile.xqnqq.com/Article/6136709.shtml
- http://www.mobile.xqnqq.com/Article/4676344.shtml
- http://www.read.usuhx.com/Article/844226.shtml

## 项目结构

```
webindexer/
├── bin/                                 # 命令行入口脚本
│   └── webindexer.js                    # 主 CLI 入口，负责解析参数与调用构建器
├── src/                                 # 核心源码目录
│   ├── core/                            # 构建流程核心模块
│   │   ├── builder.js                   # 构建编排器，协调输入解析、分类与输出
│   │   ├── cache-manager.js             # 缓存读写、增量更新与失效判断
│   │   └── link-processor.js            # URL 清洗、去重、元数据提取与状态检查
│   ├── parsers/                         # 输入解析器
│   │   ├── txt-parser.js                # 纯文本格式解析，每行一个 URL
│   │   └── csv-parser.js                # CSV 格式解析，支持自定义列映射
│   ├── generators/                      # 输出生成器
│   │   ├── html-generator.js            # 生成 HTML 索引页与详情页
│   │   └── markdown-generator.js        # 生成 Markdown 格式的资源列表与分类索引
│   ├── templates/                       # 内建模板
│   │   ├── default/                     # 默认响应式模板
│   │   │   ├── index.html               # 首页模板
│   │   │   ├── category.html            # 分类页模板
│   │   │   └── assets/                  # 静态资源（CSS、JavaScript）
│   │   └── minimal/                     # 极简模板，仅输出纯文本列表
│   └── utils/                           # 通用工具函数
│       ├── http-client.js               # 轻量 HTTP 请求封装，用于元数据获取
│       ├── logger.js                    # 日志输出，支持 verbose / quiet 模式
│       └── validator.js                 # URL 合法性校验与规范化工具
├── data/                                # 示例数据目录
│   ├── urls.txt                         # 默认输入文件示例
│   └── sample-categories.json           # 可选分类映射配置示例
├── dist/                                # 默认构建输出目录（git 忽略）
├── tests/                               # 单元测试与集成测试
│   ├── unit/                            # 单元测试用例
│   └── fixtures/                        # 测试用的固定数据集
├── docs/                                # 项目文档（详见文档导航）
├── package.json                         # npm 项目清单
├── README.md                            # 项目说明（本文件）
└── LICENSE                              # MIT 许可证文件
```

## 贡献指南

1. 查阅 issue 列表或自主提出改进方案，在 GitHub 上创建一个新的 issue 说明拟解决的问题或新增功能，等待维护者反馈以避免重复工作。

2. Fork 本仓库至个人账户，克隆到本地开发环境，并创建以 feature/ 或 fix/ 为前缀的分支进行开发。

3. 编写或修改代码后，确保所有现有单元测试通过，并为新增功能或修复补充相应的测试用例，测试文件放置于 tests/ 对应目录下。

4. 提交前运行 npm run lint 与 npm run test 进行代码风格检查与完整测试套件验证，确保无错误或警告。

5. 发起 Pull Request 到主仓库的 main 分支，描述变更内容、关联 issue 编号以及测试结果，维护者将在三个工作日内进行审查。

## 常见问题

**Q：构建时提示 "ENOTFOUND" 或超时错误，导致构建中断，如何解决？**

A：此类错误通常发生在启用元数据提取或链接检查功能时，网络请求无法到达目标服务器。解决方案：在命令行中添加 --no-metadata 和 --no-check 参数以跳过这两个步骤，仅保留 URL 清洗与分类功能。若仍需元数据，可检查网络代理设置，或通过 --timeout 参数增加请求超时时间（单位毫秒）。

**Q：输入文件中存在大量重复 URL，WebIndexer 会如何处理？**

A：构建器在解析阶段会自动对 URL 进行规范化（去除末尾斜杠、统一协议为小写等）并基于规范化后的字符串进行去重。重复条目仅保留第一次出现的记录，并在日志中输出去重统计信息（原始条目数、去重后条目数、重复移除数）。如需保留重复项用于统计目的，可使用 --keep-duplicates 参数关闭去重功能。

**Q：如何自定义分类规则，使特定域名的 URL 归入指定的类别？**

A：在项目根目录下创建分类映射配置文件（JSON 格式），通过 --classify-config 参数指定该文件路径。配置文件支持两种规则：基于域名匹配（如将 "xqnqq.com" 映射至 "移动端资源"）和基于路径前缀匹配（如将 "/Article/" 映射至 "文章归档"）。匹配优先级按配置数组中规则的先后顺序执行，首个匹配成功的规则生效。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
