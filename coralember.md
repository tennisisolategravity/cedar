# WebMap 技术资源索引

WebMap 是一个面向技术研究人员、数据采集工程师和内容聚合平台的定向外链资源汇总工具。该项目将分散在多个内容源（当前以 map.read.usuhx.com 与 map.mobile.xqnqq.com 为主）中的技术文章、数据条目和文档页面进行统一索引，提供结构化的条目级访问入口。项目本身不存储或复制任何页面内容，仅作为资源定位层，便于团队内部或特定技术群体进行批量访问、内容分析及归档管理。本项目为第 72/80 批次索引，当前批次共收录 250 个资源链接。

## 功能概览

批量资源条目导入与解析：支持按批次（每批 80 个条目）导入原始 URL 列表，自动完成协议识别、域名归类和编号提取，生成标准化索引记录。

双源并行索引架构：针对 map.read.usuhx.com 与 map.mobile.xqnqq.com 两个主要数据源分别建立索引通道，支持按来源域名过滤和统计。

文章编号快速定位：每个条目均提取 Article 目录后的数字编号，支持按编号区间检索，便于与上游数据系统交叉比对。

原始链接直出模式：所有存储和输出的 URL 均严格保持用户输入时的原始格式（包括协议类型、域名大小写、路径大小写、无尾部斜杠），不做任何自动补全或规范化改写，确保与上游系统完全兼容。

条目去重与冲突检测：自动检测重复 URL 和编号冲突，对同一文章编号在不同域名下的出现进行标记，并提供冲突解决策略。

纯文本索引导出：支持将索引结果导出为纯文本列表、Markdown 列表或 CSV 格式，便于导入其他数据分析工具或爬虫调度系统。

只读资源定位层设计：项目本身不发起对目标 URL 的自动请求，不缓存页面内容，不修改任何第三方资源，完全遵守 robots.txt 的隐含约束，仅提供人工或脚本访问所需的入口地址。

## 应用场景

技术文档批量归档：团队需要定期对 map.read.usuhx.com 域名下的技术文章进行本地归档或快照保存时，可直接使用本索引获取完整的条目列表，避免手工逐页翻找。

移动端内容差异对比：当需要对比 map.mobile.xqnqq.com 与主站同一编号文章的内容差异时，可通过索引快速筛选出两个源共有的条目编号，构建对比任务队列。

爬虫入口清单生成：数据采集工程师可将本索引输出的 URL 列表直接作为爬虫起始种子，按批次分发给不同采集节点，实现分布式抓取的入口统一管理。

历史条目状态核查：运维人员可根据索引中的编号列表，定期抽样检查各 URL 的可访问性、响应码变化或内容长度异常，监控上游资源的可用性。

## 快速开始

以下命令演示如何克隆仓库、安装基础依赖并运行一次索引构建任务。

```bash
git clone https://github.com/webmap/indexer.git
cd indexer
pip install -r requirements.txt
python build_index.py --batch 72 --source list_72.txt --output index_72.json
```

其中 list_72.txt 为包含原始 URL 列表的文本文件，每行一个 URL。build_index.py 会读取该文件，解析出文章编号和来源域名，生成索引 JSON 文件，并输出统计摘要。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，用于解析 URL 和生成索引 |
| pip | 20.0 及以上 | 管理 Python 包依赖 |
| requests | 2.25.0 及以上 | 用于可选的链接可达性检查（默认禁用） |
| pytest | 6.0.0 及以上 | 单元测试框架，仅在开发模式安装 |
| git | 2.20.0 及以上 | 用于克隆仓库和版本管理 |
| make | 3.81 及以上 | 可选，用于自动化任务脚本 |

