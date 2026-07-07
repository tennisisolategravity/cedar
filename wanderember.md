# WebMap 技术文章聚合导航

WebMap 是一个面向技术研究与数据分析人员的结构化外链资源导航系统，专注于聚合来自多个内容源的技术文章、行业报告与工程实践文档。该项目不属于传统的爬虫或采集工具，而是一套以人工筛选与源站映射为基础的资源索引框架，旨在帮助技术团队、高校研究者与独立开发者快速定位特定领域的高价值阅读材料。

项目当前覆盖移动端开发、后端架构、数据可视化、运维监控、算法工程等五大技术方向，通过对原始内容源（mobile.xqnqq.com 与 read.usuhx.com）的深度链接映射，构建出一套可维护、可扩展的参考信息库。WebMap 不存储任何第三方内容，仅提供标准化的 URL 导航与分类建议，适用于搭建内部技术周报、研究文献库或知识库外部参考索引。

## 功能概览

**结构化链接索引**：基于文章 ID 与源站特征自动生成分类标签，支持按主题快速筛选。

**多维度检索过滤**：提供按源站、预估发布时间、内容类型（教程/案例/规范/工具评测）的过滤视图。

**只读镜像访问模式**：所有外链均以原始 URL 直出，不经过中间跳转或参数重写，保证来源可追溯。

**阅读状态标记**：支持本地或后端记录已读/未读状态，便于团队协作跟踪。

**RSS 生成接口**：基于链接列表自动生成 RSS 订阅源，适配主流阅读器。

**批量导入与导出**：支持 CSV 与 JSON 格式的链接清单导入导出，便于与其他知识管理工具集成。

**去重与失效检测**：内置基于 URL 哈希的重复检测机制，并提供基础性 HTTP 状态检查（可选）。

**自定义分类树**：用户可根据项目需要创建二级分类体系，将原始链接映射至自建目录。

## 应用场景

技术团队内部周报素材库：团队技术负责人可每周从 WebMap 的索引中抽取 5-8 篇与当前项目相关的文章，作为周报的推荐阅读部分，减少成员在信息检索上的重复劳动。

高校课题文献参考导航：研究生或课题组在开展系统设计、性能评估等研究时，可将 WebMap 作为外部参考文献的入口，快速回溯来自不同源站的技术论述。

个人开发者知识积累工具：独立开发者可使用 WebMap 维护个人阅读清单，按技术栈分类存储感兴趣的深度文章，配合阅读状态标记形成长期学习路径。

技术社区内容聚合展示：中小型技术社区或爱好者站点可基于 WebMap 的链接数据构建“每日热文”或“本周精选”板块，无需自建爬虫体系。

## 快速开始

以下指令适用于 Linux/macOS 环境，Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/webmap-org/webmap-index.git
cd webmap-index

# 安装依赖（Node.js 18+ 环境）
npm install

