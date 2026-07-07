# LinkVault Core

LinkVault Core 是一个面向技术团队与内容研究者的外链资源归集与结构化管理系统。项目定位于解决分散于多源、多域名、多批次的技术文章、参考资料与外部文档的收录、分类、检索与版本追踪问题。目标用户包括技术文档工程师、开源项目维护者、知识库管理员以及需要进行大规模外链审计与合规检查的开发团队。LinkVault Core 本身不生产内容，而是提供一套标准化的外链描述规范、导入导出工具与轻量级 Web 界面，帮助用户将来自不同域名的散乱 URL 转化为可维护、可查询、可分享的资产清单。本项目当前批次收录资源共计 250 条，覆盖第 33/80 批导入任务，所有链接均经过基础可达性校验与域名归类。

## 功能概览

**多源链接批量导入** 支持从纯文本、CSV 及 Markdown 列表批量导入 URL，自动识别协议与域名，并对异常格式进行告警。

**域名聚合与分组视图** 自动按顶级域名与二级域名对资源进行分组统计，便于快速了解当前库中不同来源站点的分布比例。

**资源状态标记系统** 每条链接可标记为未读、研究中、已引用、已归档或废弃，支持状态筛选与批量更新。

**自定义标签与注解字段** 允许用户为每条链接附加多个标签（如 backend、frontend、security、tutorial）以及不超过 500 字的注解说明。

**全文检索与字段过滤** 基于标题、注解、标签和 URL 路径关键词的全文检索能力，并支持按域名、状态、标签组合过滤。

**导入导出标准化接口** 支持将当前筛选结果导出为 JSON、CSV 或结构化 Markdown 列表，便于嵌入项目文档或迁移至其他知识管理工具。

**批处理进度与历史记录** 记录每次批量导入的数量、时间、失败条目及错误日志，支持重新处理失败条目。

## 应用场景

技术文档团队进行外部参考链接整理。当编写系统设计文档或 API 使用指南时，团队成员需要引用大量外部技术博客、官方规范与社区讨论帖。LinkVault Core 可将这些散落的链接统一入库，并为每条链接标注对应的文档章节编号与审核状态，确保最终发布文档中所有外链均为有效且经过技术评审。

开源项目维护者管理外部依赖与参考资源。开源项目的 README 或贡献指南中常包含大量指向依赖库、示例项目、协议文本的链接。这些链接随着时间推移可能失效或变更。项目维护者可使用 LinkVault Core 定期导入项目中的所有外链，批量检查状态，并生成最新的可用链接列表用于文档更新。

安全与合规团队进行外链审计。企业内网环境或对公网内容有严格合规要求的团队，需要定期审查项目中引用的所有外部链接是否指向合法、安全且符合政策的内容。LinkVault Core 提供统一的资源清单导出与标签筛选功能，配合自动化状态标记流程，可显著降低人工逐条核对的开销。

## 快速开始

以下步骤适用于 Linux 与 macOS 环境，Windows 用户可使用 WSL2 或 Git Bash 执行。

```bash
git clone https://github.com/linkvault/core.git
cd core
npm install
npm run build
npm start
```

执行完成后，服务默认监听本机 3000 端口。访问 http://127.0.0.1:3000 即可进入资源管理界面。首次启动会自动创建示例数据库与默认管理员账户，登录信息请查看启动日志中的提示。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
| :--- | :--- | :--- |
| Node.js | 18.x 或 20.x LTS | 运行时环境，不支持奇数版本 |
| npm | 9.x 或以上 | 包管理器，用于安装项目依赖 |
| SQLite3 | 系统自带或由 better-sqlite3 提供 | 嵌入式数据库，无需额外安装服务 |
| Git | 2.25 或以上 | 用于克隆仓库及后续版本更新 |
| 操作系统 | Linux (glibc 2.28+), macOS 11+, 或 Windows 10 21H2+ | 支持主流开发环境 |
| 内存 | 最低 512 MB，推荐 1 GB | 用于 Web 界面与索引缓存 |
| 磁盘空间 | 最低 100 MB | 主要用于存储数据库与日志文件 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
| :--- | :--- | :--- |
| 用户手册 | docs/user-guide/ | 如何登录、导入链接、使用标签与状态筛选、执行批量导出操作 |
| 管理员指南 | docs/admin-guide/ | 如何配置数据库路径、修改端口、启用访问日志、调整批处理大小 |
| 开发参考 | docs/development/ | 项目模块划分、核心数据模型、API 路由定义及扩展插件编写方法 |
| 运维部署 | docs/deployment/ | 使用 systemd 或 Docker 部署生产环境实例、备份与恢复策略 |