生产环境建议使用 Python 3.10 及以上版本，并创建独立的虚拟环境以避免包冲突。requests 库仅在启用 --check 参数时使用，日常索引构建无需网络请求。

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user/manual.md | 如何准备输入文件、运行索引构建、解读输出结果 |
| 批次管理 | docs/admin/batch_management.md | 如何管理第 1 至 80 批次的索引数据，如何合并多批次结果 |
| 开发指南 | docs/developer/architecture.md | 索引器内部模块划分、数据流设计、扩展新数据源的方法 |
| API 参考 | docs/api/json_schema.md | 输出 JSON 文件的字段定义、数据类型和示例 |
| 常见工作流 | docs/workflows/daily_index.md | 每日新增条目的增量索引操作步骤 |
| 故障排查 | docs/troubleshooting/url_parse.md | URL 解析异常的常见原因及处理方法 |

## 资源列表

- http://map.read.usuhx.com/Article/1464.shtml
- http://map.mobile.xqnqq.com/Article/4889.shtml
- http://map.mobile.xqnqq.com/Article/4521001.shtml
- http://map.read.usuhx.com/Article/7253573.shtml
- http://map.read.usuhx.com/Article/898464.shtml
- http://map.read.usuhx.com/Article/924574.shtml
- http://map.read.usuhx.com/Article/2888.shtml
- http://map.read.usuhx.com/Article/11104.shtml
- http://map.mobile.xqnqq.com/Article/4140818.shtml
- http://map.mobile.xqnqq.com/Article/0760.shtml
- http://map.mobile.xqnqq.com/Article/01578.shtml
- http://map.mobile.xqnqq.com/Article/6881.shtml
- http://map.mobile.xqnqq.com/Article/3173.shtml
- http://map.mobile.xqnqq.com/Article/67463.shtml
- http://map.mobile.xqnqq.com/Article/493614.shtml
- http://map.mobile.xqnqq.com/Article/2556.shtml
- http://map.read.usuhx.com/Article/54650.shtml
- http://map.mobile.xqnqq.com/Article/1092764.shtml
- http://map.read.usuhx.com/Article/8397309.shtml
- http://map.read.usuhx.com/Article/629497.shtml
- http://map.mobile.xqnqq.com/Article/853314.shtml
- http://map.read.usuhx.com/Article/6161.shtml
- http://map.mobile.xqnqq.com/Article/2476311.shtml
- http://map.mobile.xqnqq.com/Article/4008246.shtml
- http://map.read.usuhx.com/Article/39980.shtml
- http://map.read.usuhx.com/Article/2420.shtml
- http://map.mobile.xqnqq.com/Article/10950.shtml
- http://map.mobile.xqnqq.com/Article/744901.shtml
- http://map.read.usuhx.com/Article/0444766.shtml
- http://map.read.usuhx.com/Article/2490344.shtml
- http://map.mobile.xqnqq.com/Article/4457248.shtml
- http://map.mobile.xqnqq.com/Article/7450.shtml
- http://map.mobile.xqnqq.com/Article/796536.shtml
- http://map.mobile.xqnqq.com/Article/404440.shtml
- http://map.read.usuhx.com/Article/491591.shtml
- http://map.read.usuhx.com/Article/3766.shtml
- http://map.read.usuhx.com/Article/451809.shtml
- http://map.read.usuhx.com/Article/45148.shtml
- http://map.mobile.xqnqq.com/Article/0982092.shtml
- http://map.read.usuhx.com/Article/04593.shtml
- http://map.read.usuhx.com/Article/7240480.shtml
- http://map.read.usuhx.com/Article/100837.shtml
- http://map.read.usuhx.com/Article/748864.shtml
- http://map.read.usuhx.com/Article/787444.shtml
- http://map.read.usuhx.com/Article/05063.shtml
- http://map.mobile.xqnqq.com/Article/1913789.shtml
- http://map.read.usuhx.com/Article/8169899.shtml
- http://map.read.usuhx.com/Article/178721.shtml
- http://map.read.usuhx.com/Article/01685.shtml
- http://map.mobile.xqnqq.com/Article/6049.shtml
- http://map.read.usuhx.com/Article/802743.shtml
- http://map.mobile.xqnqq.com/Article/70268.shtml
- http://map.mobile.xqnqq.com/Article/0657.shtml
- http://map.read.usuhx.com/Article/544494.shtml
- http://map.read.usuhx.com/Article/314979.shtml
- http://map.read.usuhx.com/Article/270887.shtml
- http://map.read.usuhx.com/Article/86307.shtml
- http://map.mobile.xqnqq.com/Article/6702494.shtml
- http://map.mobile.xqnqq.com/Article/2866561.shtml
- http://map.mobile.xqnqq.com/Article/2083.shtml
- http://map.read.usuhx.com/Article/3330.shtml
- http://map.read.usuhx.com/Article/55936.shtml
- http://map.read.usuhx.com/Article/4923525.shtml
- http://map.mobile.xqnqq.com/Article/96041.shtml
- http://map.mobile.xqnqq.com/Article/281793.shtml
- http://map.mobile.xqnqq.com/Article/99612.shtml
- http://map.mobile.xqnqq.com/Article/12585.shtml
- http://map.mobile.xqnqq.com/Article/0748593.shtml
- http://map.mobile.xqnqq.com/Article/08206.shtml
- http://map.read.usuhx.com/Article/6562776.shtml
- http://map.mobile.xqnqq.com/Article/0068043.shtml
- http://map.read.usuhx.com/Article/0619938.shtml
- http://map.read.usuhx.com/Article/5836.shtml
- http://map.read.usuhx.com/Article/020709.shtml
- http://map.mobile.xqnqq.com/Article/5201.shtml
- http://map.read.usuhx.com/Article/3630455.shtml
- http://map.read.usuhx.com/Article/2617.shtml
- http://map.mobile.xqnqq.com/Article/79473.shtml
- http://map.read.usuhx.com/Article/6841.shtml
- http://map.read.usuhx.com/Article/5795.shtml
- http://map.mobile.xqnqq.com/Article/2788.shtml
- http://map.mobile.xqnqq.com/Article/983913.shtml
- http://map.mobile.xqnqq.com/Article/4399101.shtml
- http://map.mobile.xqnqq.com/Article/8430523.shtml
- http://map.read.usuhx.com/Article/919382.shtml
- http://map.mobile.xqnqq.com/Article/918612.shtml
- http://map.read.usuhx.com/Article/41761.shtml
- http://map.read.usuhx.com/Article/5742030.shtml
- http://map.read.usuhx.com/Article/6673675.shtml
- http://map.read.usuhx.com/Article/1259.shtml
- http://map.read.usuhx.com/Article/5922.shtml
- http://map.read.usuhx.com/Article/4593281.shtml
- http://map.mobile.xqnqq.com/Article/62424.shtml
- http://map.read.usuhx.com/Article/4081.shtml
- http://map.mobile.xqnqq.com/Article/6235.shtml
- http://map.read.usuhx.com/Article/88105.shtml
- http://map.mobile.xqnqq.com/Article/7923.shtml
- http://map.mobile.xqnqq.com/Article/8274302.shtml
- http://map.read.usuhx.com/Article/4195417.shtml
- http://map.read.usuhx.com/Article/0232.shtml
- http://map.mobile.xqnqq.com/Article/635077.shtml
- http://map.mobile.xqnqq.com/Article/732210.shtml
- http://map.read.usuhx.com/Article/229533.shtml
- http://map.read.usuhx.com/Article/11015.shtml
- http://map.read.usuhx.com/Article/615312.shtml
- http://map.mobile.xqnqq.com/Article/98121.shtml
- http://map.mobile.xqnqq.com/Article/909017.shtml
- http://map.read.usuhx.com/Article/749252.shtml
- http://map.read.usuhx.com/Article/25633.shtml
- http://map.mobile.xqnqq.com/Article/0577.shtml
- http://map.mobile.xqnqq.com/Article/58934.shtml
- http://map.read.usuhx.com/Article/035327.shtml
- http://map.mobile.xqnqq.com/Article/4260.shtml
- http://map.read.usuhx.com/Article/71376.shtml
- http://map.read.usuhx.com/Article/95650.shtml
- http://map.read.usuhx.com/Article/5630114.shtml
- http://map.read.usuhx.com/Article/214165.shtml
- http://map.mobile.xqnqq.com/Article/9982.shtml
- http://map.mobile.xqnqq.com/Article/6810.shtml
- http://map.mobile.xqnqq.com/Article/269391.shtml
- http://map.mobile.xqnqq.com/Article/40763.shtml
- http://map.read.usuhx.com/Article/0171.shtml
- http://map.mobile.xqnqq.com/Article/9949.shtml
- http://map.read.usuhx.com/Article/3574.shtml
- http://map.mobile.xqnqq.com/Article/839205.shtml
- http://map.read.usuhx.com/Article/6869559.shtml
- http://map.read.usuhx.com/Article/686576.shtml
- http://map.mobile.xqnqq.com/Article/4658121.shtml
- http://map.mobile.xqnqq.com/Article/73934.shtml
- http://map.read.usuhx.com/Article/6510184.shtml
- http://map.mobile.xqnqq.com/Article/8904.shtml
- http://map.mobile.xqnqq.com/Article/56076.shtml
- http://map.mobile.xqnqq.com/Article/50019.shtml
- http://map.mobile.xqnqq.com/Article/9824.shtml
- http://map.mobile.xqnqq.com/Article/9555.shtml
- http://map.mobile.xqnqq.com/Article/2805477.shtml
- http://map.read.usuhx.com/Article/471261.shtml
- http://map.read.usuhx.com/Article/4497.shtml
- http://map.read.usuhx.com/Article/2545483.shtml
- http://map.read.usuhx.com/Article/0998.shtml
- http://map.mobile.xqnqq.com/Article/922644.shtml
- http://map.mobile.xqnqq.com/Article/41604.shtml
- http://map.mobile.xqnqq.com/Article/4709447.shtml
- http://map.read.usuhx.com/Article/679844.shtml
- http://map.mobile.xqnqq.com/Article/07137.shtml
- http://map.mobile.xqnqq.com/Article/8996.shtml
- http://map.mobile.xqnqq.com/Article/9653729.shtml
- http://map.read.usuhx.com/Article/223097.shtml
- http://map.read.usuhx.com/Article/563193.shtml
- http://map.mobile.xqnqq.com/Article/8374988.shtml
- http://map.read.usuhx.com/Article/624554.shtml
- http://map.read.usuhx.com/Article/5457.shtml
- http://map.read.usuhx.com/Article/5940.shtml
- http://map.mobile.xqnqq.com/Article/308795.shtml
- http://map.read.usuhx.com/Article/229508.shtml
- http://map.read.usuhx.com/Article/95560.shtml
- http://map.read.usuhx.com/Article/0164.shtml
- http://map.mobile.xqnqq.com/Article/3980613.shtml
- http://map.mobile.xqnqq.com/Article/3490.shtml
- http://map.mobile.xqnqq.com/Article/8727806.shtml
- http://map.read.usuhx.com/Article/1229.shtml
- http://map.mobile.xqnqq.com/Article/33139.shtml
- http://map.read.usuhx.com/Article/3003.shtml
- http://map.mobile.xqnqq.com/Article/8928.shtml
- http://map.mobile.xqnqq.com/Article/14053.shtml
- http://map.mobile.xqnqq.com/Article/555959.shtml
- http://map.read.usuhx.com/Article/3755.shtml
- http://map.mobile.xqnqq.com/Article/4267.shtml
- http://map.read.usuhx.com/Article/4209.shtml
- http://map.mobile.xqnqq.com/Article/39679.shtml
- http://map.read.usuhx.com/Article/1137610.shtml
- http://map.read.usuhx.com/Article/409766.shtml
- http://map.read.usuhx.com/Article/384548.shtml
- http://map.read.usuhx.com/Article/5788.shtml
- http://map.read.usuhx.com/Article/728529.shtml
- http://map.mobile.xqnqq.com/Article/6263.shtml
- http://map.mobile.xqnqq.com/Article/44083.shtml
- http://map.mobile.xqnqq.com/Article/887301.shtml
- http://map.mobile.xqnqq.com/Article/92097.shtml
- http://map.mobile.xqnqq.com/Article/46252.shtml
- http://map.mobile.xqnqq.com/Article/24124.shtml
- http://map.read.usuhx.com/Article/25941.shtml
- http://map.mobile.xqnqq.com/Article/732229.shtml
- http://map.read.usuhx.com/Article/62255.shtml
- http://map.mobile.xqnqq.com/Article/8493.shtml
- http://map.read.usuhx.com/Article/70642.shtml
- http://map.mobile.xqnqq.com/Article/931798.shtml
- http://map.mobile.xqnqq.com/Article/89243.shtml
- http://map.mobile.xqnqq.com/Article/1890.shtml
- http://map.read.usuhx.com/Article/3042627.shtml
- http://map.mobile.xqnqq.com/Article/6675.shtml
- http://map.mobile.xqnqq.com/Article/05414.shtml
- http://map.read.usuhx.com/Article/13203.shtml
- http://map.read.usuhx.com/Article/2194.shtml
- http://map.mobile.xqnqq.com/Article/973177.shtml
- http://map.mobile.xqnqq.com/Article/8835864.shtml
- http://map.read.usuhx.com/Article/39828.shtml
- http://map.read.usuhx.com/Article/0588010.shtml
- http://map.mobile.xqnqq.com/Article/910106.shtml
- http://map.read.usuhx.com/Article/2706992.shtml
- http://map.read.usuhx.com/Article/6826403.shtml
- http://map.read.usuhx.com/Article/2583053.shtml
- http://map.read.usuhx.com/Article/3711035.shtml
- http://map.read.usuhx.com/Article/7712060.shtml
- http://map.read.usuhx.com/Article/6526011.shtml
- http://map.read.usuhx.com/Article/6281404.shtml
- http://map.mobile.xqnqq.com/Article/69723.shtml
- http://map.read.usuhx.com/Article/57699.shtml
- http://map.read.usuhx.com/Article/98546.shtml
- http://map.read.usuhx.com/Article/7507484.shtml
- http://map.read.usuhx.com/Article/1489693.shtml
- http://map.mobile.xqnqq.com/Article/67101.shtml
- http://map.read.usuhx.com/Article/6390.shtml
- http://map.read.usuhx.com/Article/40842.shtml
- http://map.mobile.xqnqq.com/Article/1892035.shtml
- http://map.read.usuhx.com/Article/18778.shtml
- http://map.read.usuhx.com/Article/8372764.shtml
- http://map.read.usuhx.com/Article/78055.shtml
- http://map.read.usuhx.com/Article/9354.shtml
- http://map.read.usuhx.com/Article/5073.shtml
- http://map.mobile.xqnqq.com/Article/7355598.shtml
- http://map.read.usuhx.com/Article/1590645.shtml
- http://map.mobile.xqnqq.com/Article/7874.shtml
- http://map.mobile.xqnqq.com/Article/7934173.shtml
- http://map.read.usuhx.com/Article/7453548.shtml
- http://map.read.usuhx.com/Article/190500.shtml
- http://map.mobile.xqnqq.com/Article/3660846.shtml
- http://map.mobile.xqnqq.com/Article/4248.shtml
- http://map.mobile.xqnqq.com/Article/774793.shtml
- http://map.mobile.xqnqq.com/Article/934749.shtml
- http://map.read.usuhx.com/Article/741029.shtml
- http://map.mobile.xqnqq.com/Article/9145.shtml
- http://map.mobile.xqnqq.com/Article/8382.shtml
- http://map.mobile.xqnqq.com/Article/05506.shtml
- http://map.mobile.xqnqq.com/Article/4137337.shtml
- http://map.read.usuhx.com/Article/090753.shtml
- http://map.read.usuhx.com/Article/264885.shtml
- http://map.mobile.xqnqq.com/Article/2180769.shtml
- http://map.read.usuhx.com/Article/6694.shtml
- http://map.read.usuhx.com/Article/0230.shtml
- http://map.mobile.xqnqq.com/Article/3672122.shtml
- http://map.read.usuhx.com/Article/012838.shtml
- http://map.mobile.xqnqq.com/Article/899711.shtml
- http://map.read.usuhx.com/Article/590645.shtml
- http://map.mobile.xqnqq.com/Article/870475.shtml
- http://map.mobile.xqnqq.com/Article/229558.shtml
- http://map.mobile.xqnqq.com/Article/021599.shtml
- http://map.read.usuhx.com/Article/442557.shtml
- http://map.mobile.xqnqq.com/Article/94423.shtml
- http://map.read.usuhx.com/Article/29452.shtml

