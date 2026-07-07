# MapLink 聚合导航系统

MapLink 是一个面向技术文档检索与知识碎片整理的开源外链聚合系统，专门用于将散落在多个内容源、非结构化发布的静态 HTML 文章进行统一索引和分类呈现。项目定位为轻量级技术资源导航中间件，主要服务于技术博客维护者、开源文档站点管理员以及个人知识库构建者，帮助其在不改造原站点架构的前提下，通过外链映射关系快速建立可检索、可分类、可审计的参考信息目录。

本系统不提供内容抓取与存储功能，仅处理 URL 级别的元数据归类与展示逻辑，所有原始资源仍指向原始发布域名。当前批次资源覆盖第 78 至 80 批共 250 个外链条目，均以只读索引形式纳入导航体系，访问时直接回源至对应文章页面。

## 功能概览

- 纯静态外链索引引擎：基于 Markdown 配置生成完整导航页面，无需后端服务，支持部署至任何静态托管环境。

- 多级分类与标签映射：每个资源条目可关联一个主分类和多个可选标签，分类树深度最多支持四级。

- 原始链接透明透传：所有导航条目直接输出原始 Article URL，不经过中间跳转或短链服务，保证来源可追溯。

- 批次化资源管理：按采集批次（当前为第 78/80 批）组织资源视图，支持按批次过滤和批次间对比。

- 元数据扩展字段支持：每条记录预留标题摘要占位、采集时间戳和状态标记字段，便于后续二次加工。

- 多维度排序与筛选：列表视图支持按发布时间、入库时间、域名来源、文章编号进行升序或降序排列。

- 原始输出模式：为避免内容篡改风险，所有链接在导出和展示时严格保持原始字符串形式，不添加追踪参数。

- 轻量级部署依赖：仅依赖一个静态 Web 服务器，不依赖数据库、缓存或任务队列。

## 应用场景

场景一：技术博客的参考链接附录管理。博客作者在撰写系列文章时，需要引用大量外部资料作为论据支撑，但通常缺少结构化的引用管理系统。MapLink 允许作者将来自 map.mobile.xqnqq.com 和 map.read.usuhx.com 等站点的参考文章统一登记为外部资源条目，并按主题或写作进度批次分类，最终生成可公开访问的参考链接目录页。

场景二：开源项目文档站的外链审计。开源项目的 README 或 Wiki 中经常包含大量指向外部教程、API 参考和案例分析的链接。维护者可以通过 MapLink 对这类外链进行集中登记、定期检查可用性和分类标注，避免文档中的外链散落各处难以维护。本批次 250 个链接覆盖了多个技术主题方向，可作为典型审计批次导入。

场景三：个人知识库的素材来源追踪。使用双链笔记或本地 Markdown 知识库的用户，往往需要记录每个知识卡片的外部来源。MapLink 提供的纯 URL 索引列表可以直接嵌入知识库的侧边栏或索引页面，作为外部引用清单的统一入口，确保每个外部引用都有明确的原始地址记录。

## 快速开始

以下步骤适用于在本地环境快速启动 MapLink 导航系统的开发或预览实例。

```bash
# 克隆项目仓库至本地
git clone https://github.com/maplink-dev/maplink-navigator.git

# 进入项目根目录
cd maplink-navigator

# 安装依赖（基于 Node.js 18+ 与 npm）
npm install

# 复制示例配置文件并调整自定义分类规则
cp config/example.yaml config/custom.yaml

# 将资源列表导入数据目录（以批次 78-80 为例）
cp data/batch-78-80.json data/active-batch.json

# 启动开发服务器，默认监听端口 3000
npm run dev
```

访问 http://localhost:3000 即可查看当前批次的导航列表页面。生产环境构建请执行 `npm run build` 并将输出目录 `dist/` 部署至任何静态文件服务器。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或更高 | 运行时环境，用于执行构建脚本和开发服务器 |
| npm | 8.x 或更高 | 包管理器，用于安装项目依赖 |
| Git | 2.25 或更高 | 版本控制工具，用于克隆仓库和管理配置变更 |
| 静态 Web 服务器（如 Nginx） | 任意稳定版本 | 生产环境部署必需，用于托管构建产物 |
| 现代浏览器（Chromium / Firefox） | 最近两个主要版本 | 用于访问导航界面，支持 ES6 和 CSS Grid |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide/ | 如何添加、删除、修改资源条目，以及如何管理批次数据 |
| 配置参考 | /docs/config-reference/ | 分类映射规则、排序策略、元数据字段的完整配置项说明 |
| 部署指南 | /docs/deployment/ | 针对不同静态托管平台（GitHub Pages、Cloudflare Pages、自建 Nginx）的部署流程 |
| 数据格式规范 | /docs/data-format/ | JSON 数据结构的字段定义、批次文件组织方式和校验规则 |
| API 设计（内部） | /docs/internal-api/ | 前端与构建脚本之间的数据流接口说明，用于二次开发 |

