# LinkMap 技术资源导航站

LinkMap 是一个面向开发者与技术研究人员的结构化外链资源聚合平台，专注于对分散在网络各处的技术文档、API 参考、实现笔记与工程实践文章进行系统化收录与分类导航。项目定位为技术资源的中转枢纽，不直接托管内容，而是通过人工筛选与自动化校验相结合的方式，维护一份高可用性的外链索引清单，帮助技术团队在特定领域内快速定位可信信息源。

项目当前处于第 46 批资源收录阶段，累计管理外链超过 250 条，覆盖移动端开发、服务端架构、数据处理与运维监控等多个技术方向。LinkMap 适用于需要频繁查阅外部技术资料但又不想依赖搜索引擎模糊匹配的研发场景，也适合作为团队内部知识库的外链补充层。

## 功能概览

批量外链导入与去重校验 支持通过文本文件或结构化数据批量导入 URL，系统自动检测重复条目并标记历史变更记录。

分类标签与多级目录管理 每条资源可关联一个或多个自定义标签，支持按技术栈、项目阶段、文档类型等维度建立多级分类树。

链接可用性主动检测 内置 HTTP 状态码检查器，按可配置周期对已收录链接进行存活检测，自动标记失效或重定向的条目。

全文元数据提取 对目标页面进行可配置的元数据抓取，提取标题、摘要描述、发布时间及关键字段，用于增强检索与预览能力。

个性化收藏与注释 允许用户对特定资源添加私有备注与收藏标记，支持按收藏频次生成热门资源排行。

检索与过滤表达式 提供基于标签、关键词、收录时间、可用状态等多条件组合的过滤查询接口，支持正则表达式匹配。

数据导入导出标准格式 支持 JSON、CSV 与 Markdown 表格三种格式的批量导出，便于与其他知识管理工具进行数据交换。

## 应用场景

技术选型调研阶段 当团队需要评估多个开源方案或商业服务时，可通过 LinkMap 快速检索已收录的对比评测文章、官方文档与社区讨论帖，避免重复搜索与信息遗漏。

新成员入职培训 为新入职的研发人员提供一份预置的按技术方向分类的外链清单，涵盖内部规范参考、核心依赖文档与常用工具手册，缩短上手周期。

故障排查与应急响应 在系统异常处理过程中，通过标签快速定位日志分析工具、监控面板文档及历史问题处理记录对应的外部链接，减少上下文切换时间。

技术文档撰写与维护 文档维护人员可利用 LinkMap 的元数据提取功能批量获取外部参考资料的更新时间与状态，及时更新文档中的引用链接，保持文档有效性。

## 快速开始

以下步骤适用于在本地环境部署 LinkMap 服务实例，用于个人或团队内部使用。

```bash
# 克隆项目仓库
git clone https://github.com/linkmap/linkmap-core.git

# 进入项目目录
cd linkmap-core

# 安装 Python 运行时依赖（推荐使用虚拟环境）
python -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 初始化 SQLite 数据库表结构
python scripts/init_db.py

# 启动开发服务器
python app.py run --host 127.0.0.1 --port 8080
```

访问 http://127.0.0.1:8080 即可进入 LinkMap 仪表盘界面，首次启动将自动生成管理员账户，初始密码输出在控制台日志中。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行时环境，建议使用 3.11 LTS 版本 |
| SQLite | 3.35 及以上 | 默认内置数据库，用于存储资源索引与元数据 |
| Redis | 6.2 及以上 | 可选组件，用于缓存检测结果与分布式任务队列 |
| Node.js | 18.x LTS | 仅前端构建时需要，生产环境可单独部署静态资源 |
| Nginx | 1.22 及以上 | 生产环境推荐反向代理服务器，用于负载与静态缓存 |
| Git | 2.30 及以上 | 版本控制与自动更新脚本依赖 |
| curl | 7.68 及以上 | 链接可用性检测工具，系统 PATH 中需存在 |
| jq | 1.6 及以上 | 用于解析 JSON 格式的元数据输出，可选但推荐 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user/quick-start.md | 如何注册、登录、进行首次外链检索与收藏 |
| 用户手册 | docs/user/batch-import.md | 如何从 CSV 或 JSON 文件批量导入外部链接 |
| 管理员指南 | docs/admin/link-checker.md | 如何配置链接存活检测的周期、超时与告警阈值 |
| 管理员指南 | docs/admin/tag-system.md | 如何设计分类标签树、合并重复标签及权限控制 |
| 开发者文档 | docs/dev/api-reference.md | RESTful API 的端点列表、请求参数与响应格式说明 |
| 开发者文档 | docs/dev/custom-parser.md | 如何为特定域名编写自定义元数据解析插件 |
| 运维手册 | docs/ops/deployment.md | 使用 Docker Compose 或 Kubernetes 部署生产集群的配置模板 |
| 运维手册 | docs/ops/backup-restore.md | 数据库定期备份策略与故障恢复操作流程 |

