# Public Comments Dataset

作者：赵文卓 / Zhao Wenzhuo

## 数据清洗流程图 / 文本流程图

下面展示从原始候选文本到最终有效评论的清洗流程：

![文本流程图](assets/文本流程图.png)

> 这不是一个只放几个样例的演示仓库。  
> 这是我把 TXT 与 JSON 两类公开评论候选数据整理、清洗、去噪、去重、合并后形成的数据成果仓库。  
> 主库负责采集方法，本仓库负责展示数据包结构、清洗报告、字段统计、样例评论和有效语料规模。

关联主项目：

```text
https://github.com/xiaozhaozhao-stack/android-ui-tree-review-collector
```

---

## 项目一句话

本仓库是 **Android UI Tree Review Collector** 的支线数据仓库，用于展示公开评论数据包、TXT/JSON 清洗报告、字段来源统计、样例评论和最终有效语料规模。

主库负责：

```text
Android UI Tree 公开评论采集方法
采集脚本
运行流程
UI Tree / OCR 扩展思路
```

本仓库负责：

```text
蒙牛公开评论数据包
TXT 清洗报告
JSON 字段抽取结果
样例评论
数据规模统计
最终有效语料说明
```

---

## 数据规模：从 21.61 万条候选文本清洗到 4.94 万条有效评论

本数据包不是简单保存一堆原始文本，而是经过了清洗、过滤、去重和合并。

| 来源 / 阶段 | 数量 |
|---|---:|
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

一句话概括：

```text
从 21.61 万条原始候选评论/页面文本中，
经过页面噪声过滤、无意义短句删除、文件内去重和全局去重，
最终形成 4.94 万条有效公开评论语料。
```

这就是这个数据仓库最核心的价值：  
**不是“我有数据”，而是“我把一大堆脏数据清洗成了可以用于分析的有效语料”。**

---

## 数据清洗流程图

如果你上传了流程图，可以放在这里：

```markdown
![Dataset Cleaning Funnel](assets/dataset-cleaning-funnel.png)
```

建议图片文件名：

```text
assets/dataset-cleaning-funnel.png
```

---

## 数据包里到底有什么

本仓库展示的数据包包含：

```text
TXT 原始/清洗结果
JSON 字段抽取结果
按文件夹输出的评论结果
合并后的评论语料
样例评论
processing_report.csv
json_comment_processing_report.csv
json_comment_field_report.csv
file_manifest.csv
```

推荐仓库结构：

```text
mengniu-public-comments-dataset/
├── README.md
├── DATASET_INTEGRATED_REPORT.md
├── dataset_metrics_full.csv
├── json_field_source_counts.csv
├── dataset_package_file_list.csv
├── sample_comments_for_github.txt
├── NOTICE
├── LICENSE
└── assets/
    └── dataset-cleaning-funnel.png
```

完整原始数据包建议放在 GitHub Release 附件中：

```text
mengniu_public_comments_full_v0.1.zip
```

---

## TXT 数据来源说明

TXT 部分主要来自手机端公开评论页面整理结果。

| 指标 | 数量 |
|---|---:|
| TXT 原始文件数 | 62 个 |
| TXT 原始行数 | 92,637 条 |
| TXT 文件内清洗后行数 | 41,284 条 |
| TXT 文件内去重删除数量 | 17,857 条 |
| TXT 合并后唯一评论数 | 28,429 条 |

TXT 原始文本中不仅有评论正文，也会混入：

```text
页面按钮
筛选标签
价格信息
规格参数
时间信息
浏览量
短标签
重复文本
非评论正文
```

所以它不能直接拿来分析，必须先清洗。

---

## JSON 数据来源说明

JSON 部分主要来自不同字段中的评论候选文本抽取。

| 指标 | 数量 |
|---|---:|
| JSON 原始文件夹数 | 48 个 |
| JSON 文件数 | 7,114 个 |
| 可解析 JSON 文件数 | 6,960 个 |
| JSON 抽取候选评论数 | 123,430 条 |
| JSON 清洗后候选评论数 | 45,917 条 |
| JSON 文件夹内去重删除数量 | 21,944 条 |
| JSON 合并后唯一评论数 | 21,063 条 |

JSON 字段并不统一，不同来源里的评论可能藏在不同字段中，所以需要统一抽取、清洗和合并。

---

## JSON 字段来源统计

| 字段名 | 抽取原始值数量 |
|---|---:|
| content | 53,631 |
| tagCommentContent | 15,074 |
| commentData | 15,074 |
| eval_content | 12,075 |
| eval_content_input | 12,075 |
| comment | 10,653 |
| commentContent | 4,848 |

