

## TODO

* https://arxiv.org/abs/2109.10246
* ViLT
* SimVLM
* MLIM


## Survey

* [多模态预训练综述](https://mp.weixin.qq.com/s/X-G7ARBWG49rKDQSHJ1ICQ)
* [awesome-vision-language-pretraining-papers](https://github.com/yuewang-cuhk/awesome-vision-language-pretraining-papers)
* [vit-pytorch](https://github.com/lucidrains/vit-pytorch)
* [从LXMERT到VLMO：多模态预训练模型的演变史](https://mp.weixin.qq.com/s?__biz=MzIwMTc4ODE0Mw==&mid=2247547810&idx=2&sn=4e3c845e049340921c5568bae1def6ce)
* [万字综述！从21篇最新论文看多模态预训练模型研究进展](https://mp.weixin.qq.com/s?__biz=MzIwMTc4ODE0Mw==&mid=2247546641&idx=1&sn=0cdc826b91e3317674222f748873d730&chksm=96eae891a19d61879deafa00790e1d38cc7b8860b1ac3da071f341b10965ac4f4bba2d46e692&token=1937743143&lang=zh_CN&scene=21#wechat_redirect)
* [从多篇2021年顶会论文看多模态预训练模型最新研究进展](https://mp.weixin.qq.com/s?__biz=MzIwMTc4ODE0Mw==&mid=2247543295&idx=1&sn=795bd6c44a425912ba3519ed63c35d95&chksm=96eaf67fa19d7f696c75f4ce1ededc7a7c54c4403bbb873b249f32ad8d8e9768dde908d0f13c&token=1937743143&lang=zh_CN&scene=21#wechat_redirect)

### Trends in Integration of Vision and Language Research: A Survey of Tasks, Datasets, and Methods

* JAIR2021
* [paper](https://arxiv.org/abs/1907.09358?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%253A+arxiv%252FQSXk+%2528ExcitingAds%2521+cs+updates+on+arXiv.org%2529)
* 135pages
* 综述有点老


### 




## Summary

| No.      | model       | Description    |
| :---  |    :----   |          :---: |
|    1   | ViT         | ...    |
|    2   | InterBERT        | ...       |
|    3   | fashionBERT      | ...       |
|    4   | Kaleido-BERT     | ...       |









(标题中序号仅表示添加顺序)

### 1. AN IMAGE IS WORTH 16X16 WORDS: TRANSFORMERS FOR IMAGE RECOGNITION AT SCALE

* 🌟
* ICLR2021
* [paper](https://arxiv.org/abs/2010.11929)
* [code](https://github.com/google-research/vision_transformer), [vit-pytorch](https://github.com/lucidrains/vit-pytorch)
* [weixin](https://mp.weixin.qq.com/s/KyL74PwoXDWuuPLiziYPRA)

---

把图片分割成一块一块的patch，完全利用和BERT一样的结构和训练方式，将预训练从文本扩展到图片中；（属于挖新坑的工作）

![vit](images/vit.png)


### 2. InterBERT: Vision-and-Language Interaction for Multi-modal Pretraining

* KDD2020
* [paper](https://arxiv.org/abs/2003.13198)

---
* 模型结构：双流emb+单一transformer+双流输出
* 训练方法： 
    * masked segment modeling
    *  masked region modeling 
    * image-text matching

> 阿里巴巴、电商；可模仿写作

![interBERT](images/interBERT.png)

### 3. FashionBERT: Text and Image Matching with Adaptive Loss for Cross-modal Retrieval

* SIGIR20 Industry Track
* [paper](https://arxiv.org/abs/2005.09801)
* [link](https://developer.aliyun.com/article/763357)

---

* 提出一种图文匹配模型，以求对电商图像特征更好的提取和表达
* 模型结构：双流模型
* 训练方法：
  * masked language modeling
  * masked patch modeling
  * text and image alignment
  * 为多任务学习，本文还设计了一个adaptive loss自适应每个任务权重
  
![fashionbert](images/fashionbert.png)


### 4. Kaleido-BERT: Vision-Language Pre-training on Fashion Domain

* CVPR2021
* [paper](https://arxiv.org/abs/2103.16110)
* [ata link](https://ata.alibaba-inc.com/articles/210439?spm=ata.23639746.0.0.673a5da3nIPN0w)

---

* 多尺度图像特征提取（KPG）
* 图文预对齐（AAG、AGM）
* 图像自监督（task: AKPM, TIM, AMLM）

![KaleidoBERT](images/kaleidoBERT.png)

> *论文中的实验表格做的不错，相当于模型综述了*

### 5. Pixel-BERT: Aligning Image Pixels with Text by Deep Multi-Modal Transformers

* arXiv2004
* [paper](https://arxiv.org/abs/2004.00849)

---

主要目标在于通过图文匹配任务获取更好的图文联合表示，方法过于简单

1. BERT编码文字，CNN编码图片，合并接上transformer层
2. 训练任务：图文匹配任务+语言模型的MLM

![Pixel-BERT](images/pixel-bert.png)


### 6. ViLBERT: Pretraining Task-Agnostic Visiolinguistic Representations for Vision-and-Language Tasks

* arXiv1908
* [paper](https://arxiv.org/abs/1908.02265)

---

* 模型结构：双流模型
  * 文本直接通过BERT编码
  * 图像通过预训练的目标检测网络(ResNet-101+Faster R-CNN)抽取图像bounding boxes(根据置信度，数量控制在10-36)

* 训练方法
  * mask文（和bert一样）
  * mask图（Masked image regions have their image features zeroed out 90% of the time and are unaltered 10%）
  * 图文匹配任务linear(cat(<IMG>, <CLS>), 2)

![vilbert](images/vilbert.png)

![vilbert-train](images/vilbert_train.png)


### 7. UNITER: UNiversal Image-TExt Representation Learning

* ECCV2020
* [paper](https://arxiv.org/abs/1909.11740)
* [code](https://github.com/ChenRocks/UNITER)

---

* 主要目标学习图文的联合表示
* 模型结构
  * 图emb: R-CNN+location
  * 文emb: bert
  
* 训练方法
  * Masked Language Modeling (MLM)
  * Masked Region Modeling (MRM, with three variants)
  * Image-Text Matching (ITM)
  * Word-Region Alignment (WRA)
  * 从4个图文数据集训练(COCO, Visual Genome, Conceptual Captions, and SBU Captions)

![uniter](images/uniter.png)


### 8. LXMERT: Learning Cross-Modality Encoder Representations from Transformers

* EMNLP2019
* [paper](https://arxiv.org/abs/1908.07490)
* [code](https://github.com/airsplay/lxmert)

---

* 主要目标，most importantly, the alignment and relationships between these two modalities.
* 模型结构
  * 图特征，图encode
  * 文特征，文encode
  * 图文cross encoder
  
* 训练方法
  * masked language modeling 
  * masked object prediction (feature regression and label classiﬁcation) 
  * cross-modality matching 
  * image question answering

![lxmert](images/lxmbert.png)

![lxmert-pretrain](images/lxmbert_pretrain.png)


### 9. ViLT: Vision-and-Language Transformer Without Convolution or Region Supervision

* ICML 2021
* [paper](https://arxiv.org/abs/2102.03334)
* [code](https://github.com/dandelin/vilt)

---

* 主要目标，将文本、图片联合训练转到BERT的统一格式了；模型简单，效率高；
* 模型结构
  * 图emb
  * 文emb
  * 图文cross encoder
  
* 训练方法
  * ITM(image text matching)，包含WPA(word patch alignment操作)，这里效仿了UNITER中都WRA，使用的都是optimal transports方法，计算两个分布之间的最小转换代价[zhihu link](https://zhuanlan.zhihu.com/p/82424946)
  * MLM(whole word masking, 这都不算啥创新点，凑字数)
  * IA(image augment) during fine-tuning

>（思想到没啥新鲜感、多模态的论文都没啥新鲜感，连积木都懒得拼了）

![vilt-d](images/ViLT_d.png)

![vilt](images/ViLT.png)

### 10. InterBERT: Vision-and-Language Interaction for Multi-modal Pretraining

* KDD 2020
* [paper]()




### 11. Oscar:



### 12. CLIP


### 13. UNIMO


### 14. Seeing Out of tHe bOx: 

* CVPR 2021 oral
* [paper](https://arxiv.org/abs/2104.03135)
* [code](https://github.com/researchmm/soho)



### 15. VinVL

* CVPR 2021
* [paper](https://arxiv.org/abs/2101.00529)
* [code](https://github.com/pzzhang/VinVL)


### 16. Scaling Up Visual and Vision-Language Representation Learning With Noisy Text Supervision

* ICML 2021
* [paper](https://arxiv.org/abs/2102.05918)

### 17. E2E-VLP: End-to-End Vision-Language Pre-training Enhanced by Visual Learning

* ACL 2021
* [paper](https://arxiv.org/abs/2106.01804)


### 18. MURAL: Multimodal, Multitask Retrieval Across Languages

* EMNLP 2021
* [paper](https://arxiv.org/abs/2109.05125)



### 19. Large-Scale Adversarial Training for Vision-and-Language Representation Learning

* NeurIPS 2020


### 20. UNIMO: Towards Unified-Modal Understanding and Generation via Cross-Modal Contrastive Learning

* ACL 2021





