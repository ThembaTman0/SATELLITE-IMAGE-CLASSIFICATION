<div align="center">

![Satellite Banner](img/google-earth-view-7023.jpg)

<sub>Image source: [Earth View by Google Maps](https://earthview.withgoogle.com/)</sub>

# Satellite Image Classification Using HOG and DAISY Feature Descriptors

[![IEEE](https://img.shields.io/badge/IEEE-Published-00629B?style=flat&logo=ieee&logoColor=white)](https://ieeexplore.ieee.org/abstract/document/9988636)
[![University](https://img.shields.io/badge/Wits-Computer_Science-003DA5?style=flat)](https://www.wits.ac.za/)
[![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/)
[![Dataset](https://img.shields.io/badge/Dataset-UC_Merced_Land_Use-4CAF50?style=flat)](http://weegee.vision.ucmerced.edu/datasets/landuse.html)

**Themba Ngobeni** | School of Computer Science and Applied Mathematics | University of the Witwatersrand, Johannesburg

Published on IEEE Xplore: [View Paper](https://ieeexplore.ieee.org/abstract/document/9988636) | Research Summary: [View PDF](RESEARCH_SUMMARY.pdf)

</div>

---

## Abstract

Advancements in remote sensing techniques provide crucial information for a variety of applications, including landscape changes, land cover categorization, enhanced weather forecasting, and climate observation. With the recent breakthroughs that have made satellites both more powerful and cheaper to deploy, the volume of high-resolution satellite images collected has increased exponentially. Manual classification techniques of these high-resolution satellite images are too inaccurate and inefficient to handle the challenge. Hence, automation of satellite image classification has become a crucial part of the field of remote sensing.

The major purpose of this work is to evaluate the ability of a feature extraction model to identify satellite pictures utilizing different approaches. This study presents actual data demonstrating that the Bag of Feature (BoF) approach outperforms conventional feature extraction algorithms for multilabel scene classification.

We employ local feature descriptors such as DAISY features for local feature extraction and classification, and global feature descriptors such as the histogram of oriented gradients (HOG) for global feature extraction and classification, using the Bag of Features technique. The bag of feature encoding is augmented by the Mini-Batch K-Means method to decrease the complications of the feature encoding technique. A method for pooling is applied to combine DAISY and HOG data relevant to each image. Finally, we perform a 10-fold cross-validation experiment with a support vector machine (SVM) classifier and classify our results on a dataset of 21 scene categories.

The hybrid model attained an accuracy of 81.76% and the KNN model attained an accuracy of 67.14%. The study demonstrates how this categorization method may be used to identify changes in land use and land cover, as well as aid in the improvement of satellite classification.

---

## Methodology

The classification pipeline follows four stages:

```
Raw Image -> Feature Extraction -> Encoding      -> Pooling -> Classification
             DAISY (local)        Mini-Batch        L2         SVM
             HOG   (global)       K-Means
```

**Feature Extraction**

Two complementary descriptors were used:
- DAISY for local feature extraction, capturing fine-grained structural detail across image patches
- HOG for global feature extraction, capturing the overall gradient orientation across each image

**Encoding**

Bag of Features encoding via Mini-Batch K-Means clustering to reduce the complexity of the feature encoding step.

**Pooling**

L2 pooling to combine DAISY and HOG data into a fixed-length feature vector per image.

**Classification**

A 10-fold cross-validation experiment using Support Vector Machine classifiers across 21 scene categories from the UC Merced Land Use dataset.

---

## Results

The HOG classifier proved to be an unviable approach for this classification task on its own. The hybrid model combining SVM with an RBF kernel was the most effective, with the linear classifier coming in second place.

| Classifier         | Accuracy |
|--------------------|----------|
| Hybrid (SVM + RBF) | 81.42%   |
| Linear Classifier  | 76.19%   |
| DAISY only         | 73.40%   |
| KNN                | 68.02%   |
| HOG only           | 36.73%   |

**Comparison against prior work on the UC Merced dataset:**

| Method                | Year | Accuracy |
|-----------------------|------|----------|
| BOVW + SCK            | 2010 | 77.71%   |
| Dirichlet             | 2013 | 92.80%   |
| VLAD                  | 2014 | 94.30%   |
| DCNN + SIFT BOVW      | 2018 | 95.00%   |
| Inception-v3-CapsNet  | 2020 | 80.00%   |
| This work (SVM + RBF) | 2022 | 81.42%   |

The hybrid model outperforms the Inception-v3-CapsNet deep learning approach while using a classical pipeline, which is notable given the dataset constraints that make deep learning less suitable at this scale.

---

## Confusion Matrices

**DAISY Classifier**

![DAISY Confusion Matrix](img/Daisy-Classifier.png)

**Hybrid Classifier (Best Model)**

![Hybrid Confusion Matrix](img/Hybrid-Classifier.png)

**Linear Classifier**

![Linear Confusion Matrix](img/Linear-Classifier.png)

---

## Key Findings

- HOG alone is not a viable feature extractor for satellite image classification at this scale, scoring only 36.73%.
- The DAISY descriptor captures local image structure more effectively than HOG for this task.
- Combining both descriptors in a hybrid model with an SVM RBF kernel produces the best result at 81.42%.
- CNN-based approaches were excluded because the UC Merced dataset, with only 21 scene classes and limited samples per class, is too small for data-hungry deep learning models to outperform well-tuned classical pipelines.
- The results show that the Bag of Features method is a viable and competitive approach for multilabel satellite scene classification without requiring deep learning infrastructure.

---

## Limitations and Future Work

The UC Merced Land Use dataset contains only 21 scene categories, which is small relative to the diversity of classes encountered in real-world remote sensing. This constrains how well models trained on it generalise to unseen terrain types.

Planned future directions include:

- Applying convolutional neural networks on a larger dataset with more scene classes
- Exploring transfer learning to overcome the data size constraint and leverage pre-trained visual features
- Evaluating performance on more recent high-resolution satellite datasets

---

## References

[1] Engin Tola, Vincent Lepetit, and Pascal Fua. "Daisy: An efficient dense descriptor applied to wide-baseline stereo". IEEE Transactions on Pattern Analysis and Machine Intelligence, 32.5 (2009), pp. 815-830.

[2] Jobin Wilson and Muhammad Arif. "Scene recognition by combining local and global image descriptors". arXiv preprint arXiv:1702.06850 (2017). [Link](https://arxiv.org/abs/1702.06850)

---

<div align="center">

**Themba Ngobeni** | University of the Witwatersrand | School of Computer Science and Applied Mathematics

[![Read the Paper](https://img.shields.io/badge/Read_the_Paper-IEEE_Xplore-00629B?style=flat&logo=ieee&logoColor=white)](https://ieeexplore.ieee.org/abstract/document/9988636)

</div>
