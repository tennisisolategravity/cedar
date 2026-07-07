# MapLink 资源导航系统

MapLink 是一个面向技术文档聚合与外部资源导航的开源系统，专为需要高效管理大量外链文章、技术手册、行业报告及知识库条目的开发者与内容运营团队设计。该项目不属于传统爬虫或采集工具，而是一套以链接分类、元数据标注、质量评估与快速检索为核心的轻量级资源索引框架。

目标用户包括个人技术博主、开源社区文档维护者、企业知识管理团队以及教育培训机构的内容整理人员。MapLink 不提供内容存储服务，仅专注于外部链接的结构化组织与状态监控，帮助用户在信息过载的环境中维持高质量的外链资源池。

本批次 MapLink 收录资源属于第 50/80 批导入集，共包含 250 个来自 map.mobile.xqnqq.com 与 map.read.usuhx.com 双域名的技术向文章链接。系统将对这些 URL 执行可用性检查、响应时间记录、内容类型推测以及标签自动补全等标准化处理流程。

## 功能概览

外链批量导入与去重 系统支持通过 CSV 或纯文本列表批量提交 URL，自动过滤重复条目并生成导入报告，单批次处理上限为 500 条链接。

存活状态周期性检测 内置轻量级调度器，可对已收录链接按每日、每周或每月周期执行 HTTP 状态码检查，标记失效链接并记录重定向链变化。

内容元数据自动提取 对可访问的 HTML 页面自动提取标题、描述、关键词及正文语言编码，辅助后续分类与检索操作。

自定义标签与分类体系 用户可创建多级分类树，为每条链接附加一个或多个自定义标签，支持基于标签组合的快速筛选与统计。

检索与过滤查询引擎 提供基于标题、域名、标签、收录时间范围及状态码的多条件组合检索，检索结果支持按相关度或时间排序。

数据导出与订阅看板 支持将筛选后的链接列表导出为 CSV、JSON 或 HTML 摘要格式，并提供只读看板视图用于日常监控。

操作日志与变更追溯 所有导入、编辑、删除及状态变更操作均记录操作者与时间戳，支持按时间区间回溯历史改动。

## 应用场景

技术博客文章库维护 个人技术作者可使用 MapLink 统一管理自己引用过的外部参考文章，当原文链接失效时及时收到通知并替换为有效来源，避免读者访问死链。

开源项目文档外链整理 开源项目维护者可将项目 README 或 Wiki 中引用的所有外部资源纳入 MapLink 管理，确保依赖文档、参考规范及教程链接长期可用。

在线教育课程资源索引 培训机构或 MOOC 平台内容制作团队可使用 MapLink 为每门课程建立独立的外链资源包，方便学员按章节访问补充阅读材料，同时监控资源有效性。

企业内部技术知识库建设 企业技术部门可将分散在团队笔记、邮件或聊天记录中的有价值外链统一归集至 MapLink，按项目或技术领域分类，降低信息重复收集成本。

## 快速开始

以下指令适用于 Linux 与 macOS 环境，Windows 用户建议通过 WSL2 或 Git Bash 执行。

```bash
git clone https://github.com/maplink-org/maplink-nav.git
cd maplink-nav

# 安装 Python 3.10+ 虚拟环境与依赖
python -m venv venv
source venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt

# 初始化 SQLite 数据库表结构
python scripts/init_db.py

# 导入本批次资源列表（示例文件为 batch_50_80.txt）
python cli/import.py --file samples/batch_50_80.txt --batch 50

# 启动本地开发服务器
python app.py --host 127.0.0.1 --port 8080
```

