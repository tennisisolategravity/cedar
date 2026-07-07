# MapLink 聚合导航系统

MapLink 聚合导航系统是一个面向技术文档、运维手册与开发资源的高密度外链管理平台。本项目定位为技术团队内部或开源社区使用的轻量级资源汇总站，解决海量分散链接的收录、分类、溯源与可访问性管理问题。目标用户包括技术文档工程师、运维人员、全栈开发者以及开源贡献者，帮助其在开发、部署、排障过程中快速定位所需参考文档与历史归档资料。

本项目不提供爬虫或自动化采集功能，仅作为静态资源导航结构的标准实现。所有资源链接以纯文本清单形式维护，便于版本控制、审计追踪与批量健康检查。第 44/80 批次共计收录 250 个资源链接，全部来自生产环境文章映射站点，覆盖移动端适配内容、地图服务技术参考、API 示例文档、运维案例与系统配置手册等类别。通过目录树与标签体系，使用者可在无需数据库支持的条件下完成链接的语义化分组与快速检索。

## 功能概览

- 静态资源清单管理：基于 Markdown 维护全部链接列表，无需后端服务，支持 Git 版本追踪，每次变更可关联 issue 或 PR 记录。

- 多维度分类索引：通过项目结构中的目录层级实现按主题、站点来源、文档类型的三级分类，每个链接自动归属至少一个分类节点。

- 链接状态标注体系：预留状态标记字段，支持在注释中标注有效、失效、待复核、已迁移等状态，便于定期巡检。

- 批量导入与校验：提供链接清单的批量追加与格式校验脚本，自动检测协议头缺失、重复条目与非法字符。

- 自定义元数据扩展：每个链接条目可附加来源批次号、收录日期、关联工单号与简要摘要，适配企业级知识库管理需求。

- 低依赖运行环境：仅依赖标准 POSIX 环境与常见文本处理工具，可在任何支持 Markdown 渲染的平台直接展示，无需编译或安装额外运行时。

- 模块化目录设计：按照数据层、展示层、工具层、文档层与配置层划分目录结构，便于多人协作与职责分离。

- 静态站点生成适配：目录结构与元数据格式兼容主流静态站点生成器，可一键导出为 HTML 文档或 PDF 手册。

## 应用场景

内部技术文档库的导航入口：技术团队可将 MapLink 作为内部 Wiki 的补充导航页，将所有外链参考手册集中存放于一个仓库。当开发人员需要查阅第三方 SDK 文档或运维脚本示例时，可通过目录树快速定位至对应章节，避免频繁切换浏览器标签与搜索引擎检索。

开源项目的资源附录页：开源项目可在 README 或 docs 目录下引用 MapLink 的链接清单，向贡献者提供所有依赖项目、工具链文档、示例代码仓库与社区论坛的直达链接。清单的版本化特性可确保每次 Release 对应的外部资源状态可追溯。

运维故障排查的快速参考手册：运维人员可将日常使用的监控面板地址、日志查询入口、配置模板仓库与应急预案文档以链接形式纳入 MapLink，并按故障类型进行分类。当线上问题发生时，通过目录索引可在 10 秒内定位到相关排查手册或历史案例。

离线文档包的索引页生成：在无网络环境的内部网络中，MapLink 的链接清单可作为离线文档包的索引文件。管理员可将所有链接对应的静态页面或 PDF 文件下载至本地，并保持与清单一致的目录结构，实现内网环境下的完整导航体验。

技术培训与新员工入职引导：培训负责人可为新入职的开发或运维人员准备定制的链接清单，涵盖开发规范、持续集成流程、日志平台、代码评审指南与项目交接文档。新人通过浏览目录结构即可了解团队的技术栈全貌与关键资源位置。

## 快速开始

以下命令演示如何在本地环境中获取并初始化 MapLink 聚合导航系统。

