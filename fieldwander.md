# WebLink Atlas

WebLink Atlas 是一个面向技术调研、内容聚合与外部链接治理的静态资源导航与映射系统。项目定位于协助开发者、技术写作人员与运维工程师，对大规模分散于多个域名下的文章型资源进行统一收录、分类索引与结构化呈现。目标用户包括需要维护外部链接清单的项目维护者、需要快速检索特定 URL 来源的测试人员，以及希望基于现有资源构建衍生数据服务的集成工程师。项目本身不提供爬虫或自动采集能力，而是以人工整理与版本控制为核心，确保每一条外链的持久可溯性与引用准确性。通过标准的 Markdown 文档与目录树结构，WebLink Atlas 将无序的 URL 清单转化为可维护、可审计、可扩展的知识底座。

## 功能概览

多源链接统一收录：支持将来自不同域名的文章链接按照原始地址原样收录，保留协议、域名、路径与查询参数，杜绝自动改写或规范化干扰。

域名级分类视图：根据链接所属域名自动归类，便于按来源站点进行批量查看与筛选，当前内置对 map.mobile.xqnqq.com 与 map.read.usuhx.com 两域名的原生支持。

批次化资源管理：采用批次编号管理机制，每批次可承载数百条链接，并可在文档中记录批次总数、当前序号与覆盖范围，适合周期性导入与增量维护。

纯静态文档驱动：项目完全基于 Markdown 与 ASCII 目录树，无需数据库或后端服务，所有资源列表可直接嵌入 README 或独立文档，便于 Git 托管与变更追踪。

结构化元数据标注：在快速开始、安装要求、文档导航等章节中明确记录环境依赖、目录说明与文档索引，确保新成员可在十分钟内完成项目理解与环境配置。

资源列表严格保真输出：资源列表章节强制保留每个 URL 的原始格式，包括裸域名、协议类型、大小写以及路径中的数字与符号，不做任何形式的链接缩短或包装。

项目结构可视化：通过完整的 ASCII 目录树展示源码、配置、文档、脚本与外部资源五个核心子目录，每个目录附带功能注释，降低项目理解成本。

贡献流程标准化：提供清晰的 fork、分支、添加、提交与合并请求步骤，使外部贡献者能够在不破坏原有 URL 格式的前提下扩充资源清单。

## 应用场景

内部技术周报素材整理：技术编辑每周从多个内容源收集文章链接，使用 WebLink Atlas 将链接按域名与批次归档，并在 README 中统一呈现，便于团队周报引用与历史回溯。

外部依赖链接合规审计：合规人员需要定期检查项目中引用的外部文章是否仍可访问或是否存在内容变更。通过本项目维护的原始链接清单，可批量导出 URL 列表进行可用性检测。

自动化测试用例数据源：测试工程师可将资源列表中的链接作为接口测试或页面加载测试的输入数据集，利用原始 URL 构造请求，验证目标站点的响应状态与内容类型。

知识库链接迁移前评估：在进行文档平台迁移或内容系统升级时，运维人员通过本项目提供的完整链接目录，评估外部引用数量、域名分布与路径结构，从而制定合理的重定向或替换策略。

开源项目外链聚合展示：开源项目维护者需要对外展示项目所引用或推荐的第三方文章资源。WebLink Atlas 提供现成的资源列表章节与版本化记录，可直接嵌入项目主页或 Wiki。

## 快速开始

以下命令序列帮助您在本地环境中完成项目克隆、依赖安装与运行预览。

```bash
git clone https://github.com/weblink-atlas/weblink-atlas.git
cd weblink-atlas
npm install
npm run build
```

执行完毕后，静态站点文件将生成于 `dist` 目录，您可使用任意 HTTP 服务器进行本地预览，例如：