## 资源列表

- http://map.mobile.xqnqq.com/Article/6544.shtml
- http://map.mobile.xqnqq.com/Article/8179.shtml
- http://map.mobile.xqnqq.com/Article/2054.shtml
- http://map.mobile.xqnqq.com/Article/09779.shtml
- http://map.read.usuhx.com/Article/025949.shtml
- http://map.mobile.xqnqq.com/Article/775410.shtml
- http://map.mobile.xqnqq.com/Article/39010.shtml
- http://map.mobile.xqnqq.com/Article/6630451.shtml
- http://map.read.usuhx.com/Article/4234161.shtml
- http://map.mobile.xqnqq.com/Article/5396712.shtml
- http://map.mobile.xqnqq.com/Article/8259880.shtml
- http://map.mobile.xqnqq.com/Article/3608922.shtml
- http://map.mobile.xqnqq.com/Article/70492.shtml
- http://map.read.usuhx.com/Article/67420.shtml
- http://map.read.usuhx.com/Article/7304318.shtml
- http://map.mobile.xqnqq.com/Article/965704.shtml
- http://map.read.usuhx.com/Article/837635.shtml
- http://map.read.usuhx.com/Article/10113.shtml
- http://map.read.usuhx.com/Article/19284.shtml
- http://map.read.usuhx.com/Article/47843.shtml
- http://map.mobile.xqnqq.com/Article/3427758.shtml
- http://map.read.usuhx.com/Article/4487901.shtml
- http://map.mobile.xqnqq.com/Article/3540303.shtml
- http://map.read.usuhx.com/Article/135906.shtml
- http://map.read.usuhx.com/Article/147499.shtml
- http://map.mobile.xqnqq.com/Article/5891599.shtml
- http://map.mobile.xqnqq.com/Article/324671.shtml
- http://map.read.usuhx.com/Article/269818.shtml
- http://map.mobile.xqnqq.com/Article/7834848.shtml
- http://map.read.usuhx.com/Article/73910.shtml
- http://map.read.usuhx.com/Article/1622082.shtml
- http://map.read.usuhx.com/Article/5427.shtml
- http://map.mobile.xqnqq.com/Article/10215.shtml
- http://map.mobile.xqnqq.com/Article/6002085.shtml
- http://map.read.usuhx.com/Article/8940.shtml
- http://map.mobile.xqnqq.com/Article/807915.shtml
- http://map.mobile.xqnqq.com/Article/0308957.shtml
- http://map.mobile.xqnqq.com/Article/442976.shtml
- http://map.mobile.xqnqq.com/Article/1774994.shtml
- http://map.read.usuhx.com/Article/34794.shtml
- http://map.mobile.xqnqq.com/Article/12048.shtml
- http://map.read.usuhx.com/Article/57827.shtml
- http://map.read.usuhx.com/Article/8190277.shtml
- http://map.read.usuhx.com/Article/3514585.shtml
- http://map.mobile.xqnqq.com/Article/646006.shtml
- http://map.mobile.xqnqq.com/Article/01206.shtml
- http://map.read.usuhx.com/Article/4585177.shtml
- http://map.read.usuhx.com/Article/30638.shtml
- http://map.read.usuhx.com/Article/6662.shtml
- http://map.mobile.xqnqq.com/Article/5640.shtml
- http://map.mobile.xqnqq.com/Article/748033.shtml
- http://map.read.usuhx.com/Article/0670.shtml
- http://map.mobile.xqnqq.com/Article/071388.shtml
- http://map.mobile.xqnqq.com/Article/84430.shtml
- http://map.read.usuhx.com/Article/6225536.shtml
- http://map.read.usuhx.com/Article/146749.shtml
- http://map.read.usuhx.com/Article/91295.shtml
- http://map.mobile.xqnqq.com/Article/829450.shtml
- http://map.read.usuhx.com/Article/1549837.shtml
- http://map.read.usuhx.com/Article/1234.shtml
- http://map.read.usuhx.com/Article/543044.shtml
- http://map.read.usuhx.com/Article/499662.shtml
- http://map.read.usuhx.com/Article/0904.shtml
- http://map.read.usuhx.com/Article/92770.shtml
- http://map.read.usuhx.com/Article/65836.shtml
- http://map.mobile.xqnqq.com/Article/848313.shtml
- http://map.read.usuhx.com/Article/4064450.shtml
- http://map.read.usuhx.com/Article/2204655.shtml
- http://map.mobile.xqnqq.com/Article/68945.shtml
- http://map.read.usuhx.com/Article/436255.shtml
- http://map.read.usuhx.com/Article/4669950.shtml
- http://map.mobile.xqnqq.com/Article/58645.shtml
- http://map.read.usuhx.com/Article/47023.shtml
- http://map.read.usuhx.com/Article/33665.shtml
- http://map.read.usuhx.com/Article/8595726.shtml
- http://map.mobile.xqnqq.com/Article/17173.shtml
- http://map.read.usuhx.com/Article/0170.shtml
- http://map.mobile.xqnqq.com/Article/9883460.shtml
- http://map.read.usuhx.com/Article/8218.shtml
- http://map.read.usuhx.com/Article/5622.shtml
- http://map.mobile.xqnqq.com/Article/258484.shtml
- http://map.mobile.xqnqq.com/Article/750707.shtml
- http://map.mobile.xqnqq.com/Article/9461308.shtml
- http://map.read.usuhx.com/Article/7675702.shtml
- http://map.mobile.xqnqq.com/Article/377737.shtml
- http://map.read.usuhx.com/Article/7913885.shtml
- http://map.mobile.xqnqq.com/Article/58636.shtml
- http://map.read.usuhx.com/Article/601173.shtml
- http://map.mobile.xqnqq.com/Article/7582057.shtml
- http://map.read.usuhx.com/Article/4758283.shtml
- http://map.mobile.xqnqq.com/Article/18936.shtml
- http://map.read.usuhx.com/Article/8277889.shtml
- http://map.mobile.xqnqq.com/Article/2004225.shtml
- http://map.read.usuhx.com/Article/4014902.shtml
- http://map.mobile.xqnqq.com/Article/5057799.shtml
- http://map.read.usuhx.com/Article/377262.shtml
- http://map.read.usuhx.com/Article/6520.shtml
- http://map.mobile.xqnqq.com/Article/791729.shtml
- http://map.read.usuhx.com/Article/50039.shtml
- http://map.mobile.xqnqq.com/Article/0881.shtml
- http://map.mobile.xqnqq.com/Article/179252.shtml
- http://map.read.usuhx.com/Article/70325.shtml
- http://map.mobile.xqnqq.com/Article/6464.shtml
- http://map.read.usuhx.com/Article/16887.shtml
- http://map.mobile.xqnqq.com/Article/8876.shtml
- http://map.mobile.xqnqq.com/Article/77720.shtml
- http://map.mobile.xqnqq.com/Article/905047.shtml
- http://map.read.usuhx.com/Article/12926.shtml
- http://map.read.usuhx.com/Article/2314.shtml
- http://map.read.usuhx.com/Article/643652.shtml
- http://map.read.usuhx.com/Article/470980.shtml
- http://map.read.usuhx.com/Article/8215.shtml
- http://map.read.usuhx.com/Article/7317.shtml
- http://map.mobile.xqnqq.com/Article/392571.shtml
- http://map.mobile.xqnqq.com/Article/3000219.shtml
- http://map.mobile.xqnqq.com/Article/7239636.shtml
- http://map.read.usuhx.com/Article/747487.shtml
- http://map.mobile.xqnqq.com/Article/0988.shtml
- http://map.read.usuhx.com/Article/1065.shtml
- http://map.mobile.xqnqq.com/Article/6580.shtml
- http://map.mobile.xqnqq.com/Article/97403.shtml
- http://map.read.usuhx.com/Article/85658.shtml
- http://map.read.usuhx.com/Article/0761.shtml
- http://map.mobile.xqnqq.com/Article/9291.shtml
- http://map.mobile.xqnqq.com/Article/9786086.shtml
- http://map.mobile.xqnqq.com/Article/6335359.shtml
- http://map.read.usuhx.com/Article/89422.shtml
- http://map.read.usuhx.com/Article/654333.shtml
- http://map.mobile.xqnqq.com/Article/8772.shtml
- http://map.read.usuhx.com/Article/8164536.shtml
- http://map.read.usuhx.com/Article/1797982.shtml
- http://map.mobile.xqnqq.com/Article/324364.shtml
- http://map.mobile.xqnqq.com/Article/2355822.shtml
- http://map.mobile.xqnqq.com/Article/651038.shtml
- http://map.mobile.xqnqq.com/Article/510172.shtml
- http://map.read.usuhx.com/Article/9046112.shtml
- http://map.mobile.xqnqq.com/Article/3541.shtml
- http://map.read.usuhx.com/Article/27003.shtml
- http://map.mobile.xqnqq.com/Article/11303.shtml
- http://map.read.usuhx.com/Article/04120.shtml
- http://map.read.usuhx.com/Article/9091581.shtml
- http://map.read.usuhx.com/Article/62564.shtml
- http://map.mobile.xqnqq.com/Article/783797.shtml
- http://map.mobile.xqnqq.com/Article/659650.shtml
- http://map.read.usuhx.com/Article/1641.shtml
- http://map.mobile.xqnqq.com/Article/1130.shtml
- http://map.mobile.xqnqq.com/Article/3460586.shtml
- http://map.mobile.xqnqq.com/Article/40068.shtml
- http://map.mobile.xqnqq.com/Article/043135.shtml
- http://map.mobile.xqnqq.com/Article/1496263.shtml
- http://map.mobile.xqnqq.com/Article/9518.shtml
- http://map.mobile.xqnqq.com/Article/49278.shtml
- http://map.mobile.xqnqq.com/Article/8550.shtml
- http://map.read.usuhx.com/Article/6247359.shtml
- http://map.read.usuhx.com/Article/785921.shtml
- http://map.mobile.xqnqq.com/Article/0796402.shtml
- http://map.read.usuhx.com/Article/1417808.shtml
- http://map.read.usuhx.com/Article/7231984.shtml
- http://map.mobile.xqnqq.com/Article/581422.shtml
- http://map.mobile.xqnqq.com/Article/1468.shtml
- http://map.mobile.xqnqq.com/Article/932906.shtml
- http://map.mobile.xqnqq.com/Article/6809.shtml
- http://map.read.usuhx.com/Article/1384416.shtml
- http://map.mobile.xqnqq.com/Article/5094.shtml
- http://map.mobile.xqnqq.com/Article/14102.shtml
- http://map.read.usuhx.com/Article/0980.shtml
- http://map.mobile.xqnqq.com/Article/3145613.shtml
- http://map.mobile.xqnqq.com/Article/066918.shtml
- http://map.mobile.xqnqq.com/Article/7388916.shtml
- http://map.read.usuhx.com/Article/636642.shtml
- http://map.read.usuhx.com/Article/06281.shtml
- http://map.read.usuhx.com/Article/2505.shtml
- http://map.read.usuhx.com/Article/460374.shtml
- http://map.mobile.xqnqq.com/Article/500420.shtml
- http://map.mobile.xqnqq.com/Article/6146.shtml
- http://map.read.usuhx.com/Article/7262.shtml
- http://map.mobile.xqnqq.com/Article/571568.shtml
- http://map.mobile.xqnqq.com/Article/923030.shtml
- http://map.mobile.xqnqq.com/Article/4026.shtml
- http://map.mobile.xqnqq.com/Article/93507.shtml
- http://map.read.usuhx.com/Article/440204.shtml
- http://map.read.usuhx.com/Article/996878.shtml
- http://map.read.usuhx.com/Article/6650.shtml
- http://map.read.usuhx.com/Article/2424.shtml
- http://map.mobile.xqnqq.com/Article/2854505.shtml
- http://map.mobile.xqnqq.com/Article/759732.shtml
- http://map.read.usuhx.com/Article/6507.shtml
- http://map.read.usuhx.com/Article/0182.shtml
- http://map.read.usuhx.com/Article/907642.shtml
- http://map.read.usuhx.com/Article/8807317.shtml
- http://map.read.usuhx.com/Article/9570.shtml
- http://map.read.usuhx.com/Article/366481.shtml
- http://map.read.usuhx.com/Article/67247.shtml
- http://map.read.usuhx.com/Article/0446169.shtml
- http://map.mobile.xqnqq.com/Article/22789.shtml
- http://map.mobile.xqnqq.com/Article/3947846.shtml
- http://map.read.usuhx.com/Article/78893.shtml
- http://map.mobile.xqnqq.com/Article/012820.shtml
- http://map.mobile.xqnqq.com/Article/4473948.shtml
- http://map.read.usuhx.com/Article/9620867.shtml
- http://map.mobile.xqnqq.com/Article/5387828.shtml
- http://map.mobile.xqnqq.com/Article/37940.shtml
- http://map.mobile.xqnqq.com/Article/23114.shtml
- http://map.mobile.xqnqq.com/Article/238113.shtml
- http://map.mobile.xqnqq.com/Article/17298.shtml
- http://map.mobile.xqnqq.com/Article/041963.shtml
- http://map.mobile.xqnqq.com/Article/29730.shtml
- http://map.mobile.xqnqq.com/Article/8967477.shtml
- http://map.mobile.xqnqq.com/Article/45875.shtml
- http://map.mobile.xqnqq.com/Article/50124.shtml
- http://map.read.usuhx.com/Article/7829598.shtml
- http://map.mobile.xqnqq.com/Article/963184.shtml
- http://map.read.usuhx.com/Article/8971.shtml
- http://map.mobile.xqnqq.com/Article/3059835.shtml
- http://map.mobile.xqnqq.com/Article/824844.shtml
- http://map.read.usuhx.com/Article/037326.shtml
- http://map.mobile.xqnqq.com/Article/54283.shtml
- http://map.mobile.xqnqq.com/Article/5997.shtml
- http://map.read.usuhx.com/Article/3105789.shtml
- http://map.read.usuhx.com/Article/7807334.shtml
- http://map.read.usuhx.com/Article/2115116.shtml
- http://map.mobile.xqnqq.com/Article/99084.shtml
- http://map.read.usuhx.com/Article/57401.shtml
- http://map.mobile.xqnqq.com/Article/3411.shtml
- http://map.read.usuhx.com/Article/7307.shtml
- http://map.read.usuhx.com/Article/4148775.shtml
- http://map.mobile.xqnqq.com/Article/932124.shtml
- http://map.mobile.xqnqq.com/Article/3134328.shtml
- http://map.read.usuhx.com/Article/46907.shtml
- http://map.mobile.xqnqq.com/Article/8128770.shtml
- http://map.mobile.xqnqq.com/Article/38899.shtml
- http://map.mobile.xqnqq.com/Article/148851.shtml
- http://map.read.usuhx.com/Article/2324492.shtml
- http://map.mobile.xqnqq.com/Article/820970.shtml
- http://map.read.usuhx.com/Article/09506.shtml
- http://map.read.usuhx.com/Article/9269.shtml
- http://map.read.usuhx.com/Article/5186.shtml
- http://map.mobile.xqnqq.com/Article/22238.shtml
- http://map.mobile.xqnqq.com/Article/2384.shtml
- http://map.mobile.xqnqq.com/Article/6664.shtml
- http://map.mobile.xqnqq.com/Article/5839.shtml
- http://map.mobile.xqnqq.com/Article/5585370.shtml
- http://map.mobile.xqnqq.com/Article/875800.shtml
- http://map.read.usuhx.com/Article/3685.shtml
- http://map.read.usuhx.com/Article/2948072.shtml
- http://map.mobile.xqnqq.com/Article/9414691.shtml
- http://map.mobile.xqnqq.com/Article/61886.shtml
- http://map.read.usuhx.com/Article/14664.shtml
- http://map.read.usuhx.com/Article/2095868.shtml
- http://map.read.usuhx.com/Article/34074.shtml