```bash
# 克隆项目仓库至本地
git clone https://github.com/maplink-org/maplink-navigation.git

# 进入项目根目录
cd maplink-navigation

# 安装基础工具链（包含链接校验与格式化脚本）
make install-deps

# 执行链接清单完整性检查，验证全部 250 个资源链接的格式合规性
make validate

# 生成静态导航页面至 output/ 目录
make build
```

执行完上述步骤后，可在浏览器中打开 `output/index.html` 查看导航页面，或直接阅读 `docs/README.md` 获取详细使用说明。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|---|---|---|
| Git | 2.20.0 或更高 | 用于克隆仓库及提交链接变更记录 |
| GNU Make | 3.81 或更高 | 执行构建脚本与校验任务，兼容 Linux/macOS 环境 |
| Python | 3.8 或更高 | 运行链接格式校验器与元数据提取工具，依赖标准库 |
| Bash | 4.0 或更高 | 执行批处理脚本与链接状态检查，需支持关联数组 |
| Markdown 渲染器 | 任意版本 | 推荐使用 CommonMark 兼容实现，用于预览 README 与文档页面 |
| 文本编辑器 | 不限制 | 建议支持 Markdown 语法高亮与 YAML 前端元数据识别 |
| curl 或 wget | 任意版本 | 可选，用于外部链接可达性测试，非构建必需 |
| jq | 1.5 或更高 | 可选，用于 JSON 格式的元数据导出与处理 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 使用层面 | docs/usage/quick-start.md | 如何添加新链接、如何更新已有链接状态、如何生成导航页面 |
| 设计层面 | docs/design/directory-structure.md | 目录层级的设计依据、分类原则、元数据字段定义与扩展预留 |
| 运维层面 | docs/operations/link-health-check.md | 如何配置定时检查脚本、如何解读检查报告、如何处理失效链接 |
| 贡献层面 | docs/contributing/coding-standards.md | 提交 PR 的代码规范、注释格式要求、commit message 模板 |
| 管理层面 | docs/administration/batch-management.md | 批次管理流程、批次号编码规则、批次合并与冲突解决策略 |
| 元数据层面 | docs/schema/link-schema.yaml | 链接条目的完整字段定义，包含类型、枚举值与示例 |

## 资源列表

