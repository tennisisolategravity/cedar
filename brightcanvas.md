# LinkMap 定向资源聚合系统

LinkMap 是一个面向技术文献与资讯定向聚合的开源资源导航工具，定位于为开发者、研究人员与技术内容消费者提供结构化的外链资源归集与快速访问能力。本项目不提供搜索引擎或爬虫框架，而是以人工精选与半自动导入相结合的方式，将分布在多个内容源上的技术文章、规范文档与行业报告统一收纳至可检索、可分类、可版本追踪的资源池中。目标用户包括技术团队内部知识库维护者、开源社区文档协调员以及需要批量管理外部链接的个人研究者。LinkMap 通过标准化 URL 录入格式、自动校验链接可用性与批处理导入管道，解决了分散链接难以组织、重复校验效率低下、跨平台引用混乱等实际问题。

## 功能概览

**批量链接导入接口** 支持通过 CSV 与 JSON 格式批量提交 URL 列表，自动解析文章 ID 与来源域名，生成内部唯一标识符。

**来源域名自动归类** 系统自动识别资源来源域名，按 map.read.usuhx.com 与 map.mobile.xqnqq.com 等顶层域进行分组，便于按数据源维度检索。

**资源状态健康检查** 内置 HTTP 状态码探测任务，定期检查已收录链接的可访问性，标记失效链接并生成告警日志。

**分层标签管理** 允许为每条资源附加自定义标签，支持按技术领域、文档类型、优先级等维度建立多级标签体系。

**全文元数据提取** 对目标 URL 进行轻量级 HTML 元信息抓取，提取标题、概要描述及发布时间，补充至资源记录中。

**批量导出与备份** 支持将全部资源列表以 JSON Lines 格式导出，便于迁移至其他知识管理工具或进行离线分析。

**操作审计日志** 记录每一次资源新增、删除及状态变更的操作人、时间戳与变更摘要，满足团队协作场景下的追溯需求。

## 应用场景

技术团队内部知识库建设
团队文档管理员可使用 LinkMap 将分散在多个外部站点上的技术参考文章统一收录，配合标签功能按项目或技术栈分类，成员通过检索标签快速定位相关资源，减少重复搜索耗时。

开源项目文档外链整理
开源项目维护者在 README 或官方文档中需要引用大量外部规范与教程。LinkMap 提供批量导入与健康检查能力，帮助维护者一次性整理所有外链，并定期检测失效链接，避免文档中出现死链。

技术资讯周报自动生成
内容编辑人员可将一周内收集到的行业资讯链接通过导入接口批量录入系统，利用元数据提取功能自动补全文章标题与摘要，再通过导出功能生成格式统一的周报素材，降低手动整理成本。

多源数据迁移对照
在进行知识库平台迁移时，LinkMap 可作为中间层工具，将旧系统中的 URL 列表导出为标准化格式，再导入新平台。其导出功能支持增量备份，确保迁移过程中数据不丢失。

## 快速开始

以下指令适用于 Linux 与 macOS 环境，Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/linkmap/linkmap-core.git
cd linkmap-core

# 安装依赖（项目使用 Python 3.10+ 与 pipenv）
pip install pipenv
pipenv install --dev

# 初始化本地数据库（SQLite）
pipenv run python scripts/init_db.py

