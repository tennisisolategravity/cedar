# WebMap 技术资源导航站

WebMap 是一个面向开发者、技术研究人员与站点运维工程师的轻量级技术资源外链聚合平台。该项目定位于将分散于互联网各处的技术文章、操作指南、故障排查记录与最佳实践文档进行系统性归集与索引，通过简洁的目录结构与稳定的引用链路，帮助用户快速定位所需的技术信息。WebMap 本身不存储任何实质内容，仅提供结构化导航能力，适用于个人技术笔记整理、团队知识库外部引用管理以及自动化文档系统的前置索引层。

## 功能概览

**多源外链统一索引**：支持从多个来源域名采集技术文章链接，并按照文章 ID 与分类进行规范化存储与展示。

**按需筛选与排序**：提供基于文章发布时间、来源域名、内容标签的筛选与排序能力，便于用户在海量链接中快速定位。

**裸链接直出模式**：所有外链以原始 URL 形式呈现，不附加任何追踪参数、跳转中间页或 HTML 包裹层，确保链接的纯净性与可移植性。

**批量导入与校验**：支持通过简单文本格式批量导入 URL 列表，系统自动进行去重、协议一致性校验与可访问性预检。

**静态站点生成适配**：项目结构天然适配 Hugo、VuePress、Jekyll 等静态站点生成器，可一键导出为纯静态 HTML 导航站。

**多层级分类体系**：内置技术领域、编程语言、框架版本、运维场景等多维度分类标签，支持自定义扩展。

**访问状态监控**：定时检测已收录链接的 HTTP 状态码，自动标记失效链接并生成报告，辅助维护人员清理或更新资源。

**开放数据导出**：支持将全量索引数据导出为 CSV、JSON 或 Markdown 表格格式，便于嵌入其他文档系统或进行二次分析。

## 应用场景

技术团队内部知识库外链管理：技术团队在日常开发中积累大量外部参考链接，包括官方文档、社区解决方案、性能调优案例等。WebMap 可作为知识库的外部引用索引层，统一存放这些链接并附加分类标签，避免链接散落在聊天记录或零散文档中无法追溯。

个人技术研究者的阅读清单整理：研究人员在阅读技术博客、追踪前沿框架更新或复盘故障案例时，可通过 WebMap 快速收录有价值的文章链接，并利用筛选与排序功能构建个人学习路径。

自动化文档系统的前置资源池：在 CI/CD 流水线或文档生成工具中，WebMap 提供的结构化链接数据可作为动态文档的素材源，自动生成“相关资源”或“延伸阅读”模块，减少人工维护成本。

站点迁移与链接重构辅助：当团队进行站点域名迁移或 URL 结构重构时，WebMap 的批量导出与校验功能可帮助快速生成旧链接到新链接的映射清单，降低迁移风险。

## 快速开始

以下指令适用于 Linux / macOS / Windows WSL 环境，要求已安装 Git 与 Node.js 18.x 及以上版本。

```bash
git clone https://github.com/webmap-io/webmap-indexer.git
cd webmap-indexer
npm install --production
npm run build
npm start
```

执行完毕后，本地服务默认监听 3000 端口，访问 http://127.0.0.1:3000 即可查看导航站首页。数据目录位于 ./data/links.json，用户可直接编辑该文件或通过 Web 管理界面进行增删改操作。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或更高 | 运行时环境，用于执行索引构建与开发服务器 |
| npm | 9.x 或更高 | 包管理器，用于安装项目依赖 |
| Git | 2.30 或更高 | 版本控制工具，用于克隆仓库与提交变更 |
| 内存 | 512 MB 及以上 | 生产环境建议 1 GB 以上以保证并发访问性能 |
| 存储 | 200 MB 可用空间 | 用于存放链接索引文件、日志与缓存数据 |
| 操作系统 | Linux / macOS / Windows 10+ | 跨平台支持，Windows 下建议使用 WSL2 以获得最佳性能 |
| 网络 | 外网访问能力 | 用于首次启动时更新资源状态与校验链接可达性 |
| 浏览器 | 现代浏览器（Chrome / Firefox / Edge） | 管理界面与展示端访问需求 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户指南 | /docs/user-guide/ | 如何使用导航站进行链接检索、分类筛选与收藏管理 |
| 管理员手册 | /docs/admin/ | 如何添加新链接、批量导入、编辑分类与处理失效链接 |
| 开发文档 | /docs/developer/ | 项目架构说明、API 接口定义、数据模型与二次开发指引 |
| 部署指南 | /docs/deployment/ | 生产环境部署方案，包含 Nginx 配置、Docker 镜像构建与反向代理设置 |
| 设计原则 | /docs/design/ | 链接索引规范、URL 标准化规则、分类体系设计思路 |
| 常见操作 | /docs/recipes/ | 数据备份、迁移、批量替换域名、自定义主题等实操教程 |

