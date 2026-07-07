# LinkMap Core

LinkMap Core 是一个面向技术文档聚合与外部资源索引的开源元数据管理工具。该项目定位于帮助开发者、技术写作团队以及知识库维护者以结构化方式收集、分类和引用散布在多个内容源下的文章链接，并提供统一的访问入口与基础分析能力。本项目的目标用户包括需要批量管理外链资源的运维人员、负责技术内容聚合的平台开发者，以及需要对历史文章链接进行归档和可用性校验的数据处理工程师。

LinkMap Core 本身不提供内容存储服务，而是作为外部资源链接的索引层。项目通过规范化的 URL 采集流程，将来源分散的文章链接统一收录为可维护的链接清单，并支持基于该清单进行存活检测、分类标记以及批量导出。本项目包含完整的链接采集与整理工作流配置，适合作为更大规模知识中台或内容聚合系统的外围组件。

## 功能概览

批量链接录入与校验 支持从文本文件或标准输入中批量导入 URL，自动识别重复条目并给出格式异常提示。

域名分级分类 根据 URL 所属域名和路径结构自动划分资源来源，便于按站点进行数据统计与过滤。

存活状态检测 集成 HTTP 请求超时与状态码检查模块，可定期对已收录链接进行可用性探测并输出报告。

自定义元数据标注 允许用户为每条链接添加备注、标签或自定义字段，以适应不同业务场景下的分类需求。

结构化导出 支持将链接清单及元数据导出为 JSON、CSV 或纯文本格式，方便与其他系统进行数据交换。

增量更新机制 支持基于时间戳或版本号进行增量拉取与合并，避免全量重复处理。

配置化的采集规则 提供可编写的正则表达式与路径匹配规则，用于从 URL 中提取文章编号、发布时间等关键信息。

## 应用场景

文档站点外链资产管理 技术文档团队可使用 LinkMap Core 对散布在多篇文档中的外部参考链接进行统一登记，避免链接失效导致文档质量下降。

历史文章归档前检查 在进行站点迁移或内容归档时，运维人员可通过本工具快速获取所有待迁移文章的完整链接列表，并预先检测其中不可达的 URL。

内容聚合平台的数据源维护 内容聚合类应用可将 LinkMap Core 作为外部数据源管理模块，定期同步并校验合作方或采集源的文章链接有效性。

技术资源导航站构建 知识库维护者可以利用本项目的链接清单功能，快速生成按主题或来源分类的资源导航页的基础数据。

## 快速开始

以下命令演示了从克隆仓库到运行基础链接采集流程的完整步骤。

```bash
git clone https://github.com/linkmap/core.git
cd linkmap-core
pip install -r requirements.txt
cp config.example.yaml config.yaml
python cli.py import --source urls.txt --output inventory.json
python cli.py check --input inventory.json --timeout 5 --report report.csv
```

上述操作会导入 `urls.txt` 中的链接清单，执行存活检测，并将结果输出到 `report.csv` 文件中。若需自定义导入格式或检测并发数，可编辑 `config.yaml` 文件中的对应参数。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行时环境，建议使用 3.11 以获取更好性能 |
| requests | 2.28.0 及以上 | 用于发送 HTTP 请求进行链接存活检测 |
| pyyaml | 6.0 及以上 | 用于解析配置文件 config.yaml |
| click | 8.1.0 及以上 | 提供命令行交互界面，支持子命令分组 |
| urllib3 | 1.26.0 及以上 | 作为 requests 的底层依赖，用于连接池管理 |
| pytest | 7.2.0 及以上 | 仅在开发测试环境中需要，用于运行单元测试 |
| flake8 | 6.0.0 及以上 | 代码风格检查工具，仅在开发阶段使用 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user/quickstart.md | 如何安装、配置并运行第一次链接导入与检测 |
| 用户手册 | docs/user/import.md | 支持哪些导入格式，如何自定义字段映射 |
| 用户手册 | docs/user/check.md | 存活检测的原理、参数调优与报告解读 |
| 开发者指南 | docs/dev/architecture.md | 项目的模块划分、数据流向与扩展接口 |
| 开发者指南 | docs/dev/api.md | 核心类与函数的 API 说明，用于二次开发 |
| 运维参考 | docs/ops/deployment.md | 生产环境下的部署建议、日志配置与定时任务设置 |
| 运维参考 | docs/ops/troubleshooting.md | 常见错误码含义及网络环境问题排查步骤 |