## 资源列表

- http://www.read.usuhx.com/Article/3694.shtml
- http://www.mobile.xqnqq.com/Article/89729.shtml
- http://www.mobile.xqnqq.com/Article/1200424.shtml
- http://www.mobile.xqnqq.com/Article/1451.shtml
- http://www.read.usuhx.com/Article/591020.shtml
- http://www.mobile.xqnqq.com/Article/74410.shtml
- http://www.read.usuhx.com/Article/8272175.shtml
- http://www.read.usuhx.com/Article/90032.shtml
- http://www.mobile.xqnqq.com/Article/4484408.shtml
- http://www.mobile.xqnqq.com/Article/8914.shtml
- http://www.read.usuhx.com/Article/56336.shtml
- http://www.mobile.xqnqq.com/Article/9997.shtml
- http://www.mobile.xqnqq.com/Article/7164846.shtml
- http://www.read.usuhx.com/Article/7476.shtml
- http://www.read.usuhx.com/Article/01648.shtml
- http://www.read.usuhx.com/Article/46240.shtml
- http://www.read.usuhx.com/Article/9303345.shtml
- http://www.read.usuhx.com/Article/7127.shtml
- http://www.read.usuhx.com/Article/94741.shtml
- http://www.mobile.xqnqq.com/Article/144309.shtml
- http://www.mobile.xqnqq.com/Article/9877.shtml
- http://www.mobile.xqnqq.com/Article/6180.shtml
- http://www.mobile.xqnqq.com/Article/7926.shtml
- http://www.read.usuhx.com/Article/128481.shtml
- http://www.read.usuhx.com/Article/20600.shtml
- http://www.read.usuhx.com/Article/2158102.shtml
- http://www.mobile.xqnqq.com/Article/311130.shtml
- http://www.mobile.xqnqq.com/Article/34456.shtml
- http://www.read.usuhx.com/Article/6194849.shtml
- http://www.read.usuhx.com/Article/4562725.shtml
- http://www.mobile.xqnqq.com/Article/4724.shtml
- http://www.mobile.xqnqq.com/Article/25236.shtml
- http://www.read.usuhx.com/Article/953340.shtml
- http://www.mobile.xqnqq.com/Article/380772.shtml
- http://www.read.usuhx.com/Article/6413.shtml
- http://www.read.usuhx.com/Article/7963.shtml
- http://www.mobile.xqnqq.com/Article/302866.shtml
- http://www.read.usuhx.com/Article/102337.shtml
- http://www.read.usuhx.com/Article/95185.shtml
- http://www.mobile.xqnqq.com/Article/75769.shtml
- http://www.read.usuhx.com/Article/8316192.shtml
- http://www.mobile.xqnqq.com/Article/70647.shtml
- http://www.read.usuhx.com/Article/76719.shtml
- http://www.mobile.xqnqq.com/Article/3708.shtml
- http://www.mobile.xqnqq.com/Article/9192179.shtml
- http://www.read.usuhx.com/Article/824249.shtml
- http://www.mobile.xqnqq.com/Article/484066.shtml
- http://www.mobile.xqnqq.com/Article/9205184.shtml
- http://www.read.usuhx.com/Article/1018458.shtml
- http://www.read.usuhx.com/Article/7400.shtml
- http://www.read.usuhx.com/Article/9180185.shtml
- http://www.read.usuhx.com/Article/1492.shtml
- http://www.read.usuhx.com/Article/942407.shtml
- http://www.mobile.xqnqq.com/Article/0862810.shtml
- http://www.mobile.xqnqq.com/Article/40056.shtml
- http://www.read.usuhx.com/Article/72368.shtml
- http://www.mobile.xqnqq.com/Article/7539398.shtml
- http://www.read.usuhx.com/Article/73259.shtml
- http://www.read.usuhx.com/Article/5313537.shtml
- http://www.read.usuhx.com/Article/207119.shtml
- http://www.read.usuhx.com/Article/919989.shtml
- http://www.mobile.xqnqq.com/Article/1322067.shtml
- http://www.read.usuhx.com/Article/41660.shtml
- http://www.mobile.xqnqq.com/Article/4319.shtml
- http://www.read.usuhx.com/Article/739099.shtml
- http://www.mobile.xqnqq.com/Article/8027.shtml
- http://www.read.usuhx.com/Article/30922.shtml
- http://www.mobile.xqnqq.com/Article/559349.shtml
- http://www.mobile.xqnqq.com/Article/1676739.shtml
- http://www.mobile.xqnqq.com/Article/932514.shtml
- http://www.read.usuhx.com/Article/4452.shtml
- http://www.read.usuhx.com/Article/8065822.shtml
- http://www.read.usuhx.com/Article/0056501.shtml
- http://www.read.usuhx.com/Article/8500.shtml
- http://www.read.usuhx.com/Article/17267.shtml
- http://www.mobile.xqnqq.com/Article/09672.shtml
- http://www.mobile.xqnqq.com/Article/46488.shtml
- http://www.read.usuhx.com/Article/520738.shtml
- http://www.mobile.xqnqq.com/Article/172993.shtml
- http://www.mobile.xqnqq.com/Article/2271.shtml
- http://www.read.usuhx.com/Article/9316.shtml
- http://www.read.usuhx.com/Article/420045.shtml
- http://www.read.usuhx.com/Article/6556695.shtml
- http://www.mobile.xqnqq.com/Article/475069.shtml
- http://www.mobile.xqnqq.com/Article/8109967.shtml
- http://www.mobile.xqnqq.com/Article/1626.shtml
- http://www.mobile.xqnqq.com/Article/2329832.shtml
- http://www.read.usuhx.com/Article/1087.shtml
- http://www.read.usuhx.com/Article/069267.shtml
- http://www.mobile.xqnqq.com/Article/54396.shtml
- http://www.mobile.xqnqq.com/Article/2630610.shtml
- http://www.read.usuhx.com/Article/8539002.shtml
- http://www.mobile.xqnqq.com/Article/2982700.shtml
- http://www.mobile.xqnqq.com/Article/11722.shtml
- http://www.mobile.xqnqq.com/Article/7814.shtml
- http://www.mobile.xqnqq.com/Article/1150.shtml
- http://www.read.usuhx.com/Article/04752.shtml
- http://www.read.usuhx.com/Article/1350845.shtml
- http://www.read.usuhx.com/Article/728149.shtml
- http://www.read.usuhx.com/Article/98779.shtml
- http://www.read.usuhx.com/Article/27522.shtml
- http://www.read.usuhx.com/Article/1389600.shtml
- http://www.read.usuhx.com/Article/504049.shtml
- http://www.mobile.xqnqq.com/Article/7622.shtml
- http://www.mobile.xqnqq.com/Article/754525.shtml
- http://www.mobile.xqnqq.com/Article/76896.shtml
- http://www.read.usuhx.com/Article/101205.shtml
- http://www.mobile.xqnqq.com/Article/502526.shtml
- http://www.read.usuhx.com/Article/8522653.shtml
- http://www.read.usuhx.com/Article/996562.shtml
- http://www.read.usuhx.com/Article/7687.shtml
- http://www.mobile.xqnqq.com/Article/6638782.shtml
- http://www.mobile.xqnqq.com/Article/09419.shtml
- http://www.read.usuhx.com/Article/2723.shtml
- http://www.read.usuhx.com/Article/84573.shtml
- http://www.mobile.xqnqq.com/Article/1946024.shtml
- http://www.read.usuhx.com/Article/38643.shtml
- http://www.read.usuhx.com/Article/1044.shtml
- http://www.read.usuhx.com/Article/10935.shtml
- http://www.mobile.xqnqq.com/Article/575389.shtml
- http://www.read.usuhx.com/Article/7669286.shtml
- http://www.read.usuhx.com/Article/9248205.shtml
- http://www.read.usuhx.com/Article/156868.shtml
- http://www.read.usuhx.com/Article/0222.shtml
- http://www.mobile.xqnqq.com/Article/3856559.shtml
- http://www.mobile.xqnqq.com/Article/26405.shtml
- http://www.read.usuhx.com/Article/534897.shtml
- http://www.mobile.xqnqq.com/Article/17128.shtml
- http://www.mobile.xqnqq.com/Article/133037.shtml
- http://www.read.usuhx.com/Article/4263593.shtml
- http://www.read.usuhx.com/Article/232487.shtml
- http://www.read.usuhx.com/Article/82583.shtml
- http://www.read.usuhx.com/Article/858825.shtml
- http://www.mobile.xqnqq.com/Article/412416.shtml
- http://www.read.usuhx.com/Article/9637486.shtml
- http://www.read.usuhx.com/Article/519614.shtml
- http://www.mobile.xqnqq.com/Article/6076730.shtml
- http://www.mobile.xqnqq.com/Article/38184.shtml
- http://www.read.usuhx.com/Article/5859857.shtml
- http://www.read.usuhx.com/Article/942831.shtml
- http://www.read.usuhx.com/Article/8400738.shtml
- http://www.mobile.xqnqq.com/Article/451315.shtml
- http://www.mobile.xqnqq.com/Article/5201668.shtml
- http://www.mobile.xqnqq.com/Article/9744865.shtml
- http://www.read.usuhx.com/Article/5511.shtml
- http://www.read.usuhx.com/Article/1305172.shtml
- http://www.mobile.xqnqq.com/Article/5303.shtml
- http://www.mobile.xqnqq.com/Article/3234.shtml
- http://www.read.usuhx.com/Article/4156.shtml
- http://www.read.usuhx.com/Article/0765.shtml
- http://www.mobile.xqnqq.com/Article/41695.shtml
- http://www.mobile.xqnqq.com/Article/6858.shtml
- http://www.read.usuhx.com/Article/4332.shtml
- http://www.mobile.xqnqq.com/Article/6870.shtml
- http://www.read.usuhx.com/Article/254004.shtml
- http://www.mobile.xqnqq.com/Article/141412.shtml
- http://www.read.usuhx.com/Article/695995.shtml
- http://www.mobile.xqnqq.com/Article/5198929.shtml
- http://www.read.usuhx.com/Article/12888.shtml
- http://www.read.usuhx.com/Article/666705.shtml
- http://www.read.usuhx.com/Article/4540.shtml
- http://www.mobile.xqnqq.com/Article/1628554.shtml
- http://www.mobile.xqnqq.com/Article/37164.shtml
- http://www.mobile.xqnqq.com/Article/9655.shtml
- http://www.read.usuhx.com/Article/7728925.shtml
- http://www.mobile.xqnqq.com/Article/3158741.shtml
- http://www.read.usuhx.com/Article/8458.shtml
- http://www.mobile.xqnqq.com/Article/9682.shtml
- http://www.mobile.xqnqq.com/Article/525071.shtml
- http://www.read.usuhx.com/Article/8403.shtml
- http://www.read.usuhx.com/Article/08014.shtml
- http://www.mobile.xqnqq.com/Article/926162.shtml
- http://www.read.usuhx.com/Article/97202.shtml
- http://www.read.usuhx.com/Article/23154.shtml
- http://www.read.usuhx.com/Article/25656.shtml
- http://www.mobile.xqnqq.com/Article/3703.shtml
- http://www.read.usuhx.com/Article/129447.shtml
- http://www.read.usuhx.com/Article/5418286.shtml
- http://www.read.usuhx.com/Article/272036.shtml
- http://www.mobile.xqnqq.com/Article/778544.shtml
- http://www.mobile.xqnqq.com/Article/5088.shtml
- http://www.read.usuhx.com/Article/37472.shtml
- http://www.mobile.xqnqq.com/Article/12215.shtml
- http://www.mobile.xqnqq.com/Article/91832.shtml
- http://www.mobile.xqnqq.com/Article/7036418.shtml
- http://www.mobile.xqnqq.com/Article/0103.shtml
- http://www.read.usuhx.com/Article/38394.shtml
- http://www.mobile.xqnqq.com/Article/5321.shtml
- http://www.read.usuhx.com/Article/87397.shtml
- http://www.read.usuhx.com/Article/8116.shtml
- http://www.read.usuhx.com/Article/729454.shtml
- http://www.read.usuhx.com/Article/3335325.shtml
- http://www.mobile.xqnqq.com/Article/0762340.shtml
- http://www.read.usuhx.com/Article/94531.shtml
- http://www.mobile.xqnqq.com/Article/023287.shtml
- http://www.mobile.xqnqq.com/Article/47945.shtml
- http://www.read.usuhx.com/Article/89430.shtml
- http://www.read.usuhx.com/Article/976318.shtml
- http://www.read.usuhx.com/Article/613470.shtml
- http://www.mobile.xqnqq.com/Article/7747.shtml
- http://www.mobile.xqnqq.com/Article/2746780.shtml
- http://www.mobile.xqnqq.com/Article/9215.shtml
- http://www.mobile.xqnqq.com/Article/74868.shtml
- http://www.read.usuhx.com/Article/272103.shtml
- http://www.read.usuhx.com/Article/188598.shtml
- http://www.mobile.xqnqq.com/Article/35842.shtml
- http://www.mobile.xqnqq.com/Article/06111.shtml
- http://www.mobile.xqnqq.com/Article/1083364.shtml
- http://www.mobile.xqnqq.com/Article/7993.shtml
- http://www.mobile.xqnqq.com/Article/219621.shtml
- http://www.mobile.xqnqq.com/Article/2120537.shtml
- http://www.mobile.xqnqq.com/Article/332391.shtml
- http://www.mobile.xqnqq.com/Article/88404.shtml
- http://www.mobile.xqnqq.com/Article/8243.shtml
- http://www.read.usuhx.com/Article/72589.shtml
- http://www.read.usuhx.com/Article/3184.shtml
- http://www.mobile.xqnqq.com/Article/3571.shtml
- http://www.mobile.xqnqq.com/Article/51835.shtml
- http://www.mobile.xqnqq.com/Article/284894.shtml
- http://www.read.usuhx.com/Article/327727.shtml
- http://www.read.usuhx.com/Article/5016619.shtml
- http://www.mobile.xqnqq.com/Article/2260.shtml
- http://www.read.usuhx.com/Article/5126209.shtml
- http://www.mobile.xqnqq.com/Article/0237449.shtml
- http://www.mobile.xqnqq.com/Article/93745.shtml
- http://www.read.usuhx.com/Article/515621.shtml
- http://www.mobile.xqnqq.com/Article/65349.shtml
- http://www.read.usuhx.com/Article/9327284.shtml
- http://www.mobile.xqnqq.com/Article/5310.shtml
- http://www.mobile.xqnqq.com/Article/5779607.shtml
- http://www.mobile.xqnqq.com/Article/5265.shtml
- http://www.mobile.xqnqq.com/Article/08641.shtml
- http://www.mobile.xqnqq.com/Article/0624217.shtml
- http://www.read.usuhx.com/Article/19761.shtml
- http://www.mobile.xqnqq.com/Article/727417.shtml
- http://www.read.usuhx.com/Article/97276.shtml
- http://www.read.usuhx.com/Article/07779.shtml
- http://www.read.usuhx.com/Article/571678.shtml
- http://www.mobile.xqnqq.com/Article/62429.shtml
- http://www.read.usuhx.com/Article/282568.shtml
- http://www.read.usuhx.com/Article/84851.shtml
- http://www.read.usuhx.com/Article/3916.shtml
- http://www.mobile.xqnqq.com/Article/7520.shtml
- http://www.read.usuhx.com/Article/1972537.shtml
- http://www.read.usuhx.com/Article/1951.shtml
- http://www.mobile.xqnqq.com/Article/74102.shtml
- http://www.mobile.xqnqq.com/Article/0501482.shtml
- http://www.read.usuhx.com/Article/1365.shtml
- http://www.mobile.xqnqq.com/Article/528627.shtml
- http://www.mobile.xqnqq.com/Article/01544.shtml

