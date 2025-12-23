# Industrial Anomaly Detection using FastFlow on MVTec AD

This repository contains the implementation of an **unsupervised industrial anomaly detection system** using **FastFlow** on the **MVTec AD dataset**.  
This project is developed as a **university final project** and focuses on detecting and localizing industrial defects using only **normal samples during training**.

## Dataset

This project uses the **MVTec Anomaly Detection (MVTec AD) dataset**, a widely adopted benchmark for industrial anomaly detection.

- 15 industrial object and texture categories  
- High-resolution images  
- Pixel-level ground truth masks for evaluation  
- Cold-start setting (training with normal data only)

Dataset link:  
https://www.mvtec.com/company/research/datasets/mvtec-ad/downloads

## Implementation Details

- Framework: **anomalib (OpenVINO Toolkit)**  
- Model: **FastFlow**  
- Backbone: **ResNet-18 (ImageNet pretrained)**  
- Input resolution: **256 × 256**  
- Training epochs: **50**  
- Batch size: **32**  
- Evaluation metric: **Image-level AUROC**

## Method Overview — FastFlow

FastFlow is a **flow-based anomaly detection method** that models the probability distribution of deep features extracted from images.

### Workflow

1. **Feature Extraction**  
   A pretrained backbone network (ResNet-18) extracts high-level feature representations from input images.

2. **Normalizing Flow**  
   A sequence of invertible transformations maps the extracted features to a standard Gaussian distribution.

3. **Training Phase**  
   The model is trained using only normal images by maximizing the likelihood of normal feature distributions.

4. **Inference Phase**  
   Samples with low likelihood are considered anomalous, and anomaly maps are generated to localize defective regions.

This approach enables both **image-level anomaly detection** and **pixel-level defect localization**.

The model is evaluated using **image-level AUROC**, which is suitable for anomaly detection as it is **threshold-independent**.

FastFlow demonstrates strong performance on multiple MVTec AD categories and produces meaningful anomaly heatmaps for defect localization.

## Visualization