## 资源列表

- http://map.mobile.xqnqq.com/Article/9224.shtml
- http://map.mobile.xqnqq.com/Article/095744.shtml
- http://map.read.usuhx.com/Article/4858393.shtml
- http://map.mobile.xqnqq.com/Article/28499.shtml
- http://map.read.usuhx.com/Article/322144.shtml
- http://map.mobile.xqnqq.com/Article/4683.shtml
- http://map.mobile.xqnqq.com/Article/3960.shtml
- http://map.mobile.xqnqq.com/Article/1637386.shtml
- http://map.read.usuhx.com/Article/3529080.shtml
- http://map.read.usuhx.com/Article/1725935.shtml
- http://map.mobile.xqnqq.com/Article/16832.shtml
- http://map.mobile.xqnqq.com/Article/712077.shtml
- http://map.mobile.xqnqq.com/Article/8995936.shtml
- http://map.mobile.xqnqq.com/Article/415500.shtml
- http://map.read.usuhx.com/Article/439062.shtml
- http://map.mobile.xqnqq.com/Article/6574.shtml
- http://map.read.usuhx.com/Article/2921032.shtml
- http://map.read.usuhx.com/Article/3822760.shtml
- http://map.mobile.xqnqq.com/Article/60103.shtml
- http://map.read.usuhx.com/Article/757405.shtml
- http://map.mobile.xqnqq.com/Article/30377.shtml
- http://map.mobile.xqnqq.com/Article/225779.shtml
- http://map.read.usuhx.com/Article/0381.shtml
- http://map.read.usuhx.com/Article/981227.shtml
- http://map.read.usuhx.com/Article/1899500.shtml
- http://map.read.usuhx.com/Article/3012571.shtml
- http://map.mobile.xqnqq.com/Article/0277920.shtml
- http://map.mobile.xqnqq.com/Article/8181788.shtml
- http://map.read.usuhx.com/Article/088386.shtml
- http://map.read.usuhx.com/Article/9635.shtml
- http://map.read.usuhx.com/Article/3639.shtml
- http://map.read.usuhx.com/Article/727966.shtml
- http://map.read.usuhx.com/Article/0280.shtml
- http://map.mobile.xqnqq.com/Article/304662.shtml
- http://map.mobile.xqnqq.com/Article/8288.shtml
- http://map.read.usuhx.com/Article/2271.shtml
- http://map.mobile.xqnqq.com/Article/12541.shtml
- http://map.read.usuhx.com/Article/782418.shtml
- http://map.mobile.xqnqq.com/Article/113486.shtml
- http://map.mobile.xqnqq.com/Article/6570.shtml
- http://map.read.usuhx.com/Article/43341.shtml
- http://map.mobile.xqnqq.com/Article/8320283.shtml
- http://map.mobile.xqnqq.com/Article/28029.shtml
- http://map.read.usuhx.com/Article/9967206.shtml
- http://map.read.usuhx.com/Article/660350.shtml
- http://map.read.usuhx.com/Article/1306348.shtml
- http://map.mobile.xqnqq.com/Article/22121.shtml
- http://map.mobile.xqnqq.com/Article/3434676.shtml
- http://map.read.usuhx.com/Article/00527.shtml
- http://map.read.usuhx.com/Article/06826.shtml
- http://map.mobile.xqnqq.com/Article/8497045.shtml
- http://map.mobile.xqnqq.com/Article/971182.shtml
- http://map.mobile.xqnqq.com/Article/7128.shtml
- http://map.mobile.xqnqq.com/Article/2033224.shtml
- http://map.mobile.xqnqq.com/Article/33474.shtml
- http://map.mobile.xqnqq.com/Article/13162.shtml
- http://map.mobile.xqnqq.com/Article/04177.shtml
- http://map.mobile.xqnqq.com/Article/575434.shtml
- http://map.read.usuhx.com/Article/8838371.shtml
- http://map.mobile.xqnqq.com/Article/0190451.shtml
- http://map.mobile.xqnqq.com/Article/53718.shtml
- http://map.mobile.xqnqq.com/Article/3412771.shtml
- http://map.mobile.xqnqq.com/Article/627177.shtml
- http://map.read.usuhx.com/Article/883253.shtml
- http://map.read.usuhx.com/Article/236338.shtml
- http://map.read.usuhx.com/Article/046867.shtml
- http://map.mobile.xqnqq.com/Article/3250.shtml
- http://map.read.usuhx.com/Article/375799.shtml
- http://map.mobile.xqnqq.com/Article/761115.shtml
- http://map.read.usuhx.com/Article/1598299.shtml
- http://map.mobile.xqnqq.com/Article/6649791.shtml
- http://map.mobile.xqnqq.com/Article/34875.shtml
- http://map.mobile.xqnqq.com/Article/12925.shtml
- http://map.mobile.xqnqq.com/Article/44591.shtml
- http://map.mobile.xqnqq.com/Article/15647.shtml
- http://map.mobile.xqnqq.com/Article/576571.shtml
- http://map.read.usuhx.com/Article/46166.shtml
- http://map.read.usuhx.com/Article/01022.shtml
- http://map.mobile.xqnqq.com/Article/0654.shtml
- http://map.mobile.xqnqq.com/Article/75619.shtml
- http://map.mobile.xqnqq.com/Article/219937.shtml
- http://map.mobile.xqnqq.com/Article/947084.shtml
- http://map.mobile.xqnqq.com/Article/0062.shtml
- http://map.read.usuhx.com/Article/128173.shtml
- http://map.mobile.xqnqq.com/Article/9168501.shtml
- http://map.mobile.xqnqq.com/Article/4177.shtml
- http://map.read.usuhx.com/Article/9191252.shtml
- http://map.mobile.xqnqq.com/Article/4561.shtml
- http://map.mobile.xqnqq.com/Article/0343662.shtml
- http://map.read.usuhx.com/Article/20946.shtml
- http://map.mobile.xqnqq.com/Article/8870.shtml
- http://map.mobile.xqnqq.com/Article/13523.shtml
- http://map.mobile.xqnqq.com/Article/4125912.shtml
- http://map.mobile.xqnqq.com/Article/7216.shtml
- http://map.mobile.xqnqq.com/Article/714537.shtml
- http://map.mobile.xqnqq.com/Article/1982.shtml
- http://map.read.usuhx.com/Article/134595.shtml
- http://map.mobile.xqnqq.com/Article/4266055.shtml
- http://map.mobile.xqnqq.com/Article/72052.shtml
- http://map.mobile.xqnqq.com/Article/6515748.shtml
- http://map.read.usuhx.com/Article/6305544.shtml
- http://map.mobile.xqnqq.com/Article/0809.shtml
- http://map.mobile.xqnqq.com/Article/2069389.shtml
- http://map.read.usuhx.com/Article/6935.shtml
- http://map.mobile.xqnqq.com/Article/4033.shtml
- http://map.mobile.xqnqq.com/Article/2171420.shtml
- http://map.read.usuhx.com/Article/4410.shtml
- http://map.mobile.xqnqq.com/Article/6325105.shtml
- http://map.read.usuhx.com/Article/998756.shtml
- http://map.read.usuhx.com/Article/673821.shtml
- http://map.mobile.xqnqq.com/Article/8484.shtml
- http://map.read.usuhx.com/Article/0443400.shtml
- http://map.read.usuhx.com/Article/575752.shtml
- http://map.read.usuhx.com/Article/5215276.shtml
- http://map.mobile.xqnqq.com/Article/6013600.shtml
- http://map.mobile.xqnqq.com/Article/3100.shtml
- http://map.read.usuhx.com/Article/5373.shtml
- http://map.read.usuhx.com/Article/9730368.shtml
- http://map.mobile.xqnqq.com/Article/2046.shtml
- http://map.read.usuhx.com/Article/14120.shtml
- http://map.mobile.xqnqq.com/Article/3888605.shtml
- http://map.mobile.xqnqq.com/Article/96284.shtml
- http://map.mobile.xqnqq.com/Article/930312.shtml
- http://map.read.usuhx.com/Article/901066.shtml
- http://map.read.usuhx.com/Article/619365.shtml
- http://map.mobile.xqnqq.com/Article/659896.shtml
- http://map.read.usuhx.com/Article/778558.shtml
- http://map.read.usuhx.com/Article/37829.shtml
- http://map.read.usuhx.com/Article/531984.shtml
- http://map.mobile.xqnqq.com/Article/417675.shtml
- http://map.mobile.xqnqq.com/Article/21713.shtml
- http://map.mobile.xqnqq.com/Article/993781.shtml
- http://map.mobile.xqnqq.com/Article/3323.shtml
- http://map.read.usuhx.com/Article/32270.shtml
- http://map.mobile.xqnqq.com/Article/4966764.shtml
- http://map.mobile.xqnqq.com/Article/0925506.shtml
- http://map.mobile.xqnqq.com/Article/3312.shtml
- http://map.mobile.xqnqq.com/Article/4378.shtml
- http://map.mobile.xqnqq.com/Article/2578.shtml
- http://map.mobile.xqnqq.com/Article/459312.shtml
- http://map.mobile.xqnqq.com/Article/5023696.shtml
- http://map.read.usuhx.com/Article/6355.shtml
- http://map.read.usuhx.com/Article/0692384.shtml
- http://map.read.usuhx.com/Article/9406129.shtml
- http://map.read.usuhx.com/Article/562267.shtml
- http://map.mobile.xqnqq.com/Article/7924789.shtml
- http://map.mobile.xqnqq.com/Article/738545.shtml
- http://map.read.usuhx.com/Article/2534809.shtml
- http://map.read.usuhx.com/Article/2448.shtml
- http://map.read.usuhx.com/Article/5540.shtml
- http://map.mobile.xqnqq.com/Article/13246.shtml
- http://map.mobile.xqnqq.com/Article/651060.shtml
- http://map.mobile.xqnqq.com/Article/4939056.shtml
- http://map.read.usuhx.com/Article/16156.shtml
- http://map.mobile.xqnqq.com/Article/0197031.shtml
- http://map.mobile.xqnqq.com/Article/649700.shtml
- http://map.read.usuhx.com/Article/10170.shtml
- http://map.read.usuhx.com/Article/25251.shtml
- http://map.read.usuhx.com/Article/53657.shtml
- http://map.mobile.xqnqq.com/Article/598219.shtml
- http://map.read.usuhx.com/Article/7560.shtml
- http://map.read.usuhx.com/Article/21986.shtml
- http://map.mobile.xqnqq.com/Article/688049.shtml
- http://map.mobile.xqnqq.com/Article/41458.shtml
- http://map.mobile.xqnqq.com/Article/557285.shtml
- http://map.mobile.xqnqq.com/Article/59778.shtml
- http://map.mobile.xqnqq.com/Article/25131.shtml
- http://map.read.usuhx.com/Article/3087.shtml
- http://map.read.usuhx.com/Article/1170.shtml
- http://map.read.usuhx.com/Article/857287.shtml
- http://map.read.usuhx.com/Article/352712.shtml
- http://map.mobile.xqnqq.com/Article/9231827.shtml
- http://map.read.usuhx.com/Article/078408.shtml
- http://map.read.usuhx.com/Article/58849.shtml
- http://map.mobile.xqnqq.com/Article/56171.shtml
- http://map.read.usuhx.com/Article/2351303.shtml
- http://map.mobile.xqnqq.com/Article/036653.shtml
- http://map.read.usuhx.com/Article/532317.shtml
- http://map.read.usuhx.com/Article/7081288.shtml
- http://map.mobile.xqnqq.com/Article/1702.shtml
- http://map.read.usuhx.com/Article/622565.shtml
- http://map.mobile.xqnqq.com/Article/11783.shtml
- http://map.mobile.xqnqq.com/Article/05362.shtml
- http://map.read.usuhx.com/Article/040488.shtml
- http://map.mobile.xqnqq.com/Article/3878.shtml
- http://map.mobile.xqnqq.com/Article/786536.shtml
- http://map.read.usuhx.com/Article/76375.shtml
- http://map.read.usuhx.com/Article/9089053.shtml
- http://map.read.usuhx.com/Article/4965.shtml
- http://map.mobile.xqnqq.com/Article/66961.shtml
- http://map.read.usuhx.com/Article/278055.shtml
- http://map.read.usuhx.com/Article/9765.shtml
- http://map.read.usuhx.com/Article/2270882.shtml
- http://map.read.usuhx.com/Article/71591.shtml
- http://map.mobile.xqnqq.com/Article/585854.shtml
- http://map.read.usuhx.com/Article/6311987.shtml
- http://map.read.usuhx.com/Article/65293.shtml
- http://map.read.usuhx.com/Article/77205.shtml
- http://map.read.usuhx.com/Article/5270.shtml
- http://map.mobile.xqnqq.com/Article/9432725.shtml
- http://map.read.usuhx.com/Article/2040364.shtml
- http://map.read.usuhx.com/Article/61344.shtml
- http://map.read.usuhx.com/Article/4510.shtml
- http://map.mobile.xqnqq.com/Article/3974.shtml
- http://map.read.usuhx.com/Article/24936.shtml
- http://map.mobile.xqnqq.com/Article/0060.shtml
- http://map.mobile.xqnqq.com/Article/80070.shtml
- http://map.read.usuhx.com/Article/5486920.shtml
- http://map.read.usuhx.com/Article/13045.shtml
- http://map.mobile.xqnqq.com/Article/1748.shtml
- http://map.read.usuhx.com/Article/6536.shtml
- http://map.mobile.xqnqq.com/Article/2393.shtml
- http://map.read.usuhx.com/Article/26836.shtml
- http://map.mobile.xqnqq.com/Article/091230.shtml
- http://map.mobile.xqnqq.com/Article/9398.shtml
- http://map.read.usuhx.com/Article/17050.shtml
- http://map.mobile.xqnqq.com/Article/084696.shtml
- http://map.mobile.xqnqq.com/Article/3613741.shtml
- http://map.mobile.xqnqq.com/Article/77240.shtml
- http://map.read.usuhx.com/Article/6503.shtml
- http://map.read.usuhx.com/Article/7582.shtml
- http://map.read.usuhx.com/Article/9376410.shtml
- http://map.mobile.xqnqq.com/Article/793533.shtml
- http://map.mobile.xqnqq.com/Article/7582861.shtml
- http://map.read.usuhx.com/Article/4971241.shtml
- http://map.mobile.xqnqq.com/Article/22067.shtml
- http://map.read.usuhx.com/Article/3246337.shtml
- http://map.mobile.xqnqq.com/Article/2183580.shtml
- http://map.read.usuhx.com/Article/8529.shtml
- http://map.read.usuhx.com/Article/742336.shtml
- http://map.read.usuhx.com/Article/5210176.shtml
- http://map.mobile.xqnqq.com/Article/26510.shtml
- http://map.read.usuhx.com/Article/0671.shtml
- http://map.mobile.xqnqq.com/Article/4459.shtml
- http://map.read.usuhx.com/Article/66485.shtml
- http://map.mobile.xqnqq.com/Article/1857.shtml
- http://map.read.usuhx.com/Article/741719.shtml
- http://map.mobile.xqnqq.com/Article/7033.shtml
- http://map.mobile.xqnqq.com/Article/1292839.shtml
- http://map.read.usuhx.com/Article/757287.shtml
- http://map.read.usuhx.com/Article/6843551.shtml
- http://map.mobile.xqnqq.com/Article/9846.shtml
- http://map.mobile.xqnqq.com/Article/7469.shtml
- http://map.read.usuhx.com/Article/94930.shtml
- http://map.mobile.xqnqq.com/Article/6759860.shtml
- http://map.read.usuhx.com/Article/113569.shtml
- http://map.read.usuhx.com/Article/50164.shtml
- http://map.mobile.xqnqq.com/Article/8413.shtml
- http://map.mobile.xqnqq.com/Article/9020546.shtml
- http://map.mobile.xqnqq.com/Article/8920923.shtml