## 项目结构

```
maplink-navigator/
├── config/                            # 配置文件目录
│   ├── default.yaml                   # 默认全局配置（分类映射、排序规则）
│   ├── custom.yaml                    # 用户自定义配置（覆盖默认项）
│   └── schema.json                    # 配置字段的 JSON Schema 校验文件
├── data/                              # 资源数据目录
│   ├── raw/                           # 原始采集数据备份
│   │   └── batch-78-80.json           # 第 78/80 批原始 URL 清单
│   ├── active-batch.json              # 当前激活的批次数据软链接
│   └── index-meta.json                # 所有批次的元数据索引（批次号、条目数、采集时间）
├── src/                               # 源码目录
│   ├── core/                          # 核心逻辑模块
│   │   ├── parser.js                  # URL 解析与规范化校验
│   │   ├── classifier.js              # 基于配置的分类器实现
│   │   └── sorter.js                  # 多字段排序引擎
│   ├── ui/                            # 前端界面组件
│   │   ├── App.jsx                    # 根组件
│   │   ├── ListView.jsx               # 资源列表渲染组件
│   │   └── FilterPanel.jsx            # 分类与标签筛选面板
│   ├── build/                         # 构建脚本
│   │   ├── generate.js                # 从数据生成静态 HTML 的主构建脚本
│   │   └── validate.js                # 数据完整性校验脚本
│   └── styles/                        # 样式文件
│       └── main.css                   # 全局样式（基于 CSS 变量设计）
├── dist/                              # 构建输出目录（部署目标）
│   ├── index.html                     # 导航首页
│   ├── assets/                        # 静态资源（JS、CSS、字体）
│   └── data/                          # 运行时数据 JSON 文件
├── tests/                             # 单元测试目录
│   ├── parser.test.js                 # URL 解析测试用例
│   └── classifier.test.js             # 分类逻辑测试用例
├── docs/                              # 文档目录
│   ├── user-guide/                    # 用户手册章节
│   ├── config-reference/              # 配置参考文档
│   └── deployment/                    # 部署指南
├── .github/                           # GitHub 工作流配置
│   └── workflows/                     # CI/CD 流水线定义
│       └── build.yml                  # 自动构建与部署流水线
├── package.json                       # npm 依赖与脚本定义
├── README.md                          # 项目自述文件（本文档）
└── LICENSE                            # MIT 许可证文件
```

