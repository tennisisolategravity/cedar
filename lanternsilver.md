# WebLink Navigator

WebLink Navigator 是一个面向技术研究、内容聚合与知识管理场景的轻量级外链资源归集与导航系统。该项目定位于帮助个人开发者、内容策展人、研究助理以及小型团队高效管理分散在多个内容源中的深度文章、技术笔记与行业报告，通过结构化的资源索引与分类机制，降低信息碎片化带来的检索与复用成本。

与传统书签管理工具或稍后读应用不同，WebLink Navigator 并不试图替代浏览器收藏夹或笔记软件，而是提供一个专注于 URL 资源的元数据提取、标签化分类、状态跟踪与批量导入导出的中间层工具。项目本身不依赖外部数据库或云服务，所有资源索引以本地文件形式存储，支持自定义元数据字段、多级标签体系与全文检索，适合作为知识库预处理流水线的前置组件，也可独立部署为团队内部的技术参考导航页。

## 功能概览

- **批量资源导入与去重**：支持从文本列表、CSV 文件或标准输入流中批量导入 URL，自动识别重复条目并基于响应状态码与内容哈希进行去重处理，避免同一资源多次收录。

- **自定义元数据标注**：每条资源可附加标题、来源站点、收录批次、标签集合、阅读状态、重要等级以及个人备注等字段，所有元数据存储于 YAML 前置块中，便于版本控制与脚本化处理。

- **多维度筛选与检索**：基于标签、来源域名、收录时间范围、状态等维度进行组合筛选，支持正则表达式匹配标题与备注内容，检索结果可按相关性、收录时间或自定义权重排序。

- **静态站点生成模式**：内置模板渲染引擎，可将资源索引导出为静态 HTML 页面，支持响应式布局与暗色主题，适合部署到 GitHub Pages、Nginx 或任何静态托管服务，作为团队共享的技术参考门户。

- **资源存活检测与状态标记**：定期或按需对已收录资源发起 HEAD/GET 请求，检测链接可用性，自动标记失效、重定向或响应超时的资源，并记录最后一次检测时间与 HTTP 状态码。

- **导入导出兼容性**：支持导出为 Markdown 列表、JSON、CSV 以及 OPML 格式，便于与其他阅读器、书签工具或知识管理软件进行数据交换，同时支持从浏览器书签 HTML 文件中导入现有收藏。

- **批次管理机制**：针对大规模资源收录场景（如本批次 80 批共 250 个链接），提供批次编号、收录日期、来源说明与审核状态管理，方便追溯每批资源的收录背景与处理进度。

## 应用场景

- **技术文章归档与主题跟踪**：研究人员或工程师可以将日常阅读中发现的深度技术文章、教程、规格文档等资源统一收录，按编程语言、框架、领域或问题域打标签，形成个人或团队的技术知识索引，便于后续按主题回溯与系统化学习。

- **内容策展与行业报告汇总**：内容运营人员、分析师或咨询顾问可以在进行行业调研或竞品分析时，将分散在多个新闻站点、博客、白皮书库中的相关链接集中导入 WebLink Navigator，附加业务标签与优先级，生成结构化的行业动态汇总报告或周报素材库。

- **团队共享参考门户构建**：开发团队或技术文档维护者可以将常用开发工具文档、API 参考、内部系统地址、运维手册等资源通过项目提供的静态站点生成功能，构建为一个内部导航页面，无需额外搭建 CMS 或 Wiki 系统，所有数据以纯文本形式管理，方便 Git 协作与变更审计。

## 快速开始

以下命令适用于 Linux、macOS 以及 Windows WSL 环境，假设系统已安装 Git 与 Python 3.9 及以上版本。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator

# 创建虚拟环境并安装依赖
python3 -m venv venv
source venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt

# 运行初始化设置，创建默认数据目录与配置文件
python manage.py init

# 导入示例资源列表（或替换为自己的数据文件）
python manage.py import --batch 29 --file ./data/sample_batch_29.txt

