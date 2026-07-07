# LinkMap 技术资源导航

LinkMap 是一个面向开发者、技术研究人员与内容策展人的轻量级外链资源汇总平台。该项目专注于将分散于多个内容源的技术文章、数据快照与信息页面进行结构化收录，并提供统一的访问入口与基础检索能力。LinkMap 本身不存储任何正文内容，仅保留原始 URL 的索引信息与分类标签，适用于个人知识库补充、团队技术栈参考素材整理以及自动化数据采集管道中的链接中转场景。

LinkMap 定位为技术信息索引层，目标用户包括需要进行批量链接管理的运维工程师、搭建个人导航站的前端开发者，以及需要对外输出合规资源列表的内容运营人员。通过简洁的本地文件体系与可扩展的元数据配置，LinkMap 能够在五分钟内完成部署并开始收录第一批资源。

## 功能概览

批量链接导入与自动去重：支持从纯文本、CSV 及 JSON 格式批量导入 URL，自动识别重复条目并生成导入报告。

来源域名聚合视图：按照根域名与二级域名对收录链接进行分组聚合，便于评估不同源站的内容覆盖密度。

自定义标签与分类体系：允许用户为每条链接添加多个层级标签，支持基于标签组合的快速筛选与导出。

静态资源快照标记：针对特定 URL 可标记快照状态、最后校验时间与响应码，辅助判断链接活性。

全文标题与摘要抓取：在遵守 robots.txt 的前提下，自动抓取目标页面的 title 与 meta description 并存入索引字段。

多格式导出支持：支持将当前筛选结果导出为 Markdown 列表、JSON 数组或纯文本 URL 清单，便于嵌入其他文档或工具。

本地部署与单机运行：无需外部数据库，全部索引数据存储于本地 JSON 文件与 SQLite 数据库中，降低运维成本。

## 应用场景

个人技术博客的参考链接附录维护：技术博主在撰写长文时，需要引用大量外部资料。LinkMap 可以帮助博主集中管理所有引用 URL，并在文章发布前统一生成符合规范的链接列表，避免链接遗漏或格式错误。

团队内部技术周报的资源汇集：技术团队的周报通常需要包含行业动态、工具更新与优秀文章推荐。使用 LinkMap 可以建立一个共享的资源池，每位成员贡献链接后，由周报负责人统一筛选并导出为周报素材。

数据采集管道的中间链接暂存与清洗：在进行大规模数据采集时，原始采集程序往往产出大量待处理的 URL。LinkMap 可作为管道中的缓冲层，对这些 URL 进行去重、分类与初步校验，再交由下游解析程序处理。

开源文档项目的参考资料索引：开源项目的文档中常常需要附带外部参考链接。LinkMap 可以为这些链接建立独立的索引页面，方便文档维护者定期检查链接有效性，并在版本更新时同步刷新参考列表。

## 快速开始

以下命令演示如何在 Ubuntu 22.04 或 macOS 13 及以上环境中完成 LinkMap 的克隆、安装与首次运行。

```bash
git clone https://github.com/linkmap-org/linkmap.git
cd linkmap
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python3 manage.py init
python3 manage.py import --input ./samples/links.txt
python3 manage.py serve --port 8080
```

执行完毕后，访问 http://localhost:8080 即可看到当前收录的链接列表。若需要后台持续运行，可使用 `--daemon` 参数或配合 systemd 服务。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.9 - 3.12 | 核心运行环境，推荐使用 3.11 以获得最佳性能 |
| SQLite | 3.35.0 及以上 | 内置数据库，用于存储链接索引与标签关系 |
| pip | 22.0 及以上 | Python 包管理工具，用于安装项目依赖 |
| requests | 2.31.0 | HTTP 客户端库，用于链接标题与摘要抓取 |
| beautifulsoup4 | 4.12.0 | HTML 解析库，用于解析页面标题与 meta 信息 |
| lxml | 4.9.0 | 高性能 XML/HTML 解析器，作为 beautifulsoup4 的后端加速 |