## 项目结构

```
linkmap-core/
├── app/                              # 主应用模块
│   ├── __init__.py                   # 应用工厂与配置加载
│   ├── routes/                       # 路由层，处理 HTTP 请求分发
│   │   ├── api_v1.py                 # RESTful API v1 端点定义
│   │   └── web.py                    # 服务端渲染页面路由
│   ├── services/                     # 业务逻辑层
│   │   ├── link_service.py           # 链接增删改查与标签关联逻辑
│   │   ├── checker_service.py        # 链接存活检测调度与结果持久化
│   │   └── parser_service.py         # 元数据提取与自定义解析器注册
│   ├── models/                       # 数据模型与 ORM 映射
│   │   ├── link.py                   # Link 实体定义（URL、标题、状态、收录时间）
│   │   ├── tag.py                    # Tag 实体与 Link-Tag 多对多关联
│   │   └── user.py                   # 用户与收藏关系表
│   └── utils/                        # 通用工具函数
│       ├── http_client.py            # 带超时与重试策略的 HTTP 请求封装
│       └── validators.py             # URL 格式校验与规范化工具
├── scripts/                          # 运维与辅助脚本
│   ├── init_db.py                    # 初始化数据库表结构与默认标签种子
│   ├── batch_import.py               # 从外部文件批量导入链接的命令行入口
│   └── export_csv.py                 # 将当前索引导出为 CSV 格式
├── tests/                            # 单元测试与集成测试
│   ├── test_services/                # 针对 service 层的测试用例
│   └── fixtures/                     # 测试用的模拟数据与样本响应
├── frontend/                         # 前端静态资源（独立构建）
│   ├── src/                          # 前端源码（React 组件与状态管理）
│   ├── public/                       # 静态模板与 favicon
│   └── build/                        # 生产构建输出目录（由打包工具生成）
├── docs/                             # 项目文档（见文档导航章节）
├── config/                           # 环境配置
│   ├── development.yaml              # 开发环境配置（调试模式、本地数据库）
│   └── production.yaml.example       # 生产环境配置模板（需填写 Redis 与密钥）
├── requirements.txt                  # Python 生产依赖列表
├── requirements-dev.txt              # 开发与测试额外依赖
├── Dockerfile                        # 基于 Python slim 镜像的容器构建文件
├── docker-compose.yml                # 本地开发与测试用容器编排配置
├── Makefile                          # 常用命令快捷方式（test, lint, run）
└── README.md                         # 本文件
```