## 资源列表

- http://map.read.usuhx.com/Article/720590.shtml
- http://map.read.usuhx.com/Article/4359.shtml
- http://map.read.usuhx.com/Article/8318863.shtml
- http://map.read.usuhx.com/Article/9205981.shtml
- http://map.mobile.xqnqq.com/Article/5154813.shtml
- http://map.mobile.xqnqq.com/Article/941284.shtml
- http://map.read.usuhx.com/Article/227012.shtml
- http://map.mobile.xqnqq.com/Article/153313.shtml
- http://map.mobile.xqnqq.com/Article/0491498.shtml
- http://map.mobile.xqnqq.com/Article/7445773.shtml
- http://map.read.usuhx.com/Article/138595.shtml
- http://map.mobile.xqnqq.com/Article/1044476.shtml
- http://map.mobile.xqnqq.com/Article/97716.shtml
- http://map.mobile.xqnqq.com/Article/34360.shtml
- http://map.mobile.xqnqq.com/Article/789815.shtml
- http://map.read.usuhx.com/Article/634710.shtml
- http://map.read.usuhx.com/Article/4650585.shtml
- http://map.mobile.xqnqq.com/Article/1459.shtml
- http://map.read.usuhx.com/Article/411426.shtml
- http://map.mobile.xqnqq.com/Article/594277.shtml
- http://map.read.usuhx.com/Article/29418.shtml
- http://map.mobile.xqnqq.com/Article/5513.shtml
- http://map.mobile.xqnqq.com/Article/61533.shtml
- http://map.read.usuhx.com/Article/5057.shtml
- http://map.mobile.xqnqq.com/Article/04742.shtml
- http://map.mobile.xqnqq.com/Article/65509.shtml
- http://map.mobile.xqnqq.com/Article/5291.shtml
- http://map.read.usuhx.com/Article/13286.shtml
- http://map.read.usuhx.com/Article/70119.shtml
- http://map.read.usuhx.com/Article/7548.shtml
- http://map.mobile.xqnqq.com/Article/2682.shtml
- http://map.mobile.xqnqq.com/Article/19212.shtml
- http://map.mobile.xqnqq.com/Article/785831.shtml
- http://map.read.usuhx.com/Article/4027.shtml
- http://map.read.usuhx.com/Article/3140164.shtml
- http://map.mobile.xqnqq.com/Article/1241.shtml
- http://map.read.usuhx.com/Article/3151011.shtml
- http://map.mobile.xqnqq.com/Article/786461.shtml
- http://map.mobile.xqnqq.com/Article/8651.shtml
- http://map.read.usuhx.com/Article/47817.shtml
- http://map.read.usuhx.com/Article/77953.shtml
- http://map.read.usuhx.com/Article/469706.shtml
- http://map.read.usuhx.com/Article/3099.shtml
- http://map.read.usuhx.com/Article/1023796.shtml
- http://map.read.usuhx.com/Article/799496.shtml
- http://map.mobile.xqnqq.com/Article/255249.shtml
- http://map.read.usuhx.com/Article/6204336.shtml
- http://map.read.usuhx.com/Article/7138530.shtml
- http://map.read.usuhx.com/Article/7125.shtml
- http://map.read.usuhx.com/Article/013322.shtml
- http://map.read.usuhx.com/Article/8064773.shtml
- http://map.read.usuhx.com/Article/875700.shtml
- http://map.mobile.xqnqq.com/Article/9337.shtml
- http://map.read.usuhx.com/Article/5310216.shtml
- http://map.read.usuhx.com/Article/7108.shtml
- http://map.read.usuhx.com/Article/2081.shtml
- http://map.mobile.xqnqq.com/Article/55553.shtml
- http://map.mobile.xqnqq.com/Article/994900.shtml
- http://map.mobile.xqnqq.com/Article/6669887.shtml
- http://map.read.usuhx.com/Article/64038.shtml
- http://map.read.usuhx.com/Article/17955.shtml
- http://map.mobile.xqnqq.com/Article/30840.shtml
- http://map.mobile.xqnqq.com/Article/2035901.shtml
- http://map.mobile.xqnqq.com/Article/256346.shtml
- http://map.mobile.xqnqq.com/Article/60781.shtml
- http://map.mobile.xqnqq.com/Article/9993.shtml
- http://map.read.usuhx.com/Article/30618.shtml
- http://map.mobile.xqnqq.com/Article/2407349.shtml
- http://map.mobile.xqnqq.com/Article/4006845.shtml
- http://map.read.usuhx.com/Article/39634.shtml
- http://map.mobile.xqnqq.com/Article/4331.shtml
- http://map.mobile.xqnqq.com/Article/4485345.shtml
- http://map.mobile.xqnqq.com/Article/4114.shtml
- http://map.read.usuhx.com/Article/6907.shtml
- http://map.read.usuhx.com/Article/07723.shtml
- http://map.mobile.xqnqq.com/Article/947297.shtml
- http://map.read.usuhx.com/Article/7254287.shtml
- http://map.read.usuhx.com/Article/7763358.shtml
- http://map.read.usuhx.com/Article/2032.shtml
- http://map.mobile.xqnqq.com/Article/2019.shtml
- http://map.mobile.xqnqq.com/Article/26331.shtml
- http://map.mobile.xqnqq.com/Article/77598.shtml
- http://map.read.usuhx.com/Article/48284.shtml
- http://map.read.usuhx.com/Article/626681.shtml
- http://map.read.usuhx.com/Article/2283975.shtml
- http://map.mobile.xqnqq.com/Article/28311.shtml
- http://map.mobile.xqnqq.com/Article/6288.shtml
- http://map.read.usuhx.com/Article/3510.shtml
- http://map.mobile.xqnqq.com/Article/2877570.shtml
- http://map.read.usuhx.com/Article/40102.shtml
- http://map.mobile.xqnqq.com/Article/7508394.shtml
- http://map.mobile.xqnqq.com/Article/0163505.shtml
- http://map.mobile.xqnqq.com/Article/2082.shtml
- http://map.mobile.xqnqq.com/Article/144642.shtml
- http://map.mobile.xqnqq.com/Article/75659.shtml
- http://map.mobile.xqnqq.com/Article/4217.shtml
- http://map.mobile.xqnqq.com/Article/4269.shtml
- http://map.mobile.xqnqq.com/Article/2004910.shtml
- http://map.read.usuhx.com/Article/42674.shtml
- http://map.mobile.xqnqq.com/Article/3401443.shtml
- http://map.mobile.xqnqq.com/Article/7521803.shtml
- http://map.read.usuhx.com/Article/723654.shtml
- http://map.read.usuhx.com/Article/1528628.shtml
- http://map.mobile.xqnqq.com/Article/2153.shtml
- http://map.read.usuhx.com/Article/0187694.shtml
- http://map.read.usuhx.com/Article/819819.shtml
- http://map.read.usuhx.com/Article/1146.shtml
- http://map.mobile.xqnqq.com/Article/6550875.shtml
- http://map.read.usuhx.com/Article/7261.shtml
- http://map.read.usuhx.com/Article/4335846.shtml
- http://map.mobile.xqnqq.com/Article/99537.shtml
- http://map.read.usuhx.com/Article/7674701.shtml
- http://map.read.usuhx.com/Article/763139.shtml
- http://map.mobile.xqnqq.com/Article/8952.shtml
- http://map.read.usuhx.com/Article/71884.shtml
- http://map.read.usuhx.com/Article/889002.shtml
- http://map.read.usuhx.com/Article/796013.shtml
- http://map.read.usuhx.com/Article/8599758.shtml
- http://map.read.usuhx.com/Article/7501.shtml
- http://map.read.usuhx.com/Article/348691.shtml
- http://map.read.usuhx.com/Article/2279.shtml
- http://map.read.usuhx.com/Article/6604080.shtml
- http://map.mobile.xqnqq.com/Article/178854.shtml
- http://map.mobile.xqnqq.com/Article/8496817.shtml
- http://map.read.usuhx.com/Article/73774.shtml
- http://map.mobile.xqnqq.com/Article/150610.shtml
- http://map.read.usuhx.com/Article/7469.shtml
- http://map.mobile.xqnqq.com/Article/3588.shtml
- http://map.mobile.xqnqq.com/Article/916889.shtml
- http://map.read.usuhx.com/Article/6704042.shtml
- http://map.read.usuhx.com/Article/9238.shtml
- http://map.read.usuhx.com/Article/6376563.shtml
- http://map.read.usuhx.com/Article/7494.shtml
- http://map.read.usuhx.com/Article/4276800.shtml
- http://map.read.usuhx.com/Article/0772.shtml
- http://map.read.usuhx.com/Article/456290.shtml
- http://map.read.usuhx.com/Article/291093.shtml
- http://map.read.usuhx.com/Article/9507.shtml
- http://map.mobile.xqnqq.com/Article/5699.shtml
- http://map.read.usuhx.com/Article/405917.shtml
- http://map.mobile.xqnqq.com/Article/4447709.shtml
- http://map.mobile.xqnqq.com/Article/634144.shtml
- http://map.read.usuhx.com/Article/021351.shtml
- http://map.read.usuhx.com/Article/0527305.shtml
- http://map.mobile.xqnqq.com/Article/64434.shtml
- http://map.read.usuhx.com/Article/49193.shtml
- http://map.mobile.xqnqq.com/Article/7901744.shtml
- http://map.mobile.xqnqq.com/Article/1996884.shtml
- http://map.mobile.xqnqq.com/Article/99491.shtml
- http://map.mobile.xqnqq.com/Article/9060812.shtml
- http://map.read.usuhx.com/Article/3304.shtml
- http://map.mobile.xqnqq.com/Article/5074261.shtml
- http://map.mobile.xqnqq.com/Article/442437.shtml
- http://map.read.usuhx.com/Article/149802.shtml
- http://map.mobile.xqnqq.com/Article/179538.shtml
- http://map.mobile.xqnqq.com/Article/27700.shtml
- http://map.read.usuhx.com/Article/9501862.shtml
- http://map.read.usuhx.com/Article/088249.shtml
- http://map.read.usuhx.com/Article/06945.shtml
- http://map.mobile.xqnqq.com/Article/3540.shtml
- http://map.read.usuhx.com/Article/6808.shtml
- http://map.read.usuhx.com/Article/2954998.shtml
- http://map.read.usuhx.com/Article/4607085.shtml
- http://map.mobile.xqnqq.com/Article/3950.shtml
- http://map.mobile.xqnqq.com/Article/9233458.shtml
- http://map.mobile.xqnqq.com/Article/56968.shtml
- http://map.read.usuhx.com/Article/8425512.shtml
- http://map.mobile.xqnqq.com/Article/2804.shtml
- http://map.mobile.xqnqq.com/Article/745137.shtml
- http://map.mobile.xqnqq.com/Article/377912.shtml
- http://map.mobile.xqnqq.com/Article/06309.shtml
- http://map.read.usuhx.com/Article/5698682.shtml
- http://map.mobile.xqnqq.com/Article/4429652.shtml
- http://map.read.usuhx.com/Article/381308.shtml
- http://map.mobile.xqnqq.com/Article/253484.shtml
- http://map.read.usuhx.com/Article/179150.shtml
- http://map.mobile.xqnqq.com/Article/630228.shtml
- http://map.read.usuhx.com/Article/446774.shtml
- http://map.read.usuhx.com/Article/2642.shtml
- http://map.mobile.xqnqq.com/Article/46222.shtml
- http://map.mobile.xqnqq.com/Article/703371.shtml
- http://map.mobile.xqnqq.com/Article/4069829.shtml
- http://map.mobile.xqnqq.com/Article/6581.shtml
- http://map.mobile.xqnqq.com/Article/849672.shtml
- http://map.mobile.xqnqq.com/Article/085839.shtml
- http://map.mobile.xqnqq.com/Article/1070.shtml
- http://map.read.usuhx.com/Article/2301.shtml
- http://map.read.usuhx.com/Article/5014.shtml
- http://map.mobile.xqnqq.com/Article/4390.shtml
- http://map.read.usuhx.com/Article/6093645.shtml
- http://map.mobile.xqnqq.com/Article/9271061.shtml
- http://map.read.usuhx.com/Article/450338.shtml
- http://map.read.usuhx.com/Article/858525.shtml
- http://map.mobile.xqnqq.com/Article/11120.shtml
- http://map.read.usuhx.com/Article/76036.shtml
- http://map.read.usuhx.com/Article/4587208.shtml
- http://map.read.usuhx.com/Article/62380.shtml
- http://map.mobile.xqnqq.com/Article/0459.shtml
- http://map.mobile.xqnqq.com/Article/1010.shtml
- http://map.read.usuhx.com/Article/7781259.shtml
- http://map.mobile.xqnqq.com/Article/7236008.shtml
- http://map.mobile.xqnqq.com/Article/56428.shtml
- http://map.read.usuhx.com/Article/43839.shtml
- http://map.mobile.xqnqq.com/Article/7948.shtml
- http://map.read.usuhx.com/Article/842061.shtml
- http://map.mobile.xqnqq.com/Article/72928.shtml
- http://map.read.usuhx.com/Article/4618.shtml
- http://map.mobile.xqnqq.com/Article/3349.shtml
- http://map.mobile.xqnqq.com/Article/226243.shtml
- http://map.mobile.xqnqq.com/Article/558717.shtml
- http://map.read.usuhx.com/Article/14784.shtml
- http://map.mobile.xqnqq.com/Article/02871.shtml
- http://map.mobile.xqnqq.com/Article/982808.shtml
- http://map.mobile.xqnqq.com/Article/0685270.shtml
- http://map.mobile.xqnqq.com/Article/00371.shtml
- http://map.read.usuhx.com/Article/8831.shtml
- http://map.mobile.xqnqq.com/Article/35102.shtml
- http://map.read.usuhx.com/Article/218709.shtml
- http://map.mobile.xqnqq.com/Article/3885.shtml
- http://map.mobile.xqnqq.com/Article/969957.shtml
- http://map.read.usuhx.com/Article/3436.shtml
- http://map.mobile.xqnqq.com/Article/118481.shtml
- http://map.mobile.xqnqq.com/Article/6990542.shtml
- http://map.read.usuhx.com/Article/2468025.shtml
- http://map.mobile.xqnqq.com/Article/308289.shtml
- http://map.mobile.xqnqq.com/Article/780802.shtml
- http://map.mobile.xqnqq.com/Article/5856927.shtml
- http://map.mobile.xqnqq.com/Article/9211734.shtml
- http://map.mobile.xqnqq.com/Article/854422.shtml
- http://map.mobile.xqnqq.com/Article/6477681.shtml
- http://map.mobile.xqnqq.com/Article/054200.shtml
- http://map.read.usuhx.com/Article/68959.shtml
- http://map.mobile.xqnqq.com/Article/18281.shtml
- http://map.read.usuhx.com/Article/597047.shtml
- http://map.mobile.xqnqq.com/Article/087772.shtml
- http://map.mobile.xqnqq.com/Article/5450037.shtml
- http://map.read.usuhx.com/Article/072381.shtml
- http://map.mobile.xqnqq.com/Article/392439.shtml
- http://map.mobile.xqnqq.com/Article/5170911.shtml
- http://map.mobile.xqnqq.com/Article/49837.shtml
- http://map.mobile.xqnqq.com/Article/142450.shtml
- http://map.mobile.xqnqq.com/Article/8596.shtml
- http://map.mobile.xqnqq.com/Article/7620.shtml
- http://map.read.usuhx.com/Article/1804.shtml
- http://map.mobile.xqnqq.com/Article/2397.shtml
- http://map.read.usuhx.com/Article/1733.shtml
- http://map.mobile.xqnqq.com/Article/62355.shtml
- http://map.mobile.xqnqq.com/Article/101345.shtml
- http://map.mobile.xqnqq.com/Article/97154.shtml
- http://map.mobile.xqnqq.com/Article/99048.shtml

