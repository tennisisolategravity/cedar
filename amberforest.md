# WebIndex Core

WebIndex Core 是一个面向技术研究者和信息分析人员的外链资源归集与导航工具。本项目不生产原始内容，而是通过结构化方式对分散于多个内容源站点的公开文章进行索引、分类和快速检索，解决技术资料查找过程中跨站搜索效率低、链接散落、上下文缺失等突出问题。

项目定位为轻量级外链数据库，核心目标用户包括：需要进行技术文献回顾的研发工程师、从事信息汇总的文档维护人员、以及需要快速定位特定主题文章的研究者。WebIndex Core 本身不依赖数据库或重型前端框架，以纯静态索引形态交付，可部署于任何支持 HTTPS 的 Web 服务器或对象存储服务。

## 功能概览

**多源链接归集** 系统内置两个主要内容源域名的文章映射表，支持按来源域名、文章编号进行快速筛选。

**黑名单与去重机制** 基于文章 ID 和来源 URL 的双重校验，自动过滤重复录入，避免索引膨胀。

**关键字预索引** 对每篇文章的 URL 路径中的数字标识进行分词存储，支持基于文章编号的精确查找。

**来源域名分类视图** 按 `mobile.xqnqq.com` 和 `read.usuhx.com` 两个源站分别列出所属文章清单，便于按站点追溯内容。

**批量导入接口** 提供基于纯文本列表的批量 URL 导入能力，适用于定期增量更新索引库。

**静态化输出** 所有索引数据最终生成为静态 Markdown 表格和列表，无需动态解析，开箱即用。

**自定义标签扩展** 支持为每条链接附加手工标注的分类标签（如「网络协议」「前端性能」），便于按主题聚合。

**访问状态探测** 集成简单的 HTTP 头检查逻辑，可标记响应状态异常的链接，辅助清理失效资源。

## 应用场景

**技术文献回溯** 研究人员在整理某一技术方向（例如移动端渲染优化）的历史资料时，可通过本项目的文章编号索引快速定位到 `mobile.xqnqq.com` 和 `read.usuhx.com` 下相关的单篇文章，无需手动翻阅站点归档页面。

**外链有效性审计** 文档维护人员定期运行项目内置的链接探测脚本，获取全部 250 条外链的响应码，生成失效链接报表，便于及时更新或移除已下线的引用。

**多源信息聚合展示** 团队内部知识库管理员将本项目部署为子站点，作为外部参考文章的入口聚合页，成员按域名分类浏览，减少在多个标签页间切换查找的时间。

**自动化文档生成流水线** 将本项目集成至 CI 流程中，每次代码仓库更新时自动重新生成索引列表，确保发布的静态页面始终与最新外链集合保持同步。

## 快速开始

以下操作步骤适用于 Linux 与 macOS 环境，Windows 用户建议通过 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库至本地
git clone https://github.com/webindex/core.git webindex-core
cd webindex-core

# 安装依赖（项目基于 Node.js 构建，需要 npm 环境）
npm install

# 执行索引构建脚本，生成最终的文档资源
npm run build

# 启动本地预览服务，默认监听端口 8080
npm start
```

执行完成后，可通过浏览器访问 `http://localhost:8080` 查看生成的索引页面。如需自定义端口，可修改项目根目录下的 `config.yml` 文件中的 `server.port` 字段。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 18.x 或 20.x LTS | 运行时环境，用于执行构建与预览脚本 |
| npm | 9.x 或 10.x | 包管理器，用于安装项目依赖库 |
| Git | 2.30 及以上 | 版本控制工具，用于克隆仓库和管理更新 |
| curl | 7.68 及以上 | 用于链接状态探测模块的 HTTP 请求发送 |
| 磁盘空间 | 至少 50 MB | 存放源码、索引缓存和静态输出文件 |
| 内存 | 至少 512 MB | 构建过程中用于临时存储解析后的链接数据 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | `/docs/getting-started.md` | 如何在一分钟内完成项目部署并生成首个索引页面 |
| 链接格式规范 | `/docs/link-format.md` | 索引文件中的 URL 字段应遵循怎样的编码与转义规则 |
| 构建配置参考 | `/docs/config-reference.md` | 如何修改源站点域名列表、调整输出目录和并发探测数 |
| 故障排查 | `/docs/troubleshooting.md` | 构建失败、链接探测超时或输出乱码时如何处理 |

