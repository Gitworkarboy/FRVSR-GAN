# iSeeBetter: A Novel Approach to Video Super-Resolution using Adaptive Frame Recurrence and Generative Adversarial Networks

Project for Stanford CS230: Deep Learning

```Python3 | PyTorch | OpenCV2 | GANs | CNNs```

## Required Packages

```
torch==1.3.0.post2
pytorch-ssim==0.1
numpy==1.16.4
opencv-python==4.1.1.26
scikit-image==0.15.0
tqdm==4.37.0
```

To load,
```pip3 install -r requirements.txt```

## Usage


```./run.sh```

## Overview

Recently, learning-based models have enhanced the performance of Single-Image Super-Resolution (SISR). However, applying SISR successively to each video frame leads to lack of temporal consistency. On the other hand, VSR models based on convolutional neural networks outperform traditional approaches in terms of image quality metrics such as Peak Signal to Noise Ratio (PSNR) and Structural SIMilarity (SSIM). While optimizing mean squared reconstruction error during training improves PSNR and SSIM, these metrics may not capture fine details in the image leading to misrepresentation of perceptual quality. We propose an Adaptive Frame Recurrent Video Super Resolution (AFRVSR) scheme that seeks to improve temporal consistency by utilizing information multiple similar adjacent frames (both future LR frames and previous SR estimates), in addition to the current frame. Further, to improve the “naturality” associated with the reconstructed image while eliminating artifacts seen with traditional algorithms, we combine the output of the AFRVSR algorithm with a Super-Resolution Generative Adversarial Network (SRGAN). The proposed idea thus not only considers spatial information in the current frame but also temporal information in the adjacent frames thereby offering superior reconstruction fidelity. Once our implementation is complete, we plan to show results on publicly available datasets that demonstrate that the proposed algorithms surpass current state-of-the-art performance in both accuracy and efficiency. 
 
![adjacent frame similarity](https://github.com/amanchadha/iSeeBetter/blob/master/images/iSeeBetter_AFS.jpg)
Figure 1: Adjacent frame similarity
 
![network arch](https://github.com/amanchadha/iSeeBetter/blob/master/images/iSeeBetter_NNArch.jpg)
Figure 2: Network architecture

## Dataset

To evaluate our proposed model, we used the [Vimeo90K](http://data.csail.mit.edu/tofu/testset/vimeo_test_clean.zip) dataset collected in the TOFlow project of MIT CSAIL which contains around 90,000 7-frame HR sequences with a fixed resolution, extracted from 39K video clips from Vimeo.com. When training our models, we generate the corresponding LR frame for each HR input frame by performing 4x down-sampling. To extend our dataset further, we have also built a video-to-frames tool to collect more data for testing from YouTube. 

## Results

![results](https://github.com/amanchadha/iSeeBetter/blob/master/images/iSeeBetter_Results.jpg)

## Pretrained Model
Model trained for 7 epochs included under ```epochs/```

## HOW TO

# Training 

Train the model using (takes roughly an hour per epoch on an NVIDIA Tesla V100):

```python AFRVSRTrain.py```

# Testing

To use the pre-trained model and test on a random video from within the dataset:

```python AFRVSRTest.py```

## Acknowledgements

Credits:
- [SRGAN Implementation](https://github.com/leftthomas/SRGAN) by LeftThomas.
- We used [FR-SRGAN](https://github.com/ReNginx/FR-SRGAN) as a baseline for our Adaptive-FRVSR implementation.

## Citation
Cite the work as:
```
CVPR citation
```