操作系统方面，LinkMap 已测试通过 Ubuntu 20.04/22.04、Debian 11/12、macOS 12/13/14 以及 Windows 10/11 的 WSL2 环境。生产部署建议使用 Linux 发行版。

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | docs/getting-started.md | 如何安装、初始化并导入第一批链接？如何验证部署成功？ |
| 配置参考 | docs/configuration.md | 有哪些可用的环境变量与配置文件选项？如何调整抓取并发数与超时时间？ |
| 命令行工具 | docs/cli.md | import、export、check、serve 等命令的完整参数说明与使用示例 |
| API 接口 | docs/api.md | 如何通过 HTTP API 以编程方式添加、查询或删除链接？ |

## 资源列表

- http://map.read.usuhx.com/Article/6967283.shtml
- http://map.read.usuhx.com/Article/8976175.shtml
- http://map.mobile.xqnqq.com/Article/7365.shtml
- http://map.read.usuhx.com/Article/6968.shtml
- http://map.mobile.xqnqq.com/Article/6606.shtml
- http://map.mobile.xqnqq.com/Article/6927.shtml
- http://map.read.usuhx.com/Article/6262.shtml
- http://map.read.usuhx.com/Article/060286.shtml
- http://map.mobile.xqnqq.com/Article/886513.shtml
- http://map.mobile.xqnqq.com/Article/677827.shtml
- http://map.mobile.xqnqq.com/Article/746721.shtml
- http://map.read.usuhx.com/Article/41960.shtml
- http://map.read.usuhx.com/Article/75599.shtml
- http://map.mobile.xqnqq.com/Article/73276.shtml
- http://map.read.usuhx.com/Article/0036095.shtml
- http://map.mobile.xqnqq.com/Article/2177669.shtml
- http://map.mobile.xqnqq.com/Article/749228.shtml
- http://map.read.usuhx.com/Article/723326.shtml
- http://map.mobile.xqnqq.com/Article/03663.shtml
- http://map.read.usuhx.com/Article/6119.shtml
- http://map.read.usuhx.com/Article/5649642.shtml
- http://map.mobile.xqnqq.com/Article/0943.shtml
- http://map.mobile.xqnqq.com/Article/2616.shtml
- http://map.mobile.xqnqq.com/Article/4187241.shtml
- http://map.read.usuhx.com/Article/4913.shtml
- http://map.mobile.xqnqq.com/Article/94933.shtml
- http://map.mobile.xqnqq.com/Article/0267576.shtml
- http://map.read.usuhx.com/Article/892687.shtml
- http://map.mobile.xqnqq.com/Article/44744.shtml
- http://map.read.usuhx.com/Article/53677.shtml
- http://map.read.usuhx.com/Article/0665.shtml
- http://map.read.usuhx.com/Article/06148.shtml
- http://map.mobile.xqnqq.com/Article/355981.shtml
- http://map.read.usuhx.com/Article/7671.shtml
- http://map.read.usuhx.com/Article/1550.shtml
- http://map.read.usuhx.com/Article/0518.shtml
- http://map.mobile.xqnqq.com/Article/9522.shtml
- http://map.mobile.xqnqq.com/Article/0640840.shtml
- http://map.mobile.xqnqq.com/Article/4190.shtml
- http://map.read.usuhx.com/Article/3455476.shtml
- http://map.mobile.xqnqq.com/Article/418544.shtml
- http://map.read.usuhx.com/Article/2521.shtml
- http://map.read.usuhx.com/Article/053984.shtml
- http://map.mobile.xqnqq.com/Article/7772597.shtml
- http://map.mobile.xqnqq.com/Article/1175694.shtml
- http://map.read.usuhx.com/Article/6131.shtml
- http://map.mobile.xqnqq.com/Article/9947821.shtml
- http://map.mobile.xqnqq.com/Article/6080085.shtml
- http://map.mobile.xqnqq.com/Article/6545.shtml
- http://map.read.usuhx.com/Article/1693.shtml
- http://map.mobile.xqnqq.com/Article/1582625.shtml
- http://map.mobile.xqnqq.com/Article/5282046.shtml
- http://map.read.usuhx.com/Article/20415.shtml
- http://map.mobile.xqnqq.com/Article/68321.shtml
- http://map.read.usuhx.com/Article/1706.shtml
- http://map.mobile.xqnqq.com/Article/7294.shtml
- http://map.read.usuhx.com/Article/3107821.shtml
- http://map.read.usuhx.com/Article/49604.shtml
- http://map.read.usuhx.com/Article/2544.shtml
- http://map.mobile.xqnqq.com/Article/9189652.shtml
- http://map.mobile.xqnqq.com/Article/30692.shtml
- http://map.mobile.xqnqq.com/Article/701785.shtml
- http://map.read.usuhx.com/Article/2889.shtml
- http://map.mobile.xqnqq.com/Article/075733.shtml
- http://map.mobile.xqnqq.com/Article/4643713.shtml
- http://map.mobile.xqnqq.com/Article/54259.shtml
- http://map.read.usuhx.com/Article/06193.shtml
- http://map.mobile.xqnqq.com/Article/8390220.shtml
- http://map.read.usuhx.com/Article/5797020.shtml
- http://map.read.usuhx.com/Article/4895.shtml
- http://map.mobile.xqnqq.com/Article/76937.shtml
- http://map.read.usuhx.com/Article/5778.shtml
- http://map.mobile.xqnqq.com/Article/6824411.shtml
- http://map.read.usuhx.com/Article/1416906.shtml
- http://map.read.usuhx.com/Article/09684.shtml
- http://map.read.usuhx.com/Article/015850.shtml
- http://map.mobile.xqnqq.com/Article/7260.shtml
- http://map.read.usuhx.com/Article/762688.shtml
- http://map.mobile.xqnqq.com/Article/0226.shtml
- http://map.read.usuhx.com/Article/6686497.shtml
- http://map.mobile.xqnqq.com/Article/4680.shtml
- http://map.read.usuhx.com/Article/8264.shtml
- http://map.read.usuhx.com/Article/396355.shtml
- http://map.mobile.xqnqq.com/Article/71459.shtml
- http://map.mobile.xqnqq.com/Article/1576108.shtml
- http://map.read.usuhx.com/Article/7453479.shtml
- http://map.read.usuhx.com/Article/748691.shtml
- http://map.read.usuhx.com/Article/33883.shtml
- http://map.mobile.xqnqq.com/Article/1815.shtml
- http://map.read.usuhx.com/Article/55363.shtml
- http://map.read.usuhx.com/Article/2351594.shtml
- http://map.mobile.xqnqq.com/Article/1041910.shtml
- http://map.read.usuhx.com/Article/2303.shtml
- http://map.mobile.xqnqq.com/Article/7924226.shtml
- http://map.mobile.xqnqq.com/Article/526770.shtml
- http://map.read.usuhx.com/Article/37169.shtml
- http://map.mobile.xqnqq.com/Article/2124624.shtml
- http://map.mobile.xqnqq.com/Article/9696.shtml
- http://map.read.usuhx.com/Article/5317498.shtml
- http://map.mobile.xqnqq.com/Article/7611911.shtml
- http://map.mobile.xqnqq.com/Article/1052.shtml
- http://map.mobile.xqnqq.com/Article/3656465.shtml
- http://map.read.usuhx.com/Article/0378202.shtml
- http://map.read.usuhx.com/Article/793263.shtml
- http://map.read.usuhx.com/Article/1902.shtml
- http://map.mobile.xqnqq.com/Article/17683.shtml
- http://map.read.usuhx.com/Article/80057.shtml
- http://map.mobile.xqnqq.com/Article/5807842.shtml
- http://map.mobile.xqnqq.com/Article/7423.shtml
- http://map.mobile.xqnqq.com/Article/079535.shtml
- http://map.mobile.xqnqq.com/Article/625397.shtml
- http://map.mobile.xqnqq.com/Article/2729.shtml
- http://map.read.usuhx.com/Article/24652.shtml
- http://map.read.usuhx.com/Article/10029.shtml
- http://map.mobile.xqnqq.com/Article/3680377.shtml
- http://map.read.usuhx.com/Article/5251.shtml
- http://map.read.usuhx.com/Article/5237855.shtml
- http://map.read.usuhx.com/Article/781718.shtml
- http://map.mobile.xqnqq.com/Article/499454.shtml
- http://map.mobile.xqnqq.com/Article/9273.shtml
- http://map.mobile.xqnqq.com/Article/47325.shtml
- http://map.read.usuhx.com/Article/0654625.shtml
- http://map.mobile.xqnqq.com/Article/5557.shtml
- http://map.read.usuhx.com/Article/23126.shtml
- http://map.mobile.xqnqq.com/Article/92172.shtml
- http://map.read.usuhx.com/Article/4516.shtml
- http://map.read.usuhx.com/Article/3737223.shtml
- http://map.mobile.xqnqq.com/Article/1559317.shtml
- http://map.read.usuhx.com/Article/6655.shtml
- http://map.mobile.xqnqq.com/Article/90833.shtml
- http://map.read.usuhx.com/Article/224526.shtml
- http://map.read.usuhx.com/Article/730417.shtml
- http://map.read.usuhx.com/Article/106503.shtml
- http://map.read.usuhx.com/Article/45700.shtml
- http://map.mobile.xqnqq.com/Article/3691.shtml
- http://map.read.usuhx.com/Article/6693713.shtml
- http://map.mobile.xqnqq.com/Article/2407455.shtml
- http://map.mobile.xqnqq.com/Article/50337.shtml
- http://map.read.usuhx.com/Article/542331.shtml
- http://map.mobile.xqnqq.com/Article/0233808.shtml
- http://map.read.usuhx.com/Article/326218.shtml
- http://map.mobile.xqnqq.com/Article/52362.shtml
- http://map.mobile.xqnqq.com/Article/9536903.shtml
- http://map.read.usuhx.com/Article/9309704.shtml
- http://map.read.usuhx.com/Article/39448.shtml
- http://map.mobile.xqnqq.com/Article/37673.shtml
- http://map.mobile.xqnqq.com/Article/7783766.shtml
- http://map.read.usuhx.com/Article/3125.shtml
- http://map.read.usuhx.com/Article/569875.shtml
- http://map.mobile.xqnqq.com/Article/41780.shtml
- http://map.mobile.xqnqq.com/Article/0575.shtml
- http://map.read.usuhx.com/Article/325310.shtml
- http://map.read.usuhx.com/Article/20815.shtml
- http://map.mobile.xqnqq.com/Article/0262.shtml
- http://map.read.usuhx.com/Article/9715236.shtml
- http://map.mobile.xqnqq.com/Article/65368.shtml
- http://map.read.usuhx.com/Article/28203.shtml
- http://map.mobile.xqnqq.com/Article/9873024.shtml
- http://map.mobile.xqnqq.com/Article/0491640.shtml
- http://map.read.usuhx.com/Article/7479.shtml
- http://map.mobile.xqnqq.com/Article/006615.shtml
- http://map.read.usuhx.com/Article/3931577.shtml
- http://map.mobile.xqnqq.com/Article/6840.shtml
- http://map.read.usuhx.com/Article/7015533.shtml
- http://map.read.usuhx.com/Article/91631.shtml
- http://map.mobile.xqnqq.com/Article/4871284.shtml
- http://map.mobile.xqnqq.com/Article/9116437.shtml
- http://map.read.usuhx.com/Article/3249.shtml
- http://map.read.usuhx.com/Article/7229.shtml
- http://map.read.usuhx.com/Article/240199.shtml
- http://map.read.usuhx.com/Article/37220.shtml
- http://map.read.usuhx.com/Article/3660873.shtml
- http://map.read.usuhx.com/Article/850059.shtml
- http://map.read.usuhx.com/Article/6992758.shtml
- http://map.mobile.xqnqq.com/Article/3746821.shtml
- http://map.mobile.xqnqq.com/Article/5798.shtml
- http://map.mobile.xqnqq.com/Article/674584.shtml
- http://map.mobile.xqnqq.com/Article/99272.shtml
- http://map.mobile.xqnqq.com/Article/869989.shtml
- http://map.read.usuhx.com/Article/7631.shtml
- http://map.read.usuhx.com/Article/22303.shtml
- http://map.mobile.xqnqq.com/Article/910658.shtml
- http://map.read.usuhx.com/Article/5528595.shtml
- http://map.read.usuhx.com/Article/8719.shtml
- http://map.mobile.xqnqq.com/Article/02020.shtml
- http://map.read.usuhx.com/Article/0255.shtml
- http://map.read.usuhx.com/Article/8980.shtml
- http://map.read.usuhx.com/Article/63449.shtml
- http://map.mobile.xqnqq.com/Article/97748.shtml
- http://map.read.usuhx.com/Article/0869419.shtml
- http://map.read.usuhx.com/Article/01748.shtml
- http://map.read.usuhx.com/Article/0602.shtml
- http://map.mobile.xqnqq.com/Article/21248.shtml
- http://map.mobile.xqnqq.com/Article/6526169.shtml
- http://map.read.usuhx.com/Article/5430.shtml
- http://map.read.usuhx.com/Article/768480.shtml
- http://map.mobile.xqnqq.com/Article/0801.shtml
- http://map.mobile.xqnqq.com/Article/0215.shtml
- http://map.read.usuhx.com/Article/4093951.shtml
- http://map.read.usuhx.com/Article/74231.shtml
- http://map.read.usuhx.com/Article/0796522.shtml
- http://map.read.usuhx.com/Article/8455465.shtml
- http://map.read.usuhx.com/Article/025796.shtml
- http://map.read.usuhx.com/Article/0412.shtml
- http://map.mobile.xqnqq.com/Article/66554.shtml
- http://map.read.usuhx.com/Article/3221279.shtml
- http://map.read.usuhx.com/Article/794959.shtml
- http://map.read.usuhx.com/Article/693744.shtml
- http://map.mobile.xqnqq.com/Article/96837.shtml
- http://map.read.usuhx.com/Article/792267.shtml
- http://map.mobile.xqnqq.com/Article/4051826.shtml
- http://map.read.usuhx.com/Article/9425.shtml
- http://map.read.usuhx.com/Article/6595.shtml
- http://map.read.usuhx.com/Article/944287.shtml
- http://map.mobile.xqnqq.com/Article/7742339.shtml
- http://map.mobile.xqnqq.com/Article/93975.shtml
- http://map.mobile.xqnqq.com/Article/1247852.shtml
- http://map.read.usuhx.com/Article/615462.shtml
- http://map.read.usuhx.com/Article/577780.shtml
- http://map.mobile.xqnqq.com/Article/6815.shtml
- http://map.read.usuhx.com/Article/2307582.shtml
- http://map.read.usuhx.com/Article/21594.shtml
- http://map.read.usuhx.com/Article/544868.shtml
- http://map.mobile.xqnqq.com/Article/7807.shtml
- http://map.read.usuhx.com/Article/355402.shtml
- http://map.read.usuhx.com/Article/138828.shtml
- http://map.mobile.xqnqq.com/Article/225277.shtml
- http://map.mobile.xqnqq.com/Article/7882271.shtml
- http://map.mobile.xqnqq.com/Article/0893.shtml
- http://map.mobile.xqnqq.com/Article/8685150.shtml
- http://map.read.usuhx.com/Article/157946.shtml
- http://map.mobile.xqnqq.com/Article/4324.shtml
- http://map.mobile.xqnqq.com/Article/4586566.shtml
- http://map.mobile.xqnqq.com/Article/8460.shtml
- http://map.read.usuhx.com/Article/20489.shtml
- http://map.read.usuhx.com/Article/6354.shtml
- http://map.read.usuhx.com/Article/43519.shtml
- http://map.read.usuhx.com/Article/0890817.shtml
- http://map.read.usuhx.com/Article/34275.shtml
- http://map.read.usuhx.com/Article/3253485.shtml
- http://map.mobile.xqnqq.com/Article/3058.shtml
- http://map.read.usuhx.com/Article/59020.shtml
- http://map.read.usuhx.com/Article/67322.shtml
- http://map.read.usuhx.com/Article/53650.shtml
- http://map.read.usuhx.com/Article/10778.shtml
- http://map.mobile.xqnqq.com/Article/3606034.shtml
- http://map.read.usuhx.com/Article/732160.shtml
- http://map.mobile.xqnqq.com/Article/504095.shtml
- http://map.mobile.xqnqq.com/Article/467066.shtml
- http://map.mobile.xqnqq.com/Article/5359907.shtml

