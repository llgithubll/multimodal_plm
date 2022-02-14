





## Survey

### 


## Summary

(序号仅表示添加顺序)

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