## 项目结构

```
webmap-indexer/
├── build_index.py            # 主入口脚本，解析输入文件并生成索引
├── config/
│   ├── default.yaml          # 默认配置：源域名列表、输出格式、批次大小
│   └── sources.json          # 预定义数据源映射（域名 -> 别名）
├── core/
│   ├── parser.py             # URL 解析模块，提取协议、域名、文章编号
│   ├── registry.py           # 索引注册模块，管理已处理条目的内存集合
│   ├── validator.py          # URL 格式校验与重复检测逻辑
│   └── exporter.py           # 输出导出模块：JSON / CSV / Markdown
├── tests/
│   ├── test_parser.py        # URL 解析单元测试，覆盖各种异常格式
│   ├── test_registry.py      # 注册表去重与冲突检测测试
│   └── fixtures/
│       └── sample_urls.txt   # 测试用的固定 URL 样本集
├── docs/                     # 全部文档源文件（参见文档导航章节）
│   ├── user/
│   ├── admin/
│   ├── developer/
│   └── workflows/
├── scripts/
│   ├── batch_import.sh       # 批量导入历史批次数据的 Shell 辅助脚本
│   └── verify_links.py       # 可选的外部链接可达性检查脚本（使用 requests）
└── README.md                 # 本文件
```

## 贡献指南

