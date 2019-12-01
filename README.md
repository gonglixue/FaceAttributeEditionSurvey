### 综述
一般分类人脸属性分析、人脸属性操作两步（FAE, FAM）
FAE: 相当于分类检测，检测是否具有某种属性（如戴眼镜）
FAM：添加或移除某种属性

FAE可分为两种方法：基于局部的、基于整体的
* 局部：先给人脸每个位置定位，然后提取局部特征用于识别。定位的过程又可以是独立的或端到端的。独立的方法包括很多现有的人脸关键点检测、人脸语义分割
* 全局：用一个统一的网络，能够学习各属性之间的关系（和end-to-end的part-based又什么区别）。不同的层学习不同的属性。但受限于先验（？怎么理解）


FAM主要基于生成模型。根据是否映入额外的条件信息。主要可分为model-based和extra condition-based方法：
* model-based: 一个模型训一种属性
* extra condition-based：用额外的输入（如latent vector或图像），不同的额外输入将产生不同的属性编辑结果。相当于image-to-image translation。辅助的输入也不需要和原来的人同identity

### Main methods

#### deep FAE
* 2014-CVPR: PANDA: Pose Aligned Networks for Deep Attribute Modeling\[[paper](
http://openaccess.thecvf.com/content_cvpr_2014/papers/Zhang_PANDA_Pose_Aligned_2014_CVPR_paper.pdf)\]\[[CaffeCode](https://github.com/facebookarchive/pose-aligned-deep-networks)\]
	- `bounding box->many poselets`, `combine global&local`, `SVM`
* 2015-ICCV: Deep Learning Face Attributes in the Wild. \[[paper](
https://www.cv-foundation.org/openaccess/content_iccv_2015/papers/Liu_Deep_Learning_Face_ICCV_2015_paper.pdf)\]
* 2017-CVPR: Improving facial attribute prediction using semantic segmentation\[[paper](https://arxiv.org/abs/1704.08740)\]\[[pytorchCode-notOfficial](https://github.com/nbansal90/Facial_attribute_segmentation)\]
	- `region-based pooling`, `Semantic Segmentation-based Gating`
* 2018-Trans on Affective Computing: Segment-based methods for facial attribute detection from partial faces\[[paper]()\]
* 2016-ECCV: Moon: A mixed objective optimization network for the recognition of facial attributes\[[paper]()\]
* 2017-AAAI: Attributes for improved attributes: a multi-task network utilizing implicit and explicit relationships for facial attribute classification.\[[paper]()\]
* 2018-CVPR: Partially shared multi-task convolutional neural network with local constraint for face attribute learning.\[[paper]()\]

#### deep FAM



* 2018-ECCV GANimation: Anatomically-aware Facial Animation from a Single Image\[[code](
https://github.com/albertpumarola/GANimation.git)
]\[[paper](
https://arxiv.org/abs/1807.09251)\]

 * 2019-IJCV GANimation: One-shot Anatomically Consistent Facial Animation\[[code](
https://github.com/albertpumarola/GANimation)
]\[[paper](
https://link.springer.com/epdf/10.1007/s11263-019-01210-3?author_access_token=KkIt3ar1GHkWIUklAjsgjPe4RwlQNchNByi7wbcMAY5ihGyz3kHkS5TjreGbAhfYtSrG2LRv-m3aNgCcoyOIKZ9LB-hbGWZloUM-6WB9qaD_xmkWBVbaISYLi5wyD75JzmlGfeZlAtmoSH_FLE6wBQ%3D%3D)\]


### Dataset & Benchmark
#### CelebA
#### LFWA
* 40 labeled attributes
#### Attributes25K
#### Berkeley Attributes of People Dataset

### Non-learning methods