## 项目结构

```
linkmap-core/
├── cli.py                 # 命令行入口，注册所有子命令
├── config.yaml.example    # 配置文件模板，包含超时、并发数、日志级别等
├── requirements.txt       # Python 依赖清单，锁定主要版本
├── src/                   # 核心源码目录
│   ├── core/              # 核心业务逻辑模块
│   │   ├── importer.py    # 实现链接导入与格式解析
│   │   ├── checker.py     # 实现存活检测与状态报告生成
│   │   └── manager.py     # 链接清单的增删改查与元数据管理
│   ├── utils/             # 通用工具函数
│   │   ├── http.py        # 封装 requests 会话与重试策略
│   │   └── logger.py      # 日志格式化与输出控制
│   └── models/            # 数据模型定义
│       ├── link.py        # Link 类，包含 URL、来源、标签、检测时间等字段
│       └── report.py      # 检测报告的数据结构
├── tests/                 # 单元测试目录
│   ├── test_importer.py   # 导入模块的测试用例
│   └── test_checker.py    # 检测模块的测试用例
├── docs/                  # 文档目录
│   ├── user/              # 用户手册
│   └── dev/               # 开发者指南
└── scripts/               # 辅助脚本
    └── batch_import.sh    # 用于批量导入历史链接的 shell 脚本
```