## 贡献指南

提交问题报告与功能请求 通过 GitHub Issues 提交缺陷描述或改进建议，需包含环境信息、复现步骤与期望行为。对于功能请求，请说明实际使用场景与优先级依据。

代码贡献流程 派生项目仓库至个人账户，在派生副本中创建功能分支。遵循项目现有的代码风格（PEP 8 与 ESLint 配置），提交前执行 `make lint` 与 `make test` 确保检查通过。提交信息使用约定式提交格式（feat/fix/docs/chore）。

新增外链资源推荐 若希望扩充 LinkMap 的索引库，可通过提交 JSON 或 CSV 格式的资源清单至 `data/contributions/` 目录，并附带简要分类建议。维护团队将定期审核并合并合规条目。

文档完善与翻译 欢迎对用户手册、API 文档及本 README 进行勘误或补充。文档变更应同步更新对应的 `docs/` 目录下的 Markdown 文件，并保持与代码实现的一致性。

行为准则 所有参与者需遵守项目行为准则，尊重不同意见，保持专业友善的沟通氛围。维护者有权对不符合准则的贡献进行拒绝或撤回。

## 常见问题

Q: 系统如何处理目标页面不可访问或响应超时的情况？

A: LinkMap 的链接检测服务采用指数退避重试策略，默认对每个 URL 进行最多 3 次检测尝试，超时阈值设置为 10 秒。连续两次检测失败后，系统将链接状态标记为「不可达」，并在日志中记录 HTTP 状态码或错误类型。用户可在管理后台手动触发重新检测，或调整全局检测周期（默认每 72 小时扫描一次全量索引）。

Q: 如何将现有的收藏夹或书签批量导入 LinkMap？

A: 支持从浏览器导出的 HTML 书签文件（Netscape 格式）以及通用的 CSV 表格文件导入。导入功能位于管理后台的「批量操作」面板中，用户上传文件后系统自动解析标题与 URL 字段，并允许在导入前预览和调整分类标签。对于大规模导入（超过 500 条），建议使用命令行脚本 `scripts/batch_import.py` 以提高处理效率。

Q: LinkMap 能否部署在完全离线或内网环境中使用？

A: 可以。LinkMap 本身不依赖任何外部在线服务，所有核心功能（索引管理、标签分类、状态检测）均可在内网环境中正常运行。但需要注意，链接可用性检测功能在内网环境中仅能探测内网可达的地址；对于公网链接，检测结果将因网络隔离而标记为不可达。元数据提取功能同样受网络访问能力限制，若需要提取内网文档的元数据，请确保解析器配置了对应的内网访问凭证。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