## 资源列表

- http://www.mobile.xqnqq.com/Article/7876873.shtml
- http://www.mobile.xqnqq.com/Article/15808.shtml
- http://www.mobile.xqnqq.com/Article/58990.shtml
- http://www.mobile.xqnqq.com/Article/7249.shtml
- http://www.read.usuhx.com/Article/727828.shtml
- http://www.read.usuhx.com/Article/7721202.shtml
- http://www.mobile.xqnqq.com/Article/2116715.shtml
- http://www.mobile.xqnqq.com/Article/91333.shtml
- http://www.mobile.xqnqq.com/Article/05395.shtml
- http://www.mobile.xqnqq.com/Article/79159.shtml
- http://www.mobile.xqnqq.com/Article/3845.shtml
- http://www.read.usuhx.com/Article/67229.shtml
- http://www.mobile.xqnqq.com/Article/635958.shtml
- http://www.mobile.xqnqq.com/Article/96532.shtml
- http://www.read.usuhx.com/Article/0769.shtml
- http://www.read.usuhx.com/Article/96537.shtml
- http://www.read.usuhx.com/Article/1273619.shtml
- http://www.mobile.xqnqq.com/Article/6801.shtml
- http://www.mobile.xqnqq.com/Article/40075.shtml
- http://www.mobile.xqnqq.com/Article/10732.shtml
- http://www.read.usuhx.com/Article/13508.shtml
- http://www.read.usuhx.com/Article/991122.shtml
- http://www.read.usuhx.com/Article/837994.shtml
- http://www.read.usuhx.com/Article/4374.shtml
- http://www.mobile.xqnqq.com/Article/8506301.shtml
- http://www.read.usuhx.com/Article/77053.shtml
- http://www.mobile.xqnqq.com/Article/4872.shtml
- http://www.mobile.xqnqq.com/Article/844482.shtml
- http://www.mobile.xqnqq.com/Article/3724.shtml
- http://www.read.usuhx.com/Article/6859586.shtml
- http://www.mobile.xqnqq.com/Article/82902.shtml
- http://www.read.usuhx.com/Article/8281420.shtml
- http://www.read.usuhx.com/Article/78355.shtml
- http://www.read.usuhx.com/Article/6830974.shtml
- http://www.mobile.xqnqq.com/Article/54965.shtml
- http://www.mobile.xqnqq.com/Article/056935.shtml
- http://www.read.usuhx.com/Article/9590.shtml
- http://www.read.usuhx.com/Article/5273941.shtml
- http://www.read.usuhx.com/Article/4756802.shtml
- http://www.mobile.xqnqq.com/Article/6586207.shtml
- http://www.read.usuhx.com/Article/0928.shtml
- http://www.mobile.xqnqq.com/Article/001879.shtml
- http://www.read.usuhx.com/Article/80090.shtml
- http://www.mobile.xqnqq.com/Article/119813.shtml
- http://www.read.usuhx.com/Article/1618064.shtml
- http://www.read.usuhx.com/Article/03368.shtml
- http://www.mobile.xqnqq.com/Article/928013.shtml
- http://www.mobile.xqnqq.com/Article/2521.shtml
- http://www.mobile.xqnqq.com/Article/4492.shtml
- http://www.mobile.xqnqq.com/Article/7382121.shtml
- http://www.mobile.xqnqq.com/Article/27878.shtml
- http://www.read.usuhx.com/Article/598219.shtml
- http://www.read.usuhx.com/Article/8912.shtml
- http://www.mobile.xqnqq.com/Article/6891133.shtml
- http://www.mobile.xqnqq.com/Article/049587.shtml
- http://www.read.usuhx.com/Article/15375.shtml
- http://www.read.usuhx.com/Article/17187.shtml
- http://www.mobile.xqnqq.com/Article/2622464.shtml
- http://www.read.usuhx.com/Article/9357954.shtml
- http://www.mobile.xqnqq.com/Article/8695.shtml
- http://www.read.usuhx.com/Article/8146349.shtml
- http://www.read.usuhx.com/Article/9641.shtml
- http://www.mobile.xqnqq.com/Article/6454.shtml
- http://www.read.usuhx.com/Article/5598525.shtml
- http://www.mobile.xqnqq.com/Article/326180.shtml
- http://www.read.usuhx.com/Article/8501318.shtml
- http://www.mobile.xqnqq.com/Article/632926.shtml
- http://www.read.usuhx.com/Article/4782.shtml
- http://www.read.usuhx.com/Article/4394.shtml
- http://www.mobile.xqnqq.com/Article/9480936.shtml
- http://www.read.usuhx.com/Article/64669.shtml
- http://www.read.usuhx.com/Article/281873.shtml
- http://www.mobile.xqnqq.com/Article/22888.shtml
- http://www.mobile.xqnqq.com/Article/183953.shtml
- http://www.mobile.xqnqq.com/Article/25357.shtml
- http://www.mobile.xqnqq.com/Article/997179.shtml
- http://www.read.usuhx.com/Article/1284999.shtml
- http://www.read.usuhx.com/Article/1083587.shtml
- http://www.read.usuhx.com/Article/65971.shtml
- http://www.mobile.xqnqq.com/Article/4044.shtml
- http://www.read.usuhx.com/Article/26598.shtml
- http://www.mobile.xqnqq.com/Article/7950.shtml
- http://www.read.usuhx.com/Article/56969.shtml
- http://www.mobile.xqnqq.com/Article/22611.shtml
- http://www.read.usuhx.com/Article/94772.shtml
- http://www.read.usuhx.com/Article/4425.shtml
- http://www.mobile.xqnqq.com/Article/682839.shtml
- http://www.read.usuhx.com/Article/6083894.shtml
- http://www.read.usuhx.com/Article/6629767.shtml
- http://www.mobile.xqnqq.com/Article/4328.shtml
- http://www.mobile.xqnqq.com/Article/1059.shtml
- http://www.mobile.xqnqq.com/Article/457410.shtml
- http://www.mobile.xqnqq.com/Article/4405182.shtml
- http://www.mobile.xqnqq.com/Article/361123.shtml
- http://www.read.usuhx.com/Article/19151.shtml
- http://www.mobile.xqnqq.com/Article/455026.shtml
- http://www.mobile.xqnqq.com/Article/8855296.shtml
- http://www.read.usuhx.com/Article/6032.shtml
- http://www.mobile.xqnqq.com/Article/61197.shtml
- http://www.mobile.xqnqq.com/Article/381265.shtml
- http://www.read.usuhx.com/Article/86341.shtml
- http://www.read.usuhx.com/Article/3864.shtml
- http://www.read.usuhx.com/Article/450530.shtml
- http://www.read.usuhx.com/Article/049774.shtml
- http://www.read.usuhx.com/Article/07823.shtml
- http://www.read.usuhx.com/Article/5378882.shtml
- http://www.mobile.xqnqq.com/Article/481921.shtml
- http://www.read.usuhx.com/Article/664771.shtml
- http://www.mobile.xqnqq.com/Article/1836543.shtml
- http://www.read.usuhx.com/Article/944083.shtml
- http://www.mobile.xqnqq.com/Article/1980.shtml
- http://www.mobile.xqnqq.com/Article/1222.shtml
- http://www.read.usuhx.com/Article/0206.shtml
- http://www.read.usuhx.com/Article/4893.shtml
- http://www.read.usuhx.com/Article/916448.shtml
- http://www.read.usuhx.com/Article/463517.shtml
- http://www.mobile.xqnqq.com/Article/5023.shtml
- http://www.read.usuhx.com/Article/35392.shtml
- http://www.read.usuhx.com/Article/14117.shtml
- http://www.mobile.xqnqq.com/Article/656050.shtml
- http://www.mobile.xqnqq.com/Article/17701.shtml
- http://www.mobile.xqnqq.com/Article/404864.shtml
- http://www.read.usuhx.com/Article/8227.shtml
- http://www.mobile.xqnqq.com/Article/26018.shtml
- http://www.mobile.xqnqq.com/Article/22490.shtml
- http://www.read.usuhx.com/Article/9518561.shtml
- http://www.mobile.xqnqq.com/Article/46258.shtml
- http://www.mobile.xqnqq.com/Article/9469.shtml
- http://www.mobile.xqnqq.com/Article/93399.shtml
- http://www.read.usuhx.com/Article/494681.shtml
- http://www.mobile.xqnqq.com/Article/74924.shtml
- http://www.read.usuhx.com/Article/678355.shtml
- http://www.read.usuhx.com/Article/9031.shtml
- http://www.mobile.xqnqq.com/Article/298975.shtml
- http://www.read.usuhx.com/Article/993304.shtml
- http://www.mobile.xqnqq.com/Article/721682.shtml
- http://www.read.usuhx.com/Article/92164.shtml
- http://www.read.usuhx.com/Article/0304595.shtml
- http://www.mobile.xqnqq.com/Article/40327.shtml
- http://www.read.usuhx.com/Article/616790.shtml
- http://www.mobile.xqnqq.com/Article/764456.shtml
- http://www.mobile.xqnqq.com/Article/9240.shtml
- http://www.read.usuhx.com/Article/1482029.shtml
- http://www.mobile.xqnqq.com/Article/9891.shtml
- http://www.read.usuhx.com/Article/509799.shtml
- http://www.read.usuhx.com/Article/788564.shtml
- http://www.mobile.xqnqq.com/Article/6245.shtml
- http://www.mobile.xqnqq.com/Article/1461116.shtml
- http://www.read.usuhx.com/Article/782023.shtml
- http://www.mobile.xqnqq.com/Article/18683.shtml
- http://www.read.usuhx.com/Article/5043.shtml
- http://www.mobile.xqnqq.com/Article/6857658.shtml
- http://www.read.usuhx.com/Article/1613.shtml
- http://www.mobile.xqnqq.com/Article/7777755.shtml
- http://www.read.usuhx.com/Article/1945590.shtml
- http://www.read.usuhx.com/Article/1409.shtml
- http://www.read.usuhx.com/Article/6180.shtml
- http://www.read.usuhx.com/Article/452085.shtml
- http://www.mobile.xqnqq.com/Article/7662893.shtml
- http://www.read.usuhx.com/Article/755408.shtml
- http://www.mobile.xqnqq.com/Article/8935441.shtml
- http://www.mobile.xqnqq.com/Article/4050586.shtml
- http://www.read.usuhx.com/Article/13572.shtml
- http://www.mobile.xqnqq.com/Article/6249720.shtml
- http://www.mobile.xqnqq.com/Article/56697.shtml
- http://www.read.usuhx.com/Article/4216133.shtml
- http://www.mobile.xqnqq.com/Article/4454.shtml
- http://www.mobile.xqnqq.com/Article/4997953.shtml
- http://www.read.usuhx.com/Article/37871.shtml
- http://www.mobile.xqnqq.com/Article/084525.shtml
- http://www.mobile.xqnqq.com/Article/47571.shtml
- http://www.read.usuhx.com/Article/73790.shtml
- http://www.mobile.xqnqq.com/Article/65742.shtml
- http://www.mobile.xqnqq.com/Article/4761.shtml
- http://www.read.usuhx.com/Article/135298.shtml
- http://www.mobile.xqnqq.com/Article/55015.shtml
- http://www.read.usuhx.com/Article/42895.shtml
- http://www.read.usuhx.com/Article/3221.shtml
- http://www.read.usuhx.com/Article/5266660.shtml
- http://www.mobile.xqnqq.com/Article/495419.shtml
- http://www.mobile.xqnqq.com/Article/3611.shtml
- http://www.read.usuhx.com/Article/9687.shtml
- http://www.read.usuhx.com/Article/7882104.shtml
- http://www.mobile.xqnqq.com/Article/8577607.shtml
- http://www.read.usuhx.com/Article/9877.shtml
- http://www.mobile.xqnqq.com/Article/81533.shtml
- http://www.mobile.xqnqq.com/Article/9002534.shtml
- http://www.read.usuhx.com/Article/3891.shtml
- http://www.mobile.xqnqq.com/Article/470870.shtml
- http://www.mobile.xqnqq.com/Article/3232138.shtml
- http://www.mobile.xqnqq.com/Article/693791.shtml
- http://www.mobile.xqnqq.com/Article/421180.shtml
- http://www.mobile.xqnqq.com/Article/165473.shtml
- http://www.read.usuhx.com/Article/1381786.shtml
- http://www.mobile.xqnqq.com/Article/4639.shtml
- http://www.mobile.xqnqq.com/Article/9397.shtml
- http://www.mobile.xqnqq.com/Article/09579.shtml
- http://www.read.usuhx.com/Article/2593.shtml
- http://www.mobile.xqnqq.com/Article/3769.shtml
- http://www.read.usuhx.com/Article/0727.shtml
- http://www.read.usuhx.com/Article/5795587.shtml
- http://www.mobile.xqnqq.com/Article/624764.shtml
- http://www.read.usuhx.com/Article/5389.shtml
- http://www.read.usuhx.com/Article/1967764.shtml
- http://www.mobile.xqnqq.com/Article/383045.shtml
- http://www.mobile.xqnqq.com/Article/8569.shtml
- http://www.mobile.xqnqq.com/Article/8528275.shtml
- http://www.mobile.xqnqq.com/Article/6644039.shtml
- http://www.mobile.xqnqq.com/Article/528662.shtml
- http://www.read.usuhx.com/Article/939138.shtml
- http://www.read.usuhx.com/Article/4007.shtml
- http://www.mobile.xqnqq.com/Article/73227.shtml
- http://www.read.usuhx.com/Article/69945.shtml
- http://www.mobile.xqnqq.com/Article/1124906.shtml
- http://www.read.usuhx.com/Article/338776.shtml
- http://www.mobile.xqnqq.com/Article/94232.shtml
- http://www.mobile.xqnqq.com/Article/8360093.shtml
- http://www.mobile.xqnqq.com/Article/1671602.shtml
- http://www.mobile.xqnqq.com/Article/921795.shtml
- http://www.mobile.xqnqq.com/Article/438431.shtml
- http://www.mobile.xqnqq.com/Article/81651.shtml
- http://www.read.usuhx.com/Article/4820071.shtml
- http://www.mobile.xqnqq.com/Article/823906.shtml
- http://www.read.usuhx.com/Article/51382.shtml
- http://www.read.usuhx.com/Article/279526.shtml
- http://www.mobile.xqnqq.com/Article/7091206.shtml
- http://www.mobile.xqnqq.com/Article/531407.shtml
- http://www.mobile.xqnqq.com/Article/73402.shtml
- http://www.mobile.xqnqq.com/Article/5296427.shtml
- http://www.mobile.xqnqq.com/Article/32553.shtml
- http://www.mobile.xqnqq.com/Article/0825.shtml
- http://www.mobile.xqnqq.com/Article/961135.shtml
- http://www.read.usuhx.com/Article/276564.shtml
- http://www.mobile.xqnqq.com/Article/72881.shtml
- http://www.mobile.xqnqq.com/Article/89432.shtml
- http://www.read.usuhx.com/Article/0618754.shtml
- http://www.read.usuhx.com/Article/6323536.shtml
- http://www.read.usuhx.com/Article/254538.shtml
- http://www.mobile.xqnqq.com/Article/147234.shtml
- http://www.read.usuhx.com/Article/9965.shtml
- http://www.read.usuhx.com/Article/1682.shtml
- http://www.mobile.xqnqq.com/Article/7374571.shtml
- http://www.read.usuhx.com/Article/03106.shtml
- http://www.read.usuhx.com/Article/52365.shtml
- http://www.read.usuhx.com/Article/90031.shtml
- http://www.read.usuhx.com/Article/7503226.shtml
- http://www.mobile.xqnqq.com/Article/05079.shtml
- http://www.read.usuhx.com/Article/16997.shtml
- http://www.mobile.xqnqq.com/Article/779031.shtml
- http://www.mobile.xqnqq.com/Article/2325328.shtml