访问 http://127.0.0.1:8080/dashboard 可查看看板界面。首次启动将自动执行约 30 秒的链接预检测。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Python | 3.10 至 3.12 | 核心运行环境，3.13 暂未完成兼容性测试 |
| SQLite | 3.35.0 或更高 | 内置数据库引擎，用于存储链接元数据与检测记录 |
| requests | 2.31.0 或更高 | HTTP 客户端库，用于执行链接状态检测与内容获取 |
| beautifulsoup4 | 4.12.0 或更高 | HTML 解析库，用于提取页面标题及描述信息 |
| lxml | 4.9.0 或更高 | 作为 beautifulsoup4 的解析器后端，提供更高性能 |
| Flask | 2.3.0 或更高 | 仅在看板与 API 服务启用时需要，核心 CLI 模式可不安装 |
| gunicorn | 21.0.0 或更高 | 生产环境推荐部署的 WSGI 服务器 |
| pytest | 7.4.0 或更高 | 仅单元测试与集成测试时需要，非运行必需 |
| schedule | 1.2.0 或更高 | 用于定时执行链接状态批量检查任务 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user-guide/ | 如何批量导入链接、如何创建分类标签、如何设置状态检测频率 |
| 管理员指南 | docs/admin-guide/ | 如何备份数据库、如何迁移至 PostgreSQL、如何配置邮件告警 |
| 开发参考 | docs/developer-guide/ | 插件式检测器如何扩展、元数据提取器接口定义、测试用例编写规范 |
| 部署方案 | docs/deployment/ | 单机 Docker 运行、集群模式配置、反向代理与 HTTPS 终端设置 |
| API 文档 | docs/api/ | RESTful API 所有端点说明、请求参数格式、错误码及示例响应 |
| 常见任务 | docs/recipes/ | 定时清理 404 链接、标签合并、批量更新标题的实操脚本模板 |

## 资源列表

