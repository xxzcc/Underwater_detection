# 赛事基本信息

[toc]

赛题链接：https://www.kesci.com/home/competition/5e535a612537a0002ca864ac/content/2

参赛成员：
李智敏 华中科技大学 研一

罗文斌 电子科技大学 研一
艾宏峰 曼切斯特大学 应届研究生


## 赛事背景

“水下目标检测算法赛”属于2020年全国水下机器人（湛江）大赛的线上赛，本次算法赛由国家自然科学基金委员会、鹏城实验室和湛江市人民政府主办，将面向国内及海外各院校和科研机构、科技企业招募优秀选手，深化和拓宽水下机器人和水下目标检测领域的相关研究，推进算法技术向实际产业应用进行赋能。

## 算法赛日程

报名阶段：2020-2-25 (12:00:00 中午） 至 2020-4-10 (12:00:00 中午）

**初赛阶段：2020-2-28 (12:00:00 中午） 至 2020-4-11 (12:00:00 中午）**

综合评审：2020-4-13 (12:00:00 中午） 至 2020-4-17 (12:00:00 中午）

线上答辩：4 月 21 日 - 4 月 22 日（暂定）

## 赛题

- 初赛任务：在真实海底图片数据中检测出不同海产品（海参、海胆、扇贝、海星）的位置
- 线上答辩：采取网上远程答辩，形式包括PPT、视频等进行展示。由评委提问、打分决定最终排名。

## 数据描述

**1、初赛训练集：**

初赛训练集：提供5543幅训练图像（含人工标注真值数据），数据集结构如下，

| 一级目录 | 二级目录                   | 解释说明     | 格式 |
| -------- | -------------------------- | ------------ | ---- |
| train/   | image/                     | 所有训练图片 | jpg  |
| box/     | 同名图像文件的对应标注结果 | xml          |      |

 其中train/image文件夹中包含所有训练数据，这些图片之间不存在帧间连续性。

 图片路径示例如下：train/image/000001.jpg，其对应的目标检测标注真值位于路径 train/box/000001.xml文件中，该文件包含了对应图像中所有物体的类别以及目标框参数（位置和尺寸）。

 本届比赛需检测的目标类别包括**海参“holothurian”**，**海胆“echinus”**，**扇贝****“scallop”**和**海星“starfish”**四类。训练数据真值中可能存在**水草“waterweeds”**这一类别，请忽略这一类。比赛不限制参赛队伍使用其他来源的数据进行预训练/训练。

**2、初赛测试集：**

A榜测试集：800幅测试图像，详见数据下载

B榜测试集：1200幅测试图像（与A榜不重复），详见数据下载

## 评审规则

### **一、初赛评审**

#### **1、客观评审**

#####  **1）精度评审**

  **评测方法：**

- **初赛阶段的评审采用COCO mAP[@0.5:0.05:0.95] 指标（mean Average Precision) 进行计算，即将10个不同IOU阈值下的mAP取平均值作为最终结果**
- 对于任意一IOU阈值，其对应的mAP计算公式如下：

   ![img](https://cdn.kesci.com/upload/images/q6dahoe9r.png)

   ![img](https://cdn.kesci.com/upload/images/q66we7v4n.png)

   ![img](https://cdn.kesci.com/upload/images/q66wemel2.png)

- p(r) 为当召回率（recall）为r时，检测结果的准确率(precision)
- [mAP指标的基本介绍](https://github.com/rafaelpadilla/Object-Detection-Metrics)
- AP (Average Precision) 的计算方式采用PASCAL VOC 2010年之后的版本，关于该版本的mAP细节和原理参考[The PASCAL Visual Object Classes (VOC) Challenge](http://homepages.inf.ed.ac.uk/ckiw/postscript/ijcv_voc09.pdf)
- 本次客观评审的测评算法的实现参考[Facebook Research Detectron](https://github.com/liuhaotian9420/Detectron/blob/master/detectron/datasets/voc_eval.py)（注意该IOU阈值默认为0.5）
- 测评指标的关键参数： 
  - IOU 阈值：0.5 + 0.05*i (i = 0,1,2...9)

  **评审说明：**

- 初赛排行榜采用 A/B 榜机制，即在初赛第一阶段（ A 榜：2020-2-28 (12:00:00 中午） 至 2020-4-10 (12:00:00 中午）），每个队伍拥有每天 1 次提交与测评排名的机会，大赛页面实时更新排行榜，从高到低排序。
- 在初赛第二阶段（ B榜: 2020-4-10（12:00:01 中午） 至 2020-4-11（12:00:00 中午）），每个队伍拥有共计 2 次提交与测评排名的机会，精度评审阶段的最终有效成绩与有效排名将以第二阶段（B榜）排行榜为准。

 

#####   **2）精度和速度综合评审**

​    **评审说明：**

​    B榜排行榜前【20】支团队需要在初赛结束后的4天内，在组委会提供的云计算平台上部署测试代码（包括训练好的模型），组委会负责确认该测试代码的精度和速度。**初赛综合排行榜**将根据代码的精度和速度计算综合得分，此榜的成绩与排名将作为团队的初赛最终成绩。

   *备注：综合测评”精度和速度“的具体规则将于3月中旬左右发布。

​         云计算平台部署指南将于初赛结束后12小时内发布。

#### **2、主观评审**

B榜排行榜前【20】支团队需要在初赛结束后 24 小时内，在指定的提交入口提交审核材料，审核材料有K-Lab Notebook（含有算法思路、亮点解读、建模算力与环境、使用的预训练模型相关论文及模型下载链接的说明文档）、参赛项目 Github 链接，并配合提交其他技术委员会要求追加的材料。

主观评审结果决定**初赛综合排行榜的**成绩是否有效，初赛综合排行榜前【15】支团队将晋级线上答辩环节。

### **二、线上答辩**

评审说明：采取网上远程答辩，形式包括 PPT、视频等进行展示。由评委提问、打分决定最终排名。

### **三、算法赛总成绩**

评测方法：总成绩 = 0.7 * 初赛成绩 + 0.3 * 答辩成绩
