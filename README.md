# Baidu-2020-Language-and-Intelligent-Technology-Competition-Relation-Extraction-rank15

比赛链接：https://aistudio.baidu.com/aistudio/competition/detail/31?isFromCcf=true<br>
结果<br>
| precision  | recall   | f1     | team member|
| --------   | -----:   | :----: | :----: |
| 0.7806       | 0.7587   | 0.7695 | https://github.com/aker218  |


## 主要思路
&#8194;&#8194;将任务分割为关系类别识别和关系实体识别，模型先进行关系类别识别，根据给定的55个关系类别，我们进行55个二分类，即判断这55个关系是否在当前句子内出现；然后根据关系识别模型判断的在句子内出现的n个关系；分别将这n个关系作为特征同原始句子结合生成n个样本，输入二阶段的关系实体识别模型识别出属于每个关系的主体及客体；最后对句子内每个关系识别出的多个关系主体和关系客体进行排列组合，生成不同的关系三元组。
1. 关系分类模型：采用Robera+腾讯预训练词向量进行字词混合编码，然后使用DGCNN及Conditional layernorm进行后续处理及分类
2. 关系主客体识别模型：Roberta+BiLSTM/DGCNN+CRF
3. 后处理：使用训练集构建知识库对输出结果进行补充校验

## 运行方法
打开main.ipynb，按照其内的顺序及指引依次运行即可<br>
需要自行下载Roberta-wwm-ext及腾讯词向量<br>
Roberta-wwm-ext: https://github.com/ymcui/Chinese-BERT-wwm<br>
腾讯词向量: https://ai.tencent.com/ailab/nlp/zh/embedding.html


## 参考资料
https://spaces.ac.cn/archives/6671<br>
https://kexue.fm/archives/7124<br>