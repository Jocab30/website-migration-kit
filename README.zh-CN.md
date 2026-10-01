# 网站迁移模板

用于网站改版的 URL 清单、项目需求、SEO 交付和上线验收模板。示例路径为虚构数据，使用时替换成项目实际内容。

[English](README.md) · [网站改版流程](https://zequnweb.com/blog/website-redesign-checklist/)

## 文件

- `url-inventory.csv`：页面保留、迁移或退休决策，以及责任人和验证记录。
- `redirect-map.tsv`：两列、无表头的重定向样例，可用于检查器。
- `project-brief.csv`：目标客户、范围、语言、资料、系统和验收标准。
- `seo-deliverables.csv`：SEO 工作对应的交付物和验收方式。
- `launch-checklist.csv`：迁移、索引、表单、移动端、回退和上线后检查。
- `.zh-HK.csv`：URL 清单、需求表和 SEO 验收表的繁体中文版本。

## 使用顺序

下载文件 → 填写 URL 决策 → 为真正迁移的页面选择相关目标 → 导出旧 URL 和新 URL 两列 TSV → [检查循环与冲突](https://zequnweb.com/tools/redirect-map-checker/) → 配置服务器 → 验证生产环境响应。

多列、有表头的 CSV 清单不能直接粘贴进检查器。保留和退休页面不属于重定向输入。检查器只看计划关系，上线后仍需验证实际状态码、内容、canonical、内链和索引设置。

由 [ZequnWeb](https://zequnweb.com/zh/) 维护，模板与文档使用 [MIT 许可证](LICENSE)。