## 项目结构

```
webindex-core/
├── src/                                # 核心源码目录
│   ├── collectors/                     # 链接采集器模块
│   │   ├── fetcher.js                  # 基于 curl 的 HTTP 请求封装
│   │   └── parser.js                   # 响应内容解析与链接提取
│   ├── indexer/                        # 索引构建模块
│   │   ├── builder.js                  # 主索引构建流程控制
│   │   └── dedup.js                    # 基于 URL 和 ID 的去重算法
│   ├── output/                         # 输出渲染模块
│   │   ├── markdown.js                 # 将索引数据渲染为 Markdown 表格
│   │   └── static.js                   # 生成最终的静态 HTML 包装页
│   └── utils/                          # 通用工具函数
│       ├── validator.js                # URL 格式校验与规范化
│       └── logger.js                   # 带时间戳的日志输出工具
├── config/                             # 配置目录
│   ├── default.yml                     # 默认配置（源域名、并发数、超时）
│   └── custom.yml.example              # 自定义配置模板
├── data/                               # 数据存储目录
│   ├── raw/                            # 原始链接列表缓存（按批次存放）
│   │   └── batch_10.txt                # 第 10/80 批原始链接清单
│   └── index/                          # 构建生成的索引快照
│       └── snapshot_20260708.json      # 当前索引全量数据
├── docs/                               # 项目文档
│   ├── getting-started.md              # 入门指南
│   ├── link-format.md                  # 链接格式规范
│   ├── config-reference.md             # 配置参数参考
│   └── troubleshooting.md              # 故障排查手册
├── scripts/                            # 辅助运维脚本
│   ├── probe.sh                        # 批量探测链接可用性的 Shell 脚本
│   └── import.sh                       # 从文本文件导入新链接的批处理脚本
├── test/                               # 单元测试与集成测试
│   ├── unit/                           # 单元测试用例
│   └── integration/                    # 端到端构建测试
├── .github/                            # GitHub 社区文件
│   └── workflows/                      # CI 流水线定义
│       └── build.yml                   # 每次推送时自动执行构建验证
├── .gitignore                          # Git 忽略规则
├── package.json                        # Node.js 项目清单与依赖声明
├── package-lock.json                   # 依赖版本锁定文件
└── README.md                           # 项目说明文档（本文件）
```

