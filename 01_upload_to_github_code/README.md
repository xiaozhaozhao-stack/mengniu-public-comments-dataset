# mengniu-public-comments-dataset

作者：赵文卓 / Zhao Wenzhuo

本仓库是一个独立的数据仓库，用于展示蒙牛及相关乳品公开评论数据包、TXT 与 JSON 数据来源、清洗报告、样例数据和最终有效语料统计。

它是主项目 [android-ui-tree-review-collector](https://github.com/xiaozhaozhao-stack/android-ui-tree-review-collector) 的支线数据仓库。主库负责 Android UI Tree 公开评论采集方法；本仓库负责蒙牛公开评论数据包、清洗报告和有效语料统计。

## 仓库定位

本仓库 Code 区只保留轻量级说明、统计报告和样例文件，不上传完整原始数据大包。完整压缩包建议通过 GitHub Release 的 Assets 发布。

建议 Release Assets：

- `mengniu_public_comments_full_v0.1.zip`：完整公开评论数据包，包含 TXT 清洗结果、JSON 字段抽取结果、报告和合并语料。
- `json_comments.zip`：补充放入的 JSON 评论清洗结果压缩包。

这两个压缩包如果放在本地仓库目录中，应放在 `release_assets/` 下；该目录已被 `.gitignore` 忽略，不进入 GitHub Code 区。

## 数据包包含什么

完整 Release 数据包建议包含：

- TXT 原始/清洗结果
- JSON 字段抽取结果
- 按文件夹输出的评论结果
- 合并后的评论语料
- 样例评论
- `processing_report.csv`
- `json_comment_processing_report.csv`
- `json_comment_field_report.csv`
- `file_manifest.csv`

本仓库根目录保留这些展示和统计文件：

- `DATASET_INTEGRATED_REPORT.md`
- `dataset_metrics_full.csv`
- `json_field_source_counts.csv`
- `dataset_package_file_list.csv`
- `sample_comments_for_github.txt`
- `NOTICE`
- `LICENSE`

## 数据来源

TXT 数据来源是公开评论页面采集后保存的 `.txt` 文本文件，共 62 个原始 TXT 文件。清洗时按原文件名保留对应结果，并生成 `processing_report.csv` 用于记录每个文件的原始行数、清洗后行数、去重数量和输出路径。

JSON 数据来源是公开评论接口或页面响应保存后的 JSON 文件，共 48 个原始 JSON 文件夹、7,114 个 JSON 文件。清洗时从 `commentData`、`tagCommentContent`、`commentContent`、`eval_content`、`eval_content_input`、`comment` 和经过二次过滤的 `content` 等字段抽取评论正文，并生成 JSON 评论处理报告与字段来源统计。

## 清洗范围

清洗过程面向公开评论正文，主要去除：

- 空行、重复评论和跨来源重复内容
- 页面按钮与标签，例如“展开”“回复”“全部”“好评”“差评”“客服”“加入购物车”
- 商品页导航、价格、物流、店铺、榜单、推荐语等页面杂项
- 用户昵称、疑似用户 ID、链接、手机号、地址、订单或接口痕迹
- JSON 响应中的非评论字段、商家/平台回复、接口元数据和无关商品串入内容

清洗保留原始评论语言形态，包括简体中文、繁体中文、港式中文和粤语评论正文。

## 数据规模

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

## 使用边界

本数据仅用于学习、科研、论文方法展示和公开评论文本分析。不得用于个人识别、骚扰、隐私提取、违规采集、绕过平台限制、商业滥用或任何违反平台规则的用途。

代码和说明文件采用 MIT License。数据使用仍需遵守上述边界、平台规则及适用法律法规。