# 启动本地预览服务
python manage.py serve --port 8080
```

访问 http://localhost:8080 即可查看已收录资源的索引页面。如需生成静态站点，执行 `python manage.py build --output ./dist` 即可将全部资源输出为独立 HTML 文件。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 及以上 | 核心运行环境，建议使用 3.10 或 3.11 长期支持版本 |
| Git | 2.25 及以上 | 用于克隆仓库与版本管理，非运行必需但推荐 |
| requests | 2.28.0 及以上 | 处理 HTTP 请求，用于资源存活检测与响应分析 |
| pyyaml | 6.0 及以上 | 解析与生成 YAML 格式的元数据前置块 |
| jinja2 | 3.1.0 及以上 | 模板渲染引擎，用于生成静态站点页面 |
| markdown | 3.4.0 及以上 | 将备注字段中的 Markdown 内容渲染为 HTML |
| python-dateutil | 2.8.2 及以上 | 解析与格式化时间戳，处理时区转换 |
| click | 8.1.0 及以上 | 命令行接口框架，用于子命令解析与参数校验 |
| pytest | 7.2.0 及以上 | 单元测试框架，仅开发与测试环境需要 |
| black | 22.3.0 及以上 | 代码格式化工具，仅贡献代码时需要 |
| mypy | 0.990 及以上 | 静态类型检查工具，仅贡献代码时需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/user-guide/quick-start.md | 如何快速安装、导入第一批资源并启动本地服务 |
| 用户手册 | docs/user-guide/batch-management.md | 如何管理多批次资源、查看批次统计与处理进度 |
| 用户手册 | docs/user-guide/filtering-and-search.md | 如何使用标签、域名、状态等维度筛选资源，以及检索语法说明 |
| 运维参考 | docs/operations/static-site-generation.md | 如何配置模板、自定义主题并生成可部署的静态站点 |
| 运维参考 | docs/operations/link-health-check.md | 如何配置定时检测、处理失效链接与导出检测报告 |
| 开发指南 | docs/development/data-model.md | 资源元数据的数据结构定义、字段说明与扩展方式 |
| 开发指南 | docs/development/import-export-format.md | 支持的所有导入导出格式规范及自定义分隔符配置 |
| 开发指南 | docs/development/api-cli.md | 命令行所有子命令的完整参数列表与使用示例 |

## 资源列表

- http://www.read.usuhx.com/Article/8362350.shtml
- http://www.read.usuhx.com/Article/7909058.shtml
- http://www.read.usuhx.com/Article/272310.shtml
- http://www.mobile.xqnqq.com/Article/9929710.shtml
- http://www.mobile.xqnqq.com/Article/40251.shtml
- http://www.mobile.xqnqq.com/Article/1552.shtml
- http://www.mobile.xqnqq.com/Article/1269.shtml
- http://www.mobile.xqnqq.com/Article/54657.shtml
- http://www.mobile.xqnqq.com/Article/70889.shtml
- http://www.read.usuhx.com/Article/6636.shtml
- http://www.mobile.xqnqq.com/Article/2512.shtml
- http://www.mobile.xqnqq.com/Article/1187603.shtml
- http://www.mobile.xqnqq.com/Article/2721.shtml
- http://www.read.usuhx.com/Article/1887663.shtml
- http://www.read.usuhx.com/Article/4271028.shtml
- http://www.mobile.xqnqq.com/Article/1324494.shtml
- http://www.mobile.xqnqq.com/Article/4940778.shtml
- http://www.read.usuhx.com/Article/3103340.shtml
- http://www.read.usuhx.com/Article/86500.shtml
- http://www.read.usuhx.com/Article/783870.shtml
- http://www.read.usuhx.com/Article/59578.shtml
- http://www.mobile.xqnqq.com/Article/69040.shtml
- http://www.read.usuhx.com/Article/073479.shtml
- http://www.read.usuhx.com/Article/2428.shtml
- http://www.read.usuhx.com/Article/567214.shtml
- http://www.mobile.xqnqq.com/Article/773665.shtml
- http://www.read.usuhx.com/Article/3288861.shtml
- http://www.read.usuhx.com/Article/63526.shtml
- http://www.mobile.xqnqq.com/Article/72842.shtml
- http://www.read.usuhx.com/Article/6804.shtml
- http://www.read.usuhx.com/Article/71012.shtml
- http://www.read.usuhx.com/Article/18359.shtml
- http://www.mobile.xqnqq.com/Article/6124430.shtml
- http://www.mobile.xqnqq.com/Article/231262.shtml
- http://www.mobile.xqnqq.com/Article/52190.shtml
- http://www.mobile.xqnqq.com/Article/622957.shtml
- http://www.read.usuhx.com/Article/0327301.shtml
- http://www.read.usuhx.com/Article/23122.shtml
- http://www.read.usuhx.com/Article/5619.shtml
- http://www.read.usuhx.com/Article/902511.shtml
- http://www.mobile.xqnqq.com/Article/9576.shtml
- http://www.mobile.xqnqq.com/Article/80065.shtml
- http://www.read.usuhx.com/Article/5092.shtml
- http://www.read.usuhx.com/Article/36714.shtml
- http://www.mobile.xqnqq.com/Article/0485.shtml
- http://www.mobile.xqnqq.com/Article/014701.shtml
- http://www.mobile.xqnqq.com/Article/218874.shtml
- http://www.mobile.xqnqq.com/Article/7445571.shtml
- http://www.mobile.xqnqq.com/Article/8394929.shtml
- http://www.read.usuhx.com/Article/685706.shtml
- http://www.mobile.xqnqq.com/Article/59280.shtml
- http://www.read.usuhx.com/Article/8987864.shtml
- http://www.read.usuhx.com/Article/6044519.shtml
- http://www.read.usuhx.com/Article/4778.shtml
- http://www.mobile.xqnqq.com/Article/64849.shtml
- http://www.mobile.xqnqq.com/Article/89880.shtml
- http://www.read.usuhx.com/Article/84398.shtml
- http://www.mobile.xqnqq.com/Article/0634.shtml
- http://www.read.usuhx.com/Article/420754.shtml
- http://www.mobile.xqnqq.com/Article/2405063.shtml
- http://www.mobile.xqnqq.com/Article/558854.shtml
- http://www.mobile.xqnqq.com/Article/89163.shtml
- http://www.read.usuhx.com/Article/45836.shtml
- http://www.mobile.xqnqq.com/Article/9853146.shtml
- http://www.read.usuhx.com/Article/34718.shtml
- http://www.mobile.xqnqq.com/Article/5973.shtml
- http://www.mobile.xqnqq.com/Article/031378.shtml
- http://www.mobile.xqnqq.com/Article/144795.shtml
- http://www.mobile.xqnqq.com/Article/400573.shtml
- http://www.mobile.xqnqq.com/Article/9444.shtml
- http://www.mobile.xqnqq.com/Article/6234.shtml
- http://www.mobile.xqnqq.com/Article/51904.shtml
- http://www.read.usuhx.com/Article/60880.shtml
- http://www.mobile.xqnqq.com/Article/035253.shtml
- http://www.mobile.xqnqq.com/Article/8825203.shtml
- http://www.mobile.xqnqq.com/Article/120112.shtml
- http://www.mobile.xqnqq.com/Article/238932.shtml
- http://www.read.usuhx.com/Article/8249.shtml
- http://www.read.usuhx.com/Article/0229.shtml
- http://www.read.usuhx.com/Article/8497.shtml
- http://www.mobile.xqnqq.com/Article/674400.shtml
- http://www.read.usuhx.com/Article/547396.shtml
- http://www.read.usuhx.com/Article/27455.shtml
- http://www.mobile.xqnqq.com/Article/76660.shtml
- http://www.mobile.xqnqq.com/Article/828223.shtml
- http://www.read.usuhx.com/Article/747101.shtml
- http://www.mobile.xqnqq.com/Article/2248825.shtml
- http://www.mobile.xqnqq.com/Article/0044815.shtml
- http://www.read.usuhx.com/Article/295057.shtml
- http://www.mobile.xqnqq.com/Article/1046079.shtml
- http://www.mobile.xqnqq.com/Article/4211328.shtml
- http://www.mobile.xqnqq.com/Article/983684.shtml
- http://www.mobile.xqnqq.com/Article/9981928.shtml
- http://www.mobile.xqnqq.com/Article/5712461.shtml
- http://www.mobile.xqnqq.com/Article/55645.shtml
- http://www.mobile.xqnqq.com/Article/30691.shtml
- http://www.mobile.xqnqq.com/Article/67041.shtml
- http://www.read.usuhx.com/Article/16154.shtml
- http://www.mobile.xqnqq.com/Article/47800.shtml
- http://www.read.usuhx.com/Article/651309.shtml
- http://www.mobile.xqnqq.com/Article/049231.shtml
- http://www.read.usuhx.com/Article/38945.shtml
- http://www.read.usuhx.com/Article/89979.shtml
- http://www.mobile.xqnqq.com/Article/05595.shtml
- http://www.read.usuhx.com/Article/8224.shtml
- http://www.mobile.xqnqq.com/Article/63139.shtml
- http://www.mobile.xqnqq.com/Article/6160.shtml
- http://www.mobile.xqnqq.com/Article/8888.shtml
- http://www.read.usuhx.com/Article/7598.shtml
- http://www.mobile.xqnqq.com/Article/97841.shtml
- http://www.read.usuhx.com/Article/122568.shtml
- http://www.mobile.xqnqq.com/Article/1676.shtml
- http://www.read.usuhx.com/Article/615789.shtml
- http://www.read.usuhx.com/Article/82223.shtml
- http://www.mobile.xqnqq.com/Article/64946.shtml
- http://www.mobile.xqnqq.com/Article/5116780.shtml
- http://www.mobile.xqnqq.com/Article/936924.shtml
- http://www.read.usuhx.com/Article/80933.shtml
- http://www.mobile.xqnqq.com/Article/6268.shtml
- http://www.read.usuhx.com/Article/0516356.shtml
- http://www.mobile.xqnqq.com/Article/6755.shtml
- http://www.mobile.xqnqq.com/Article/8899.shtml
- http://www.mobile.xqnqq.com/Article/1783720.shtml
- http://www.read.usuhx.com/Article/974994.shtml
- http://www.read.usuhx.com/Article/70067.shtml
- http://www.read.usuhx.com/Article/1655.shtml
- http://www.read.usuhx.com/Article/164285.shtml
- http://www.mobile.xqnqq.com/Article/08790.shtml
- http://www.read.usuhx.com/Article/75821.shtml
- http://www.mobile.xqnqq.com/Article/6247768.shtml
- http://www.mobile.xqnqq.com/Article/173182.shtml
- http://www.read.usuhx.com/Article/60413.shtml
- http://www.read.usuhx.com/Article/0133.shtml
- http://www.mobile.xqnqq.com/Article/194343.shtml
- http://www.read.usuhx.com/Article/117040.shtml
- http://www.read.usuhx.com/Article/09185.shtml
- http://www.mobile.xqnqq.com/Article/62586.shtml
- http://www.mobile.xqnqq.com/Article/5066260.shtml
- http://www.mobile.xqnqq.com/Article/1708.shtml
- http://www.read.usuhx.com/Article/44026.shtml
- http://www.read.usuhx.com/Article/7646.shtml
- http://www.read.usuhx.com/Article/976250.shtml
- http://www.mobile.xqnqq.com/Article/2911.shtml
- http://www.read.usuhx.com/Article/466658.shtml
- http://www.read.usuhx.com/Article/3713.shtml
- http://www.read.usuhx.com/Article/05858.shtml
- http://www.mobile.xqnqq.com/Article/999182.shtml
- http://www.mobile.xqnqq.com/Article/417476.shtml
- http://www.mobile.xqnqq.com/Article/84678.shtml
- http://www.mobile.xqnqq.com/Article/459548.shtml
- http://www.read.usuhx.com/Article/9559.shtml
- http://www.mobile.xqnqq.com/Article/2309815.shtml
- http://www.read.usuhx.com/Article/6727.shtml
- http://www.read.usuhx.com/Article/8859406.shtml
- http://www.read.usuhx.com/Article/4239309.shtml
- http://www.mobile.xqnqq.com/Article/4550384.shtml
- http://www.mobile.xqnqq.com/Article/0138333.shtml
- http://www.read.usuhx.com/Article/51847.shtml
- http://www.read.usuhx.com/Article/2254356.shtml
- http://www.mobile.xqnqq.com/Article/1960185.shtml
- http://www.read.usuhx.com/Article/44174.shtml
- http://www.read.usuhx.com/Article/5133118.shtml
- http://www.read.usuhx.com/Article/4038596.shtml
- http://www.mobile.xqnqq.com/Article/5848507.shtml
- http://www.mobile.xqnqq.com/Article/328170.shtml
- http://www.read.usuhx.com/Article/7585407.shtml
- http://www.mobile.xqnqq.com/Article/806831.shtml
- http://www.mobile.xqnqq.com/Article/9576791.shtml
- http://www.mobile.xqnqq.com/Article/71752.shtml
- http://www.read.usuhx.com/Article/80044.shtml
- http://www.read.usuhx.com/Article/2491211.shtml
- http://www.mobile.xqnqq.com/Article/11601.shtml
- http://www.read.usuhx.com/Article/94938.shtml
- http://www.read.usuhx.com/Article/4262553.shtml
- http://www.mobile.xqnqq.com/Article/11327.shtml
- http://www.mobile.xqnqq.com/Article/3465253.shtml
- http://www.read.usuhx.com/Article/54042.shtml
- http://www.read.usuhx.com/Article/0288.shtml
- http://www.read.usuhx.com/Article/1620.shtml
- http://www.mobile.xqnqq.com/Article/17377.shtml
- http://www.read.usuhx.com/Article/090106.shtml
- http://www.read.usuhx.com/Article/6783366.shtml
- http://www.read.usuhx.com/Article/0877.shtml
- http://www.mobile.xqnqq.com/Article/4523784.shtml
- http://www.read.usuhx.com/Article/083778.shtml
- http://www.mobile.xqnqq.com/Article/62714.shtml
- http://www.read.usuhx.com/Article/9557.shtml
- http://www.read.usuhx.com/Article/73678.shtml
- http://www.mobile.xqnqq.com/Article/96810.shtml
- http://www.read.usuhx.com/Article/85351.shtml
- http://www.mobile.xqnqq.com/Article/8296206.shtml
- http://www.mobile.xqnqq.com/Article/153656.shtml
- http://www.mobile.xqnqq.com/Article/7498.shtml
- http://www.mobile.xqnqq.com/Article/28997.shtml
- http://www.read.usuhx.com/Article/1650962.shtml
- http://www.mobile.xqnqq.com/Article/20374.shtml
- http://www.read.usuhx.com/Article/5342.shtml
- http://www.read.usuhx.com/Article/689096.shtml
- http://www.mobile.xqnqq.com/Article/967289.shtml
- http://www.read.usuhx.com/Article/1738.shtml
- http://www.mobile.xqnqq.com/Article/65466.shtml
- http://www.mobile.xqnqq.com/Article/1107102.shtml
- http://www.mobile.xqnqq.com/Article/454180.shtml
- http://www.read.usuhx.com/Article/0716724.shtml
- http://www.read.usuhx.com/Article/957752.shtml
- http://www.mobile.xqnqq.com/Article/9583285.shtml
- http://www.read.usuhx.com/Article/6529.shtml
- http://www.read.usuhx.com/Article/6036370.shtml
- http://www.mobile.xqnqq.com/Article/9492609.shtml
- http://www.read.usuhx.com/Article/2881.shtml
- http://www.read.usuhx.com/Article/7009540.shtml
- http://www.mobile.xqnqq.com/Article/58388.shtml
- http://www.mobile.xqnqq.com/Article/424478.shtml
- http://www.read.usuhx.com/Article/8577.shtml
- http://www.mobile.xqnqq.com/Article/581741.shtml
- http://www.mobile.xqnqq.com/Article/9034.shtml
- http://www.read.usuhx.com/Article/2659.shtml
- http://www.read.usuhx.com/Article/864972.shtml
- http://www.read.usuhx.com/Article/3684968.shtml
- http://www.read.usuhx.com/Article/41611.shtml
- http://www.mobile.xqnqq.com/Article/10097.shtml
- http://www.read.usuhx.com/Article/0391918.shtml
- http://www.mobile.xqnqq.com/Article/8120.shtml
- http://www.read.usuhx.com/Article/39944.shtml
- http://www.read.usuhx.com/Article/9664431.shtml
- http://www.read.usuhx.com/Article/5849.shtml
- http://www.read.usuhx.com/Article/9361.shtml
- http://www.mobile.xqnqq.com/Article/71000.shtml
- http://www.read.usuhx.com/Article/0887476.shtml
- http://www.mobile.xqnqq.com/Article/3848.shtml
- http://www.mobile.xqnqq.com/Article/73143.shtml
- http://www.read.usuhx.com/Article/1811.shtml
- http://www.mobile.xqnqq.com/Article/6634.shtml
- http://www.read.usuhx.com/Article/6279178.shtml
- http://www.read.usuhx.com/Article/20782.shtml
- http://www.read.usuhx.com/Article/6693613.shtml
- http://www.mobile.xqnqq.com/Article/51698.shtml
- http://www.read.usuhx.com/Article/58434.shtml
- http://www.mobile.xqnqq.com/Article/95340.shtml
- http://www.mobile.xqnqq.com/Article/5774.shtml
- http://www.read.usuhx.com/Article/4066807.shtml
- http://www.read.usuhx.com/Article/11397.shtml
- http://www.read.usuhx.com/Article/4093.shtml
- http://www.mobile.xqnqq.com/Article/081135.shtml
- http://www.mobile.xqnqq.com/Article/3887.shtml
- http://www.read.usuhx.com/Article/11932.shtml
- http://www.mobile.xqnqq.com/Article/71633.shtml
- http://www.read.usuhx.com/Article/5545227.shtml
- http://www.mobile.xqnqq.com/Article/81211.shtml
- http://www.read.usuhx.com/Article/7292550.shtml

## 项目结构

```
weblink-navigator/
├── manage.py                        # 命令行入口，注册所有子命令
├── requirements.txt                 # 生产环境依赖列表
├── pyproject.toml                   # 项目元数据与构建配置
├── .gitignore                       # Git 忽略规则
├── README.md                        # 项目说明文档
├── LICENSE                          # MIT 许可证文件
│
├── src/                             # 核心源代码目录
│   ├── __init__.py                  # 包初始化
│   ├── cli/                         # 命令行子命令实现
│   │   ├── __init__.py
│   │   ├── import_cmd.py            # import 子命令：批量导入资源
│   │   ├── export_cmd.py            # export 子命令：导出为多种格式
│   │   ├── serve_cmd.py             # serve 子命令：启动本地预览服务
│   │   ├── build_cmd.py             # build 子命令：生成静态站点
│   │   └── health_cmd.py            # health 子命令：链接存活检测
│   ├── core/                        # 核心数据模型与业务逻辑
│   │   ├── __init__.py
│   │   ├── resource.py              # Resource 类：单条资源的数据结构
│   │   ├── collection.py            # Collection 类：资源集合管理
│   │   ├── batch.py                 # Batch 类：批次元数据与状态
│   │   ├── indexer.py               # 索引构建与检索逻辑
│   │   └── dedup.py                 # 去重算法：URL 规范化与内容哈希
│   ├── storage/                     # 持久化存储适配器
│   │   ├── __init__.py
│   │   ├── file_storage.py          # 本地文件系统读写
│   │   ├── yaml_serializer.py       # YAML 序列化与反序列化
│   │   └── migrations/              # 数据格式升级迁移脚本
│   │       └── v1_to_v2.py
│   ├── fetcher/                     # HTTP 请求与响应处理
│   │   ├── __init__.py
│   │   ├── http_client.py           # 会话管理、重试策略、超时控制
│   │   ├── response_parser.py       # 响应头解析与状态判定
│   │   └── robots.py                # robots.txt 缓存与合规检查
│   └── render/                      # 模板渲染与静态生成
│       ├── __init__.py
│       ├── engine.py                # Jinja2 环境初始化与过滤器注册
│       ├── themes/                  # 内置主题目录
│       │   ├── default/             # 默认主题
│       │   │   ├── templates/       # HTML 模板文件
│       │   │   └── static/          # CSS、JS 与图标资源
│       │   └── compact/             # 紧凑型主题
│       └── page_builder.py          # 分页逻辑与索引页组装
│
├── tests/                           # 单元测试与集成测试
│   ├── __init__.py
│   ├── test_resource.py
│   ├── test_collection.py
│   ├── test_dedup.py
│   ├── test_http_client.py
│   └── fixtures/                    # 测试用固定数据
│       ├── sample_links.txt
│       └── sample_metadata.yaml
│
├── data/                            # 用户数据目录（运行时生成）
│   ├── batches/                     # 批次数据子目录，按批次编号存放
│   │   └── 29/                      # 第 29 批资源数据
│   │       ├── metadata.yaml        # 批次元数据（来源、日期、标签等）
│   │       └── resources.yaml       # 该批次全部资源详情
│   ├── index/                       # 全局索引缓存
│   │   └── search_index.json
│   └── logs/                        # 操作日志与检测报告
│       └── health_report_20260708.log
│
├── dist/                            # 静态站点构建输出目录（执行 build 后生成）
│   ├── index.html
│   ├── batch_29.html
│   ├── tags/
│   ├── assets/
│   └── ...
│
└── docs/                            # 项目文档源文件
    ├── user-guide/
    ├── operations/
    ├── development/
    └── _static/                     # 文档引用的图片与样式
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库至个人账号，并克隆到本地开发环境。建议在主干分支基础上新建一个功能分支，分支命名遵循 `feature/` 或 `fix/` 前缀加简要描述，例如 `feature/add-opml-export`。