- http://map.mobile.xqnqq.com/Article/027852.shtml
- http://map.mobile.xqnqq.com/Article/8147705.shtml
- http://map.mobile.xqnqq.com/Article/97281.shtml
- http://map.mobile.xqnqq.com/Article/6513866.shtml
- http://map.read.usuhx.com/Article/028541.shtml
- http://map.mobile.xqnqq.com/Article/420975.shtml
- http://map.mobile.xqnqq.com/Article/518656.shtml
- http://map.mobile.xqnqq.com/Article/5903.shtml
- http://map.mobile.xqnqq.com/Article/0487208.shtml
- http://map.mobile.xqnqq.com/Article/2756252.shtml
- http://map.mobile.xqnqq.com/Article/0292.shtml
- http://map.read.usuhx.com/Article/1578319.shtml
- http://map.mobile.xqnqq.com/Article/7693942.shtml
- http://map.read.usuhx.com/Article/5546.shtml
- http://map.mobile.xqnqq.com/Article/956817.shtml
- http://map.mobile.xqnqq.com/Article/949706.shtml
- http://map.mobile.xqnqq.com/Article/163883.shtml
- http://map.read.usuhx.com/Article/28089.shtml
- http://map.read.usuhx.com/Article/271340.shtml
- http://map.mobile.xqnqq.com/Article/383203.shtml
- http://map.mobile.xqnqq.com/Article/641162.shtml
- http://map.mobile.xqnqq.com/Article/4789200.shtml
- http://map.read.usuhx.com/Article/8140836.shtml
- http://map.mobile.xqnqq.com/Article/295608.shtml
- http://map.read.usuhx.com/Article/9192102.shtml
- http://map.read.usuhx.com/Article/1572903.shtml
- http://map.mobile.xqnqq.com/Article/9997107.shtml
- http://map.read.usuhx.com/Article/9755.shtml
- http://map.read.usuhx.com/Article/6875414.shtml
- http://map.mobile.xqnqq.com/Article/690590.shtml
- http://map.mobile.xqnqq.com/Article/08072.shtml
- http://map.read.usuhx.com/Article/37789.shtml
- http://map.mobile.xqnqq.com/Article/121593.shtml
- http://map.mobile.xqnqq.com/Article/49444.shtml
- http://map.read.usuhx.com/Article/7354.shtml
- http://map.mobile.xqnqq.com/Article/640418.shtml
- http://map.mobile.xqnqq.com/Article/69900.shtml
- http://map.mobile.xqnqq.com/Article/2727.shtml
- http://map.mobile.xqnqq.com/Article/4258743.shtml
- http://map.read.usuhx.com/Article/29407.shtml
- http://map.mobile.xqnqq.com/Article/34902.shtml
- http://map.read.usuhx.com/Article/554309.shtml
- http://map.read.usuhx.com/Article/9127554.shtml
- http://map.mobile.xqnqq.com/Article/824535.shtml
- http://map.mobile.xqnqq.com/Article/89571.shtml
- http://map.read.usuhx.com/Article/52165.shtml
- http://map.read.usuhx.com/Article/35343.shtml
- http://map.read.usuhx.com/Article/0434851.shtml
- http://map.mobile.xqnqq.com/Article/742038.shtml
- http://map.mobile.xqnqq.com/Article/34643.shtml
- http://map.read.usuhx.com/Article/135323.shtml
- http://map.mobile.xqnqq.com/Article/8911884.shtml
- http://map.mobile.xqnqq.com/Article/5708264.shtml
- http://map.mobile.xqnqq.com/Article/31531.shtml
- http://map.mobile.xqnqq.com/Article/9645481.shtml
- http://map.read.usuhx.com/Article/0547791.shtml
- http://map.read.usuhx.com/Article/7074799.shtml
- http://map.read.usuhx.com/Article/69941.shtml
- http://map.read.usuhx.com/Article/140427.shtml
- http://map.mobile.xqnqq.com/Article/5974.shtml
- http://map.mobile.xqnqq.com/Article/3643.shtml
- http://map.mobile.xqnqq.com/Article/5434.shtml
- http://map.read.usuhx.com/Article/3921232.shtml
- http://map.mobile.xqnqq.com/Article/50891.shtml
- http://map.read.usuhx.com/Article/44639.shtml
- http://map.mobile.xqnqq.com/Article/8451834.shtml
- http://map.read.usuhx.com/Article/189578.shtml
- http://map.mobile.xqnqq.com/Article/4444.shtml
- http://map.read.usuhx.com/Article/3038.shtml
- http://map.mobile.xqnqq.com/Article/090023.shtml
- http://map.read.usuhx.com/Article/3996.shtml
- http://map.read.usuhx.com/Article/5673.shtml
- http://map.read.usuhx.com/Article/100010.shtml
- http://map.mobile.xqnqq.com/Article/29867.shtml
- http://map.read.usuhx.com/Article/075784.shtml
- http://map.mobile.xqnqq.com/Article/90850.shtml
- http://map.mobile.xqnqq.com/Article/240486.shtml
- http://map.mobile.xqnqq.com/Article/77406.shtml
- http://map.read.usuhx.com/Article/309816.shtml
- http://map.read.usuhx.com/Article/1763629.shtml
- http://map.mobile.xqnqq.com/Article/4438.shtml
- http://map.mobile.xqnqq.com/Article/159657.shtml
- http://map.mobile.xqnqq.com/Article/6629663.shtml
- http://map.mobile.xqnqq.com/Article/508064.shtml
- http://map.mobile.xqnqq.com/Article/48140.shtml
- http://map.read.usuhx.com/Article/170311.shtml
- http://map.read.usuhx.com/Article/8750.shtml
- http://map.mobile.xqnqq.com/Article/3973.shtml
- http://map.mobile.xqnqq.com/Article/835066.shtml
- http://map.read.usuhx.com/Article/067255.shtml
- http://map.mobile.xqnqq.com/Article/45608.shtml
- http://map.read.usuhx.com/Article/2180012.shtml
- http://map.read.usuhx.com/Article/18456.shtml
- http://map.read.usuhx.com/Article/5420366.shtml
- http://map.read.usuhx.com/Article/0046.shtml
- http://map.mobile.xqnqq.com/Article/776415.shtml
- http://map.read.usuhx.com/Article/082365.shtml
- http://map.mobile.xqnqq.com/Article/80591.shtml
- http://map.mobile.xqnqq.com/Article/148297.shtml
- http://map.mobile.xqnqq.com/Article/1933388.shtml
- http://map.read.usuhx.com/Article/37287.shtml
- http://map.read.usuhx.com/Article/96195.shtml
- http://map.mobile.xqnqq.com/Article/69891.shtml
- http://map.mobile.xqnqq.com/Article/983591.shtml
- http://map.mobile.xqnqq.com/Article/3523039.shtml
- http://map.read.usuhx.com/Article/005978.shtml
- http://map.read.usuhx.com/Article/92971.shtml
- http://map.read.usuhx.com/Article/49276.shtml
- http://map.mobile.xqnqq.com/Article/937807.shtml
- http://map.mobile.xqnqq.com/Article/42741.shtml
- http://map.mobile.xqnqq.com/Article/4223173.shtml
- http://map.read.usuhx.com/Article/373665.shtml
- http://map.mobile.xqnqq.com/Article/1877.shtml
- http://map.read.usuhx.com/Article/6332496.shtml
- http://map.read.usuhx.com/Article/2786093.shtml
- http://map.read.usuhx.com/Article/2312.shtml
- http://map.read.usuhx.com/Article/789919.shtml
- http://map.read.usuhx.com/Article/2741.shtml
- http://map.mobile.xqnqq.com/Article/9131341.shtml
- http://map.read.usuhx.com/Article/7671609.shtml
- http://map.mobile.xqnqq.com/Article/5897.shtml
- http://map.mobile.xqnqq.com/Article/88848.shtml
- http://map.read.usuhx.com/Article/078789.shtml
- http://map.mobile.xqnqq.com/Article/6773352.shtml
- http://map.mobile.xqnqq.com/Article/4351910.shtml
- http://map.read.usuhx.com/Article/2125.shtml
- http://map.read.usuhx.com/Article/2435.shtml
- http://map.read.usuhx.com/Article/612465.shtml
- http://map.read.usuhx.com/Article/0732897.shtml
- http://map.read.usuhx.com/Article/1429.shtml
- http://map.read.usuhx.com/Article/57982.shtml
- http://map.read.usuhx.com/Article/26883.shtml
- http://map.read.usuhx.com/Article/284440.shtml
- http://map.read.usuhx.com/Article/292962.shtml
- http://map.mobile.xqnqq.com/Article/59302.shtml
- http://map.read.usuhx.com/Article/80475.shtml
- http://map.mobile.xqnqq.com/Article/7559667.shtml
- http://map.mobile.xqnqq.com/Article/03997.shtml
- http://map.mobile.xqnqq.com/Article/359639.shtml
- http://map.read.usuhx.com/Article/3200271.shtml
- http://map.read.usuhx.com/Article/41085.shtml
- http://map.read.usuhx.com/Article/812531.shtml
- http://map.mobile.xqnqq.com/Article/4983035.shtml
- http://map.read.usuhx.com/Article/43528.shtml
- http://map.read.usuhx.com/Article/68248.shtml
- http://map.mobile.xqnqq.com/Article/766848.shtml
- http://map.mobile.xqnqq.com/Article/3012.shtml
- http://map.mobile.xqnqq.com/Article/8722675.shtml
- http://map.mobile.xqnqq.com/Article/04254.shtml
- http://map.read.usuhx.com/Article/7664.shtml
- http://map.mobile.xqnqq.com/Article/20085.shtml
- http://map.mobile.xqnqq.com/Article/7340156.shtml
- http://map.read.usuhx.com/Article/1404513.shtml
- http://map.read.usuhx.com/Article/807629.shtml
- http://map.mobile.xqnqq.com/Article/1486431.shtml
- http://map.read.usuhx.com/Article/3098.shtml
- http://map.mobile.xqnqq.com/Article/186431.shtml
- http://map.mobile.xqnqq.com/Article/4093.shtml
- http://map.mobile.xqnqq.com/Article/42372.shtml
- http://map.mobile.xqnqq.com/Article/294354.shtml
- http://map.mobile.xqnqq.com/Article/057269.shtml
- http://map.read.usuhx.com/Article/4622898.shtml
- http://map.read.usuhx.com/Article/39371.shtml
- http://map.read.usuhx.com/Article/838080.shtml
- http://map.read.usuhx.com/Article/34348.shtml
- http://map.read.usuhx.com/Article/786414.shtml
- http://map.mobile.xqnqq.com/Article/74893.shtml
- http://map.read.usuhx.com/Article/102101.shtml
- http://map.read.usuhx.com/Article/461632.shtml
- http://map.mobile.xqnqq.com/Article/058263.shtml
- http://map.read.usuhx.com/Article/7811.shtml
- http://map.read.usuhx.com/Article/74547.shtml
- http://map.read.usuhx.com/Article/9677.shtml
- http://map.read.usuhx.com/Article/68193.shtml
- http://map.mobile.xqnqq.com/Article/785445.shtml
- http://map.mobile.xqnqq.com/Article/675494.shtml
- http://map.read.usuhx.com/Article/91905.shtml
- http://map.mobile.xqnqq.com/Article/2196941.shtml
- http://map.mobile.xqnqq.com/Article/09127.shtml
- http://map.read.usuhx.com/Article/913689.shtml
- http://map.read.usuhx.com/Article/53849.shtml
- http://map.mobile.xqnqq.com/Article/4809.shtml
- http://map.read.usuhx.com/Article/43251.shtml
- http://map.read.usuhx.com/Article/343750.shtml
- http://map.read.usuhx.com/Article/4505.shtml
- http://map.mobile.xqnqq.com/Article/1056777.shtml
- http://map.read.usuhx.com/Article/7463.shtml
- http://map.read.usuhx.com/Article/380249.shtml
- http://map.read.usuhx.com/Article/48437.shtml
- http://map.mobile.xqnqq.com/Article/1408.shtml
- http://map.mobile.xqnqq.com/Article/1364419.shtml
- http://map.read.usuhx.com/Article/385607.shtml
- http://map.mobile.xqnqq.com/Article/938246.shtml
- http://map.read.usuhx.com/Article/1500.shtml
- http://map.read.usuhx.com/Article/7088046.shtml
- http://map.read.usuhx.com/Article/287994.shtml
- http://map.read.usuhx.com/Article/501887.shtml
- http://map.read.usuhx.com/Article/141284.shtml
- http://map.mobile.xqnqq.com/Article/7324.shtml
- http://map.mobile.xqnqq.com/Article/05285.shtml
- http://map.mobile.xqnqq.com/Article/7852811.shtml
- http://map.mobile.xqnqq.com/Article/945997.shtml
- http://map.mobile.xqnqq.com/Article/167320.shtml
- http://map.read.usuhx.com/Article/18370.shtml
- http://map.mobile.xqnqq.com/Article/991529.shtml
- http://map.read.usuhx.com/Article/545117.shtml
- http://map.read.usuhx.com/Article/147186.shtml
- http://map.mobile.xqnqq.com/Article/66679.shtml
- http://map.read.usuhx.com/Article/18845.shtml
- http://map.read.usuhx.com/Article/86995.shtml
- http://map.read.usuhx.com/Article/286957.shtml
- http://map.read.usuhx.com/Article/89111.shtml
- http://map.read.usuhx.com/Article/082388.shtml
- http://map.read.usuhx.com/Article/0984628.shtml
- http://map.read.usuhx.com/Article/0612.shtml
- http://map.mobile.xqnqq.com/Article/50850.shtml
- http://map.mobile.xqnqq.com/Article/014254.shtml
- http://map.mobile.xqnqq.com/Article/4302366.shtml
- http://map.read.usuhx.com/Article/833289.shtml
- http://map.mobile.xqnqq.com/Article/770829.shtml
- http://map.read.usuhx.com/Article/8891080.shtml
- http://map.read.usuhx.com/Article/4027170.shtml
- http://map.mobile.xqnqq.com/Article/67886.shtml
- http://map.mobile.xqnqq.com/Article/756066.shtml
- http://map.mobile.xqnqq.com/Article/25110.shtml
- http://map.read.usuhx.com/Article/8989946.shtml
- http://map.mobile.xqnqq.com/Article/64346.shtml
- http://map.read.usuhx.com/Article/7287.shtml
- http://map.mobile.xqnqq.com/Article/0439746.shtml
- http://map.read.usuhx.com/Article/711381.shtml
- http://map.read.usuhx.com/Article/0506940.shtml
- http://map.read.usuhx.com/Article/45011.shtml
- http://map.read.usuhx.com/Article/8948.shtml
- http://map.mobile.xqnqq.com/Article/627284.shtml
- http://map.read.usuhx.com/Article/2460.shtml
- http://map.read.usuhx.com/Article/00886.shtml
- http://map.read.usuhx.com/Article/6934872.shtml
- http://map.mobile.xqnqq.com/Article/137186.shtml
- http://map.read.usuhx.com/Article/4859.shtml
- http://map.read.usuhx.com/Article/38915.shtml
- http://map.mobile.xqnqq.com/Article/6393.shtml
- http://map.read.usuhx.com/Article/475668.shtml
- http://map.read.usuhx.com/Article/93783.shtml
- http://map.read.usuhx.com/Article/51347.shtml
- http://map.read.usuhx.com/Article/1363.shtml
- http://map.mobile.xqnqq.com/Article/6960609.shtml
- http://map.read.usuhx.com/Article/4636343.shtml
- http://map.mobile.xqnqq.com/Article/7113.shtml
- http://map.read.usuhx.com/Article/8951308.shtml
- http://map.mobile.xqnqq.com/Article/422648.shtml

