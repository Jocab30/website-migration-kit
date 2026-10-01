# 网站迁移完整实战示例

[English](MIGRATION.md) | [简体中文](MIGRATION.zh-CN.md) | [日本語](MIGRATION.ja.md) | [繁體中文](MIGRATION.zh-HK.md)

本例把 `/old-contact.html` 迁移到 `/contact/`，把 `/company-profile.html` 合并到 `/about/`，并下线 `/expired-campaign/`。这些路径都是虚构数据。部署后还要检查实际响应和目标内容，才能完成验收。

## 1. 先决定页面去向，再写规则

填写 [URL 清单](url-inventory.zh-CN.csv)，记录旧 URL、处理方式、最终目标、理由、责任人及实测结果。有价值且不需要迁移的页面可以保留原 URL；已迁移页面指向相关的新内容；没有合适替代内容的下线页面应返回适当的 404 或 410，而不是统一跳到首页。

仍有用途的推广参数可以保留，废弃参数应通过明确规则处理。路径、大小写、查询参数、尾斜线都需要分别核对，映射检查器会把它们视为不同 URL。

## 2. 只导出真正需要跳转的映射

```text
/old-contact.html	/contact/
/company-profile.html	/about/
```

两列之间是制表符。不要带表头、其他清单列、原样保留的页面或 404/410 决策。[redirect-map.tsv](redirect-map.tsv) 是可以直接检查的示例。

克隆[本地检查器](https://github.com/awesomellm/redirect-map-checker/blob/main/README.zh-CN.md)，在检查器目录中指定导出文件路径运行：

```sh
node check.mjs ../website-migration-kit/redirect-map.tsv https://example.com
```

修正循环、目标冲突和中间跳转，人工确认外部目标。映射关系没有问题，不代表服务器已经使用这些规则。

## 3. 在实际托管层配置

按[配置教程](https://github.com/awesomellm/redirect-map-checker/blob/main/DEPLOYMENT.zh-CN.md)选择 Cloudflare、Nginx 或 Apache。规则中的精确路径和最终目标应与已确认的清单一致，具体规则放在宽泛规则之前。先在预览环境验证，保留旧配置，指定回退责任人。

内部链接、规范 URL、导航、语言切换和网站地图直接指向最终页面。重定向用于接住旧链接，站内新内容也应同步使用新地址。

## 4. 部署后检查实际 GET 响应

```sh
curl -sS -D - -o /dev/null 'https://example.com/old-contact.html?utm_source=test'
curl -sS -L --max-redirs 5 -D - -o /dev/null 'https://example.com/old-contact.html?utm_source=test'
```

第一条命令显示初始状态和 `Location`，第二条显示跳转链。把示例域名换成你管理的网站，核对永久跳转状态、参数处理、最终 200 响应以及内容相关性。下线路径单独测试。还要用手机操作目标页面，并向自己控制的接收端提交约定的测试询盘。

## 5. 保存验收和后续观察

填写[上线验收表](launch-checklist.zh-CN.csv)、[询盘验收表](inquiry-acceptance.zh-CN.csv)和[跟踪计划](tracking-plan.zh-CN.csv)。记录测试 URL、时间、结果、证据及责任人。上线后立即检查重要旧地址、导航和接收系统，之后按天及周观察实际 404、网站地图处理和相关页面的搜索索引。比较完整的报告窗口，短期波动不能直接证明成功或失败。

## 6. 交接到可操作的程度

交付[账号与项目交接表](handover-checklist.zh-CN.csv)、已确认清单、实际规则、测试结果和回退步骤。企业应知道谁管理域名、托管、内容和询盘接收。本文提供规划与验证流程，不会部署规则，也不保证搜索排名。

[Google 网站迁移说明](https://developers.google.com/search/docs/crawling-indexing/site-move-with-url-changes?hl=zh-CN) · [ZequnWeb 中文网站](https://zequnweb.com/zh/)
