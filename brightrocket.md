# WebIndex Gateway

WebIndex Gateway 是一个面向技术文献与移动端内容聚合的轻量级外链索引与管理平台，专为需要批量维护、分类展示和快速检索外部文章链接的开发者与内容运营者设计。该项目定位于技术资源导航与富外链站点构建，通过结构化数据组织与静态生成策略，将大量散落的文章链接转化为可维护、可浏览、可分享的知识索引体系。

项目核心目标用户包括开源技术文档维护者、个人知识管理实践者以及小型团队内部资源整理负责人。WebIndex Gateway 不提供内容存储服务，而是专注于链接的规范化收录、标签化分类与多维度筛选展示，解决在信息碎片化环境下链接散落、遗忘、失效与检索困难的问题。

## 功能概览

链接规范化入库，自动去重与格式校验
对收录的每一篇外链文章执行头信息抓取与基础元数据提取，支持标题、发布时间与来源域名的自动补全。

多级分类与标签体系
允许为每个链接分配多个分类标签，支持无限层级的目录结构，便于构建从宽泛主题到具体技术栈的导航路径。

全文检索与高级筛选
内置基于关键词的标题与内容摘要检索能力，同时支持按域名、文件类型、时间范围等多条件组合过滤。

批量导入导出与外部数据同步
提供 CSV 与 JSON 格式的批量链接导入导出接口，支持通过定时任务从指定数据源同步新增链接。

响应式前端展示模板
面向桌面与移动设备自适应的列表与卡片视图，支持按最近更新、热度与自定义排序规则展示链接集合。

访问统计与链接可用性监测
记录每个外链的点击次数与最后访问时间，定期执行链接可达性检测，标记失效或响应异常的资源。

用户自定义视图与收藏夹
注册用户可创建个人收藏夹与自定义导航面板，将高频使用的链接分组置顶，提升日常查阅效率。

## 应用场景

技术团队内部知识库外链聚合
开发团队可将日常参考的技术博客、官方文档、API 手册与问题修复讨论帖统一收录至 WebIndex Gateway，按项目或技术栈分类，新成员入职时可快速了解团队常用资源脉络。

个人技术写作素材管理与参考溯源
技术博主与内容创作者在撰写文章时，可将调研过程中查阅的参考文献、数据来源与延伸阅读链接统一入库，后续写作时通过关键词检索快速定位原始资料，避免重复搜索。

开源项目文档站的外链附录生成
开源项目维护者可在项目文档中嵌入 WebIndex Gateway 生成的静态链接列表页面，作为“相关资源”或“延伸阅读”章节的自动化数据源，保持外链附录与收录数据实时同步。

课程与培训材料配套资源导航
教育机构或培训讲师可将课程各章节推荐的课外阅读、实验指导与视频教程链接按教学单元组织，生成独立的资源导航站点供学员课后查阅。

## 快速开始

以下指令适用于 Linux 与 macOS 环境，Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
git clone https://github.com/webindex-gateway/webindex-gateway.git
cd webindex-gateway

# 安装项目依赖
npm install

# 构建生产版本
npm run build