## 项目结构

```
maplink-navigation/
├── data/                                   # 数据层：存放所有链接清单与元数据
│   ├── batches/                            # 按批次划分的原始链接列表
│   │   ├── batch-044.txt                   # 第44批次原始链接，共250条
│   │   └── batch-045.txt                   # 第45批次预留模板
│   ├── categories/                         # 分类映射表，定义主题与目录的对应关系
│   │   ├── mobile-map.yaml                 # 移动端地图服务分类规则
│   │   └── server-ops.yaml                 # 服务器运维与配置分类规则
│   └── metadata/                           # 链接扩展属性，包含状态与备注
│       ├── status-enum.yaml                # 状态字段枚举定义
│       └── link-annotations.yaml           # 人工添加的摘要与工单关联
├── src/                                    # 源码层：构建与校验脚本
│   ├── validators/                         # 格式与协议校验器
│   │   ├── check-url.py                    # URL 合规性检查脚本
│   │   └── deduplicate.sh                  # 重复条目过滤脚本
│   ├── generators/                         # 导航页面生成器
│   │   ├── render-index.py                 # 生成主索引 HTML
│   │   └── render-category.py              # 按分类生成子页面
│   └── utils/                              # 公共工具函数
│       ├── logger.sh                       # 带时间戳的日志记录函数
│       └── config-loader.py                # 加载 YAML 配置并合并
├── docs/                                   # 文档层：用户手册与设计文档
│   ├── usage/                              # 使用指南
│   │   ├── quick-start.md                  # 快速开始详细版
│   │   └── advanced-tips.md                # 批量操作与 CI 集成
│   ├── design/                             # 设计文档
│   │   ├── directory-structure.md          # 目录设计决策与演进历史
│   │   └── metadata-schema.md              # 元数据字段完整说明
│   ├── operations/                         # 运维文档
│   │   ├── health-check.md                 # 链接健康检查方案
│   │   └── disaster-recovery.md            # 清单损坏恢复流程
│   └── contributing/                       # 贡献指南扩展
│       └── pull-request-template.md        # PR 模板与检查清单
├── output/                                 # 构建输出目录，不纳入版本控制
│   ├── index.html                          # 生成的静态导航首页
│   ├── categories/                         # 分类子页面输出目录
│   └── assets/                             # CSS 与 JavaScript 静态资源
├── tests/                                  # 测试层：单元测试与集成测试
│   ├── test-validators.py                  # 校验器单元测试
│   └── fixtures/                           # 测试用的固定数据样本
│       ├── sample-urls.txt                 # 样本链接列表
│       └── expected-output.html            # 期望生成的 HTML 片段
├── .github/                                # GitHub 专用配置
│   └── workflows/                          # CI 工作流定义
│       ├── validate-on-push.yaml           # 推送时自动校验链接格式
│       └── weekly-health-check.yaml        # 每周定时检查链接可达性
├── Makefile                                # 构建入口，封装常用命令
├── README.md                               # 项目主文档，即本文档
└── LICENSE                                 # MIT 许可证文件
```

