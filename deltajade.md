# LinkBridge 技术资源聚合导航

LinkBridge 是一个面向技术研究、内容聚合与知识管理场景的开源外链资源导航系统。该项目定位于帮助技术团队、内容运营者、研究人员以及个人开发者高效组织、分类和检索散落在互联网各处的文章链接与技术文档。LinkBridge 不生产内容，而是提供一套轻量级、可自托管的链接管理框架，支持批量导入、标签分类、全文元数据抓取与多维度检索，解决技术资料分散、收藏夹混乱、链接失效不可追溯等常见痛点。

LinkBridge 适用于需要长期维护技术知识库、团队共享阅读清单、或对特定领域（如开源软件、移动开发、系统运维）进行持续信息追踪的用户。项目以纯静态前端结合轻量后端服务的方式交付，支持 Docker 一键部署，也提供 Python 源码直接运行模式，便于二次开发和定制扩展。

## 功能概览

**批量链接导入与解析** 支持从纯文本、CSV 或 JSON 文件批量导入链接列表，自动识别 URL 并提取标题、域名、状态码等基础元数据。

**自定义标签与分类体系** 允许用户创建多级分类标签，对链接进行灵活标注，支持一链接多标签，便于交叉检索。

**全文检索与过滤** 基于链接标题、描述、标签、域名等字段提供实时搜索，支持按状态码、文件类型、收录时间等多条件组合过滤。

**链接健康状态监测** 定时检测已收录链接的可访问性，标记失效链接并记录响应时间变化，辅助清理死链。

**快照与摘要存储** 支持为每个链接保存手动编写的摘要或自动抓取的页面描述，形成本地化的知识摘要库，防止原文下线后信息丢失。

**数据导入导出与迁移** 提供标准化的 JSON 和 Markdown 表格格式导出，支持在不同部署实例之间迁移数据，也便于备份和版本管理。

## 应用场景

技术团队内部知识库维护 技术负责人或架构师可以使用 LinkBridge 收集团队推荐的博客文章、官方文档、API 参考和最佳实践案例，通过共享分类体系让新成员快速了解团队技术栈和常用工具链，减少重复答疑成本。

个人开发者的阅读清单管理 日常浏览技术社区时会产生大量待读或值得收藏的链接，LinkBridge 提供简洁的收录界面和标签系统，帮助开发者按学习主题（如 Rust 异步编程、Kubernetes 网络插件）组织资料，避免浏览器收藏夹杂乱无章。

开源项目文档外链聚合 开源项目维护者可以在项目仓库中集成 LinkBridge 实例，集中管理外部参考链接、社区教程、视频演讲和相关项目地址，为社区贡献者提供便捷的导航入口，降低参与门槛。

技术调研与竞品分析 产品经理或技术调研人员在进行技术选型或竞品分析时，需要长期追踪大量新闻稿、产品公告、技术评测和用户反馈，LinkBridge 的标签过滤和健康监测功能可以辅助筛选有效信息源，提高调研效率。

## 快速开始

以下指令适用于 Linux / macOS 环境，Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/linkbridge.git
cd linkbridge

# 安装 Python 依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化 SQLite 数据库并创建默认配置
python manage.py initdb
python manage.py migrate