```bash
npx serve dist
```

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Node.js | 18.x 或更高 | 用于运行构建脚本与本地开发服务器 |
| npm | 9.x 或更高 | 依赖安装与脚本执行管理 |
| Git | 2.30 或更高 | 版本控制与克隆操作 |
| markdownlint-cli | 0.33 或更高 | 用于校验 README 及文档中的 Markdown 格式规范 |
| shellcheck | 0.8 或更高 | 用于检查辅助脚本中的 shell 语法 |
| Python | 3.9 或更高（可选） | 仅在运行额外数据分析脚本时需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 项目入口 | /README.md | 项目是什么、如何开始、包含哪些资源 |
| 资源清单 | /docs/resources.md | 所有收录 URL 的完整列表与批次信息 |
| 结构说明 | /docs/structure.md | 目录树详解、各模块职责与扩展方式 |
| 贡献指南 | /CONTRIBUTING.md | 如何新增链接、更新文档与提交合并请求 |

## 资源列表

- http://map.mobile.xqnqq.com/Article/3925.shtml
- http://map.read.usuhx.com/Article/642729.shtml
- http://map.read.usuhx.com/Article/8137721.shtml
- http://map.read.usuhx.com/Article/3377343.shtml
- http://map.read.usuhx.com/Article/9549.shtml
- http://map.read.usuhx.com/Article/6320260.shtml
- http://map.read.usuhx.com/Article/53838.shtml
- http://map.mobile.xqnqq.com/Article/62119.shtml
- http://map.mobile.xqnqq.com/Article/18340.shtml
- http://map.mobile.xqnqq.com/Article/1027.shtml
- http://map.read.usuhx.com/Article/04404.shtml
- http://map.mobile.xqnqq.com/Article/3282408.shtml
- http://map.read.usuhx.com/Article/7755327.shtml
- http://map.read.usuhx.com/Article/472744.shtml
- http://map.read.usuhx.com/Article/11229.shtml
- http://map.mobile.xqnqq.com/Article/46094.shtml
- http://map.read.usuhx.com/Article/5419245.shtml
- http://map.mobile.xqnqq.com/Article/546183.shtml
- http://map.mobile.xqnqq.com/Article/1851.shtml
- http://map.read.usuhx.com/Article/58051.shtml
- http://map.read.usuhx.com/Article/984479.shtml
- http://map.read.usuhx.com/Article/8878.shtml
- http://map.mobile.xqnqq.com/Article/6860.shtml
- http://map.read.usuhx.com/Article/5566.shtml
- http://map.mobile.xqnqq.com/Article/26177.shtml
- http://map.mobile.xqnqq.com/Article/711534.shtml
- http://map.mobile.xqnqq.com/Article/14731.shtml
- http://map.mobile.xqnqq.com/Article/89210.shtml
- http://map.read.usuhx.com/Article/88086.shtml
- http://map.read.usuhx.com/Article/03134.shtml
- http://map.mobile.xqnqq.com/Article/5004.shtml
- http://map.mobile.xqnqq.com/Article/93140.shtml
- http://map.mobile.xqnqq.com/Article/7275.shtml
- http://map.read.usuhx.com/Article/01295.shtml
- http://map.mobile.xqnqq.com/Article/0629719.shtml
- http://map.mobile.xqnqq.com/Article/44893.shtml
- http://map.mobile.xqnqq.com/Article/5344.shtml
- http://map.mobile.xqnqq.com/Article/199451.shtml
- http://map.read.usuhx.com/Article/325264.shtml
- http://map.mobile.xqnqq.com/Article/657713.shtml
- http://map.mobile.xqnqq.com/Article/030507.shtml
- http://map.mobile.xqnqq.com/Article/4030.shtml
- http://map.read.usuhx.com/Article/60178.shtml
- http://map.mobile.xqnqq.com/Article/84448.shtml
- http://map.read.usuhx.com/Article/638498.shtml
- http://map.read.usuhx.com/Article/081922.shtml
- http://map.mobile.xqnqq.com/Article/95635.shtml
- http://map.read.usuhx.com/Article/8311589.shtml
- http://map.mobile.xqnqq.com/Article/2532263.shtml
- http://map.read.usuhx.com/Article/788056.shtml
- http://map.read.usuhx.com/Article/210463.shtml
- http://map.read.usuhx.com/Article/940850.shtml
- http://map.read.usuhx.com/Article/47804.shtml
- http://map.read.usuhx.com/Article/7483.shtml
- http://map.read.usuhx.com/Article/2428866.shtml
- http://map.mobile.xqnqq.com/Article/345763.shtml
- http://map.read.usuhx.com/Article/657205.shtml
- http://map.read.usuhx.com/Article/2824693.shtml
- http://map.read.usuhx.com/Article/31630.shtml
- http://map.read.usuhx.com/Article/717527.shtml
- http://map.mobile.xqnqq.com/Article/7384.shtml
- http://map.mobile.xqnqq.com/Article/1894.shtml
- http://map.mobile.xqnqq.com/Article/4913.shtml
- http://map.mobile.xqnqq.com/Article/2987.shtml
- http://map.read.usuhx.com/Article/173136.shtml
- http://map.mobile.xqnqq.com/Article/730052.shtml
- http://map.read.usuhx.com/Article/679246.shtml
- http://map.read.usuhx.com/Article/1622602.shtml
- http://map.read.usuhx.com/Article/58372.shtml
- http://map.read.usuhx.com/Article/891720.shtml
- http://map.read.usuhx.com/Article/708052.shtml
- http://map.mobile.xqnqq.com/Article/244054.shtml
- http://map.read.usuhx.com/Article/8743563.shtml
- http://map.read.usuhx.com/Article/6369316.shtml
- http://map.mobile.xqnqq.com/Article/179797.shtml
- http://map.read.usuhx.com/Article/9990232.shtml
- http://map.read.usuhx.com/Article/40746.shtml
- http://map.read.usuhx.com/Article/38457.shtml
- http://map.read.usuhx.com/Article/80731.shtml
- http://map.mobile.xqnqq.com/Article/26925.shtml
- http://map.mobile.xqnqq.com/Article/1142.shtml
- http://map.read.usuhx.com/Article/4747.shtml
- http://map.mobile.xqnqq.com/Article/125851.shtml
- http://map.read.usuhx.com/Article/5614949.shtml
- http://map.read.usuhx.com/Article/3173.shtml
- http://map.mobile.xqnqq.com/Article/09437.shtml
- http://map.mobile.xqnqq.com/Article/57439.shtml
- http://map.read.usuhx.com/Article/6972883.shtml
- http://map.read.usuhx.com/Article/22191.shtml
- http://map.mobile.xqnqq.com/Article/0118231.shtml
- http://map.mobile.xqnqq.com/Article/8677897.shtml
- http://map.mobile.xqnqq.com/Article/2146019.shtml
- http://map.mobile.xqnqq.com/Article/86281.shtml
- http://map.mobile.xqnqq.com/Article/27833.shtml
- http://map.read.usuhx.com/Article/681558.shtml
- http://map.read.usuhx.com/Article/015858.shtml
- http://map.read.usuhx.com/Article/562537.shtml
- http://map.mobile.xqnqq.com/Article/86285.shtml
- http://map.read.usuhx.com/Article/374976.shtml
- http://map.mobile.xqnqq.com/Article/6944076.shtml
- http://map.read.usuhx.com/Article/414873.shtml
- http://map.mobile.xqnqq.com/Article/7666734.shtml
- http://map.read.usuhx.com/Article/7834.shtml
- http://map.mobile.xqnqq.com/Article/8640903.shtml
- http://map.mobile.xqnqq.com/Article/4404.shtml
- http://map.read.usuhx.com/Article/836635.shtml
- http://map.mobile.xqnqq.com/Article/3239226.shtml
- http://map.mobile.xqnqq.com/Article/812720.shtml
- http://map.read.usuhx.com/Article/2226038.shtml
- http://map.mobile.xqnqq.com/Article/0408053.shtml
- http://map.mobile.xqnqq.com/Article/42977.shtml
- http://map.mobile.xqnqq.com/Article/153149.shtml
- http://map.mobile.xqnqq.com/Article/32043.shtml
- http://map.mobile.xqnqq.com/Article/5948.shtml
- http://map.read.usuhx.com/Article/417580.shtml
- http://map.read.usuhx.com/Article/4111.shtml
- http://map.mobile.xqnqq.com/Article/253991.shtml
- http://map.mobile.xqnqq.com/Article/05914.shtml
- http://map.read.usuhx.com/Article/9742.shtml
- http://map.mobile.xqnqq.com/Article/52685.shtml
- http://map.read.usuhx.com/Article/5686873.shtml
- http://map.mobile.xqnqq.com/Article/29488.shtml
- http://map.read.usuhx.com/Article/796916.shtml
- http://map.read.usuhx.com/Article/6636200.shtml
- http://map.mobile.xqnqq.com/Article/8859.shtml
- http://map.read.usuhx.com/Article/255287.shtml
- http://map.mobile.xqnqq.com/Article/6744.shtml
- http://map.read.usuhx.com/Article/5810618.shtml
- http://map.read.usuhx.com/Article/9545776.shtml
- http://map.read.usuhx.com/Article/3792713.shtml
- http://map.mobile.xqnqq.com/Article/6946.shtml
- http://map.mobile.xqnqq.com/Article/3272650.shtml
- http://map.read.usuhx.com/Article/649753.shtml
- http://map.mobile.xqnqq.com/Article/410932.shtml
- http://map.read.usuhx.com/Article/10008.shtml
- http://map.read.usuhx.com/Article/340198.shtml
- http://map.mobile.xqnqq.com/Article/9836.shtml
- http://map.mobile.xqnqq.com/Article/5642975.shtml
- http://map.mobile.xqnqq.com/Article/788903.shtml
- http://map.mobile.xqnqq.com/Article/109407.shtml
- http://map.read.usuhx.com/Article/957188.shtml
- http://map.mobile.xqnqq.com/Article/7037.shtml
- http://map.mobile.xqnqq.com/Article/73659.shtml
- http://map.mobile.xqnqq.com/Article/2051.shtml
- http://map.read.usuhx.com/Article/99060.shtml
- http://map.mobile.xqnqq.com/Article/8330.shtml
- http://map.read.usuhx.com/Article/39258.shtml
- http://map.read.usuhx.com/Article/0789515.shtml
- http://map.mobile.xqnqq.com/Article/056733.shtml
- http://map.read.usuhx.com/Article/3595515.shtml
- http://map.read.usuhx.com/Article/7257967.shtml
- http://map.read.usuhx.com/Article/1256.shtml
- http://map.read.usuhx.com/Article/728632.shtml
- http://map.read.usuhx.com/Article/6825.shtml
- http://map.mobile.xqnqq.com/Article/4356.shtml
- http://map.read.usuhx.com/Article/514087.shtml
- http://map.read.usuhx.com/Article/9271.shtml
- http://map.mobile.xqnqq.com/Article/641759.shtml
- http://map.read.usuhx.com/Article/27836.shtml
- http://map.mobile.xqnqq.com/Article/64693.shtml
- http://map.read.usuhx.com/Article/9481815.shtml
- http://map.read.usuhx.com/Article/221867.shtml
- http://map.mobile.xqnqq.com/Article/3098.shtml
- http://map.read.usuhx.com/Article/30440.shtml
- http://map.read.usuhx.com/Article/874820.shtml
- http://map.read.usuhx.com/Article/12955.shtml
- http://map.mobile.xqnqq.com/Article/410589.shtml
- http://map.read.usuhx.com/Article/8745.shtml
- http://map.read.usuhx.com/Article/9068.shtml
- http://map.mobile.xqnqq.com/Article/2404.shtml
- http://map.read.usuhx.com/Article/296639.shtml
- http://map.read.usuhx.com/Article/0150077.shtml
- http://map.read.usuhx.com/Article/8246332.shtml
- http://map.mobile.xqnqq.com/Article/8878999.shtml
- http://map.read.usuhx.com/Article/0958571.shtml
- http://map.mobile.xqnqq.com/Article/5274.shtml
- http://map.read.usuhx.com/Article/1074.shtml
- http://map.mobile.xqnqq.com/Article/45700.shtml
- http://map.mobile.xqnqq.com/Article/47479.shtml
- http://map.read.usuhx.com/Article/810800.shtml
- http://map.mobile.xqnqq.com/Article/8409488.shtml
- http://map.read.usuhx.com/Article/2554.shtml
- http://map.read.usuhx.com/Article/13415.shtml
- http://map.read.usuhx.com/Article/501880.shtml
- http://map.mobile.xqnqq.com/Article/1144361.shtml
- http://map.read.usuhx.com/Article/6730984.shtml
- http://map.mobile.xqnqq.com/Article/2933.shtml
- http://map.read.usuhx.com/Article/3048741.shtml
- http://map.mobile.xqnqq.com/Article/2010.shtml
- http://map.mobile.xqnqq.com/Article/67110.shtml
- http://map.mobile.xqnqq.com/Article/5333.shtml
- http://map.read.usuhx.com/Article/72386.shtml
- http://map.mobile.xqnqq.com/Article/609423.shtml
- http://map.read.usuhx.com/Article/0328.shtml
- http://map.read.usuhx.com/Article/51327.shtml
- http://map.read.usuhx.com/Article/2136924.shtml
- http://map.read.usuhx.com/Article/4470.shtml
- http://map.mobile.xqnqq.com/Article/28206.shtml
- http://map.mobile.xqnqq.com/Article/8148.shtml
- http://map.mobile.xqnqq.com/Article/52113.shtml
- http://map.mobile.xqnqq.com/Article/637917.shtml
- http://map.read.usuhx.com/Article/599947.shtml
- http://map.mobile.xqnqq.com/Article/92879.shtml
- http://map.read.usuhx.com/Article/9307.shtml
- http://map.mobile.xqnqq.com/Article/20901.shtml
- http://map.mobile.xqnqq.com/Article/8414.shtml
- http://map.mobile.xqnqq.com/Article/6973.shtml
- http://map.read.usuhx.com/Article/26231.shtml
- http://map.mobile.xqnqq.com/Article/16267.shtml
- http://map.mobile.xqnqq.com/Article/3944.shtml
- http://map.read.usuhx.com/Article/33538.shtml
- http://map.mobile.xqnqq.com/Article/1244.shtml
- http://map.mobile.xqnqq.com/Article/75753.shtml
- http://map.mobile.xqnqq.com/Article/0275130.shtml
- http://map.mobile.xqnqq.com/Article/405311.shtml
- http://map.mobile.xqnqq.com/Article/13894.shtml
- http://map.read.usuhx.com/Article/927894.shtml
- http://map.read.usuhx.com/Article/18036.shtml
- http://map.mobile.xqnqq.com/Article/158460.shtml
- http://map.read.usuhx.com/Article/8463821.shtml
- http://map.mobile.xqnqq.com/Article/72294.shtml
- http://map.mobile.xqnqq.com/Article/56762.shtml
- http://map.read.usuhx.com/Article/9575.shtml
- http://map.read.usuhx.com/Article/2813836.shtml
- http://map.mobile.xqnqq.com/Article/5388959.shtml
- http://map.mobile.xqnqq.com/Article/92510.shtml
- http://map.read.usuhx.com/Article/387990.shtml
- http://map.mobile.xqnqq.com/Article/7445.shtml
- http://map.mobile.xqnqq.com/Article/57503.shtml
- http://map.mobile.xqnqq.com/Article/470549.shtml
- http://map.read.usuhx.com/Article/238569.shtml
- http://map.mobile.xqnqq.com/Article/9361.shtml
- http://map.mobile.xqnqq.com/Article/7643.shtml
- http://map.read.usuhx.com/Article/9488585.shtml
- http://map.mobile.xqnqq.com/Article/8400.shtml
- http://map.read.usuhx.com/Article/577746.shtml
- http://map.mobile.xqnqq.com/Article/304620.shtml
- http://map.read.usuhx.com/Article/025855.shtml
- http://map.read.usuhx.com/Article/19194.shtml
- http://map.mobile.xqnqq.com/Article/9892.shtml
- http://map.read.usuhx.com/Article/5887.shtml
- http://map.mobile.xqnqq.com/Article/31299.shtml
- http://map.read.usuhx.com/Article/1359.shtml
- http://map.mobile.xqnqq.com/Article/9826216.shtml
- http://map.read.usuhx.com/Article/7160.shtml
- http://map.mobile.xqnqq.com/Article/505353.shtml
- http://map.read.usuhx.com/Article/4623244.shtml
- http://map.read.usuhx.com/Article/1718972.shtml
- http://map.read.usuhx.com/Article/8415.shtml
- http://map.read.usuhx.com/Article/0520685.shtml