## 贡献指南

提交新链接批次或更新现有清单时，请遵循以下标准化流程以确保一致性与可追溯性。

第一步：克隆仓库并创建特性分支。从 main 分支签出新的分支，分支命名格式为 `batch/add-<批次号>` 或 `fix/update-<日期>`，避免直接在主分支操作。

第二步：编辑数据文件。在 `data/batches/` 目录下找到对应的批次文件，按行追加或修改链接。每个链接必须单独占一行，且必须以 `http://` 或 `https://` 开头。若新增整批链接，需同步更新 `data/categories/` 下的分类映射，为新链接指定合理的分类标签。

第三步：运行本地校验。在项目根目录执行 `make validate` 命令，确保所有链接格式正确、无重复条目且分类引用有效。若校验失败，根据错误提示修正后重新执行，直到全部通过。

第四步：更新文档与元数据。若新增链接涉及新的技术领域或站点来源，请在 `data/metadata/link-annotations.yaml` 中添加简要摘要，并在 `docs/design/directory-structure.md` 中评估是否需要调整目录结构。

第五步：提交变更并发起拉取请求。提交信息格式为 `docs(batch): 更新第44批次链接，新增250条资源` 或 `fix(links): 修复失效链接并更新状态标记`。在 PR 描述中附上校验通过的截图或日志，等待至少一名维护者审核后合并。