2. 确保本地 Python 环境为 3.9 及以上版本，安装开发依赖 `pip install -r requirements-dev.txt`（该文件包含 pytest、black、mypy、pre-commit 等工具）。运行 `pre-commit install` 启用提交前自动检查。

3. 编写或修改代码时，请保持与现有代码风格一致。提交前执行 `black .` 进行自动格式化，并运行 `mypy src/` 进行静态类型检查，确保无新增类型错误。所有新增功能需在 `tests/` 目录下补充对应的单元测试用例，并确保 `pytest` 全部通过。

4. 提交变更时，编写清晰的提交信息，遵循 Conventional Commits 规范（如 `feat: add batch merge command` 或 `fix: handle redirect loop in health check`）。提交后推送至个人 Fork 仓库，并通过 GitHub 界面发起 Pull Request 到主仓库的 `main` 分支。

5. Pull Request 描述中请说明本次变更的目的、涉及的功能模块、测试覆盖情况以及可能的兼容性影响。项目维护者会在 3 个工作日内进行 Review，必要时会提出修改意见，所有反馈沟通在 PR 评论区进行。

## 常见问题

**问：导入资源时提示去重检测发现重复条目，但 URL 字符串看起来并不完全相同，这是为什么？**

答：项目的去重逻辑不仅比较原始 URL 字符串，还会对 URL 进行规范化处理，包括移除默认端口号、对百分号编码进行统一解码、将主机名转换为小写、移除尾部斜杠以及部分常见的跟踪参数（如 utm_source、ref 等）。如果两条 URL 在规范化后指向相同资源，系统会将其标记为重复并保留首次导入的版本。您可以通过 `--no-dedup` 参数强制关闭去重检测，或使用 `--strict` 模式仅基于原始字符串进行比较。

**问：静态站点生成后，部分资源的标题和描述显示为空白，如何补全这些信息？**

答：系统在导入资源时，默认会尝试从目标页面的 HTML 中提取 `<title>` 标签内容作为标题，以及 `<meta name="description">` 作为备注。但如果目标页面无法访问、返回非 HTML 内容或结构不标准，则这些字段会留空。您可以通过 `edit` 子命令手动编辑单条资源，或使用 `--metadata-file` 参数在导入时附加一个包含标题、备注、标签等信息的 YAML 或 CSV 补充文件，系统会根据 URL 匹配并合并这些字段。

**问：链接健康检测功能的频率和并发数如何调整？是否会对目标服务器造成压力？**

答：健康检测命令 `health` 支持 `--concurrency` 参数控制并发请求数，默认值为 5，可根据网络环境和目标站点承受能力适当调低。检测间隔通过 `--delay` 参数控制每个请求之间的最小延迟时间，单位为秒，默认 0.5 秒。在批量检测大量资源时，建议设置 `--concurrency 2 --delay 1.5` 以避免触发目标服务器的访问频率限制。所有检测请求均包含 `User-Agent: WebLinkNavigator-HealthCheck/1.0` 头部，便于服务器管理员识别与过滤。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