## 贡献指南

1. 复刻项目仓库至个人账户，并在本地克隆复刻后的副本。所有改动均通过分支提交，主分支仅接收来自 Pull Request 的合并。

2. 新增或修改资源批次数据时，请将原始 URL 清单放置在 `data/raw/` 目录下，并按照 `data-format.md` 中定义的 JSON 结构编写条目，确保每个条目至少包含 `url` 和 `batchId` 字段。

3. 运行 `npm run validate` 校验数据格式是否符合 Schema 定义，并执行 `npm test` 确保现有单元测试全部通过。新增功能需同步添加对应的测试用例。

4. 提交代码前请确保代码风格符合项目 ESLint 配置，并更新受影响的文档章节（特别是 `docs/user-guide/` 和 `docs/config-reference/` 下的相关内容）。

5. 发起 Pull Request 至主仓库的 `develop` 分支，描述中需说明本次变更的目的、影响范围以及测试覆盖情况。合并前至少需要一名核心维护者审核通过。

## 常见问题

问题：资源列表中部分链接返回 404 或无法访问，应该如何处理？

回答：MapLink 系统本身不缓存或代理原始内容，所有链接直接回源。若发现某条链接失效，建议先访问原始站点确认是否临时维护或内容迁移。若确认永久失效，可在数据文件中将该条目状态标记为 `deprecated`，并在下次构建时排除。系统不提供自动死链检测功能，但用户可结合第三方链接检查工具定期扫描。

问题：如何将多个批次的资源合并显示在同一个导航页面中？

回答：系统默认每次仅加载一个批次的资源。若需合并显示，可将多个批次 JSON 文件的 `entries` 数组合并后保存为新的批次文件，并重新运行构建命令。合并时需要注意不同批次的元数据字段应保持一致，避免排序和筛选逻辑异常。

问题：是否支持在导航页面上直接编辑或删除资源条目？

回答：当前版本不提供 Web 界面的在线编辑功能。所有数据修改均通过本地编辑 JSON 文件后重新构建实现。这样设计是为了保证导航列表的版本可控性和审核可追溯性，避免前端误操作导致数据混乱。未来的版本计划中，将考虑引入基于 Git 后端的轻量级编辑界面。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