- http://map.mobile.xqnqq.com/Article/7876873.shtml
- http://map.mobile.xqnqq.com/Article/15808.shtml
- http://map.mobile.xqnqq.com/Article/58990.shtml
- http://map.mobile.xqnqq.com/Article/7249.shtml
- http://map.read.usuhx.com/Article/727828.shtml
- http://map.read.usuhx.com/Article/7721202.shtml
- http://map.mobile.xqnqq.com/Article/2116715.shtml
- http://map.mobile.xqnqq.com/Article/91333.shtml
- http://map.mobile.xqnqq.com/Article/05395.shtml
- http://map.mobile.xqnqq.com/Article/79159.shtml
- http://map.mobile.xqnqq.com/Article/3845.shtml
- http://map.read.usuhx.com/Article/67229.shtml
- http://map.mobile.xqnqq.com/Article/635958.shtml
- http://map.mobile.xqnqq.com/Article/96532.shtml
- http://map.read.usuhx.com/Article/0769.shtml
- http://map.read.usuhx.com/Article/96537.shtml
- http://map.read.usuhx.com/Article/1273619.shtml
- http://map.mobile.xqnqq.com/Article/6801.shtml
- http://map.mobile.xqnqq.com/Article/40075.shtml
- http://map.mobile.xqnqq.com/Article/10732.shtml
- http://map.read.usuhx.com/Article/13508.shtml
- http://map.read.usuhx.com/Article/991122.shtml
- http://map.read.usuhx.com/Article/837994.shtml
- http://map.read.usuhx.com/Article/4374.shtml
- http://map.mobile.xqnqq.com/Article/8506301.shtml
- http://map.read.usuhx.com/Article/77053.shtml
- http://map.mobile.xqnqq.com/Article/4872.shtml
- http://map.mobile.xqnqq.com/Article/844482.shtml
- http://map.mobile.xqnqq.com/Article/3724.shtml
- http://map.read.usuhx.com/Article/6859586.shtml
- http://map.mobile.xqnqq.com/Article/82902.shtml
- http://map.read.usuhx.com/Article/8281420.shtml
- http://map.read.usuhx.com/Article/78355.shtml
- http://map.read.usuhx.com/Article/6830974.shtml
- http://map.mobile.xqnqq.com/Article/54965.shtml
- http://map.mobile.xqnqq.com/Article/056935.shtml
- http://map.read.usuhx.com/Article/9590.shtml
- http://map.read.usuhx.com/Article/5273941.shtml
- http://map.read.usuhx.com/Article/4756802.shtml
- http://map.mobile.xqnqq.com/Article/6586207.shtml
- http://map.read.usuhx.com/Article/0928.shtml
- http://map.mobile.xqnqq.com/Article/001879.shtml
- http://map.read.usuhx.com/Article/80090.shtml
- http://map.mobile.xqnqq.com/Article/119813.shtml
- http://map.read.usuhx.com/Article/1618064.shtml
- http://map.read.usuhx.com/Article/03368.shtml
- http://map.mobile.xqnqq.com/Article/928013.shtml
- http://map.mobile.xqnqq.com/Article/2521.shtml
- http://map.mobile.xqnqq.com/Article/4492.shtml
- http://map.mobile.xqnqq.com/Article/7382121.shtml
- http://map.mobile.xqnqq.com/Article/27878.shtml
- http://map.read.usuhx.com/Article/598219.shtml
- http://map.read.usuhx.com/Article/8912.shtml
- http://map.mobile.xqnqq.com/Article/6891133.shtml
- http://map.mobile.xqnqq.com/Article/049587.shtml
- http://map.read.usuhx.com/Article/15375.shtml
- http://map.read.usuhx.com/Article/17187.shtml
- http://map.mobile.xqnqq.com/Article/2622464.shtml
- http://map.read.usuhx.com/Article/9357954.shtml
- http://map.mobile.xqnqq.com/Article/8695.shtml
- http://map.read.usuhx.com/Article/8146349.shtml
- http://map.read.usuhx.com/Article/9641.shtml
- http://map.mobile.xqnqq.com/Article/6454.shtml
- http://map.read.usuhx.com/Article/5598525.shtml
- http://map.mobile.xqnqq.com/Article/326180.shtml
- http://map.read.usuhx.com/Article/8501318.shtml
- http://map.mobile.xqnqq.com/Article/632926.shtml
- http://map.read.usuhx.com/Article/4782.shtml
- http://map.read.usuhx.com/Article/4394.shtml
- http://map.mobile.xqnqq.com/Article/9480936.shtml
- http://map.read.usuhx.com/Article/64669.shtml
- http://map.read.usuhx.com/Article/281873.shtml
- http://map.mobile.xqnqq.com/Article/22888.shtml
- http://map.mobile.xqnqq.com/Article/183953.shtml
- http://map.mobile.xqnqq.com/Article/25357.shtml
- http://map.mobile.xqnqq.com/Article/997179.shtml
- http://map.read.usuhx.com/Article/1284999.shtml
- http://map.read.usuhx.com/Article/1083587.shtml
- http://map.read.usuhx.com/Article/65971.shtml
- http://map.mobile.xqnqq.com/Article/4044.shtml
- http://map.read.usuhx.com/Article/26598.shtml
- http://map.mobile.xqnqq.com/Article/7950.shtml
- http://map.read.usuhx.com/Article/56969.shtml
- http://map.mobile.xqnqq.com/Article/22611.shtml
- http://map.read.usuhx.com/Article/94772.shtml
- http://map.read.usuhx.com/Article/4425.shtml
- http://map.mobile.xqnqq.com/Article/682839.shtml
- http://map.read.usuhx.com/Article/6083894.shtml
- http://map.read.usuhx.com/Article/6629767.shtml
- http://map.mobile.xqnqq.com/Article/4328.shtml
- http://map.mobile.xqnqq.com/Article/1059.shtml
- http://map.mobile.xqnqq.com/Article/457410.shtml
- http://map.mobile.xqnqq.com/Article/4405182.shtml
- http://map.mobile.xqnqq.com/Article/361123.shtml
- http://map.read.usuhx.com/Article/19151.shtml
- http://map.mobile.xqnqq.com/Article/455026.shtml
- http://map.mobile.xqnqq.com/Article/8855296.shtml
- http://map.read.usuhx.com/Article/6032.shtml
- http://map.mobile.xqnqq.com/Article/61197.shtml
- http://map.mobile.xqnqq.com/Article/381265.shtml
- http://map.read.usuhx.com/Article/86341.shtml
- http://map.read.usuhx.com/Article/3864.shtml
- http://map.read.usuhx.com/Article/450530.shtml
- http://map.read.usuhx.com/Article/049774.shtml
- http://map.read.usuhx.com/Article/07823.shtml
- http://map.read.usuhx.com/Article/5378882.shtml
- http://map.mobile.xqnqq.com/Article/481921.shtml
- http://map.read.usuhx.com/Article/664771.shtml
- http://map.mobile.xqnqq.com/Article/1836543.shtml
- http://map.read.usuhx.com/Article/944083.shtml
- http://map.mobile.xqnqq.com/Article/1980.shtml
- http://map.mobile.xqnqq.com/Article/1222.shtml
- http://map.read.usuhx.com/Article/0206.shtml
- http://map.read.usuhx.com/Article/4893.shtml
- http://map.read.usuhx.com/Article/916448.shtml
- http://map.read.usuhx.com/Article/463517.shtml
- http://map.mobile.xqnqq.com/Article/5023.shtml
- http://map.read.usuhx.com/Article/35392.shtml
- http://map.read.usuhx.com/Article/14117.shtml
- http://map.mobile.xqnqq.com/Article/656050.shtml
- http://map.mobile.xqnqq.com/Article/17701.shtml
- http://map.mobile.xqnqq.com/Article/404864.shtml
- http://map.read.usuhx.com/Article/8227.shtml
- http://map.mobile.xqnqq.com/Article/26018.shtml
- http://map.mobile.xqnqq.com/Article/22490.shtml
- http://map.read.usuhx.com/Article/9518561.shtml
- http://map.mobile.xqnqq.com/Article/46258.shtml
- http://map.mobile.xqnqq.com/Article/9469.shtml
- http://map.mobile.xqnqq.com/Article/93399.shtml
- http://map.read.usuhx.com/Article/494681.shtml
- http://map.mobile.xqnqq.com/Article/74924.shtml
- http://map.read.usuhx.com/Article/678355.shtml
- http://map.read.usuhx.com/Article/9031.shtml
- http://map.mobile.xqnqq.com/Article/298975.shtml
- http://map.read.usuhx.com/Article/993304.shtml
- http://map.mobile.xqnqq.com/Article/721682.shtml
- http://map.read.usuhx.com/Article/92164.shtml
- http://map.read.usuhx.com/Article/0304595.shtml
- http://map.mobile.xqnqq.com/Article/40327.shtml
- http://map.read.usuhx.com/Article/616790.shtml
- http://map.mobile.xqnqq.com/Article/764456.shtml
- http://map.mobile.xqnqq.com/Article/9240.shtml
- http://map.read.usuhx.com/Article/1482029.shtml
- http://map.mobile.xqnqq.com/Article/9891.shtml
- http://map.read.usuhx.com/Article/509799.shtml
- http://map.read.usuhx.com/Article/788564.shtml
- http://map.mobile.xqnqq.com/Article/6245.shtml
- http://map.mobile.xqnqq.com/Article/1461116.shtml
- http://map.read.usuhx.com/Article/782023.shtml
- http://map.mobile.xqnqq.com/Article/18683.shtml
- http://map.read.usuhx.com/Article/5043.shtml
- http://map.mobile.xqnqq.com/Article/6857658.shtml
- http://map.read.usuhx.com/Article/1613.shtml
- http://map.mobile.xqnqq.com/Article/7777755.shtml
- http://map.read.usuhx.com/Article/1945590.shtml
- http://map.read.usuhx.com/Article/1409.shtml
- http://map.read.usuhx.com/Article/6180.shtml
- http://map.read.usuhx.com/Article/452085.shtml
- http://map.mobile.xqnqq.com/Article/7662893.shtml
- http://map.read.usuhx.com/Article/755408.shtml
- http://map.mobile.xqnqq.com/Article/8935441.shtml
- http://map.mobile.xqnqq.com/Article/4050586.shtml
- http://map.read.usuhx.com/Article/13572.shtml
- http://map.mobile.xqnqq.com/Article/6249720.shtml
- http://map.mobile.xqnqq.com/Article/56697.shtml
- http://map.read.usuhx.com/Article/4216133.shtml
- http://map.mobile.xqnqq.com/Article/4454.shtml
- http://map.mobile.xqnqq.com/Article/4997953.shtml
- http://map.read.usuhx.com/Article/37871.shtml
- http://map.mobile.xqnqq.com/Article/084525.shtml
- http://map.mobile.xqnqq.com/Article/47571.shtml
- http://map.read.usuhx.com/Article/73790.shtml
- http://map.mobile.xqnqq.com/Article/65742.shtml
- http://map.mobile.xqnqq.com/Article/4761.shtml
- http://map.read.usuhx.com/Article/135298.shtml
- http://map.mobile.xqnqq.com/Article/55015.shtml
- http://map.read.usuhx.com/Article/42895.shtml
- http://map.read.usuhx.com/Article/3221.shtml
- http://map.read.usuhx.com/Article/5266660.shtml
- http://map.mobile.xqnqq.com/Article/495419.shtml
- http://map.mobile.xqnqq.com/Article/3611.shtml
- http://map.read.usuhx.com/Article/9687.shtml
- http://map.read.usuhx.com/Article/7882104.shtml
- http://map.mobile.xqnqq.com/Article/8577607.shtml
- http://map.read.usuhx.com/Article/9877.shtml
- http://map.mobile.xqnqq.com/Article/81533.shtml
- http://map.mobile.xqnqq.com/Article/9002534.shtml
- http://map.read.usuhx.com/Article/3891.shtml
- http://map.mobile.xqnqq.com/Article/470870.shtml
- http://map.mobile.xqnqq.com/Article/3232138.shtml
- http://map.mobile.xqnqq.com/Article/693791.shtml
- http://map.mobile.xqnqq.com/Article/421180.shtml
- http://map.mobile.xqnqq.com/Article/165473.shtml
- http://map.read.usuhx.com/Article/1381786.shtml
- http://map.mobile.xqnqq.com/Article/4639.shtml
- http://map.mobile.xqnqq.com/Article/9397.shtml
- http://map.mobile.xqnqq.com/Article/09579.shtml
- http://map.read.usuhx.com/Article/2593.shtml
- http://map.mobile.xqnqq.com/Article/3769.shtml
- http://map.read.usuhx.com/Article/0727.shtml
- http://map.read.usuhx.com/Article/5795587.shtml
- http://map.mobile.xqnqq.com/Article/624764.shtml
- http://map.read.usuhx.com/Article/5389.shtml
- http://map.read.usuhx.com/Article/1967764.shtml
- http://map.mobile.xqnqq.com/Article/383045.shtml
- http://map.mobile.xqnqq.com/Article/8569.shtml
- http://map.mobile.xqnqq.com/Article/8528275.shtml
- http://map.mobile.xqnqq.com/Article/6644039.shtml
- http://map.mobile.xqnqq.com/Article/528662.shtml
- http://map.read.usuhx.com/Article/939138.shtml
- http://map.read.usuhx.com/Article/4007.shtml
- http://map.mobile.xqnqq.com/Article/73227.shtml
- http://map.read.usuhx.com/Article/69945.shtml
- http://map.mobile.xqnqq.com/Article/1124906.shtml
- http://map.read.usuhx.com/Article/338776.shtml
- http://map.mobile.xqnqq.com/Article/94232.shtml
- http://map.mobile.xqnqq.com/Article/8360093.shtml
- http://map.mobile.xqnqq.com/Article/1671602.shtml
- http://map.mobile.xqnqq.com/Article/921795.shtml
- http://map.mobile.xqnqq.com/Article/438431.shtml
- http://map.mobile.xqnqq.com/Article/81651.shtml
- http://map.read.usuhx.com/Article/4820071.shtml
- http://map.mobile.xqnqq.com/Article/823906.shtml
- http://map.read.usuhx.com/Article/51382.shtml
- http://map.read.usuhx.com/Article/279526.shtml
- http://map.mobile.xqnqq.com/Article/7091206.shtml
- http://map.mobile.xqnqq.com/Article/531407.shtml
- http://map.mobile.xqnqq.com/Article/73402.shtml
- http://map.mobile.xqnqq.com/Article/5296427.shtml
- http://map.mobile.xqnqq.com/Article/32553.shtml
- http://map.mobile.xqnqq.com/Article/0825.shtml
- http://map.mobile.xqnqq.com/Article/961135.shtml
- http://map.read.usuhx.com/Article/276564.shtml
- http://map.mobile.xqnqq.com/Article/72881.shtml
- http://map.mobile.xqnqq.com/Article/89432.shtml
- http://map.read.usuhx.com/Article/0618754.shtml
- http://map.read.usuhx.com/Article/6323536.shtml
- http://map.read.usuhx.com/Article/254538.shtml
- http://map.mobile.xqnqq.com/Article/147234.shtml
- http://map.read.usuhx.com/Article/9965.shtml
- http://map.read.usuhx.com/Article/1682.shtml
- http://map.mobile.xqnqq.com/Article/7374571.shtml
- http://map.read.usuhx.com/Article/03106.shtml
- http://map.read.usuhx.com/Article/52365.shtml
- http://map.read.usuhx.com/Article/90031.shtml
- http://map.read.usuhx.com/Article/7503226.shtml
- http://map.mobile.xqnqq.com/Article/05079.shtml
- http://map.read.usuhx.com/Article/16997.shtml
- http://map.mobile.xqnqq.com/Article/779031.shtml
- http://map.mobile.xqnqq.com/Article/2325328.shtml