## 常见问题

问：如何确认一个链接是否仍然有效，以及失效链接应该如何处理？

答：项目提供了每周定时执行的健康检查工作流，会在 GitHub Actions 中自动测试全部链接的可达性。检查结果会生成报告并上传至 Actions 工件。若发现失效链接，建议先访问原站点确认是否为临时故障；若站点已永久迁移或关闭，请在对应批次文件中将该链接行注释或标记为 `[DEPRECATED]`，并在 PR 中说明原因。不建议直接删除链接行，以保留历史记录。

问：新增链接时必须指定分类吗？如果找不到合适的分类怎么办？

答：是的，每个链接必须至少归属于一个分类，否则无法通过校验。若现有分类无法覆盖新链接的主题，请在 `data/categories/` 中新增分类定义文件，并在 `docs/design/directory-structure.md` 中补充该分类的设计说明。新增分类需要同步更新分类枚举列表，并在 PR 中提供充分的理由，以便维护者评审。

问：这个项目是否支持外部链接的自动抓取与内容备份？

答：不支持。MapLink 项目明确定位为静态链接导航系统，不包含爬虫、内容下载或离线缓存功能。所有链接均指向原始第三方站点，项目本身不存储页面内容。若需要离线访问或内容归档，建议使用专用的文档下载工具或浏览器插件，并与 MapLink 的链接清单配合使用。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