## 项目结构

```
weblink-atlas/
├── src/                          # 核心源代码目录
│   ├── collectors/               # 链接收集与格式化模块
│   ├── validators/               # URL 格式校验与去重逻辑
│   └── generators/               # README 与资源列表生成器
├── config/                       # 项目配置文件目录
│   ├── domains.json              # 受支持域名清单与别名映射
│   └── batch.json                # 当前批次编号与总量记录
├── docs/                         # 项目文档与资源清单
│   ├── resources.md              # 完整资源列表（自动生成）
│   ├── structure.md              # 项目结构深度说明
│   └── changelog.md              # 批次更新历史与变更摘要
├── scripts/                      # 辅助运维脚本
│   ├── validate-urls.sh          # 批量校验 URL 可访问性
│   ├── generate-toc.sh           # 自动生成目录树文本
│   └── sync-batch.sh             # 批次号递增与归档工具
├── tests/                        # 单元测试与集成测试
│   ├── collector.test.js         # 收集器模块测试
│   └── validator.test.js         # 校验器模块测试
├── dist/                         # 构建输出目录（静态站点）
│   ├── index.html                # 入口页面
│   └── resources.html            # 资源列表渲染页
├── .github/                      # GitHub 社区文件
│   ├── ISSUE_TEMPLATE/           # 问题模板
│   └── PULL_REQUEST_TEMPLATE.md  # 合并请求模板
├── README.md                     # 项目主文档
├── CONTRIBUTING.md               # 贡献指南详解
├── LICENSE                       # MIT 许可证文件
├── package.json                  # Node.js 依赖清单
└── .markdownlint.json            # Markdown 格式检查规则
```