# 启动开发服务器（默认监听 127.0.0.1:8000）
python manage.py runserver
```

访问 http://127.0.0.1:8000 即可进入 LinkBridge 主界面。生产环境部署建议使用 Gunicorn + Nginx 组合，或参考 `deploy/` 目录下的 Docker Compose 示例。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
| :--- | :--- | :--- |
| Python | 3.9 及以上 | 核心运行环境，推荐使用 3.11 或 3.12 以获得更好性能 |
| SQLite | 3.35 及以上 | 默认数据库，支持 JSON 字段存储标签和元数据，无需额外安装 |
| pip | 22.0 及以上 | Python 包管理工具，用于安装 requirements.txt 中的依赖 |
| requests | 2.31.0 及以上 | 用于链接健康检测和元数据抓取，支持 HTTP/HTTPS 代理配置 |
| beautifulsoup4 | 4.12.0 及以上 | HTML 解析库，用于提取页面标题和描述信息，可选的增强功能 |
| gunicorn | 21.2.0 及以上 | 生产环境 WSGI 服务器，仅在生产部署时需要 |
| nodejs | 18.x 及以上 | 仅当需要构建前端静态资源时必需，使用预构建包可跳过 |
| npm | 9.x 及以上 | 配合 nodejs 管理前端构建工具，非必需场景可不安装 |
| Docker | 20.10 及以上 | 可选，使用容器化部署时需要，提供一致的运行环境 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
| :--- | :--- | :--- |
| 用户手册 | `docs/user/` | 如何添加链接、如何创建标签、如何检索已收藏的内容、如何导出数据备份 |
| 部署指南 | `docs/deployment/` | 如何安装系统依赖、配置环境变量、使用 Docker 或 systemd 实现开机自启 |
| 开发指南 | `docs/development/` | 项目代码组织结构、API 接口设计规范、前端组件开发流程、如何提交补丁 |
| 架构设计 | `docs/architecture/` | 系统模块划分、数据库表结构设计、缓存策略、扩展点设计以及性能调优建议 |
| 运维手册 | `docs/operations/` | 日志管理、数据备份恢复、链接健康检查任务的调度配置、升级回滚步骤 |
| 常见问题 | `docs/faq/` | 收录链接失效怎么办、如何迁移数据库、搜索功能为什么返回空结果 |

## 资源列表

- http://www.read.usuhx.com/Article/2049861.shtml
- http://www.mobile.xqnqq.com/Article/6755106.shtml
- http://www.read.usuhx.com/Article/56448.shtml
- http://www.mobile.xqnqq.com/Article/6026.shtml
- http://www.mobile.xqnqq.com/Article/102030.shtml
- http://www.read.usuhx.com/Article/1378.shtml
- http://www.mobile.xqnqq.com/Article/3041604.shtml
- http://www.read.usuhx.com/Article/2531675.shtml
- http://www.mobile.xqnqq.com/Article/6854053.shtml
- http://www.read.usuhx.com/Article/0029263.shtml
- http://www.read.usuhx.com/Article/0127952.shtml
- http://www.mobile.xqnqq.com/Article/26961.shtml
- http://www.read.usuhx.com/Article/76409.shtml
- http://www.mobile.xqnqq.com/Article/13404.shtml
- http://www.mobile.xqnqq.com/Article/15737.shtml
- http://www.mobile.xqnqq.com/Article/48597.shtml
- http://www.mobile.xqnqq.com/Article/4463283.shtml
- http://www.mobile.xqnqq.com/Article/920654.shtml
- http://www.mobile.xqnqq.com/Article/9377786.shtml
- http://www.mobile.xqnqq.com/Article/744284.shtml
- http://www.mobile.xqnqq.com/Article/543915.shtml
- http://www.read.usuhx.com/Article/7544433.shtml
- http://www.read.usuhx.com/Article/435956.shtml
- http://www.read.usuhx.com/Article/786493.shtml
- http://www.mobile.xqnqq.com/Article/330959.shtml
- http://www.mobile.xqnqq.com/Article/8447.shtml
- http://www.read.usuhx.com/Article/1431.shtml
- http://www.read.usuhx.com/Article/4818.shtml
- http://www.mobile.xqnqq.com/Article/81561.shtml
- http://www.mobile.xqnqq.com/Article/5939846.shtml
- http://www.mobile.xqnqq.com/Article/38863.shtml
- http://www.read.usuhx.com/Article/57348.shtml
- http://www.mobile.xqnqq.com/Article/0689433.shtml
- http://www.read.usuhx.com/Article/39559.shtml
- http://www.mobile.xqnqq.com/Article/4363.shtml
- http://www.mobile.xqnqq.com/Article/884174.shtml
- http://www.read.usuhx.com/Article/987977.shtml
- http://www.mobile.xqnqq.com/Article/9581287.shtml
- http://www.mobile.xqnqq.com/Article/0824499.shtml
- http://www.mobile.xqnqq.com/Article/8654137.shtml
- http://www.read.usuhx.com/Article/759351.shtml
- http://www.read.usuhx.com/Article/7661445.shtml
- http://www.read.usuhx.com/Article/01418.shtml
- http://www.mobile.xqnqq.com/Article/2843228.shtml
- http://www.read.usuhx.com/Article/8175.shtml
- http://www.mobile.xqnqq.com/Article/5257131.shtml
- http://www.mobile.xqnqq.com/Article/58426.shtml
- http://www.read.usuhx.com/Article/159003.shtml
- http://www.read.usuhx.com/Article/78182.shtml
- http://www.read.usuhx.com/Article/1926119.shtml
- http://www.mobile.xqnqq.com/Article/1005.shtml
- http://www.mobile.xqnqq.com/Article/59846.shtml
- http://www.mobile.xqnqq.com/Article/0656.shtml
- http://www.mobile.xqnqq.com/Article/8105.shtml
- http://www.read.usuhx.com/Article/037590.shtml
- http://www.mobile.xqnqq.com/Article/9684166.shtml
- http://www.mobile.xqnqq.com/Article/289563.shtml
- http://www.read.usuhx.com/Article/2756.shtml
- http://www.mobile.xqnqq.com/Article/74534.shtml
- http://www.read.usuhx.com/Article/99170.shtml
- http://www.mobile.xqnqq.com/Article/715923.shtml
- http://www.read.usuhx.com/Article/4268728.shtml
- http://www.read.usuhx.com/Article/97375.shtml
- http://www.read.usuhx.com/Article/15931.shtml
- http://www.mobile.xqnqq.com/Article/656523.shtml
- http://www.mobile.xqnqq.com/Article/83130.shtml
- http://www.read.usuhx.com/Article/9406.shtml
- http://www.read.usuhx.com/Article/665295.shtml
- http://www.read.usuhx.com/Article/3938.shtml
- http://www.mobile.xqnqq.com/Article/5975983.shtml
- http://www.read.usuhx.com/Article/5175889.shtml
- http://www.mobile.xqnqq.com/Article/6885836.shtml
- http://www.read.usuhx.com/Article/39933.shtml
- http://www.read.usuhx.com/Article/174490.shtml
- http://www.read.usuhx.com/Article/5771.shtml
- http://www.read.usuhx.com/Article/08554.shtml
- http://www.mobile.xqnqq.com/Article/8158.shtml
- http://www.mobile.xqnqq.com/Article/94539.shtml
- http://www.read.usuhx.com/Article/2134460.shtml
- http://www.mobile.xqnqq.com/Article/873515.shtml
- http://www.mobile.xqnqq.com/Article/7459.shtml
- http://www.mobile.xqnqq.com/Article/38275.shtml
- http://www.read.usuhx.com/Article/5009323.shtml
- http://www.read.usuhx.com/Article/526088.shtml
- http://www.read.usuhx.com/Article/4182498.shtml
- http://www.mobile.xqnqq.com/Article/309882.shtml
- http://www.read.usuhx.com/Article/90434.shtml
- http://www.read.usuhx.com/Article/291933.shtml
- http://www.mobile.xqnqq.com/Article/1333788.shtml
- http://www.mobile.xqnqq.com/Article/340167.shtml
- http://www.mobile.xqnqq.com/Article/2302935.shtml
- http://www.read.usuhx.com/Article/44692.shtml
- http://www.read.usuhx.com/Article/0596445.shtml
- http://www.read.usuhx.com/Article/494036.shtml
- http://www.mobile.xqnqq.com/Article/2691946.shtml
- http://www.read.usuhx.com/Article/1157868.shtml
- http://www.mobile.xqnqq.com/Article/38505.shtml
- http://www.read.usuhx.com/Article/8744632.shtml
- http://www.mobile.xqnqq.com/Article/4056278.shtml
- http://www.mobile.xqnqq.com/Article/469011.shtml
- http://www.read.usuhx.com/Article/31873.shtml
- http://www.read.usuhx.com/Article/49583.shtml
- http://www.mobile.xqnqq.com/Article/5050018.shtml
- http://www.mobile.xqnqq.com/Article/3265569.shtml
- http://www.read.usuhx.com/Article/200276.shtml
- http://www.mobile.xqnqq.com/Article/85016.shtml
- http://www.read.usuhx.com/Article/82089.shtml
- http://www.read.usuhx.com/Article/67221.shtml
- http://www.read.usuhx.com/Article/22814.shtml
- http://www.mobile.xqnqq.com/Article/42908.shtml
- http://www.mobile.xqnqq.com/Article/6938966.shtml
- http://www.mobile.xqnqq.com/Article/2213.shtml
- http://www.mobile.xqnqq.com/Article/33504.shtml
- http://www.read.usuhx.com/Article/575554.shtml
- http://www.mobile.xqnqq.com/Article/0670388.shtml
- http://www.read.usuhx.com/Article/881800.shtml
- http://www.mobile.xqnqq.com/Article/0209603.shtml
- http://www.read.usuhx.com/Article/5876271.shtml
- http://www.mobile.xqnqq.com/Article/3424.shtml
- http://www.read.usuhx.com/Article/4079.shtml
- http://www.read.usuhx.com/Article/84522.shtml
- http://www.read.usuhx.com/Article/9986429.shtml
- http://www.read.usuhx.com/Article/9149243.shtml
- http://www.mobile.xqnqq.com/Article/784511.shtml
- http://www.read.usuhx.com/Article/508052.shtml
- http://www.read.usuhx.com/Article/5348666.shtml
- http://www.read.usuhx.com/Article/1855.shtml
- http://www.mobile.xqnqq.com/Article/71639.shtml
- http://www.read.usuhx.com/Article/15759.shtml
- http://www.read.usuhx.com/Article/11699.shtml
- http://www.read.usuhx.com/Article/7915377.shtml
- http://www.mobile.xqnqq.com/Article/365302.shtml
- http://www.read.usuhx.com/Article/8690233.shtml
- http://www.mobile.xqnqq.com/Article/83730.shtml
- http://www.mobile.xqnqq.com/Article/8739.shtml
- http://www.mobile.xqnqq.com/Article/960533.shtml
- http://www.mobile.xqnqq.com/Article/5796267.shtml
- http://www.read.usuhx.com/Article/287086.shtml
- http://www.read.usuhx.com/Article/6746821.shtml
- http://www.mobile.xqnqq.com/Article/5649321.shtml
- http://www.read.usuhx.com/Article/531390.shtml
- http://www.read.usuhx.com/Article/92198.shtml
- http://www.mobile.xqnqq.com/Article/028902.shtml
- http://www.mobile.xqnqq.com/Article/087743.shtml
- http://www.read.usuhx.com/Article/6297.shtml
- http://www.mobile.xqnqq.com/Article/033900.shtml
- http://www.mobile.xqnqq.com/Article/99566.shtml
- http://www.read.usuhx.com/Article/0961.shtml
- http://www.mobile.xqnqq.com/Article/0694.shtml
- http://www.read.usuhx.com/Article/1339941.shtml
- http://www.mobile.xqnqq.com/Article/446205.shtml
- http://www.read.usuhx.com/Article/0748980.shtml
- http://www.mobile.xqnqq.com/Article/8076.shtml
- http://www.mobile.xqnqq.com/Article/395202.shtml
- http://www.mobile.xqnqq.com/Article/17089.shtml
- http://www.read.usuhx.com/Article/268347.shtml
- http://www.mobile.xqnqq.com/Article/0338883.shtml
- http://www.read.usuhx.com/Article/6752.shtml
- http://www.mobile.xqnqq.com/Article/61943.shtml
- http://www.read.usuhx.com/Article/5583931.shtml
- http://www.mobile.xqnqq.com/Article/20898.shtml
- http://www.mobile.xqnqq.com/Article/4465328.shtml
- http://www.read.usuhx.com/Article/261260.shtml
- http://www.read.usuhx.com/Article/85603.shtml
- http://www.mobile.xqnqq.com/Article/1704155.shtml
- http://www.mobile.xqnqq.com/Article/43273.shtml
- http://www.mobile.xqnqq.com/Article/5873772.shtml
- http://www.mobile.xqnqq.com/Article/301902.shtml
- http://www.mobile.xqnqq.com/Article/6207419.shtml
- http://www.read.usuhx.com/Article/0291934.shtml
- http://www.mobile.xqnqq.com/Article/577163.shtml
- http://www.mobile.xqnqq.com/Article/55218.shtml
- http://www.mobile.xqnqq.com/Article/74578.shtml
- http://www.mobile.xqnqq.com/Article/2698.shtml
- http://www.read.usuhx.com/Article/498436.shtml
- http://www.mobile.xqnqq.com/Article/974588.shtml
- http://www.mobile.xqnqq.com/Article/64405.shtml
- http://www.read.usuhx.com/Article/722518.shtml
- http://www.read.usuhx.com/Article/09242.shtml
- http://www.mobile.xqnqq.com/Article/4370.shtml
- http://www.mobile.xqnqq.com/Article/3959.shtml
- http://www.mobile.xqnqq.com/Article/584249.shtml
- http://www.read.usuhx.com/Article/806952.shtml
- http://www.mobile.xqnqq.com/Article/1680.shtml
- http://www.read.usuhx.com/Article/26463.shtml
- http://www.read.usuhx.com/Article/27091.shtml
- http://www.read.usuhx.com/Article/681010.shtml
- http://www.mobile.xqnqq.com/Article/3629.shtml
- http://www.mobile.xqnqq.com/Article/552346.shtml
- http://www.mobile.xqnqq.com/Article/587634.shtml
- http://www.mobile.xqnqq.com/Article/773882.shtml
- http://www.mobile.xqnqq.com/Article/927498.shtml
- http://www.mobile.xqnqq.com/Article/738170.shtml
- http://www.mobile.xqnqq.com/Article/191937.shtml
- http://www.mobile.xqnqq.com/Article/0477.shtml
- http://www.read.usuhx.com/Article/8074.shtml
- http://www.mobile.xqnqq.com/Article/113542.shtml
- http://www.mobile.xqnqq.com/Article/443195.shtml
- http://www.mobile.xqnqq.com/Article/289021.shtml
- http://www.mobile.xqnqq.com/Article/5095989.shtml
- http://www.read.usuhx.com/Article/8827545.shtml
- http://www.read.usuhx.com/Article/23883.shtml
- http://www.mobile.xqnqq.com/Article/35779.shtml
- http://www.read.usuhx.com/Article/5385.shtml
- http://www.mobile.xqnqq.com/Article/3180.shtml
- http://www.mobile.xqnqq.com/Article/063379.shtml
- http://www.mobile.xqnqq.com/Article/66316.shtml
- http://www.read.usuhx.com/Article/4386492.shtml
- http://www.read.usuhx.com/Article/0643.shtml
- http://www.mobile.xqnqq.com/Article/7599163.shtml
- http://www.mobile.xqnqq.com/Article/488090.shtml
- http://www.mobile.xqnqq.com/Article/5933423.shtml
- http://www.mobile.xqnqq.com/Article/644975.shtml
- http://www.read.usuhx.com/Article/38281.shtml
- http://www.read.usuhx.com/Article/92731.shtml
- http://www.read.usuhx.com/Article/55483.shtml
- http://www.mobile.xqnqq.com/Article/5859419.shtml
- http://www.read.usuhx.com/Article/16364.shtml
- http://www.mobile.xqnqq.com/Article/5166824.shtml
- http://www.mobile.xqnqq.com/Article/928663.shtml
- http://www.mobile.xqnqq.com/Article/622964.shtml
- http://www.mobile.xqnqq.com/Article/041043.shtml
- http://www.read.usuhx.com/Article/72584.shtml
- http://www.read.usuhx.com/Article/46751.shtml
- http://www.mobile.xqnqq.com/Article/35106.shtml
- http://www.mobile.xqnqq.com/Article/3396.shtml
- http://www.mobile.xqnqq.com/Article/7973.shtml
- http://www.mobile.xqnqq.com/Article/82744.shtml
- http://www.read.usuhx.com/Article/9416.shtml
- http://www.mobile.xqnqq.com/Article/5994296.shtml
- http://www.mobile.xqnqq.com/Article/3460020.shtml
- http://www.mobile.xqnqq.com/Article/14535.shtml
- http://www.mobile.xqnqq.com/Article/96615.shtml
- http://www.mobile.xqnqq.com/Article/26478.shtml
- http://www.mobile.xqnqq.com/Article/2644.shtml
- http://www.mobile.xqnqq.com/Article/545760.shtml
- http://www.read.usuhx.com/Article/9605399.shtml
- http://www.mobile.xqnqq.com/Article/21753.shtml
- http://www.read.usuhx.com/Article/74886.shtml
- http://www.mobile.xqnqq.com/Article/76570.shtml
- http://www.read.usuhx.com/Article/0905.shtml
- http://www.read.usuhx.com/Article/3787.shtml
- http://www.read.usuhx.com/Article/6271.shtml
- http://www.mobile.xqnqq.com/Article/68386.shtml
- http://www.read.usuhx.com/Article/5397.shtml
- http://www.read.usuhx.com/Article/311815.shtml
- http://www.read.usuhx.com/Article/2195.shtml
- http://www.read.usuhx.com/Article/9185510.shtml
- http://www.mobile.xqnqq.com/Article/47105.shtml
- http://www.read.usuhx.com/Article/8935.shtml

## 项目结构

```
linkbridge/
├── backend/                          # 后端 Python 服务核心代码
│   ├── api/                          # RESTful API 路由与视图函数
│   │   ├── routes/                   # 按资源类型划分的路由模块（link, tag, health）
│   │   └── schemas/                  # Pydantic 模型定义，用于请求与响应数据校验
│   ├── core/                         # 核心业务逻辑层
│   │   ├── crawler/                  # 链接元数据抓取与健康检查引擎
│   │   ├── indexer/                  # 全文索引构建与检索实现（基于 SQLite FTS5）
│   │   └── manager/                  # 链接生命周期管理（增删改查、标签关联）
│   ├── models/                       # SQLAlchemy ORM 实体定义
│   │   ├── link.py                   # Link 表结构，含 URL、标题、摘要、状态码等字段
│   │   ├── tag.py                    # Tag 表结构，支持树形分类
│   │   └── snapshot.py               # 快照表，存储历史抓取记录
│   ├── utils/                        # 通用工具函数
│   │   ├── http.py                   # 自定义 HTTP 客户端封装，含超时与重试策略
│   │   ├── parser.py                 # HTML 解析辅助函数，基于 BeautifulSoup
│   │   └── validators.py             # URL 校验与规范化工具
│   └── config.py                     # 配置管理模块，支持环境变量与 .env 文件
├── frontend/                         # 前端静态资源（Vue 3 + Vite）
│   ├── src/
│   │   ├── components/               # 可复用 UI 组件（导航栏、链接卡片、搜索框）
│   │   ├── views/                    # 页面级组件（首页、分类页、详情页、导入页）
│   │   ├── stores/                   # Pinia 状态管理（链接列表、标签树、搜索状态）
│   │   └── assets/                   # 样式文件与静态图片资源
│   └── dist/                         # 构建输出目录，部署时由后端提供静态服务
├── deploy/                           # 部署相关配置文件
│   ├── docker/                       # Dockerfile 与 docker-compose.yml 示例
│   ├── nginx/                        # Nginx 反向代理配置模板
│   └── systemd/                      # systemd 服务单元文件，用于开机自启
├── scripts/                          # 运维与开发辅助脚本
│   ├── import_demo_links.py          # 批量导入示例数据脚本
│   ├── export_backup.py              # 数据导出备份脚本
│   └── health_check_runner.py        # 定时健康检查任务触发器
├── tests/                            # 单元测试与集成测试
│   ├── unit/                         # 针对核心模块的细粒度测试用例
│   └── integration/                  # API 端到端测试，模拟真实 HTTP 请求
├── docs/                             # 项目文档（详见文档导航章节）
├── requirements.txt                  # 生产环境 Python 依赖锁定清单
├── requirements-dev.txt              # 开发环境额外依赖（测试、代码检查、构建工具）
├── manage.py                         # 项目统一管理命令行入口
├── .env.example                      # 环境变量配置模板
├── .gitignore                        # Git 忽略文件规则
└── README.md                         # 本文件
```

## 贡献指南

贡献者请遵循以下流程以确保代码质量和项目一致性。

1. 查阅问题追踪列表 访问 GitHub Issues 页面，查找标记为 `help wanted` 或 `good first issue` 的任务，避免与其他贡献者重复工作。对于较大的功能提案，建议先创建讨论议题征求维护者意见。

2. 派生仓库并创建功能分支 从主仓库派生副本到个人账户，然后克隆本地。创建分支时使用 `feature/` 或 `fix/` 前缀，例如 `feature/add-import-csv-support`，确保分支名称简洁描述变更内容。

3. 编写代码并添加测试 所有新功能必须包含对应的单元测试，修复缺陷时也建议补充回归测试用例。代码风格遵循 PEP 8 规范，提交前运行 `make lint` 和 `make test` 确保无检查项失败。

4. 提交变更并签署开发者原创声明 提交信息使用约定式提交格式（如 `feat: 增加批量导入CSV功能` 或 `fix: 修复标签删除时未解除关联的缺陷`）。提交时需通过 `git commit -s` 添加 Signed-off-by 行，表示同意开发者原创声明。

5. 发起拉取请求 推送分支到派生仓库后，向主仓库的 `main` 分支发起 Pull Request。描述中需引用相关 Issue 编号，并详细说明变更内容、测试结果以及可能的兼容性影响。等待维护者审核，期间可能需要根据反馈进行修改。

## 常见问题

问：LinkBridge 是否支持 HTTPS 访问和自定义域名？

答：LinkBridge 后端本身不处理 TLS 终结，推荐将服务部署在 Nginx 或 Caddy 等反向代理之后，由代理层处理 HTTPS 证书配置。项目在 `deploy/nginx/` 目录下提供了参考配置模板，用户只需修改 `server_name` 和 `proxy_pass` 目标地址即可启用自定义域名和 HTTPS。

问：收录的链接如果失效了，系统会如何处理？

答：系统默认每小时执行一次后台健康检查任务，对状态码为 200 或 30x 的链接标记为正常，对其他状态码或超时链接标记为异常。用户可以在链接列表界面按状态过滤，手动确认后删除或更新失效链接。同时，系统会保留每次检查的历史记录，便于追溯链接状态变化趋势。

问：是否可以将 LinkBridge 的数据迁移到其他系统，如 WordPress 或 Notion？

答：LinkBridge 提供 JSON 和 Markdown 表格两种导出格式。JSON 格式包含完整的元数据、标签关联和时间戳，适合程序化导入其他支持 JSON 的系统。Markdown 表格格式则适合人工复制粘贴到 Notion 或飞书文档中。如果需要迁移到 WordPress，可以使用内置的导出脚本生成 RSS 或 CSV 格式，再通过 WordPress 的导入插件完成迁移。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