这说明数据不是单一来源、单一格式，而是需要从多个字段中抽取候选评论，再统一整理成可分析语料。

---

## 清洗到底清洗掉了什么

清洗和过滤内容包括：

```text
空行
重复评论
页面按钮
筛选标签
商品价格
规格参数
时间信息
浏览量信息
物流/页面提示
无意义短句
非评论正文
明显页面杂项
```

原始候选文本中有大量页面噪声。  
如果不清洗，后续做 TF-IDF、词频统计、感官词映射时，结果会被“全部、好评、差评、查看更多、价格、规格”等杂项污染。

因此，这个数据包的重点不是“堆数量”，而是：

```text
大规模候选文本
↓
规则清洗
↓
去噪
↓
去重
↓
合并
↓
形成可用于分析的有效评论语料
```

---

## 为什么这个数据仓库有价值

对于本科生、课程项目或没有企业接口的数据分析研究来说，最难的往往不是模型，而是数据。

常见困难包括：

```text
没有企业合作接口
拿不到平台级大规模评论数据
网页端可见评论数量有限
手机端手动复制效率极低
不同 App 页面结构不一致
原始文本混有大量页面噪声
```

本项目的意义在于：

```text
1. 使用公开可见评论文本作为研究基础；
2. 整合 TXT 与 JSON 两类候选数据；
3. 保留清洗报告和字段统计，过程可追溯；
4. 从 21.61 万条原始候选文本中清洗出 4.94 万条有效评论；
5. 为乳品感官词提取、TF-IDF 分析和消费者评论研究提供基础语料。
```

这不是随便复制几条评论。  
这是一个从数据采集、候选抽取、规则清洗、噪声过滤、去重合并到统计展示的完整数据整理流程。

---

## 可以用于什么

本数据仓库可用于：

```text
乳品消费者评论研究
液态奶感官词提取
TF-IDF 关键词分析
评论文本清洗示例
本科论文方法展示
公开评论语料整理流程演示
```

可以支持的问题包括：

```text
消费者如何描述奶香、口感、甜味、浓淡、新鲜度？
哪些词更常出现在乳品评论中？
公开评论能否辅助构建消费者感官评价维度？
大规模评论文本如何从页面噪声中清洗成有效语料？
```

---

## 与主项目的关系

主项目：

```text
android-ui-tree-review-collector
```

主项目地址：

```text
https://github.com/xiaozhaozhao-stack/android-ui-tree-review-collector
```

关系说明：

```text
主库：采集工具、UI Tree 方法、运行流程、OCR 备用思路
本库：蒙牛公开评论数据包、清洗报告、统计结果、样例评论
```

简单说：

```text
主库证明：我能采集和整理公开评论文本
本库证明：我真实整理过一批有规模的数据，并完成了清洗去噪和有效语料构建
```

---

## 文件说明

| 文件 | 作用 |
|---|---|
| DATASET_INTEGRATED_REPORT.md | 完整数据包整合说明 |
| dataset_metrics_full.csv | 数据规模统计表 |
| json_field_source_counts.csv | JSON 字段来源统计 |
| dataset_package_file_list.csv | 数据包文件清单 |
| sample_comments_for_github.txt | 少量样例评论 |
| mengniu_public_comments_full_v0.1.zip | 完整原始数据包，建议放 Release 附件 |

---

## 完整数据包下载

完整原始数据包建议放在 GitHub Release 中：

```text
Releases → v0.1-mengniu-dataset → Assets
```

文件名建议：

```text
mengniu_public_comments_full_v0.1.zip
```

说明：

```text
Code 页面放说明、统计表和样例数据；
Release 附件放完整原始数据包。
```

这样既能展示完整成果，又不会让仓库主页变得混乱。

---

## 合规边界

本数据仅用于：

```text
学习
科研
论文方法展示
公开评论文本分析
```

不得用于：

```text
个人识别
骚扰
隐私提取
违规采集
违反平台规则的用途
```

公开发布前应去除或避免暴露：

```text
昵称
手机号
地址
订单信息
配送信息
私信内容
账号数据
其他个人敏感信息
```

---

## 作者说明

本数据仓库由赵文卓 / Zhao Wenzhuo 整理。

```text
Author: 赵文卓 / Zhao Wenzhuo
Dataset: Mengniu Public Comments Dataset
Related Project: Android UI Tree Review Collector
```

如果你使用、引用、修改或二次发布本项目，请保留作者署名。