## 项目结构

```
linkmap/
├── cmd/                            # 命令行入口包
│   ├── cli.py                      # 主命令行调度器，解析子命令
│   └── serve.py                    # 内置 Web 服务启动器
├── internal/                       # 内部核心逻辑（不对外暴露）
│   ├── indexer/                    # 链接索引引擎
│   │   ├── loader.py               # 从文件/标准输入加载 URL 列表
│   │   ├── dedup.py                # 基于哈希与标准化 URL 的去重算法
│   │   └── fetcher.py              # 异步 HTTP 抓取器，含超时与重试策略
│   ├── storage/                    # 存储适配层
│   │   ├── sqlite_repo.py          # SQLite 数据库操作实现
│   │   └── json_repo.py            # JSON 文件备份与导入导出
│   └── tags/                       # 标签系统
│       ├── parser.py               # 标签语法解析（支持空格、逗号、#前缀）
│       └── filter.py               # 标签组合筛选逻辑（AND / OR / NOT）
├── pkg/                            # 可复用的公共包
│   ├── http_client/                # 封装 requests 会话与连接池
│   ├── url_utils/                  # URL 标准化、域名提取、路径规范化
│   └── logger/                     # 结构化日志输出（JSON 格式）
├── web/                            # Web 界面相关
│   ├── templates/                  # Jinja2 模板文件
│   │   ├── index.html              # 链接列表主页
│   │   └── detail.html             # 单条链接详情页
│   └── static/                     # CSS 与 JavaScript 资源
├── config/                         # 配置文件目录
│   ├── default.yaml                # 默认配置（含抓取并发数、超时、端口）
│   └── schema.json                 # 配置项 JSON Schema 校验文件
├── scripts/                        # 辅助运维脚本
│   ├── backup.sh                   # 每日备份数据库与索引文件
│   └── import_from_csv.py          # 从 CSV 批量导入的辅助脚本
├── tests/                          # 单元测试与集成测试
│   ├── unit/                       # 单模块测试用例
│   └── integration/                # 端到端功能测试
├── samples/                        # 示例数据文件
│   └── links.txt                   # 供快速开始使用的示例链接列表
├── docs/                           # 完整文档源文件
├── requirements.txt                # Python 依赖列表
├── setup.py                        # 项目安装脚本
└── README.md                       # 项目说明文档（本文件）
```