# 启动开发服务器（默认监听 3000 端口）
npm run dev
```

启动成功后，访问控制台输出的本地地址即可浏览当前索引库。生产环境部署请参考 `docs/deploy.md` 中的 Nginx 或 Caddy 配置示例。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或 20.x LTS | 运行时环境，推荐使用 nvm 管理版本 |
| npm | 9.x 及以上 | 包管理器，随 Node.js 一同安装 |
| SQLite | 3.35.0 及以上 | 内置链接索引存储，无需额外配置 |
| Git | 2.30.0 及以上 | 用于克隆仓库及版本管理 |
| 内存 | 最低 512 MB | 开发环境建议 1 GB 以上 |
| 磁盘空间 | 200 MB | 不含 node_modules 缓存 |
| 操作系统 | Linux / macOS / Windows (WSL) | 生产环境推荐 Debian 11 或 Ubuntu 22.04 |
| 网络 | 可访问公网 | 用于获取原始文章内容（非必须，离线模式亦可浏览索引） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | `docs/quick-start.md` | 如何在 5 分钟内完成本地部署并浏览第一条链接？ |
| 索引维护 | `docs/maintenance.md` | 如何新增、更新或移除链接条目？分类标签如何定义？ |
| 数据格式 | `docs/data-schema.md` | 索引库的 JSON 结构、字段含义与扩展方法是什么？ |
| 部署运营 | `docs/deployment.md` | 如何将 WebMap 部署至生产服务器，并配置自动更新？ |
| 进阶定制 | `docs/customization.md` | 如何修改前端 UI、添加自定义分类或接入外部 API？ |
| 性能调优 | `docs/performance.md` | 当链接数量超过 5000 条时，如何优化查询响应速度？ |
| 故障排查 | `docs/troubleshooting.md` | 常见启动错误、SQLite 锁问题及网络超时如何解决？ |

## 资源列表

- http://map.mobile.xqnqq.com/Article/612316.shtml
- http://map.read.usuhx.com/Article/1042.shtml
- http://map.mobile.xqnqq.com/Article/009607.shtml
- http://map.mobile.xqnqq.com/Article/492706.shtml
- http://map.mobile.xqnqq.com/Article/5221110.shtml
- http://map.read.usuhx.com/Article/2423.shtml
- http://map.read.usuhx.com/Article/1355319.shtml
- http://map.mobile.xqnqq.com/Article/4655853.shtml
- http://map.read.usuhx.com/Article/99068.shtml
- http://map.mobile.xqnqq.com/Article/428466.shtml
- http://map.read.usuhx.com/Article/96651.shtml
- http://map.read.usuhx.com/Article/9820.shtml
- http://map.read.usuhx.com/Article/189115.shtml
- http://map.read.usuhx.com/Article/57316.shtml
- http://map.read.usuhx.com/Article/17686.shtml
- http://map.mobile.xqnqq.com/Article/685380.shtml
- http://map.mobile.xqnqq.com/Article/31685.shtml
- http://map.read.usuhx.com/Article/41356.shtml
- http://map.read.usuhx.com/Article/1968.shtml
- http://map.read.usuhx.com/Article/5027534.shtml
- http://map.mobile.xqnqq.com/Article/6561.shtml
- http://map.mobile.xqnqq.com/Article/1128.shtml
- http://map.mobile.xqnqq.com/Article/6952.shtml
- http://map.read.usuhx.com/Article/57275.shtml
- http://map.read.usuhx.com/Article/03737.shtml
- http://map.read.usuhx.com/Article/63504.shtml
- http://map.mobile.xqnqq.com/Article/7610.shtml
- http://map.read.usuhx.com/Article/925682.shtml
- http://map.mobile.xqnqq.com/Article/085705.shtml
- http://map.mobile.xqnqq.com/Article/0336.shtml
- http://map.mobile.xqnqq.com/Article/4591198.shtml
- http://map.mobile.xqnqq.com/Article/4008089.shtml
- http://map.mobile.xqnqq.com/Article/42211.shtml
- http://map.mobile.xqnqq.com/Article/0205298.shtml
- http://map.read.usuhx.com/Article/93614.shtml
- http://map.read.usuhx.com/Article/335995.shtml
- http://map.mobile.xqnqq.com/Article/974982.shtml
- http://map.mobile.xqnqq.com/Article/1461.shtml
- http://map.mobile.xqnqq.com/Article/297703.shtml
- http://map.read.usuhx.com/Article/4258354.shtml
- http://map.mobile.xqnqq.com/Article/8026.shtml
- http://map.read.usuhx.com/Article/889035.shtml
- http://map.mobile.xqnqq.com/Article/8885.shtml
- http://map.mobile.xqnqq.com/Article/408271.shtml
- http://map.mobile.xqnqq.com/Article/345133.shtml
- http://map.mobile.xqnqq.com/Article/618729.shtml
- http://map.mobile.xqnqq.com/Article/92841.shtml
- http://map.mobile.xqnqq.com/Article/7354069.shtml
- http://map.mobile.xqnqq.com/Article/6995.shtml
- http://map.read.usuhx.com/Article/8138.shtml
- http://map.mobile.xqnqq.com/Article/3206.shtml
- http://map.mobile.xqnqq.com/Article/184962.shtml
- http://map.read.usuhx.com/Article/242876.shtml
- http://map.read.usuhx.com/Article/55853.shtml
- http://map.mobile.xqnqq.com/Article/8325796.shtml
- http://map.mobile.xqnqq.com/Article/881621.shtml
- http://map.read.usuhx.com/Article/9320194.shtml
- http://map.read.usuhx.com/Article/7993.shtml
- http://map.mobile.xqnqq.com/Article/6433.shtml
- http://map.read.usuhx.com/Article/20052.shtml
- http://map.mobile.xqnqq.com/Article/2483551.shtml
- http://map.mobile.xqnqq.com/Article/53118.shtml
- http://map.read.usuhx.com/Article/49781.shtml
- http://map.mobile.xqnqq.com/Article/6276.shtml
- http://map.mobile.xqnqq.com/Article/384608.shtml
- http://map.mobile.xqnqq.com/Article/9137729.shtml
- http://map.read.usuhx.com/Article/33936.shtml
- http://map.mobile.xqnqq.com/Article/7940.shtml
- http://map.read.usuhx.com/Article/4226999.shtml
- http://map.mobile.xqnqq.com/Article/048040.shtml
- http://map.mobile.xqnqq.com/Article/572918.shtml
- http://map.read.usuhx.com/Article/28060.shtml
- http://map.read.usuhx.com/Article/586517.shtml
- http://map.mobile.xqnqq.com/Article/2068684.shtml
- http://map.read.usuhx.com/Article/9226665.shtml
- http://map.mobile.xqnqq.com/Article/70694.shtml
- http://map.mobile.xqnqq.com/Article/3873951.shtml
- http://map.mobile.xqnqq.com/Article/327122.shtml
- http://map.mobile.xqnqq.com/Article/6760514.shtml
- http://map.read.usuhx.com/Article/1956.shtml
- http://map.mobile.xqnqq.com/Article/5427.shtml
- http://map.read.usuhx.com/Article/537028.shtml
- http://map.read.usuhx.com/Article/0049.shtml
- http://map.mobile.xqnqq.com/Article/0820962.shtml
- http://map.read.usuhx.com/Article/3555.shtml
- http://map.mobile.xqnqq.com/Article/39612.shtml
- http://map.mobile.xqnqq.com/Article/73959.shtml
- http://map.read.usuhx.com/Article/479788.shtml
- http://map.mobile.xqnqq.com/Article/56437.shtml
- http://map.mobile.xqnqq.com/Article/0905081.shtml
- http://map.read.usuhx.com/Article/84141.shtml
- http://map.mobile.xqnqq.com/Article/04732.shtml
- http://map.read.usuhx.com/Article/6901155.shtml
- http://map.mobile.xqnqq.com/Article/963052.shtml
- http://map.read.usuhx.com/Article/460399.shtml
- http://map.read.usuhx.com/Article/0637.shtml
- http://map.mobile.xqnqq.com/Article/878140.shtml
- http://map.read.usuhx.com/Article/7462197.shtml
- http://map.mobile.xqnqq.com/Article/32493.shtml
- http://map.mobile.xqnqq.com/Article/7808.shtml
- http://map.read.usuhx.com/Article/751227.shtml
- http://map.read.usuhx.com/Article/47950.shtml
- http://map.read.usuhx.com/Article/4293391.shtml
- http://map.mobile.xqnqq.com/Article/13662.shtml
- http://map.read.usuhx.com/Article/748679.shtml
- http://map.mobile.xqnqq.com/Article/4835530.shtml
- http://map.mobile.xqnqq.com/Article/166743.shtml
- http://map.mobile.xqnqq.com/Article/6761792.shtml
- http://map.read.usuhx.com/Article/4337.shtml
- http://map.read.usuhx.com/Article/154559.shtml
- http://map.mobile.xqnqq.com/Article/490288.shtml
- http://map.read.usuhx.com/Article/1960.shtml
- http://map.read.usuhx.com/Article/75603.shtml
- http://map.mobile.xqnqq.com/Article/8588613.shtml
- http://map.mobile.xqnqq.com/Article/9352.shtml
- http://map.read.usuhx.com/Article/7792882.shtml
- http://map.read.usuhx.com/Article/7360305.shtml
- http://map.read.usuhx.com/Article/5980.shtml
- http://map.mobile.xqnqq.com/Article/8165.shtml
- http://map.read.usuhx.com/Article/920681.shtml
- http://map.read.usuhx.com/Article/785371.shtml
- http://map.read.usuhx.com/Article/311054.shtml
- http://map.mobile.xqnqq.com/Article/5872542.shtml
- http://map.read.usuhx.com/Article/9955.shtml
- http://map.mobile.xqnqq.com/Article/1620.shtml
- http://map.mobile.xqnqq.com/Article/506024.shtml
- http://map.read.usuhx.com/Article/68434.shtml
- http://map.read.usuhx.com/Article/948368.shtml
- http://map.read.usuhx.com/Article/6100548.shtml
- http://map.read.usuhx.com/Article/094521.shtml
- http://map.mobile.xqnqq.com/Article/3041971.shtml
- http://map.mobile.xqnqq.com/Article/2965.shtml
- http://map.read.usuhx.com/Article/7561376.shtml
- http://map.mobile.xqnqq.com/Article/000801.shtml
- http://map.read.usuhx.com/Article/658741.shtml
- http://map.read.usuhx.com/Article/46464.shtml
- http://map.read.usuhx.com/Article/1830.shtml
- http://map.read.usuhx.com/Article/8565285.shtml
- http://map.mobile.xqnqq.com/Article/109308.shtml
- http://map.read.usuhx.com/Article/967569.shtml
- http://map.read.usuhx.com/Article/17794.shtml
- http://map.read.usuhx.com/Article/0956.shtml
- http://map.mobile.xqnqq.com/Article/25685.shtml
- http://map.mobile.xqnqq.com/Article/6005.shtml
- http://map.read.usuhx.com/Article/09024.shtml
- http://map.read.usuhx.com/Article/9173.shtml
- http://map.mobile.xqnqq.com/Article/8429.shtml
- http://map.read.usuhx.com/Article/6524.shtml
- http://map.mobile.xqnqq.com/Article/187759.shtml
- http://map.mobile.xqnqq.com/Article/4915.shtml
- http://map.mobile.xqnqq.com/Article/9374799.shtml
- http://map.read.usuhx.com/Article/7004.shtml
- http://map.mobile.xqnqq.com/Article/562386.shtml
- http://map.read.usuhx.com/Article/6709175.shtml
- http://map.mobile.xqnqq.com/Article/77187.shtml
- http://map.mobile.xqnqq.com/Article/4652.shtml
- http://map.read.usuhx.com/Article/37283.shtml
- http://map.read.usuhx.com/Article/6413637.shtml
- http://map.mobile.xqnqq.com/Article/991633.shtml
- http://map.mobile.xqnqq.com/Article/851641.shtml
- http://map.read.usuhx.com/Article/7875.shtml
- http://map.read.usuhx.com/Article/733072.shtml
- http://map.read.usuhx.com/Article/00764.shtml
- http://map.mobile.xqnqq.com/Article/1501.shtml
- http://map.read.usuhx.com/Article/1190.shtml
- http://map.read.usuhx.com/Article/4008.shtml
- http://map.mobile.xqnqq.com/Article/71225.shtml
- http://map.read.usuhx.com/Article/477762.shtml
- http://map.mobile.xqnqq.com/Article/83077.shtml
- http://map.read.usuhx.com/Article/0085638.shtml
- http://map.mobile.xqnqq.com/Article/66558.shtml
- http://map.mobile.xqnqq.com/Article/5196.shtml
- http://map.mobile.xqnqq.com/Article/5433.shtml
- http://map.read.usuhx.com/Article/91357.shtml
- http://map.mobile.xqnqq.com/Article/13428.shtml
- http://map.read.usuhx.com/Article/2463.shtml
- http://map.mobile.xqnqq.com/Article/616093.shtml
- http://map.read.usuhx.com/Article/7857902.shtml
- http://map.mobile.xqnqq.com/Article/49226.shtml
- http://map.mobile.xqnqq.com/Article/11941.shtml
- http://map.mobile.xqnqq.com/Article/015575.shtml
- http://map.read.usuhx.com/Article/7367060.shtml
- http://map.read.usuhx.com/Article/0490304.shtml
- http://map.read.usuhx.com/Article/2251485.shtml
- http://map.read.usuhx.com/Article/698792.shtml
- http://map.read.usuhx.com/Article/1548.shtml
- http://map.mobile.xqnqq.com/Article/3577228.shtml
- http://map.mobile.xqnqq.com/Article/60595.shtml
- http://map.read.usuhx.com/Article/5740.shtml
- http://map.mobile.xqnqq.com/Article/5014.shtml
- http://map.read.usuhx.com/Article/32104.shtml
- http://map.mobile.xqnqq.com/Article/2376680.shtml
- http://map.read.usuhx.com/Article/6009.shtml
- http://map.read.usuhx.com/Article/22043.shtml
- http://map.mobile.xqnqq.com/Article/672455.shtml
- http://map.read.usuhx.com/Article/6440381.shtml
- http://map.read.usuhx.com/Article/4461436.shtml
- http://map.read.usuhx.com/Article/66736.shtml
- http://map.read.usuhx.com/Article/8108949.shtml
- http://map.read.usuhx.com/Article/767506.shtml
- http://map.mobile.xqnqq.com/Article/4057505.shtml
- http://map.mobile.xqnqq.com/Article/385807.shtml
- http://map.read.usuhx.com/Article/512372.shtml
- http://map.mobile.xqnqq.com/Article/2382.shtml
- http://map.mobile.xqnqq.com/Article/10138.shtml
- http://map.mobile.xqnqq.com/Article/52448.shtml
- http://map.mobile.xqnqq.com/Article/72920.shtml
- http://map.mobile.xqnqq.com/Article/1531740.shtml
- http://map.mobile.xqnqq.com/Article/85672.shtml
- http://map.read.usuhx.com/Article/90852.shtml
- http://map.mobile.xqnqq.com/Article/510545.shtml
- http://map.mobile.xqnqq.com/Article/7329.shtml
- http://map.read.usuhx.com/Article/7441330.shtml
- http://map.mobile.xqnqq.com/Article/9483.shtml
- http://map.read.usuhx.com/Article/0087301.shtml
- http://map.mobile.xqnqq.com/Article/76526.shtml
- http://map.mobile.xqnqq.com/Article/89665.shtml
- http://map.read.usuhx.com/Article/3029709.shtml
- http://map.read.usuhx.com/Article/0949683.shtml
- http://map.read.usuhx.com/Article/337635.shtml
- http://map.mobile.xqnqq.com/Article/10133.shtml
- http://map.read.usuhx.com/Article/0102.shtml
- http://map.read.usuhx.com/Article/1563.shtml
- http://map.mobile.xqnqq.com/Article/2438.shtml
- http://map.mobile.xqnqq.com/Article/1197394.shtml
- http://map.mobile.xqnqq.com/Article/4652070.shtml
- http://map.read.usuhx.com/Article/556939.shtml
- http://map.mobile.xqnqq.com/Article/3218782.shtml
- http://map.mobile.xqnqq.com/Article/3477.shtml
- http://map.read.usuhx.com/Article/343793.shtml
- http://map.read.usuhx.com/Article/4432588.shtml
- http://map.read.usuhx.com/Article/0803.shtml
- http://map.mobile.xqnqq.com/Article/231377.shtml
- http://map.read.usuhx.com/Article/86276.shtml
- http://map.read.usuhx.com/Article/1243483.shtml
- http://map.mobile.xqnqq.com/Article/007372.shtml
- http://map.mobile.xqnqq.com/Article/88509.shtml
- http://map.mobile.xqnqq.com/Article/6401578.shtml
- http://map.read.usuhx.com/Article/237031.shtml
- http://map.read.usuhx.com/Article/960068.shtml
- http://map.mobile.xqnqq.com/Article/8881229.shtml
- http://map.mobile.xqnqq.com/Article/282163.shtml
- http://map.read.usuhx.com/Article/2934155.shtml
- http://map.read.usuhx.com/Article/369334.shtml
- http://map.mobile.xqnqq.com/Article/0277337.shtml
- http://map.mobile.xqnqq.com/Article/7929148.shtml
- http://map.mobile.xqnqq.com/Article/77485.shtml
- http://map.mobile.xqnqq.com/Article/3706006.shtml
- http://map.read.usuhx.com/Article/6975.shtml
- http://map.read.usuhx.com/Article/9490222.shtml

## 项目结构

```
webmap-index/
├── src/                                # 核心源代码目录
│   ├── core/                           # 索引引擎与数据访问层
│   │   ├── loader.ts                   # 外部链接批量加载器，支持分批次导入
│   │   ├── resolver.ts                 # URL 解析与规范化工具（保留原始协议）
│   │   └── cache.ts                    # SQLite 查询缓存与连接池管理
│   ├── routes/                         # HTTP 路由定义
│   │   ├── index.ts                    # 首页与分类视图路由
│   │   ├── api.ts                      # RESTful API 端点（列表/详情/状态）
│   │   └── feed.ts                     # RSS 生成与输出格式适配
│   ├── ui/                             # 前端界面组件
│   │   ├── layouts/                    # 页面布局模板
│   │   ├── components/                 # 可复用 UI 组件（筛选器/分页/标签）
│   │   └── static/                     # CSS 样式与前端静态资源
│   └── utils/                          # 通用辅助函数
│       ├── validator.ts                # 链接格式与来源白名单校验
│       └── logger.ts                   # 结构化日志输出（JSON 格式）
├── data/                               # 数据存储目录
│   ├── index.db                        # SQLite 主数据库文件
│   └── seeds/                          # 批次导入种子数据（JSON）
├── docs/                               # 完整项目文档
│   ├── quick-start.md                  # 5 分钟快速上手指南
│   ├── maintenance.md                  # 索引库日常维护流程
│   ├── data-schema.md                  # 数据库表结构与字段说明
│   ├── deployment.md                   # 生产环境部署与反向代理配置
│   ├── customization.md                # UI 定制与分类扩展方法
│   ├── performance.md                  # 性能优化与压测建议
│   └── troubleshooting.md              # 常见故障排查步骤
├── tests/                              # 单元测试与集成测试
│   ├── unit/                           # 针对 loader/resolver 的独立测试
│   └── integration/                    # API 端点与数据库交互测试
├── scripts/                            # 运维与辅助脚本
│   ├── import-batch.js                 # 手动导入新批次链接的命令行工具
│   ├── health-check.js                 # 批量检查外链可用性的脚本
│   └── backup-db.sh                    # 数据库自动备份脚本（cron 适配）
├── config/                             # 环境配置文件
│   ├── default.json                    # 默认端口、分页大小、超时配置
│   └── production.json                 # 生产环境覆盖配置（只读模式）
├── .github/                            # GitHub 社区规范
│   ├── ISSUE_TEMPLATE/                 # 问题反馈与建议模板
│   └── workflows/                      # CI 测试与自动部署工作流
├── package.json                        # npm 项目清单与脚本定义
├── tsconfig.json                       # TypeScript 编译配置
└── README.md                           # 本文件
```

## 贡献指南

我们欢迎任何形式的贡献，包括但不限于新增链接源站、改进分类体系、优化前端交互、修复文档错漏。请遵循以下步骤参与协作。

第一步：查阅现有 Issue 与项目看板，确认待处理任务或提出新议题。建议先通过 Issue 与维护者沟通改动方向，避免重复工作。

第二步：Fork 本仓库至个人账号，并在本地创建功能分支（如 `feat/add-new-source` 或 `fix/loader-timeout`）。分支命名应体现改动类型与简要内容。

第三步：完成代码或文档修改后，确保通过全部单元测试（`npm run test`）并保持代码风格一致（`npm run lint`）。新增功能需附带对应测试用例。

第四步：提交 Pull Request 至主仓库的 `main` 分支，PR 描述中需明确关联 Issue 编号、改动范围、测试结果及可能的兼容性影响。

第五步：维护者将在 3 个工作日内进行 Code Review，必要时会提出修改意见。合并后您的贡献将自动归入下一批次发布。

## 常见问题

**问：为什么所有链接都采用 http 协议而非 https？部分浏览器可能会提示不安全，如何解决？**

答：WebMap 严格遵循原始 URL 的协议格式，不进行任何自动升级或降级，以保证来源的绝对可追溯性。若部分链接支持 HTTPS，用户可在浏览器中手动将协议替换为 https 访问。项目本身不代理或改写外部资源，因此浏览器的不安全提示来自第三方源站，与 WebMap 无关。建议用户在内部网络或受信任环境中使用，或将相关域名加入浏览器的安全例外列表。

**问：链接数量增长后，前端加载和筛选会不会变慢？有什么优化建议？**

答：WebMap 在数据层采用 SQLite 索引与分页查询机制，默认每页只返回 50 条记录，不会一次性加载全部链接。前端筛选操作均转换为后端 SQL 条件，避免浏览器端大数组遍历。当索引量超过 1 万条时，建议在 `config/production.json` 中启用缓存头（Cache-Control）并配合 Nginx 的 gzip 压缩。对于更高并发场景，可考虑将 SQLite 替换为 PostgreSQL（项目已提供适配层，详见 `docs/deployment.md`）。

**问：我能否将 WebMap 部署到内网环境，完全不访问公网？**

答：可以。WebMap 本身不依赖任何外部 API 或 CDN 资源（前端框架已本地打包）。部署在内网时，只需确保所有原始链接在内网中可被访问即可。若内网无法访问这些外部域名，WebMap 仍可作为链接清单的浏览工具使用，只是无法通过点击跳转查看原文。所有静态资源均随项目打包，无需在线下载。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
