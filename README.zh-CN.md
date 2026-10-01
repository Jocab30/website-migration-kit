# 网站迁移模板

[English](README.md) | [简体中文](README.zh-CN.md) | [日本語](README.ja.md) | [繁體中文](README.zh-HK.md)

用于网站改版的 URL 清单、项目需求、SEO 交付和上线验收模板。示例路径为虚构数据，使用时替换成项目实际内容。

[网站改版流程](https://zequnweb.com/blog/website-redesign-checklist/)（英文）。

## 文件

| 文件 | 用途 |
| --- | --- |
| [url-inventory.csv](url-inventory.csv) | 决定页面保留、迁移、合并或下线，记录责任人和验证结果 |
| [redirect-map.tsv](redirect-map.tsv) | 三条直接重定向样例，与检查器兼容 |
| [project-brief.csv](project-brief.csv) | 整理受众、范围、语言、资料、系统集成和验收标准 |
| [seo-deliverables.csv](seo-deliverables.csv) | 为每项 SEO 工作明确可检查的交付物和责任人 |
| [launch-checklist.csv](launch-checklist.csv) | 检查内容、重定向、索引、表单、设备适配和上线责任 |

默认 CSV 模板为英文。另有三份繁体中文版本：[URL 清单](url-inventory.zh-HK.csv)、[项目需求表](project-brief.zh-HK.csv)、[SEO 交付表](seo-deliverables.zh-HK.csv)。

## 使用顺序

1. 从仓库的代码菜单下载 ZIP 压缩包，或克隆本仓库。
2. 用电子表格打开 CSV 文件。保留有价值的旧 URL，选择相关的新目标，为每项决策指定责任人。
3. 只导出真正需要重定向的页面，保留旧 URL 和目标 URL 两列，以制表符分隔，删除表头，每行一条映射。
4. 用[在线重定向检查器](https://zequnweb.com/tools/redirect-map-checker/)（英文界面）或[本地 JavaScript 版本](https://github.com/awesomellm/redirect-map-checker/blob/main/README.zh-CN.md)检查映射。
5. 在服务器配置规则，再测试实际 HTTP 响应、目标内容、内部链接和索引设置。
6. 在验收表中记录表单投递、上线审批、回退责任和上线后的问题。

**多列 CSV 清单不能直接作为检查器输入。** 保留或下线页面的决策不能粘贴进检查器。仓库中的 `redirect-map.tsv` 已是两列、无表头格式。

## 功能边界

这些文件用于项目规划，不是服务器配置或网站爬虫。它们不会验证生产环境中的重定向，也不保证排名稳定。不要把所有下线页面都重定向到首页；应选择相关的替代页面，没有替代内容时使用适当的未找到响应。

## 参考资料

- [Google：更改网址的网站迁移](https://developers.google.com/search/docs/crawling-indexing/site-move-with-url-changes)
- [ZequnWeb：网站改版检查清单](https://zequnweb.com/blog/website-redesign-checklist/)（英文）

## 参与改进

请提出具体缺失的决策、验收项目或示例。公开提交问题时使用虚构数据。

## 维护者与许可

由独立 B2B 网站设计与开发工作室 [ZequnWeb](https://zequnweb.com/zh/) 整理。模板与文档使用 [MIT 许可证](LICENSE)。