## 贡献指南

1. 克隆项目仓库并在本地执行 `npm install` 安装所有开发依赖，确保 Node.js 版本符合要求。

2. 在 `data/raw/` 目录下新建或编辑批次文件（格式为每行一个完整 URL），遵循既有的命名规范（如 `batch_11.txt`）。

3. 运行 `npm run build` 验证索引构建流程是否正常通过，确保新增链接未引入格式错误或重复项。

4. 编写或更新对应的单元测试文件（位于 `test/unit/` 目录下），覆盖率不应低于 80%。

5. 提交 Pull Request 至主仓库的 `develop` 分支，并在 PR 描述中明确说明本次变更的批次编号、新增链接数量以及构建结果截图。

## 常见问题

**问：构建过程中出现「链接探测超时」错误，如何解决？**

答：该错误通常由网络环境不稳定或目标服务器响应缓慢导致。可在 `config/default.yml` 中调整 `probe.timeout` 参数（单位毫秒），默认值为 5000，可适当增加至 10000。同时检查本地网络出口是否对目标域名有访问限制。

**问：索引文件中出现重复链接，但 `dedup.js` 去重机制未生效？**

答：请确认重复链接的字符串完全一致，包括协议、大小写和末尾斜杠。当前去重基于精确字符串匹配。若链接包含查询参数或锚点，建议在导入前统一使用 `validator.js` 中的 `normalizeUrl` 函数进行标准化处理。

**问：项目是否支持 Windows 环境下的原生运行？**

答：核心构建逻辑基于 Node.js 实现，可在 Windows 下运行。但 `scripts/probe.sh` 探测脚本依赖 Bash 环境，建议在 Windows 上使用 Git Bash 或 WSL 执行完整的构建与探测流程。若仅需生成索引，可直接运行 `npm run build`，该命令不依赖 Shell 脚本。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
