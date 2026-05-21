# GitHub Upload Guide

仓库名称：`mengniu-public-comments-dataset`

作者：赵文卓 / Zhao Wenzhuo

## 1. 上传到 GitHub Code 区

请把 `01_upload_to_github_code/` 里面的文件上传到 GitHub 仓库根目录。

这个目录包含：

- `README.md`
- `DATASET_INTEGRATED_REPORT.md`
- `dataset_metrics_full.csv`
- `json_field_source_counts.csv`
- `dataset_package_file_list.csv`
- `sample_comments_for_github.txt`
- `NOTICE`
- `LICENSE`
- `.gitignore`

不要把 `02_upload_to_github_release_assets/` 上传到 Code 区。

## 2. 上传到 GitHub Release Assets

在 GitHub 仓库页面新建 Release，例如 `v0.1`，然后把 `02_upload_to_github_release_assets/` 里的两个压缩包上传到 Release Assets：

- `mengniu_public_comments_full_v0.1.zip`
- `json_comments.zip`

## 3. 仓库说明

主库负责 Android UI Tree 公开评论采集方法；本仓库负责蒙牛公开评论数据包、清洗报告和有效语料统计。

主项目链接：https://github.com/xiaozhaozhao-stack/android-ui-tree-review-collector

## 4. 数据使用边界

本数据仅用于学习、科研、论文方法展示和公开评论文本分析。不得用于个人识别、骚扰、隐私提取、违规采集或违反平台规则的用途。