# 启动服务，默认监听 3000 端口
npm start
```

启动后访问 http://localhost:3000 即可进入管理界面。首次启动将自动创建 SQLite 数据库文件与默认管理员账户，管理员密码将在终端日志中输出，请及时修改。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 18.x 或 20.x LTS | 运行时环境，推荐使用官方预编译二进制或 nvm 管理 |
| npm | 9.x 或更高 | 随 Node.js 一并安装，用于依赖管理与脚本执行 |
| SQLite3 | 3.35 或更高 | 嵌入式数据库，生产环境建议使用系统级安装以提升性能 |
| Git | 2.25 或更高 | 用于克隆仓库与版本管理，非运行时必需但开发必需 |
| Nginx 或 Caddy | 推荐 1.20+ | 生产环境反向代理与静态资源缓存，非必需但强烈建议 |
| PM2 | 5.x 或更高 | 生产环境进程守护工具，用于保持服务持续运行 |
| curl / wget | 任意版本 | 用于链接可用性检测模块的外部请求，系统通常预装 |
| libsqlite3-dev | 对应系统版本 | 若使用 SQLite 编译扩展，需安装开发头文件，Linux 下通过包管理器获取 |
| Python 3.9+ | 仅构建文档索引时需要 | 用于可选的文本摘要生成模块，非核心功能依赖 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|-----|------|-----------|
| 入门指南 | /docs/getting-started.md | 如何快速完成首次部署、创建第一个链接分类并收录首批外链 |
| 配置参考 | /docs/configuration.md | 环境变量、配置文件结构与各模块开关参数的完整说明 |
| API 手册 | /docs/api-reference.md | 面向开发者与管理员的 RESTful API 端点、请求示例与响应格式 |
| 部署运维 | /docs/deployment.md | 生产环境下的进程管理、日志轮转、数据库备份与监控告警配置 |
| 数据格式 | /docs/data-format.md | 链接导入导出的 JSON 与 CSV 结构定义、字段映射与扩展字段说明 |
| 前端定制 | /docs/frontend-customization.md | 主题切换、模板变量与自定义页面的开发指南 |

## 资源列表

- http://map.read.usuhx.com/Article/4018.shtml
- http://map.mobile.xqnqq.com/Article/2146.shtml
- http://map.read.usuhx.com/Article/1089219.shtml
- http://map.mobile.xqnqq.com/Article/1732.shtml
- http://map.read.usuhx.com/Article/612233.shtml
- http://map.mobile.xqnqq.com/Article/4849646.shtml
- http://map.read.usuhx.com/Article/43573.shtml
- http://map.mobile.xqnqq.com/Article/300836.shtml
- http://map.mobile.xqnqq.com/Article/8063.shtml
- http://map.mobile.xqnqq.com/Article/955496.shtml
- http://map.mobile.xqnqq.com/Article/58482.shtml
- http://map.read.usuhx.com/Article/55791.shtml
- http://map.read.usuhx.com/Article/210418.shtml
- http://map.mobile.xqnqq.com/Article/6588.shtml
- http://map.read.usuhx.com/Article/716268.shtml
- http://map.mobile.xqnqq.com/Article/86880.shtml
- http://map.mobile.xqnqq.com/Article/8964987.shtml
- http://map.read.usuhx.com/Article/97604.shtml
- http://map.mobile.xqnqq.com/Article/417293.shtml
- http://map.mobile.xqnqq.com/Article/3962668.shtml
- http://map.mobile.xqnqq.com/Article/59044.shtml
- http://map.mobile.xqnqq.com/Article/0526.shtml
- http://map.mobile.xqnqq.com/Article/3762.shtml
- http://map.read.usuhx.com/Article/98110.shtml
- http://map.read.usuhx.com/Article/991250.shtml
- http://map.mobile.xqnqq.com/Article/6292390.shtml
- http://map.read.usuhx.com/Article/7672392.shtml
- http://map.mobile.xqnqq.com/Article/99232.shtml
- http://map.mobile.xqnqq.com/Article/045887.shtml
- http://map.mobile.xqnqq.com/Article/2625306.shtml
- http://map.read.usuhx.com/Article/297167.shtml
- http://map.mobile.xqnqq.com/Article/387828.shtml
- http://map.read.usuhx.com/Article/5491.shtml
- http://map.mobile.xqnqq.com/Article/17897.shtml
- http://map.mobile.xqnqq.com/Article/706743.shtml
- http://map.mobile.xqnqq.com/Article/1668.shtml
- http://map.mobile.xqnqq.com/Article/468677.shtml
- http://map.mobile.xqnqq.com/Article/93760.shtml
- http://map.read.usuhx.com/Article/448772.shtml
- http://map.read.usuhx.com/Article/720651.shtml
- http://map.read.usuhx.com/Article/5920.shtml
- http://map.mobile.xqnqq.com/Article/5778.shtml
- http://map.mobile.xqnqq.com/Article/658026.shtml
- http://map.mobile.xqnqq.com/Article/8808869.shtml
- http://map.read.usuhx.com/Article/8898.shtml
- http://map.read.usuhx.com/Article/2327978.shtml
- http://map.mobile.xqnqq.com/Article/044387.shtml
- http://map.mobile.xqnqq.com/Article/5581.shtml
- http://map.read.usuhx.com/Article/806332.shtml
- http://map.read.usuhx.com/Article/187207.shtml
- http://map.read.usuhx.com/Article/950115.shtml
- http://map.mobile.xqnqq.com/Article/3886085.shtml
- http://map.mobile.xqnqq.com/Article/39154.shtml
- http://map.read.usuhx.com/Article/728092.shtml
- http://map.read.usuhx.com/Article/948932.shtml
- http://map.read.usuhx.com/Article/8144.shtml
- http://map.read.usuhx.com/Article/4012518.shtml
- http://map.mobile.xqnqq.com/Article/6323059.shtml
- http://map.read.usuhx.com/Article/30369.shtml
- http://map.mobile.xqnqq.com/Article/54675.shtml
- http://map.read.usuhx.com/Article/6431.shtml
- http://map.mobile.xqnqq.com/Article/5163.shtml
- http://map.read.usuhx.com/Article/1236.shtml
- http://map.read.usuhx.com/Article/4481.shtml
- http://map.read.usuhx.com/Article/20955.shtml
- http://map.mobile.xqnqq.com/Article/98347.shtml
- http://map.read.usuhx.com/Article/6215423.shtml
- http://map.read.usuhx.com/Article/1051126.shtml
- http://map.mobile.xqnqq.com/Article/892080.shtml
- http://map.read.usuhx.com/Article/8170.shtml
- http://map.read.usuhx.com/Article/1895712.shtml
- http://map.read.usuhx.com/Article/01119.shtml
- http://map.mobile.xqnqq.com/Article/4162.shtml
- http://map.mobile.xqnqq.com/Article/618276.shtml
- http://map.read.usuhx.com/Article/1824.shtml
- http://map.read.usuhx.com/Article/770726.shtml
- http://map.read.usuhx.com/Article/2269.shtml
- http://map.mobile.xqnqq.com/Article/65339.shtml
- http://map.read.usuhx.com/Article/9200877.shtml
- http://map.mobile.xqnqq.com/Article/0365.shtml
- http://map.read.usuhx.com/Article/7540982.shtml
- http://map.read.usuhx.com/Article/2040.shtml
- http://map.read.usuhx.com/Article/048262.shtml
- http://map.mobile.xqnqq.com/Article/68009.shtml
- http://map.read.usuhx.com/Article/87812.shtml
- http://map.mobile.xqnqq.com/Article/47362.shtml
- http://map.read.usuhx.com/Article/4044.shtml
- http://map.mobile.xqnqq.com/Article/5278.shtml
- http://map.read.usuhx.com/Article/01348.shtml
- http://map.read.usuhx.com/Article/79482.shtml
- http://map.mobile.xqnqq.com/Article/7506638.shtml
- http://map.mobile.xqnqq.com/Article/0394821.shtml
- http://map.read.usuhx.com/Article/2057551.shtml
- http://map.read.usuhx.com/Article/81956.shtml
- http://map.read.usuhx.com/Article/8021201.shtml
- http://map.read.usuhx.com/Article/2988.shtml
- http://map.read.usuhx.com/Article/24143.shtml
- http://map.read.usuhx.com/Article/140686.shtml
- http://map.read.usuhx.com/Article/8631.shtml
- http://map.read.usuhx.com/Article/54330.shtml
- http://map.read.usuhx.com/Article/0662536.shtml
- http://map.mobile.xqnqq.com/Article/8520864.shtml
- http://map.mobile.xqnqq.com/Article/81443.shtml
- http://map.mobile.xqnqq.com/Article/04234.shtml
- http://map.mobile.xqnqq.com/Article/2138247.shtml
- http://map.read.usuhx.com/Article/89839.shtml
- http://map.mobile.xqnqq.com/Article/871597.shtml
- http://map.mobile.xqnqq.com/Article/6728.shtml
- http://map.mobile.xqnqq.com/Article/7164720.shtml
- http://map.read.usuhx.com/Article/169058.shtml
- http://map.mobile.xqnqq.com/Article/763457.shtml
- http://map.mobile.xqnqq.com/Article/44580.shtml
- http://map.read.usuhx.com/Article/486049.shtml
- http://map.read.usuhx.com/Article/1001.shtml
- http://map.mobile.xqnqq.com/Article/2766715.shtml
- http://map.mobile.xqnqq.com/Article/9034615.shtml
- http://map.read.usuhx.com/Article/064321.shtml
- http://map.mobile.xqnqq.com/Article/35902.shtml
- http://map.mobile.xqnqq.com/Article/18759.shtml
- http://map.read.usuhx.com/Article/872531.shtml
- http://map.mobile.xqnqq.com/Article/193223.shtml
- http://map.mobile.xqnqq.com/Article/3289953.shtml
- http://map.read.usuhx.com/Article/379154.shtml
- http://map.read.usuhx.com/Article/4015.shtml
- http://map.read.usuhx.com/Article/076289.shtml
- http://map.read.usuhx.com/Article/47809.shtml
- http://map.mobile.xqnqq.com/Article/514639.shtml
- http://map.read.usuhx.com/Article/82755.shtml
- http://map.read.usuhx.com/Article/8525.shtml
- http://map.read.usuhx.com/Article/921098.shtml
- http://map.read.usuhx.com/Article/233631.shtml
- http://map.read.usuhx.com/Article/283840.shtml
- http://map.read.usuhx.com/Article/1938.shtml
- http://map.read.usuhx.com/Article/15293.shtml
- http://map.read.usuhx.com/Article/7335.shtml
- http://map.mobile.xqnqq.com/Article/3207718.shtml
- http://map.read.usuhx.com/Article/8877704.shtml
- http://map.mobile.xqnqq.com/Article/82116.shtml
- http://map.mobile.xqnqq.com/Article/3286197.shtml
- http://map.mobile.xqnqq.com/Article/174295.shtml
- http://map.read.usuhx.com/Article/8222.shtml
- http://map.mobile.xqnqq.com/Article/3456.shtml
- http://map.mobile.xqnqq.com/Article/5785904.shtml
- http://map.mobile.xqnqq.com/Article/2580822.shtml
- http://map.read.usuhx.com/Article/325691.shtml
- http://map.read.usuhx.com/Article/58517.shtml
- http://map.mobile.xqnqq.com/Article/2039.shtml
- http://map.mobile.xqnqq.com/Article/9618971.shtml
- http://map.mobile.xqnqq.com/Article/963026.shtml
- http://map.mobile.xqnqq.com/Article/374986.shtml
- http://map.read.usuhx.com/Article/6446.shtml
- http://map.read.usuhx.com/Article/15435.shtml
- http://map.read.usuhx.com/Article/23290.shtml
- http://map.mobile.xqnqq.com/Article/0620.shtml
- http://map.read.usuhx.com/Article/863479.shtml
- http://map.mobile.xqnqq.com/Article/3039.shtml
- http://map.mobile.xqnqq.com/Article/6547978.shtml
- http://map.read.usuhx.com/Article/9723.shtml
- http://map.mobile.xqnqq.com/Article/0888.shtml
- http://map.mobile.xqnqq.com/Article/261550.shtml
- http://map.read.usuhx.com/Article/47138.shtml
- http://map.read.usuhx.com/Article/8871721.shtml
- http://map.read.usuhx.com/Article/16110.shtml
- http://map.read.usuhx.com/Article/6494975.shtml
- http://map.mobile.xqnqq.com/Article/52337.shtml
- http://map.read.usuhx.com/Article/7289688.shtml
- http://map.read.usuhx.com/Article/6935607.shtml
- http://map.read.usuhx.com/Article/8740.shtml
- http://map.read.usuhx.com/Article/1389.shtml
- http://map.mobile.xqnqq.com/Article/2799569.shtml
- http://map.read.usuhx.com/Article/540730.shtml
- http://map.mobile.xqnqq.com/Article/9657488.shtml
- http://map.read.usuhx.com/Article/7107723.shtml
- http://map.mobile.xqnqq.com/Article/2507.shtml
- http://map.read.usuhx.com/Article/6389597.shtml
- http://map.read.usuhx.com/Article/291815.shtml
- http://map.mobile.xqnqq.com/Article/936468.shtml
- http://map.read.usuhx.com/Article/7667.shtml
- http://map.read.usuhx.com/Article/3699859.shtml
- http://map.read.usuhx.com/Article/66866.shtml
- http://map.mobile.xqnqq.com/Article/385398.shtml
- http://map.read.usuhx.com/Article/5941.shtml
- http://map.read.usuhx.com/Article/6506610.shtml
- http://map.read.usuhx.com/Article/244277.shtml
- http://map.read.usuhx.com/Article/0412396.shtml
- http://map.mobile.xqnqq.com/Article/9651.shtml
- http://map.read.usuhx.com/Article/8582.shtml
- http://map.mobile.xqnqq.com/Article/496683.shtml
- http://map.mobile.xqnqq.com/Article/4708.shtml
- http://map.read.usuhx.com/Article/13958.shtml
- http://map.mobile.xqnqq.com/Article/562611.shtml
- http://map.read.usuhx.com/Article/5833.shtml
- http://map.mobile.xqnqq.com/Article/7526877.shtml
- http://map.read.usuhx.com/Article/2218.shtml
- http://map.mobile.xqnqq.com/Article/654285.shtml
- http://map.mobile.xqnqq.com/Article/7650.shtml
- http://map.read.usuhx.com/Article/2705.shtml
- http://map.mobile.xqnqq.com/Article/221367.shtml
- http://map.mobile.xqnqq.com/Article/3368389.shtml
- http://map.read.usuhx.com/Article/7740.shtml
- http://map.read.usuhx.com/Article/9838.shtml
- http://map.mobile.xqnqq.com/Article/471314.shtml
- http://map.read.usuhx.com/Article/0939.shtml
- http://map.mobile.xqnqq.com/Article/8545405.shtml
- http://map.read.usuhx.com/Article/499496.shtml
- http://map.read.usuhx.com/Article/0801989.shtml
- http://map.mobile.xqnqq.com/Article/540283.shtml
- http://map.read.usuhx.com/Article/5863254.shtml
- http://map.read.usuhx.com/Article/6062943.shtml
- http://map.read.usuhx.com/Article/6519.shtml
- http://map.read.usuhx.com/Article/0180.shtml
- http://map.read.usuhx.com/Article/9677264.shtml
- http://map.read.usuhx.com/Article/8283320.shtml
- http://map.mobile.xqnqq.com/Article/00430.shtml
- http://map.mobile.xqnqq.com/Article/71301.shtml
- http://map.read.usuhx.com/Article/73223.shtml
- http://map.mobile.xqnqq.com/Article/28966.shtml
- http://map.mobile.xqnqq.com/Article/517130.shtml
- http://map.mobile.xqnqq.com/Article/1458.shtml
- http://map.mobile.xqnqq.com/Article/496211.shtml
- http://map.mobile.xqnqq.com/Article/2048.shtml
- http://map.mobile.xqnqq.com/Article/526998.shtml
- http://map.read.usuhx.com/Article/914889.shtml
- http://map.mobile.xqnqq.com/Article/439025.shtml
- http://map.read.usuhx.com/Article/40838.shtml
- http://map.read.usuhx.com/Article/70872.shtml
- http://map.mobile.xqnqq.com/Article/72824.shtml
- http://map.read.usuhx.com/Article/9112.shtml
- http://map.read.usuhx.com/Article/671767.shtml
- http://map.mobile.xqnqq.com/Article/245035.shtml
- http://map.mobile.xqnqq.com/Article/5269.shtml
- http://map.read.usuhx.com/Article/1389492.shtml
- http://map.mobile.xqnqq.com/Article/277945.shtml
- http://map.read.usuhx.com/Article/420715.shtml
- http://map.read.usuhx.com/Article/6877061.shtml
- http://map.mobile.xqnqq.com/Article/59621.shtml
- http://map.mobile.xqnqq.com/Article/449019.shtml
- http://map.mobile.xqnqq.com/Article/978334.shtml
- http://map.read.usuhx.com/Article/3253411.shtml
- http://map.mobile.xqnqq.com/Article/89169.shtml
- http://map.mobile.xqnqq.com/Article/5314.shtml
- http://map.mobile.xqnqq.com/Article/0754094.shtml
- http://map.read.usuhx.com/Article/02144.shtml
- http://map.mobile.xqnqq.com/Article/8634.shtml
- http://map.read.usuhx.com/Article/8522307.shtml
- http://map.mobile.xqnqq.com/Article/0131.shtml
- http://map.read.usuhx.com/Article/2788.shtml
- http://map.read.usuhx.com/Article/35494.shtml
- http://map.mobile.xqnqq.com/Article/265655.shtml
- http://map.read.usuhx.com/Article/2822.shtml

## 项目结构

```
webindex-gateway/
├── src/                                # 核心源代码目录
│   ├── core/                           # 核心业务逻辑模块
│   │   ├── crawler.js                  # 链接元数据抓取与解析引擎
│   │   ├── dedup.js                    # 链接去重与规范化校验器
│   │   └── health.js                   # 链接可达性监测与状态报告
│   ├── api/                            # RESTful API 路由与控制器
│   │   ├── v1/                         # API 版本 v1 端点实现
│   │   │   ├── links.js                # 链接增删改查及筛选接口
│   │   │   ├── categories.js           # 分类管理与树形结构接口
│   │   │   └── stats.js                # 访问统计与健康数据接口
│   │   └── middleware/                 # 认证、日志与限流中间件
│   ├── services/                       # 数据服务与外部集成层
│   │   ├── database.js                 # SQLite 连接池与查询构建器
│   │   ├── search.js                   # 全文检索引擎封装
│   │   └── sync.js                     # 批量导入导出与同步服务
│   ├── web/                            # 前端展示与管理界面
│   │   ├── views/                      # EJS 模板视图文件
│   │   │   ├── layouts/                # 基础布局与导航模板
│   │   │   └── partials/               # 卡片、列表与分页组件
│   │   └── static/                     # CSS、JavaScript 与字体资源
│   │       ├── css/                    # 响应式样式表与主题变量
│   │       └── js/                     # 前端交互与数据请求逻辑
│   └── utils/                          # 通用工具函数与常量定义
│       ├── validators.js               # URL 与数据格式校验器
│       └── formatters.js               # 日期、大小写与编码转换工具
├── config/                             # 环境配置与默认参数
│   ├── default.yaml                    # 默认配置项，包含端口、数据库路径与超时阈值
│   ├── production.yaml                 # 生产环境覆盖配置
│   └── development.yaml                # 开发环境覆盖配置
├── data/                               # 数据存储目录
│   ├── db/                             # SQLite 数据库文件存放位置
│   └── cache/                          # 链接元数据与检索索引缓存
├── scripts/                            # 运维与工具脚本
│   ├── init-db.js                      # 首次启动数据库初始化与默认数据填充
│   ├── backup.js                       # 数据库与配置备份脚本
│   └── migrate.js                      # 数据结构版本迁移工具
├── tests/                              # 单元测试与集成测试
│   ├── unit/                           # 针对核心模块的单元测试用例
│   └── integration/                    # API 与数据库交互的集成测试
├── docs/                               # 项目文档目录
│   ├── getting-started.md              # 入门指南
│   ├── configuration.md                # 配置参考手册
│   └── api-reference.md                # API 详细说明与示例
├── .env.example                        # 环境变量配置模板
├── package.json                        # npm 依赖声明与脚本入口
├── README.md                           # 项目总览与快速入门（本文件）
└── LICENSE                             # MIT 许可证文本
```

## 贡献指南

提交 Issue 报告缺陷或功能请求前，请先查阅现有 Issue 列表避免重复，并提供清晰的重现步骤、运行环境版本与相关日志片段。

Fork 本仓库并创建功能分支，分支命名采用 feature/功能简述 或 fix/问题简述 格式，确保与主分支保持同步。

编写代码时遵循项目内置的 ESLint 与 Prettier 配置，提交前执行 npm run lint 与 npm run test 确保代码风格与测试用例均通过。

提交 Pull Request 时，请在描述中说明修改动机、实现方案与测试覆盖情况，并关联相关的 Issue 编号。重大功能变更需附带更新后的文档说明。

接受贡献后，提交者将被列入项目贡献者列表，并可在项目官网的贡献者页面中展示个人主页链接。

## 常见问题

Q: 首次启动后管理员密码在哪里查看？
A: 首次运行 npm start 后，终端日志中会输出一行包含初始管理员账户与随机生成密码的信息，格式为 Admin account created: admin / 随机密码。请复制该密码完成首次登录，随后在个人设置页面中修改为强密码。若日志滚动过快，可查看 data/db/ 目录下的初始化日志文件。

Q: 如何迁移现有链接数据至新部署的实例？
A: 使用项目提供的导入功能，将已有链接数据整理为符合 data-format.md 中定义的 JSON 数组格式，通过管理界面中的“批量导入”功能上传，或使用 curl 调用 /api/v1/links/import 接口提交。导入前建议先执行导出备份操作，避免数据覆盖丢失。

Q: 链接可用性检测模块的检测频率与超时时间如何调整？
A: 检测频率与超时阈值在 config/default.yaml 中的 healthChecker 字段下配置，interval 参数控制检测间隔（单位秒），timeout 参数控制单次请求超时时间（单位毫秒）。修改后重启服务生效。若检测任务积压，可适当调大 interval 值或增加 worker 线程数。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 00:32:20