## 项目结构

```
maplink-nav/
├── app/                           # 核心应用包
│   ├── __init__.py                # 包初始化与 Flask 应用工厂
│   ├── routes/                    # 路由层，按功能拆分
│   │   ├── dashboard.py           # 看板与统计视图路由
│   │   ├── import_export.py       # 导入导出接口路由
│   │   └── api_v1.py              # RESTful API 端点实现
│   ├── models/                    # 数据模型层，使用 SQLAlchemy ORM
│   │   ├── link.py                # Link 实体，包含 URL、标题、状态等字段
│   │   ├── tag.py                 # Tag 实体，支持多对多关联
│   │   └── check_record.py        # 检测历史记录模型
│   ├── services/                  # 业务逻辑服务层
│   │   ├── checker.py             # 链接状态检测器，含重定向跟随与超时控制
│   │   ├── extractor.py           # 元数据提取器，基于 BeautifulSoup
│   │   └── scheduler.py           # 定时任务调度器，依赖 schedule 库
│   └── utils/                     # 通用工具函数集
│       ├── validators.py          # URL 格式校验与域名白名单过滤
│       └── logger.py              # 统一日志配置，支持文件与控制台双输出
├── cli/                           # 命令行工具入口
│   ├── __init__.py
│   ├── import.py                  # 批量导入链接主逻辑
│   ├── check.py                   # 手动触发链接状态检查
│   └── export.py                  # 按条件导出链接数据
├── scripts/                       # 运维与辅助脚本
│   ├── init_db.py                 # 初始化 SQLite 数据库与基础表
│   ├── migrate_v1_to_v2.py        # 版本迁移脚本（示例）
│   └── seed_demo_data.py          # 生成演示数据用于测试环境
├── tests/                         # 测试目录，采用 pytest 框架
│   ├── unit/                      # 单元测试，覆盖模型与工具函数
│   └── integration/               # 集成测试，覆盖 API 与数据库交互
├── docs/                          # 完整文档源码，采用 Markdown 编写
│   ├── user-guide/                # 用户手册分章节
│   ├── admin-guide/               # 管理员指南
│   └── developer-guide/           # 开发参考文档
├── samples/                       # 示例数据目录
│   └── batch_50_80.txt            # 本批次 250 条链接的原始列表文件
├── requirements.txt               # 生产环境依赖清单
├── requirements-dev.txt           # 开发与测试环境额外依赖
├── app.py                         # 应用启动入口（开发模式）
├── config.py                      # 配置文件，含数据库 URI、检测超时、调度间隔
└── README.md                      # 项目说明文档（本文件）
```