## 项目结构

```
core/
├── src/                                # 核心源代码目录
│   ├── main/                           # 主程序入口与全局配置
│   │   ├── app.js                      # Express 应用初始化与中间件加载
│   │   └── config.js                   # 环境变量解析与运行时配置对象
│   ├── routes/                         # HTTP 路由定义层
│   │   ├── api/                        # RESTful API 路由，按资源拆分
│   │   │   ├── links.js                # 链接资源的 CRUD 与批量操作接口
│   │   │   ├── tags.js                 # 标签管理接口
│   │   │   └── import.js               # 批量导入专用端点
│   │   └── web/                        # 服务端渲染页面路由
│   │       └── dashboard.js            # 主控制面板页面路由
│   ├── services/                       # 业务逻辑服务层
│   │   ├── linkService.js              # 链接增删改查、状态更新与检索服务
│   │   ├── importService.js            # 解析不同格式输入并批量写入数据库
│   │   └── statsService.js             # 域名聚合、状态计数等统计服务
│   ├── repositories/                   # 数据访问层，封装 SQLite 操作
│   │   ├── linkRepository.js           # 链接表的基础查询与写入方法
│   │   ├── tagRepository.js            # 标签表与关联表的操作
│   │   └── migrationRepository.js      # 数据库版本迁移与初始化脚本
│   ├── models/                         # 数据模型与类型定义
│   │   ├── Link.js                     # 链接实体类，包含校验逻辑
│   │   └── ImportBatch.js              # 批量导入批次记录模型
│   ├── utils/                          # 通用工具函数集
│   │   ├── urlValidator.js             # URL 格式校验、域名提取与规范化
│   │   ├── logger.js                   # 基于 winston 的日志封装
│   │   └── fileParser.js               # CSV 与纯文本文件解析辅助
│   └── views/                          # 前端模板引擎视图文件
│       ├── layouts/                    # 基础布局模板
│       └── partials/                   # 可复用的页面片段
├── tests/                              # 单元测试与集成测试套件
│   ├── unit/                           # 各服务与工具函数的单测
│   └── integration/                    # API 端到端测试与数据库操作测试
├── scripts/                            # 辅助运维脚本
│   ├── seed.js                         # 初始化示例数据
│   └── healthcheck.js                  # 服务健康状态检查脚本
├── docs/                               # 项目文档，详见上方文档导航
├── .env.example                        # 环境变量配置示例文件
├── package.json                        # npm 项目配置与依赖声明
├── README.md                           # 本文件
└── LICENSE                             # MIT 许可证全文
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库，并将 Fork 后的仓库克隆至本地开发环境。请确保本地 Node.js 版本与安装要求中的指定版本一致。

2. 创建新的功能分支，分支命名采用 `feat/` 或 `fix/` 前缀，后接简要英文描述，例如 `feat/batch-tag-update`。禁止直接在 main 分支上进行开发。

3. 编写代码时请遵循项目根目录下的 `.eslintrc` 与 `.prettierrc` 配置。所有新增或修改的 API 接口必须附带对应的单元测试，测试文件放置于 `tests/unit/` 或 `tests/integration/` 下。

4. 提交代码前运行 `npm run test` 确保全部测试用例通过，且测试覆盖率不低于现有基准线。运行 `npm run lint` 检查代码风格，所有警告必须在提交前修复。

5. 发起 Pull Request 至本仓库的 main 分支。PR 描述中请清晰说明变更目的、影响范围及是否涉及数据库迁移或配置变更。PR 需要至少一位项目维护者审核通过后方可合并。

## 常见问题

**问：导入包含大量 URL 的文件时，界面响应缓慢或出现超时怎么办？**

答：系统默认单次导入上限为 500 条，超出此数量会触发分批处理机制。如果导入文件超过 2000 条，建议使用命令行导入脚本 `scripts/bulk-import.js`，该脚本绕开 Web 请求超时限制，并支持断点续传。您也可以调整环境变量 `IMPORT_BATCH_SIZE` 的值来控制每批处理的数量。

**问：数据库文件能否迁移至 PostgreSQL 或其他关系型数据库？**

答：当前版本仅内置对 SQLite 的支持，但数据访问层已抽象为 Repository 模式。若需要迁移至 PostgreSQL，您需要自行实现 `repositories/` 下对应数据库方言的适配器，并修改 `src/main/config.js` 中的数据库连接配置。项目团队计划在后续大版本中提供官方 PostgreSQL 适配器。

**问：如何批量更新一批链接的状态或标签？**

答：在链接列表页面中，使用筛选条件定位到目标链接组，然后点击「批量操作」按钮，选择「修改状态」或「追加标签」。系统会异步执行更新任务，执行进度可在「任务中心」页面查看。若需通过 API 操作，可使用 `PATCH /api/links/batch` 端点，请求体中传入筛选条件和更新字段。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