## 资源列表

- http://map.mobile.xqnqq.com/Article/2232821.shtml
- http://map.read.usuhx.com/Article/7517.shtml
- http://map.read.usuhx.com/Article/579577.shtml
- http://map.mobile.xqnqq.com/Article/2940.shtml
- http://map.read.usuhx.com/Article/61335.shtml
- http://map.read.usuhx.com/Article/1598.shtml
- http://map.read.usuhx.com/Article/2043.shtml
- http://map.read.usuhx.com/Article/488891.shtml
- http://map.read.usuhx.com/Article/6257630.shtml
- http://map.read.usuhx.com/Article/8387.shtml
- http://map.read.usuhx.com/Article/7840.shtml
- http://map.mobile.xqnqq.com/Article/3791135.shtml
- http://map.read.usuhx.com/Article/984510.shtml
- http://map.read.usuhx.com/Article/90641.shtml
- http://map.mobile.xqnqq.com/Article/89216.shtml
- http://map.mobile.xqnqq.com/Article/0310.shtml
- http://map.mobile.xqnqq.com/Article/26480.shtml
- http://map.read.usuhx.com/Article/59450.shtml
- http://map.mobile.xqnqq.com/Article/460140.shtml
- http://map.mobile.xqnqq.com/Article/460094.shtml
- http://map.mobile.xqnqq.com/Article/3434.shtml
- http://map.read.usuhx.com/Article/8241.shtml
- http://map.mobile.xqnqq.com/Article/55089.shtml
- http://map.mobile.xqnqq.com/Article/2976011.shtml
- http://map.mobile.xqnqq.com/Article/265803.shtml
- http://map.read.usuhx.com/Article/9335844.shtml
- http://map.mobile.xqnqq.com/Article/3683.shtml
- http://map.read.usuhx.com/Article/70332.shtml
- http://map.mobile.xqnqq.com/Article/6625.shtml
- http://map.mobile.xqnqq.com/Article/8394571.shtml
- http://map.read.usuhx.com/Article/35853.shtml
- http://map.read.usuhx.com/Article/4364.shtml
- http://map.mobile.xqnqq.com/Article/5809841.shtml
- http://map.mobile.xqnqq.com/Article/1372.shtml
- http://map.read.usuhx.com/Article/1534.shtml
- http://map.read.usuhx.com/Article/3595.shtml
- http://map.mobile.xqnqq.com/Article/4977.shtml
- http://map.read.usuhx.com/Article/8539941.shtml
- http://map.read.usuhx.com/Article/26182.shtml
- http://map.mobile.xqnqq.com/Article/7062392.shtml
- http://map.mobile.xqnqq.com/Article/01039.shtml
- http://map.read.usuhx.com/Article/5341.shtml
- http://map.mobile.xqnqq.com/Article/859365.shtml
- http://map.mobile.xqnqq.com/Article/5128496.shtml
- http://map.read.usuhx.com/Article/72880.shtml
- http://map.read.usuhx.com/Article/2710441.shtml
- http://map.read.usuhx.com/Article/43139.shtml
- http://map.mobile.xqnqq.com/Article/46180.shtml
- http://map.read.usuhx.com/Article/37647.shtml
- http://map.read.usuhx.com/Article/16283.shtml
- http://map.mobile.xqnqq.com/Article/4692.shtml
- http://map.mobile.xqnqq.com/Article/7685.shtml
- http://map.mobile.xqnqq.com/Article/3982.shtml
- http://map.read.usuhx.com/Article/1439472.shtml
- http://map.read.usuhx.com/Article/173437.shtml
- http://map.mobile.xqnqq.com/Article/3918448.shtml
- http://map.read.usuhx.com/Article/13806.shtml
- http://map.read.usuhx.com/Article/52905.shtml
- http://map.mobile.xqnqq.com/Article/2192.shtml
- http://map.mobile.xqnqq.com/Article/555107.shtml
- http://map.mobile.xqnqq.com/Article/919114.shtml
- http://map.mobile.xqnqq.com/Article/058620.shtml
- http://map.read.usuhx.com/Article/7964442.shtml
- http://map.read.usuhx.com/Article/944608.shtml
- http://map.mobile.xqnqq.com/Article/8862.shtml
- http://map.mobile.xqnqq.com/Article/273576.shtml
- http://map.mobile.xqnqq.com/Article/39054.shtml
- http://map.mobile.xqnqq.com/Article/97819.shtml
- http://map.mobile.xqnqq.com/Article/6514961.shtml
- http://map.read.usuhx.com/Article/8604.shtml
- http://map.read.usuhx.com/Article/7386198.shtml
- http://map.mobile.xqnqq.com/Article/30255.shtml
- http://map.read.usuhx.com/Article/86035.shtml
- http://map.read.usuhx.com/Article/65711.shtml
- http://map.mobile.xqnqq.com/Article/5279.shtml
- http://map.read.usuhx.com/Article/483614.shtml
- http://map.read.usuhx.com/Article/18718.shtml
- http://map.read.usuhx.com/Article/8955.shtml
- http://map.read.usuhx.com/Article/3461.shtml
- http://map.mobile.xqnqq.com/Article/2235853.shtml
- http://map.mobile.xqnqq.com/Article/875729.shtml
- http://map.read.usuhx.com/Article/5914244.shtml
- http://map.read.usuhx.com/Article/9697.shtml
- http://map.mobile.xqnqq.com/Article/5101963.shtml
- http://map.read.usuhx.com/Article/0038503.shtml
- http://map.mobile.xqnqq.com/Article/43089.shtml
- http://map.mobile.xqnqq.com/Article/790849.shtml
- http://map.read.usuhx.com/Article/0744614.shtml
- http://map.read.usuhx.com/Article/99017.shtml
- http://map.read.usuhx.com/Article/076013.shtml
- http://map.mobile.xqnqq.com/Article/5029.shtml
- http://map.mobile.xqnqq.com/Article/9767.shtml
- http://map.mobile.xqnqq.com/Article/83880.shtml
- http://map.read.usuhx.com/Article/473491.shtml
- http://map.read.usuhx.com/Article/7157181.shtml
- http://map.read.usuhx.com/Article/578202.shtml
- http://map.read.usuhx.com/Article/949284.shtml
- http://map.mobile.xqnqq.com/Article/234751.shtml
- http://map.mobile.xqnqq.com/Article/44921.shtml
- http://map.mobile.xqnqq.com/Article/98710.shtml
- http://map.mobile.xqnqq.com/Article/3594489.shtml
- http://map.mobile.xqnqq.com/Article/7974210.shtml
- http://map.read.usuhx.com/Article/746174.shtml
- http://map.mobile.xqnqq.com/Article/52484.shtml
- http://map.read.usuhx.com/Article/791580.shtml
- http://map.mobile.xqnqq.com/Article/182486.shtml
- http://map.read.usuhx.com/Article/7293978.shtml
- http://map.read.usuhx.com/Article/30845.shtml
- http://map.mobile.xqnqq.com/Article/9952.shtml
- http://map.mobile.xqnqq.com/Article/088530.shtml
- http://map.read.usuhx.com/Article/0196653.shtml
- http://map.read.usuhx.com/Article/184310.shtml
- http://map.mobile.xqnqq.com/Article/5015845.shtml
- http://map.read.usuhx.com/Article/14357.shtml
- http://map.read.usuhx.com/Article/99309.shtml
- http://map.read.usuhx.com/Article/58471.shtml
- http://map.mobile.xqnqq.com/Article/48956.shtml
- http://map.read.usuhx.com/Article/540127.shtml
- http://map.mobile.xqnqq.com/Article/86112.shtml
- http://map.read.usuhx.com/Article/09447.shtml
- http://map.mobile.xqnqq.com/Article/04071.shtml
- http://map.mobile.xqnqq.com/Article/65409.shtml
- http://map.mobile.xqnqq.com/Article/3194.shtml
- http://map.mobile.xqnqq.com/Article/58047.shtml
- http://map.mobile.xqnqq.com/Article/0798623.shtml
- http://map.read.usuhx.com/Article/4582.shtml
- http://map.mobile.xqnqq.com/Article/79295.shtml
- http://map.mobile.xqnqq.com/Article/65855.shtml
- http://map.mobile.xqnqq.com/Article/88090.shtml
- http://map.mobile.xqnqq.com/Article/4306.shtml
- http://map.mobile.xqnqq.com/Article/28544.shtml
- http://map.mobile.xqnqq.com/Article/3708095.shtml
- http://map.read.usuhx.com/Article/7749.shtml
- http://map.read.usuhx.com/Article/8611.shtml
- http://map.mobile.xqnqq.com/Article/578787.shtml
- http://map.mobile.xqnqq.com/Article/3375.shtml
- http://map.read.usuhx.com/Article/4233.shtml
- http://map.mobile.xqnqq.com/Article/43382.shtml
- http://map.read.usuhx.com/Article/9516.shtml
- http://map.mobile.xqnqq.com/Article/657346.shtml
- http://map.read.usuhx.com/Article/94389.shtml
- http://map.read.usuhx.com/Article/5576853.shtml
- http://map.read.usuhx.com/Article/305305.shtml
- http://map.mobile.xqnqq.com/Article/45172.shtml
- http://map.mobile.xqnqq.com/Article/30694.shtml
- http://map.mobile.xqnqq.com/Article/07644.shtml
- http://map.read.usuhx.com/Article/004674.shtml
- http://map.read.usuhx.com/Article/24010.shtml
- http://map.read.usuhx.com/Article/1561.shtml
- http://map.mobile.xqnqq.com/Article/26562.shtml
- http://map.mobile.xqnqq.com/Article/839764.shtml
- http://map.read.usuhx.com/Article/516901.shtml
- http://map.mobile.xqnqq.com/Article/0007675.shtml
- http://map.mobile.xqnqq.com/Article/129512.shtml
- http://map.mobile.xqnqq.com/Article/6157.shtml
- http://map.mobile.xqnqq.com/Article/0985733.shtml
- http://map.mobile.xqnqq.com/Article/96826.shtml
- http://map.read.usuhx.com/Article/9212.shtml
- http://map.mobile.xqnqq.com/Article/9742.shtml
- http://map.read.usuhx.com/Article/1388.shtml
- http://map.read.usuhx.com/Article/85098.shtml
- http://map.mobile.xqnqq.com/Article/04500.shtml
- http://map.read.usuhx.com/Article/18983.shtml
- http://map.read.usuhx.com/Article/7958.shtml
- http://map.read.usuhx.com/Article/190883.shtml
- http://map.read.usuhx.com/Article/6144.shtml
- http://map.read.usuhx.com/Article/9969.shtml
- http://map.read.usuhx.com/Article/0233119.shtml
- http://map.mobile.xqnqq.com/Article/2476.shtml
- http://map.mobile.xqnqq.com/Article/969897.shtml
- http://map.mobile.xqnqq.com/Article/30410.shtml
- http://map.read.usuhx.com/Article/0052.shtml
- http://map.read.usuhx.com/Article/5510736.shtml
- http://map.mobile.xqnqq.com/Article/5124875.shtml
- http://map.mobile.xqnqq.com/Article/07660.shtml
- http://map.read.usuhx.com/Article/2193.shtml
- http://map.read.usuhx.com/Article/878866.shtml
- http://map.mobile.xqnqq.com/Article/802511.shtml
- http://map.read.usuhx.com/Article/8808053.shtml
- http://map.mobile.xqnqq.com/Article/506706.shtml
- http://map.read.usuhx.com/Article/4949.shtml
- http://map.read.usuhx.com/Article/54711.shtml
- http://map.mobile.xqnqq.com/Article/738656.shtml
- http://map.read.usuhx.com/Article/00128.shtml
- http://map.mobile.xqnqq.com/Article/18773.shtml
- http://map.read.usuhx.com/Article/7907268.shtml
- http://map.read.usuhx.com/Article/79774.shtml
- http://map.mobile.xqnqq.com/Article/76916.shtml
- http://map.read.usuhx.com/Article/11209.shtml
- http://map.mobile.xqnqq.com/Article/8893.shtml
- http://map.read.usuhx.com/Article/4641718.shtml
- http://map.mobile.xqnqq.com/Article/614676.shtml
- http://map.mobile.xqnqq.com/Article/24931.shtml
- http://map.mobile.xqnqq.com/Article/708659.shtml
- http://map.read.usuhx.com/Article/34784.shtml
- http://map.mobile.xqnqq.com/Article/25057.shtml
- http://map.read.usuhx.com/Article/1425.shtml
- http://map.mobile.xqnqq.com/Article/3223.shtml
- http://map.mobile.xqnqq.com/Article/772876.shtml
- http://map.read.usuhx.com/Article/63158.shtml
- http://map.read.usuhx.com/Article/04463.shtml
- http://map.mobile.xqnqq.com/Article/6924059.shtml
- http://map.read.usuhx.com/Article/2533.shtml
- http://map.read.usuhx.com/Article/9491.shtml
- http://map.mobile.xqnqq.com/Article/3920.shtml
- http://map.mobile.xqnqq.com/Article/215280.shtml
- http://map.mobile.xqnqq.com/Article/467605.shtml
- http://map.mobile.xqnqq.com/Article/5503795.shtml
- http://map.mobile.xqnqq.com/Article/1838077.shtml
- http://map.mobile.xqnqq.com/Article/435876.shtml
- http://map.mobile.xqnqq.com/Article/178664.shtml
- http://map.mobile.xqnqq.com/Article/816039.shtml
- http://map.read.usuhx.com/Article/4927305.shtml
- http://map.read.usuhx.com/Article/4439654.shtml
- http://map.mobile.xqnqq.com/Article/8203.shtml
- http://map.read.usuhx.com/Article/777673.shtml
- http://map.read.usuhx.com/Article/638907.shtml
- http://map.read.usuhx.com/Article/0887184.shtml
- http://map.mobile.xqnqq.com/Article/4662957.shtml
- http://map.read.usuhx.com/Article/1440.shtml
- http://map.mobile.xqnqq.com/Article/9332320.shtml
- http://map.mobile.xqnqq.com/Article/01566.shtml
- http://map.read.usuhx.com/Article/9942.shtml
- http://map.read.usuhx.com/Article/80956.shtml
- http://map.mobile.xqnqq.com/Article/802827.shtml
- http://map.mobile.xqnqq.com/Article/34497.shtml
- http://map.mobile.xqnqq.com/Article/9968.shtml
- http://map.read.usuhx.com/Article/9899462.shtml
- http://map.mobile.xqnqq.com/Article/6221.shtml
- http://map.mobile.xqnqq.com/Article/734236.shtml
- http://map.mobile.xqnqq.com/Article/67352.shtml
- http://map.mobile.xqnqq.com/Article/13512.shtml
- http://map.mobile.xqnqq.com/Article/1954.shtml
- http://map.mobile.xqnqq.com/Article/258795.shtml
- http://map.read.usuhx.com/Article/73592.shtml
- http://map.mobile.xqnqq.com/Article/650341.shtml
- http://map.mobile.xqnqq.com/Article/5881909.shtml
- http://map.read.usuhx.com/Article/565733.shtml
- http://map.read.usuhx.com/Article/7900.shtml
- http://map.mobile.xqnqq.com/Article/00223.shtml
- http://map.mobile.xqnqq.com/Article/5930851.shtml
- http://map.mobile.xqnqq.com/Article/444021.shtml
- http://map.mobile.xqnqq.com/Article/2694.shtml
- http://map.mobile.xqnqq.com/Article/98999.shtml
- http://map.read.usuhx.com/Article/54204.shtml
- http://map.mobile.xqnqq.com/Article/8143.shtml
- http://map.mobile.xqnqq.com/Article/89740.shtml
- http://map.mobile.xqnqq.com/Article/70122.shtml
- http://map.mobile.xqnqq.com/Article/6912182.shtml
- http://map.read.usuhx.com/Article/9024399.shtml