## 贡献指南

提交 Issue 报告缺陷或功能请求 访问 GitHub Issues 页面，使用提供的模板描述问题或需求，并附上必要的日志或复现步骤。

创建功能分支进行开发 从 main 分支切出新的 feature 分支，命名格式为 `feature/简要描述` 或 `fix/问题编号`。

编写或更新单元测试 所有新增或修改的代码必须覆盖对应的单元测试用例，确保测试通过率为 100%。

提交 Pull Request 前进行自检 运行 `flake8 src/` 检查代码风格，执行 `pytest tests/` 确认所有测试通过，并在 PR 描述中关联相关 Issue。

更新文档 若改动涉及用户可见的功能或配置变更，需同步更新 docs/ 目录下对应的手册章节。

## 常见问题

问题：导入链接时提示格式解析失败，但我的文件内容看起来正常。

回答：请检查文件编码是否为 UTF-8，并确认每行仅包含一个 URL。若文件包含 BOM 头或非打印字符，可使用 `dos2unix` 工具转换。此外，可尝试使用 `--format plain` 参数强制以纯文本方式读取。

问题：存活检测返回大量超时错误，如何调整？

回答：检测超时默认设置为 5 秒。若网络环境较差，可在 config.yaml 中增大 `check.timeout` 值，并适当降低 `check.concurrent` 并发数。同时建议检查是否存在防火墙或代理限制。

问题：如何只检测特定来源域名的链接？

回答：可使用 `--filter` 参数传入域名关键词，例如 `--filter usuhx.com` 仅检测该域名下的链接。该过滤功能适用于导入和检测两个子命令。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