# 启动开发服务器
pipenv run python manage.py runserver --host 0.0.0.0 --port 8000
```

访问 http://localhost:8000 查看 Web 管理界面。默认管理员账号为 admin，初始密码在首次启动时由 init_db.py 输出至控制台。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10 或更高 | 核心运行环境，低于 3.10 将导致类型注解解析错误 |
| SQLite | 3.35 或更高 | 默认内嵌数据库，支持 JSON 字段存储标签数据 |
| pipenv | 2023.x 或更高 | 依赖管理与虚拟环境隔离工具 |
| requests | 2.31.0 | 用于 HTTP 健康检查与元数据抓取 |
| beautifulsoup4 | 4.12.0 | HTML 解析库，提取页面标题与摘要 |
| pytest | 7.4.0 | 单元测试框架，运行测试套件时使用 |
| gunicorn | 21.2.0 | 生产环境 WSGI 服务器（可选） |
| redis | 6.2 或更高 | 缓存层，用于提升健康检查任务性能（可选） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何快速部署开发环境并导入第一批资源链接 |
| 接口规范 | docs/api-reference.md | 批量导入、导出及状态查询的 RESTful API 端点定义 |
| 运维手册 | docs/operations.md | 生产环境部署、健康检查任务调度及日志轮转配置 |
| 数据模型 | docs/data-model.md | 资源表、标签表与审计日志表的字段定义与关联关系 |
| 贡献规范 | docs/contributing.md | 代码风格、提交信息格式与 Pull Request 流程 |

## 资源列表

- http://map.read.usuhx.com/Article/7684199.shtml
- http://map.read.usuhx.com/Article/467014.shtml
- http://map.mobile.xqnqq.com/Article/27012.shtml
- http://map.mobile.xqnqq.com/Article/4307703.shtml
- http://map.mobile.xqnqq.com/Article/9191741.shtml
- http://map.read.usuhx.com/Article/098307.shtml
- http://map.mobile.xqnqq.com/Article/5922017.shtml
- http://map.read.usuhx.com/Article/69257.shtml
- http://map.mobile.xqnqq.com/Article/755909.shtml
- http://map.mobile.xqnqq.com/Article/4272.shtml
- http://map.mobile.xqnqq.com/Article/2785309.shtml
- http://map.mobile.xqnqq.com/Article/6816.shtml
- http://map.mobile.xqnqq.com/Article/3121537.shtml
- http://map.mobile.xqnqq.com/Article/6709379.shtml
- http://map.mobile.xqnqq.com/Article/28176.shtml
- http://map.mobile.xqnqq.com/Article/73574.shtml
- http://map.mobile.xqnqq.com/Article/7929.shtml
- http://map.read.usuhx.com/Article/08310.shtml
- http://map.read.usuhx.com/Article/8675402.shtml
- http://map.mobile.xqnqq.com/Article/46154.shtml
- http://map.read.usuhx.com/Article/7310570.shtml
- http://map.read.usuhx.com/Article/0151.shtml
- http://map.mobile.xqnqq.com/Article/102112.shtml
- http://map.mobile.xqnqq.com/Article/1571.shtml
- http://map.mobile.xqnqq.com/Article/676914.shtml
- http://map.read.usuhx.com/Article/1794.shtml
- http://map.mobile.xqnqq.com/Article/417314.shtml
- http://map.mobile.xqnqq.com/Article/705285.shtml
- http://map.read.usuhx.com/Article/97546.shtml
- http://map.mobile.xqnqq.com/Article/1735840.shtml
- http://map.mobile.xqnqq.com/Article/4917720.shtml
- http://map.mobile.xqnqq.com/Article/709602.shtml
- http://map.mobile.xqnqq.com/Article/8942615.shtml
- http://map.mobile.xqnqq.com/Article/203286.shtml
- http://map.read.usuhx.com/Article/6414622.shtml
- http://map.read.usuhx.com/Article/99003.shtml
- http://map.read.usuhx.com/Article/0748.shtml
- http://map.read.usuhx.com/Article/989548.shtml
- http://map.read.usuhx.com/Article/398714.shtml
- http://map.mobile.xqnqq.com/Article/0747840.shtml
- http://map.read.usuhx.com/Article/1166.shtml
- http://map.mobile.xqnqq.com/Article/33484.shtml
- http://map.read.usuhx.com/Article/911412.shtml
- http://map.read.usuhx.com/Article/60404.shtml
- http://map.mobile.xqnqq.com/Article/70779.shtml
- http://map.read.usuhx.com/Article/35274.shtml
- http://map.read.usuhx.com/Article/8279714.shtml
- http://map.mobile.xqnqq.com/Article/912690.shtml
- http://map.read.usuhx.com/Article/4080.shtml
- http://map.mobile.xqnqq.com/Article/90941.shtml
- http://map.read.usuhx.com/Article/20655.shtml
- http://map.read.usuhx.com/Article/8642.shtml
- http://map.read.usuhx.com/Article/4532698.shtml
- http://map.read.usuhx.com/Article/4724.shtml
- http://map.mobile.xqnqq.com/Article/667802.shtml
- http://map.mobile.xqnqq.com/Article/3399.shtml
- http://map.read.usuhx.com/Article/647997.shtml
- http://map.read.usuhx.com/Article/3990737.shtml
- http://map.read.usuhx.com/Article/084393.shtml
- http://map.mobile.xqnqq.com/Article/850186.shtml
- http://map.mobile.xqnqq.com/Article/67460.shtml
- http://map.read.usuhx.com/Article/875732.shtml
- http://map.read.usuhx.com/Article/8391.shtml
- http://map.read.usuhx.com/Article/3085.shtml
- http://map.read.usuhx.com/Article/7576.shtml
- http://map.read.usuhx.com/Article/3432848.shtml
- http://map.read.usuhx.com/Article/60425.shtml
- http://map.read.usuhx.com/Article/337738.shtml
- http://map.read.usuhx.com/Article/924784.shtml
- http://map.read.usuhx.com/Article/0320.shtml
- http://map.mobile.xqnqq.com/Article/451103.shtml
- http://map.read.usuhx.com/Article/30534.shtml
- http://map.read.usuhx.com/Article/497524.shtml
- http://map.mobile.xqnqq.com/Article/1210.shtml
- http://map.read.usuhx.com/Article/9653660.shtml
- http://map.read.usuhx.com/Article/4771.shtml
- http://map.mobile.xqnqq.com/Article/575406.shtml
- http://map.read.usuhx.com/Article/846097.shtml
- http://map.mobile.xqnqq.com/Article/36819.shtml
- http://map.read.usuhx.com/Article/344154.shtml
- http://map.read.usuhx.com/Article/204457.shtml
- http://map.read.usuhx.com/Article/852191.shtml
- http://map.read.usuhx.com/Article/4283.shtml
- http://map.read.usuhx.com/Article/2582.shtml
- http://map.read.usuhx.com/Article/12867.shtml
- http://map.mobile.xqnqq.com/Article/36363.shtml
- http://map.read.usuhx.com/Article/699832.shtml
- http://map.read.usuhx.com/Article/0581891.shtml
- http://map.mobile.xqnqq.com/Article/9000.shtml
- http://map.mobile.xqnqq.com/Article/11527.shtml
- http://map.read.usuhx.com/Article/0327239.shtml
- http://map.read.usuhx.com/Article/0760.shtml
- http://map.mobile.xqnqq.com/Article/20722.shtml
- http://map.mobile.xqnqq.com/Article/890341.shtml
- http://map.read.usuhx.com/Article/4290228.shtml
- http://map.read.usuhx.com/Article/0849249.shtml
- http://map.mobile.xqnqq.com/Article/2214.shtml
- http://map.read.usuhx.com/Article/3231693.shtml
- http://map.read.usuhx.com/Article/7727.shtml
- http://map.read.usuhx.com/Article/38297.shtml
- http://map.read.usuhx.com/Article/15138.shtml
- http://map.mobile.xqnqq.com/Article/80156.shtml
- http://map.read.usuhx.com/Article/264044.shtml
- http://map.mobile.xqnqq.com/Article/6143.shtml
- http://map.mobile.xqnqq.com/Article/92234.shtml
- http://map.mobile.xqnqq.com/Article/1969976.shtml
- http://map.mobile.xqnqq.com/Article/6132110.shtml
- http://map.mobile.xqnqq.com/Article/95497.shtml
- http://map.read.usuhx.com/Article/7886755.shtml
- http://map.read.usuhx.com/Article/27388.shtml
- http://map.read.usuhx.com/Article/7147.shtml
- http://map.mobile.xqnqq.com/Article/980230.shtml
- http://map.mobile.xqnqq.com/Article/50605.shtml
- http://map.read.usuhx.com/Article/0346.shtml
- http://map.read.usuhx.com/Article/28316.shtml
- http://map.mobile.xqnqq.com/Article/36907.shtml
- http://map.read.usuhx.com/Article/4959911.shtml
- http://map.mobile.xqnqq.com/Article/4083.shtml
- http://map.read.usuhx.com/Article/19181.shtml
- http://map.read.usuhx.com/Article/367528.shtml
- http://map.mobile.xqnqq.com/Article/0500458.shtml
- http://map.mobile.xqnqq.com/Article/2754.shtml
- http://map.mobile.xqnqq.com/Article/6105718.shtml
- http://map.read.usuhx.com/Article/57213.shtml
- http://map.read.usuhx.com/Article/748975.shtml
- http://map.mobile.xqnqq.com/Article/104570.shtml
- http://map.mobile.xqnqq.com/Article/16272.shtml
- http://map.mobile.xqnqq.com/Article/13516.shtml
- http://map.read.usuhx.com/Article/293565.shtml
- http://map.mobile.xqnqq.com/Article/533957.shtml
- http://map.read.usuhx.com/Article/1637485.shtml
- http://map.read.usuhx.com/Article/6053.shtml
- http://map.mobile.xqnqq.com/Article/6557.shtml
- http://map.mobile.xqnqq.com/Article/595813.shtml
- http://map.read.usuhx.com/Article/3394.shtml
- http://map.mobile.xqnqq.com/Article/015879.shtml
- http://map.read.usuhx.com/Article/9918492.shtml
- http://map.read.usuhx.com/Article/0873675.shtml
- http://map.read.usuhx.com/Article/40439.shtml
- http://map.read.usuhx.com/Article/4156644.shtml
- http://map.mobile.xqnqq.com/Article/5023639.shtml
- http://map.mobile.xqnqq.com/Article/3108.shtml
- http://map.read.usuhx.com/Article/9727109.shtml
- http://map.read.usuhx.com/Article/39701.shtml
- http://map.mobile.xqnqq.com/Article/15757.shtml
- http://map.read.usuhx.com/Article/06928.shtml
- http://map.mobile.xqnqq.com/Article/57815.shtml
- http://map.read.usuhx.com/Article/90361.shtml
- http://map.read.usuhx.com/Article/1913539.shtml
- http://map.mobile.xqnqq.com/Article/2379.shtml
- http://map.read.usuhx.com/Article/46357.shtml
- http://map.mobile.xqnqq.com/Article/15867.shtml
- http://map.mobile.xqnqq.com/Article/170332.shtml
- http://map.read.usuhx.com/Article/132432.shtml
- http://map.mobile.xqnqq.com/Article/7173.shtml
- http://map.mobile.xqnqq.com/Article/564337.shtml
- http://map.mobile.xqnqq.com/Article/248019.shtml
- http://map.read.usuhx.com/Article/70752.shtml
- http://map.mobile.xqnqq.com/Article/916883.shtml
- http://map.mobile.xqnqq.com/Article/013344.shtml
- http://map.read.usuhx.com/Article/50496.shtml
- http://map.mobile.xqnqq.com/Article/4253.shtml
- http://map.read.usuhx.com/Article/3214201.shtml
- http://map.read.usuhx.com/Article/93612.shtml
- http://map.read.usuhx.com/Article/021937.shtml
- http://map.mobile.xqnqq.com/Article/077552.shtml
- http://map.mobile.xqnqq.com/Article/3702152.shtml
- http://map.mobile.xqnqq.com/Article/847214.shtml
- http://map.read.usuhx.com/Article/81506.shtml
- http://map.read.usuhx.com/Article/45754.shtml
- http://map.mobile.xqnqq.com/Article/622812.shtml
- http://map.mobile.xqnqq.com/Article/5294209.shtml
- http://map.read.usuhx.com/Article/1799838.shtml
- http://map.read.usuhx.com/Article/0310874.shtml
- http://map.mobile.xqnqq.com/Article/3015078.shtml
- http://map.mobile.xqnqq.com/Article/4966877.shtml
- http://map.mobile.xqnqq.com/Article/6224030.shtml
- http://map.mobile.xqnqq.com/Article/9772.shtml
- http://map.read.usuhx.com/Article/8538847.shtml
- http://map.mobile.xqnqq.com/Article/268025.shtml
- http://map.read.usuhx.com/Article/8342934.shtml
- http://map.read.usuhx.com/Article/22617.shtml
- http://map.mobile.xqnqq.com/Article/34658.shtml
- http://map.mobile.xqnqq.com/Article/9199.shtml
- http://map.mobile.xqnqq.com/Article/2580.shtml
- http://map.mobile.xqnqq.com/Article/5125753.shtml
- http://map.read.usuhx.com/Article/9890.shtml
- http://map.mobile.xqnqq.com/Article/4379.shtml
- http://map.read.usuhx.com/Article/6224201.shtml
- http://map.mobile.xqnqq.com/Article/0799446.shtml
- http://map.read.usuhx.com/Article/9086493.shtml
- http://map.mobile.xqnqq.com/Article/1557.shtml
- http://map.mobile.xqnqq.com/Article/8754.shtml
- http://map.read.usuhx.com/Article/45468.shtml
- http://map.read.usuhx.com/Article/817189.shtml
- http://map.mobile.xqnqq.com/Article/6297.shtml
- http://map.mobile.xqnqq.com/Article/001505.shtml
- http://map.mobile.xqnqq.com/Article/9651951.shtml
- http://map.mobile.xqnqq.com/Article/6037984.shtml
- http://map.read.usuhx.com/Article/539116.shtml
- http://map.read.usuhx.com/Article/77737.shtml
- http://map.read.usuhx.com/Article/0011.shtml
- http://map.read.usuhx.com/Article/3847.shtml
- http://map.mobile.xqnqq.com/Article/050923.shtml
- http://map.mobile.xqnqq.com/Article/01052.shtml
- http://map.read.usuhx.com/Article/104170.shtml
- http://map.read.usuhx.com/Article/01522.shtml
- http://map.mobile.xqnqq.com/Article/21186.shtml
- http://map.read.usuhx.com/Article/3603022.shtml
- http://map.mobile.xqnqq.com/Article/6241.shtml
- http://map.read.usuhx.com/Article/5848.shtml
- http://map.mobile.xqnqq.com/Article/1643155.shtml
- http://map.mobile.xqnqq.com/Article/17345.shtml
- http://map.read.usuhx.com/Article/6473599.shtml
- http://map.mobile.xqnqq.com/Article/9061.shtml
- http://map.mobile.xqnqq.com/Article/1788.shtml
- http://map.mobile.xqnqq.com/Article/59757.shtml
- http://map.mobile.xqnqq.com/Article/377203.shtml
- http://map.mobile.xqnqq.com/Article/2793.shtml
- http://map.read.usuhx.com/Article/99354.shtml
- http://map.mobile.xqnqq.com/Article/5689104.shtml
- http://map.mobile.xqnqq.com/Article/0914944.shtml
- http://map.mobile.xqnqq.com/Article/721272.shtml
- http://map.mobile.xqnqq.com/Article/5859046.shtml
- http://map.read.usuhx.com/Article/981647.shtml
- http://map.mobile.xqnqq.com/Article/0418000.shtml
- http://map.read.usuhx.com/Article/410834.shtml
- http://map.mobile.xqnqq.com/Article/74707.shtml
- http://map.mobile.xqnqq.com/Article/81285.shtml
- http://map.mobile.xqnqq.com/Article/25753.shtml
- http://map.mobile.xqnqq.com/Article/1770.shtml
- http://map.mobile.xqnqq.com/Article/392216.shtml
- http://map.mobile.xqnqq.com/Article/00327.shtml
- http://map.mobile.xqnqq.com/Article/467073.shtml
- http://map.mobile.xqnqq.com/Article/41817.shtml
- http://map.mobile.xqnqq.com/Article/603137.shtml
- http://map.read.usuhx.com/Article/1196.shtml
- http://map.mobile.xqnqq.com/Article/6999536.shtml
- http://map.read.usuhx.com/Article/597896.shtml
- http://map.mobile.xqnqq.com/Article/78288.shtml
- http://map.read.usuhx.com/Article/3830280.shtml
- http://map.mobile.xqnqq.com/Article/6343597.shtml
- http://map.read.usuhx.com/Article/0345541.shtml
- http://map.mobile.xqnqq.com/Article/6259674.shtml
- http://map.mobile.xqnqq.com/Article/213335.shtml
- http://map.mobile.xqnqq.com/Article/7236809.shtml
- http://map.mobile.xqnqq.com/Article/9185903.shtml
- http://map.mobile.xqnqq.com/Article/6136709.shtml
- http://map.mobile.xqnqq.com/Article/4676344.shtml
- http://map.read.usuhx.com/Article/844226.shtml

## 项目结构

```
linkmap-core/
├── src/                                 # 核心源代码目录
│   ├── adapters/                        # 外部数据源适配器
│   │   ├── http_client.py               # 异步 HTTP 请求封装，含重试与超时策略
│   │   └── parser.py                    # HTML 元信息解析器，基于 BeautifulSoup
│   ├── models/                          # 数据模型与 ORM 映射
│   │   ├── resource.py                  # Resource 表定义，包含 URL、状态、时间戳字段
│   │   ├── tag.py                       # 标签模型，支持多对多关联
│   │   └── audit_log.py                 # 审计日志模型，记录操作历史
│   ├── services/                        # 业务逻辑层
│   │   ├── importer.py                  # 批量导入服务，支持 CSV/JSON 格式校验
│   │   ├── health_checker.py            # 链接健康检查调度器，使用 requests 探测状态
│   │   └── exporter.py                  # 导出服务，生成 JSON Lines 格式输出
│   ├── api/                             # RESTful API 路由与控制器
│   │   ├── routes.py                    # 路由注册与蓝本定义
│   │   └── validators.py                # 请求参数校验器，使用 Pydantic 模型
│   └── utils/                           # 通用工具函数
│       ├── logger.py                    # 日志配置，支持文件轮转与结构化输出
│       └── id_generator.py              # 基于时间戳与随机数的唯一 ID 生成器
├── tests/                               # 单元测试与集成测试
│   ├── test_importer.py                 # 导入服务测试用例，覆盖正常与异常路径
│   ├── test_health_checker.py           # 健康检查任务模拟测试
│   └── conftest.py                      # pytest 共享夹具与数据库测试配置
├── scripts/                             # 运维与辅助脚本
│   ├── init_db.py                       # 初始化 SQLite 数据库表结构及默认账户
│   ├── seed_demo_data.py                # 填充演示数据用于开发调试
│   └── run_health_check.py              # 手动触发健康检查的命令行脚本
├── config/                              # 配置文件目录
│   ├── development.toml                 # 开发环境配置，开启调试与详细日志
│   ├── production.toml                  # 生产环境配置，使用 gunicorn 与 redis 缓存
│   └── logging.conf                     # 日志格式与输出级别配置
├── docs/                                # 项目文档
│   ├── getting-started.md               # 快速入门指南
│   ├── api-reference.md                 # 完整 API 端点文档与示例
│   └── operations.md                    # 部署与运维手册
├── requirements.txt                     # 生产环境依赖列表（pip 格式）
├── requirements-dev.txt                 # 开发环境额外依赖（测试、代码检查工具）
├── manage.py                            # 项目管理入口（启动、迁移、命令行工具）
├── pyproject.toml                       # 项目元数据与构建配置
└── README.md                            # 项目说明文档（本文件）
```

## 贡献指南

1. 阅读项目行为准则与贡献规范文档 docs/contributing.md，确认遵守代码风格要求（PEP 8 与 Google Python Style Guide 子集）。
2. 从 GitHub 仓库 Fork 项目至个人账号，克隆 Fork 后的仓库，并在本地创建功能分支，分支命名格式为 feature/简短描述或 fix/问题编号。
3. 编写代码时同步补充单元测试，新增功能或修复缺陷均需提供对应测试用例，确保 pytest 套件通过率为 100%。
4. 提交代码前运行代码检查工具，执行 make lint 命令（包含 flake8、black 与 mypy 检查），修复所有报错与警告。
5. 提交 Pull Request 至主仓库的 develop 分支，在 PR 描述中关联对应 Issue 编号，并附上测试结果截图或日志。

## 常见问题

Q: 导入大量 URL 时是否会阻塞 Web 界面响应？

A: 导入服务设计为异步后台任务模式。调用批量导入接口后，系统立即返回任务 ID，实际解析与入库操作在独立工作线程中执行。用户可通过 /api/task/{task_id}/status 端点轮询导入进度。默认 SQLite 配置下，单次导入 1000 条以内链接不会对界面操作产生可感知的延迟。

Q: 健康检查任务如何判定链接失效？

A: 健康检查器遵循以下判定规则：若 HTTP 响应状态码在 200 至 299 之间视为有效；状态码 301 或 302 会跟随重定向最多 3 次，最终状态码有效则判定为可访问；连接超时（默认 5 秒）或 SSL 证书错误均判定为失效。失效链接将在 Web 管理界面的资源列表中标记红色状态标识，并写入日志文件供后续分析。

Q: 如何将数据从开发环境迁移至生产环境？

A: 使用内置导出功能生成 JSON Lines 格式的完整资源快照，在生产环境执行导入接口完成数据恢复。如需迁移标签与审计日志，需在导出时附加 --include-metadata 参数。不推荐直接复制 SQLite 数据库文件，因开发环境与生产环境可能使用不同数据库引擎（SQLite 与 PostgreSQL）。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