## 贡献指南

1. 复刻项目仓库至个人账号，并在本地克隆复刻版本。请确保使用主分支的最新提交作为工作基础。

2. 创建新的功能分支，分支名称需反映本次变更类型，例如 `feat/add-batch-55` 或 `fix/url-typo-correction`。

3. 在 `docs/resources.md` 或对应的资源清单文件中，按照现有格式追加或修改 URL 条目。每个 URL 必须单独占一行，并且严格保持原始协议、域名与路径不变。

4. 执行项目本地构建命令，确认 README 与资源列表生成无误，同时运行校验脚本确保所有 URL 格式符合预期标准。

5. 提交变更并推送至远程分支，随后在原始仓库中发起合并请求。请求说明中需附上本次变更的批次编号、新增链接数量以及任何可能影响已有数据的注意事项。

## 常见问题

**问：为什么资源列表中的 URL 不能统一改为 HTTPS 或去除 www 前缀？**

答：本项目定位为原始外链的忠实记录系统，强调引用来源的不可篡改性。即使目标站点同时支持 HTTPS，我们仍然保留用户提供的原始协议与域名形式，以确保与历史记录、第三方引用以及原有系统中的链接完全一致。任何自动改写都可能导致链接失效或引用歧义。

**问：如何快速检查资源列表中是否存在重复或失效的 URL？**

答：项目提供 `scripts/validate-urls.sh` 脚本，可对当前资源列表进行去重检测与 HTTP 状态码检查。执行该脚本需要安装 curl 与 jq 工具。建议在每次新增批次后运行此脚本，并将结果输出至 `docs/validation-report.md` 以便审阅。

**问：是否可以添加非 `map.mobile.xqnqq.com` 与 `map.read.usuhx.com` 域名的链接？**

答：可以。项目本身不限制域名范围，但建议在 `config/domains.json` 中为新域名添加简要说明，以便分类视图与统计功能能够正确识别。如果新域名数量较多，建议单独新建一个批次进行集中收录。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
