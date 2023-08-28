# ET-FSM
Codes for ***Expert Teacher Based on Foundation Image Segmentation Model for Object Detection in Aerial Images***

[Yinhui Yu],[Xu Sun],[Qing Cheng]




## Update
- [2023/6] Training codes and config files are public available.
- [2023/4] Release inference code for infrared-visible image fusion and medical image fusion.



## Abstract

Multi-modality (MM) image fusion aims to render fused images that maintain the merits of different modalities, e.g., functional highlight and detailed textures. To tackle the challenge in modeling cross-modality features and decomposing desirable modality-specific and modality-shared features, we propose a novel Correlation-Driven feature Decomposition Fusion (CDDFuse) network. Firstly, CDDFuse uses Restormer blocks to extract cross-modality shallow features. We then introduce a dual-branch Transformer-CNN feature extractor with Lite Transformer (LT) blocks leveraging long-range attention to handle low-frequency global features and Invertible Neural Networks (INN) blocks focusing on extracting high-frequency local information. A correlation-driven loss is further proposed to make the low-frequency features correlated while the high-frequency features uncorrelated based on the embedded information. Then, the LT-based global fusion and INN-based local fusion layers output the fused image. Extensive experiments demonstrate that our CDDFuse achieves promising results in multiple fusion tasks, including infrared-visible image fusion and medical image fusion. We also show that CDDFuse can boost the performance in downstream infrared-visible semantic segmentation and object detection in a unified benchmark.

## 🌐 Usage

### ⚙ Network Architecture

Our CDDFuse is implemented in ``net.py``.

### 🏊 Training
**1. Virtual Environment**
```
# create virtual environment
conda create -n cddfuse python=3.8.10
conda activate cddfuse
# select pytorch version yourself
# install cddfuse requirements
pip install -r requirements.txt
```

**2. Data Preparation**

Download the MSRS dataset from [this link](https://github.com/Linfeng-Tang/MSRS) and place it in the folder ``'./MSRS_train/'``.

**3. Pre-Processing**

Run 
```
python dataprocessing.py
``` 
and the processed training dataset is in ``'./data/MSRS_train_imgsize_128_stride_200.h5'``.

**4. CDDFuse Training**

Run 
```
python train.py
``` 
and the trained model is available in ``'./models/'``.

### 🏄 Testing

**1. Pretrained models**

Pretrained models are available in ``'./models/CDDFuse_IVF.pth'`` and ``'./models/CDDFuse_MIF.pth'``, which are responsible for the Infrared-Visible Fusion (IVF) and Medical Image Fusion (MIF) tasks, respectively. 

**2. Test datasets**

The test datasets used in the paper have been stored in ``'./test_img/RoadScene'``, ``'./test_img/TNO'`` for IVF, ``'./test_img/MRI_CT'``, ``'./test_img/MRI_PET'`` and ``'./test_img/MRI_SPECT'`` for MIF.

Unfortunately, since the size of **MSRS dataset** for IVF is 500+MB, we can not upload it for exhibition. It can be downloaded via [this link](https://github.com/Linfeng-Tang/MSRS). The other datasets contain all the test images.


## 🙌 CDDFuse

### Illustration of our CDDFuse model.

<img src="image//Workflow.png" width="90%" align=center />

### Qualitative fusion results.

<img src="image//IVF1.png" width="90%" align=center />

<img src="image//IVF2.png" width="90%" align=center />

<img src="image//MIF.png" width="60%" align=center />

### Quantitative fusion results.

Infrared-Visible Image Fusion

<img src="image//Quantitative_IVF.png" width="60%" align=center />

Medical Image Fusion

<img src="image//Quantitative_MIF.png" width="60%" align=center />

MM detection

<img src="image//MMDet.png" width="60%" align=center />

MM segmentation

<img src="image//MMSeg.png" width="60%" align=center />