提交新批次数据：在 data/raw/ 目录下创建以 batch_{序号}.txt 命名的文件，每行一个原始 URL，随后运行 python build_index.py --batch {序号} 生成索引，并通过 Pull Request 提交。

新增数据源支持：修改 config/sources.json 添加新的域名映射，同时在 core/parser.py 中补充对应的编号提取规则，确保新源的文章编号能正确解析。

完善文档：所有文档位于 docs/ 目录，使用 Markdown 格式。修改后需确保内部链接有效，并在 Pull Request 描述中说明文档变更点。

报告解析错误：若发现某个 URL 无法正确提取文章编号或协议被误判，请在 Issues 中附上原始 URL 和期望的输出格式，并标注批次号。

性能优化：索引构建在条目数超过 5000 时可能出现内存压力，欢迎提交使用生成器或分批写入的优化方案，并附上基准测试对比数据。

## 常见问题

问题 1：输入的 URL 中包含大小写混合的路径，索引器会如何处理？

索引器保留 URL 原始格式，包括路径中的大小写。在解析编号时使用正则表达式提取 Article/ 后的数字部分，不改变原始 URL 的字符。输出时完全恢复用户输入的原貌。

问题 2：两个不同域名下出现了相同的文章编号，索引是否会覆盖？

索引器默认以 (domain, article_id) 作为唯一键，不同域名的相同编号会被视为不同条目。若用户希望检测全局重复编号，可在配置中启用 cross_domain_check 选项，此时会在日志中输出警告，但不会阻止索引生成。

问题 3：项目是否会自动访问这些 URL 以验证有效性？

默认情况下不会。build_index.py 仅进行本地字符串解析，不发起任何网络请求。若需要验证可达性，可单独运行 scripts/verify_links.py 脚本，该脚本会使用 requests 库进行 HEAD 请求，但用户需自行承担网络请求的合规责任。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
