### 综述
一般分类人脸属性分析、人脸属性操作两步（FAE, FAM）
FAE: 相当于分类检测，检测是否具有某种属性（如戴眼镜）
FAM：添加或移除某种属性

FAE可分为两种方法：基于局部的、基于整体的
* 局部：先给人脸每个位置定位，然后提取局部特征用于识别。定位的过程又可以是独立的或端到端的。独立的方法包括很多现有的人脸关键点检测、人脸语义分割
* 全局：用一个统一的网络，能够学习各属性之间的关系（和end-to-end的part-based又什么区别）。不同的层学习不同的属性。但受限于先验（？怎么理解）


FAM主要基于生成模型。根据是否映入额外的条件信息，主要可分为model-based和extra condition-based方法：
* model-based: 一个模型训一种属性
* extra condition-based：用额外的输入（如latent vector或图像），不同的额外输入将产生不同的属性编辑结果。相当于image-to-image translation。辅助的输入也不需要和原来的人同identity
---

### FAE&FAM Paper List

#### 1. deep FAE
* 2014-CVPR: PANDA: Pose Aligned Networks for Deep Attribute Modeling\[[paper](
http://openaccess.thecvf.com/content_cvpr_2014/papers/Zhang_PANDA_Pose_Aligned_2014_CVPR_paper.pdf)\]\[[CaffeCode](https://github.com/facebookarchive/pose-aligned-deep-networks)\]
	- `bounding box->many poselets`, `combine global&local`, `SVM`
* 2015-ICCV: Deep Learning Face Attributes in the Wild. \[[paper](
https://www.cv-foundation.org/openaccess/content_iccv_2015/papers/Liu_Deep_Learning_Face_ICCV_2015_paper.pdf)\]
	- `coarse-to-fine face localization`, `feature extraction`, `SVM`
* 2017-CVPR: Improving facial attribute prediction using semantic segmentation\[[paper](https://arxiv.org/abs/1704.08740)\]\[[pytorchCode-notOfficial](https://github.com/nbansal90/Facial_attribute_segmentation)\]
	- `region-based pooling`, `Semantic Segmentation-based Gating`
* 2018-Trans on Affective Computing: Segment-based methods for facial attribute detection from partial faces\[[paper]()\]
	- To deal with the cases with partial faces.
* 2016-ECCV: Moon: A mixed objective optimization network for the recognition of facial attributes\[[paper](https://arxiv.org/pdf/1603.07027.pdf)\]\[[mxnetCode](https://github.com/tornadomeet/mxnet-face#face-attribute-prediction)\]
	- Motivation: Multi-task is beneficial. Multi-objective training is difficult to perform data balance.
	- Contribution: domain-adapted multitask loss function.
* 2017-AAAI: Attributes for improved attributes: a multi-task network utilizing implicit and explicit relationships for facial attribute classification.\[[paper](https://arxiv.org/abs/1604.07360)\]
	- attributes grouping manually 
* 2018-CVPR: Partially shared multi-task convolutional neural network with local constraint for face attribute learning.\[[paper](http://openaccess.thecvf.com/content_cvpr_2018/papers/Cao_Partially_Shared_Multi-Task_CVPR_2018_paper.pdf)\]
	- identity information, multi-task, information flow between tasks
* 2018-IJCAI: Harnessing synthesized abstraction images to improve facial attribute recognition\[[paper](http://www.yugangjiang.info/publication/18IJCAI-FacialAttributes.pdf)\]\[[caffeCode](https://github.com/TencentYoutuResearch/FaceAttribute-FAN)\]

#### 2. deep FAM
* 2017-CVPR: Learning residual images for face attribute manipulation(ResGAN)\[[tfCode](
https://github.com/MingtaoGuo/Learning-Residual-Images-for-Face-Attribute-Manipulation/blob/master/Face_Attribute_Manipulation.py)]\[[paper](https://arxiv.org/pdf/1612.05363.pdf)\]
	- GAN, dual inverse manipulation, residual learning, focuses on the
attribute-specific face area, metric

* 2017-CVPR: Age progression/regression by conditional adversarial autoencoder\[[tfCode](https://github.com/ZZUTK/Face-Aging-CAAE)]\[[paper](http://web.eecs.utk.edu/~zzhang61/docs/papers/2017_CVPR_Age.pdf)\]
	- GAN, conditional latent vector, impose prior distribution on latent vector, one-hot age label

* 2016-NIPSW: Invertible Conditional GANS(IcGANs)\[[torchCode](
https://github.com/Guim3/IcGAN)
]\[[paper](
https://arxiv.org/pdf/1611.06355.pdf)\]
	- change multiple attributes

* 2016-ICML: Autoencoding beyond pixels using a learned similarity metric\[[torchCode](
https://github.com/daQuincy/VAE-GAN-Autoencoding-Beyond-Pixels-Using-a-Similarity-Metric)
]\[[paper](
https://arxiv.org/pdf/1512.09300.pdf)\]

* 2017-NIPS: Fader Networks: Manipulating Images by Sliding Attributes\[[PytorchCode](https://github.com/facebookresearch/FaderNetworks)]\[[paper](https://arxiv.org/abs/1706.00409)\]
	- alter attributes continuously, latent representation, disentangle

* 2017-BMVC: GeneGAN: Learning Object Transfiguration and Attribute Subspace from Unpaired Data\[[tfCode](https://github.com/Prinsphield/GeneGAN)]\[[paper](https://prinsphield.github.io/publication/BMVC-2017-GeneGAN)\]
	- conditioned on reference examples, Object Transfiguration, exchange attributes, disentangle


* 2018-CVPR StarGAN: Unified generative
adversarial networks for multi-domain image-to-image
translation\[[PytorchCode](https://github.com/yunjey/stargan)]\[[paper](https://zpascal.net/cvpr2018/Choi_StarGAN_Unified_Generative_CVPR_2018_paper.pdf)\]
	- multi-dataset multi-domain, domain vector, cycle consistent

* 2018-ECCV: SaGAN: Generative Adversarial Network with Spatial Attention for Face Attribute Editing\[[PytorchCode](https://github.com/Prinsphield/ELEGANT)]\[[paper](https://github.com/Prinsphield/ELEGANT)\]
	- spatial attention

* 2018-ECCV: Elegant: Exchanging latent encodings with gan for transferring multiple face attributes.\[[PytorchCode](https://github.com/Prinsphield/ELEGANT)]\[[paper](https://github.com/Prinsphield/ELEGANT)\]
	- transfer multiple attributes, divide latent codes into different parts(iterative training strategy), high quality, disentangle, multi-scale descriminator

* 2018-ECCV GANimation: Anatomically-aware Facial Animation from a Single Image\[[code](
https://github.com/albertpumarola/GANimation.git)
]\[[paper](
https://arxiv.org/abs/1807.09251)\]

 * 2019-IJCV GANimation: One-shot Anatomically Consistent Facial Animation\[[code](
https://github.com/albertpumarola/GANimation)
]\[[paper](
https://link.springer.com/epdf/10.1007/s11263-019-01210-3?author_access_token=KkIt3ar1GHkWIUklAjsgjPe4RwlQNchNByi7wbcMAY5ihGyz3kHkS5TjreGbAhfYtSrG2LRv-m3aNgCcoyOIKZ9LB-hbGWZloUM-6WB9qaD_xmkWBVbaISYLi5wyD75JzmlGfeZlAtmoSH_FLE6wBQ%3D%3D)\]

---

### Dataset & Benchmark
#### 1. CelebA
#### 2. LFWA
* 40 labeled attributes
#### 3. Attributes25K
#### 4. Berkeley Attributes of People Dataset

---
### Non-learning methods

---
### Other Interesting Portrait Special Effects
* 2019-ICCV Deep Single-Image Portrait Relighting\[[pytorchCode](
https://github.com/zhhoper/DPR)
]\[[paper&dataset](
https://zhhoper.github.io/)\]