## 项目结构

```
webmap-indexer/
├── bin/                           # 可执行入口文件目录
│   └── webmap-cli.js              # CLI 工具入口，支持导入/导出/校验命令
├── config/                        # 配置文件目录
│   ├── default.yaml               # 默认配置项（端口、缓存时间、分页大小）
│   ├── sources.json               # 数据源域名白名单与别名映射
│   └── categories.yaml            # 内置分类层级定义
├── src/                           # 核心源代码目录
│   ├── core/                      # 核心逻辑模块
│   │   ├── indexer.js             # 链接索引构建器，负责解析与规范化 URL
│   │   ├── validator.js           # 链接校验器，执行 HTTP 状态检查
│   │   └── cache.js               # 缓存管理模块，基于 LRU 策略
│   ├── api/                       # RESTful API 接口层
│   │   ├── routes.js              # 路由定义（列表/详情/导入/导出）
│   │   └── controllers.js         # 请求控制器实现
│   ├── ui/                        # 前端界面组件
│   │   ├── pages/                 # 页面级组件（首页/列表页/详情页）
│   │   ├── components/            # 可复用 UI 组件（表格/筛选器/分页）
│   │   └── static/                # 静态资源（CSS/JS/字体）
│   ├── adapters/                  # 存储适配器
│   │   ├── jsonfile.js            # JSON 文件读写适配器（默认）
│   │   └── sqlite.js              # SQLite 适配器（可选）
│   └── utils/                     # 工具函数集合
│       ├── url-helper.js          # URL 解析、域名提取、路径规范化
│       └── logger.js              # 日志输出封装
├── data/                          # 数据存储目录
│   ├── links.json                 # 主索引数据文件（所有链接记录）
│   ├── checksums.json             # 链接校验结果缓存
│   └── imports/                   # 批量导入临时文件存放目录
├── docs/                          # 完整文档体系
│   ├── user-guide/                # 用户指南文档
│   ├── admin/                     # 管理员操作文档
│   ├── developer/                 # 开发与 API 文档
│   └── deployment/                # 部署与运维文档
├── tests/                         # 单元测试与集成测试
│   ├── unit/                      # 单元测试用例
│   └── integration/               # 端到端集成测试
├── scripts/                       # 辅助脚本
│   ├── migrate.js                 # 数据迁移脚本（版本升级）
│   └── health-check.js            # 定时健康检查脚本
├── .github/                       # GitHub 配置
│   └── workflows/                 # CI 流水线定义
│       ├── test.yml               # 测试流水线
│       └── deploy.yml             # 自动部署流水线
├── package.json                   # Node.js 项目清单
├── README.md                      # 项目主文档（当前文件）
└── LICENSE                        # MIT 许可证文本
```