## 贡献指南

提交 Issue 报告缺陷或功能请求：请使用 GitHub Issues 模板，清晰描述问题现象、复现步骤、预期行为与实际行为的差异。如涉及链接抓取异常，请附带目标 URL 示例。

Fork 仓库并创建功能分支：从 main 分支签出新的分支，分支命名遵循 `feature/功能简述` 或 `fix/问题简述` 格式。避免在 main 分支上直接修改。

编写或更新单元测试：所有新增功能或缺陷修复必须包含对应的单元测试用例，测试覆盖率不得低于现有基线。运行 `pytest tests/` 确认全部测试通过。

提交 Pull Request 前同步上游代码：确保分支与上游 main 分支保持同步，解决冲突后再提交 PR。PR 描述中请关联对应的 Issue 编号。

遵循代码风格规范：Python 代码遵循 PEP 8 规范，使用 Black 格式化工具（版本 23.0 及以上），导入语句按标准库、第三方库、本地模块分组。

## 常见问题

Q: LinkMap 抓取页面标题时是否会触发反爬机制？
A: LinkMap 默认使用 `requests` 库的默认 User-Agent，并设置 5 秒超时与最多 2 次重试。为避免对目标站点造成压力，抓取并发数默认限制为 3。用户可在配置文件中调整并发数、超时时间以及自定义 User-Agent 头。对于明确声明 `User-Agent` 过滤规则的站点，建议用户自行配置白名单或关闭抓取功能。

Q: 如何迁移已有的链接数据到新版本？
A: LinkMap 的数据存储于 `data/` 目录下的 SQLite 数据库文件与 JSON 元数据文件中。升级前请执行 `python3 manage.py export --output backup.json` 导出完整数据。新版本部署完成后，使用 `python3 manage.py import --input backup.json --format json` 完成恢复。跨大版本升级前建议阅读 `docs/upgrade.md` 中的迁移说明。

Q: 能否在 Windows 原生环境下运行 LinkMap？
A: LinkMap 的核心依赖均兼容 Windows 平台，但推荐在 WSL2 环境中运行以获得最佳性能与文件系统兼容性。若在原生 Windows 环境中运行，请确保已安装 Visual C++ Redistributable，并使用 PowerShell 或 Git Bash 执行命令行操作。文件路径中的反斜杠问题已在 v1.2.0 中通过 `pathlib` 统一处理。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