## 贡献指南

1. 查阅问题跟踪器 访问 GitHub Issues 查看未被认领的任务或功能请求，选择与自身技能匹配的事项。新功能建议先通过 Issue 讨论再行实现。

2. 派生仓库并创建功能分支 将主仓库派生至个人账户，基于 main 分支创建以 feature/ 或 fix/ 为前缀的分支名称。分支命名应简要描述变更内容，例如 feature/support-json-export。

3. 编写代码与单元测试 所有新增服务或工具函数必须附带对应的 pytest 单元测试，测试覆盖率不低于 80%。对于涉及外部 HTTP 请求的模块，应使用 responses 或 pytest-mock 模拟网络交互。

4. 运行完整测试套件 在提交前于本地执行 pytest tests/ 确保全部测试通过，同时使用 flake8 与 black 进行代码风格检查与自动格式化。

5. 提交变更并创建拉取请求 提交信息应遵循 Conventional Commits 规范，使用 fix:、feat:、docs: 等前缀。拉取请求描述需清晰说明变更目的、影响范围以及手动测试步骤。

## 常见问题

Q: 导入链接时遇到大量超时或连接拒绝错误，如何调整？

A: 可通过修改 config.py 中的 REQUEST_TIMEOUT 参数（单位秒）增加超时上限，默认值为 10 秒。对于网络条件较差的区域，建议设置为 30 至 60 秒。同时可以调整 CHECKER_CONCURRENCY 参数控制并发检测数量，降低并发数以减轻目标服务器压力。

Q: 能否迁移至 PostgreSQL 或 MySQL 作为后端数据库？

A: 可以。项目使用 SQLAlchemy ORM，理论上支持所有主流关系型数据库。迁移时需修改 config.py 中的 SQLALCHEMY_DATABASE_URI 为对应数据库连接串，并安装相应的数据库驱动（如 psycopg2-binary 或 pymysql）。注意 PostgreSQL 和 MySQL 对索引长度与字符集有不同限制，建议执行 scripts/migrate_v1_to_v2.py 进行适配调整。

Q: 检测结果中的状态码为 0 代表什么含义？

A: 状态码 0 表示检测过程中未能成功建立 HTTP 连接，通常由 DNS 解析失败、目标主机不可达或网络层阻断导致。此种情况与 HTTP 层面的 4xx 或 5xx 错误不同，属于网络连通性问题，建议检查本地网络环境或目标域名是否仍有效。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