## 贡献指南

1. 复刻项目仓库至个人账户，并在本地完成开发环境搭建。请确保 Node.js 版本符合要求，并执行 npm install 安装全部依赖。所有新增依赖需在 package.json 中明确声明版本。

2. 在 src/ 目录下新增或修改功能时，请严格遵守现有代码风格（使用 ESLint 配置）。所有公共函数必须附带 JSDoc 注释，说明参数类型、返回值与可能抛出的异常。新增功能需在 tests/ 下补充对应的单元测试用例。

3. 提交代码前请运行 npm run test 确保所有测试通过，并运行 npm run lint 检查代码规范。提交信息请遵循 Conventional Commits 格式，使用 feat / fix / docs / style / refactor / test / chore 等前缀，并简要描述变更内容。

4. 提交 Pull Request 时，请在描述中清晰说明解决的问题、实现方案以及测试覆盖情况。若涉及数据模型或配置结构变更，必须提供迁移脚本或详细的升级指引。

5. 文档类贡献可直接在 docs/ 目录下修改或新增 .md 文件。若新增分类标签或操作指南，请同步更新文档导航表格中的目录条目，确保文档体系保持完整与一致。

## 常见问题

问：索引站收录的链接访问时返回 404 或超时，应如何处理？

系统每日凌晨自动执行一次全量链接健康检查，并将状态更新至 data/checksums.json。用户可在管理界面的“失效链接”视图中查看所有异常记录。对于确认失效的链接，管理员可手动标记为“已失效”或删除该条目。若链接临时不可用，系统会在连续三次检查失败后方标记失效，避免因短暂网络波动导致误判。

问：如何批量导入自定义链接列表，而不是逐条手动添加？

在管理界面进入“批量导入”功能，选择 CSV 或纯文本格式文件上传。CSV 文件需包含 url 列，可选 title、category、tags 列；纯文本文件每行一个 URL。系统会自动进行去重与格式校验，并在导入完成后展示新增数量、跳过数量与异常记录。导入后的数据会自动合并到 data/links.json 中，原有数据不受影响。

问：项目是否支持私有化部署与离线环境使用？

完全支持。WebMap 所有依赖项在安装时即完整下载到本地 node_modules 目录，运行时无需额外联网（除链接健康检查功能外）。用户可将整个项目目录拷贝至内网服务器，修改 config/default.yaml 中的 listen 地址与端口即可启动。健康检查功能可通过配置关闭或切换为内网探测模式，以适应离线环境。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
