# Dataset Integrated Report

作者：赵文卓 / Zhao Wenzhuo

## 项目关系

本数据仓库是主项目 `android-ui-tree-review-collector` 的支线数据仓库。主项目关注 Android UI Tree 公开评论采集方法，本仓库关注蒙牛公开评论数据包、清洗报告、样例数据和有效语料统计。

主项目链接：https://github.com/xiaozhaozhao-stack/android-ui-tree-review-collector

## 数据来源

数据来自两类公开评论采集结果：

- TXT 来源：根目录公开评论文本文件，共 62 个原始 TXT 文件。
- JSON 来源：子文件夹公开评论 API 或页面响应，共 48 个原始 JSON 文件夹、7,114 个 JSON 文件。

JSON 评论抽取字段包括 `commentData`、`tagCommentContent`、`commentContent`、`eval_content`、`eval_content_input`、`comment` 和经过二次过滤的 `content` 字段。

## 清洗范围

清洗去除了空行、重复评论、页面标签、商品页噪声、商家回复、接口元数据、用户 ID、链接、手机号、地址和明显非评论内容。清洗保留中文评论正文，并保留原始数据中已有的繁体中文、港式中文和粤语表达。

## 核心指标

| 指标 | 数值 |
| --- | ---: |
| TXT 原始文件数 | 62 个 |
| JSON 原始文件夹数 | 48 个 |
| JSON 文件数 | 7,114 个 |
| TXT 原始候选文本 | 92,637 条 |
| JSON 原始候选文本 | 123,430 条 |
| 综合原始候选文本 | 216,067 条，约 21.61 万条 |
| 清洗后候选文本 | 87,201 条，约 8.72 万条 |
| 最终全局去重后有效评论 | 49,367 条，约 4.94 万条 |
| 过滤/剔除噪声与重复内容 | 166,700 条 |
| 最终有效保留率 | 22.85% |

## Release Asset 建议

完整数据压缩包建议放在 GitHub Release 的 Assets 中，不放入 Code 区。建议上传：

- `mengniu_public_comments_full_v0.1.zip`
- `json_comments.zip`

Code 区仅保留本报告、指标 CSV、字段来源统计、包文件清单和小样例评论。仓库中的 `release_assets/` 目录只作为本地整理与手动上传 Release 的暂存位置，已通过 `.gitignore` 排除。
