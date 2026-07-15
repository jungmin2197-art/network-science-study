# CH8. Modern Convolutional Neural Networks

## Overview

LeNet은 Convolutional Neural Network(CNN)의 가능성을 보여준 최초의 성공적인 모델이었지만, 작은 데이터셋을 대상으로 설계되어 복잡한 이미지 인식 문제를 해결하기에는 한계가 있었다. 이후 ImageNet과 같은 대규모 데이터셋과 GPU의 발전으로 더 깊고 효율적인 CNN 구조가 등장하기 시작하였다.

이 장에서는 현대 CNN이 어떻게 발전해 왔는지를 대표적인 모델들을 통해 살펴본다. 각 모델은 이전 모델의 한계를 해결하기 위해 새로운 아이디어를 제안하였으며, 이러한 발전 과정은 현재의 Computer Vision 모델의 기반이 되었다.

---

# 학습 목표

이 장에서는 다음 내용을 중심으로 학습한다.

- Deep CNN이 등장하게 된 배경 이해
- 대표적인 CNN Architecture의 구조와 핵심 아이디어 이해
- 각 모델이 해결하고자 했던 문제 이해
- CNN 구조가 어떻게 발전해 왔는지 전체 흐름 이해

---

# Modern CNN의 발전 과정

```text
LeNet (1998)
    │
    ▼
AlexNet (2012)
    │
    ▼
VGG (2014)
    │
    ▼
Network in Network (NiN) (2013~2014)
    │
    ▼
GoogLeNet (2014)
    │
    ▼
Batch Normalization (2015)
    │
    ▼
ResNet / ResNeXt (2015~2017)
    │
    ▼
DenseNet (2017)
    │
    ▼
RegNet (2020)
```

각 모델은 단순히 성능을 높이는 것이 아니라 이전 모델의 한계를 해결하면서 발전하였다.

---

# Chapter Contents

## 8.1 AlexNet

- Deep CNN의 시작
- ReLU
- Dropout
- Data Augmentation
- GPU Training

---

## 8.2 VGG

- 작은 Convolution Kernel (3×3)
- 깊은 Network 설계
- VGG Block

---

## 8.3 Network in Network (NiN)

- MLPConv
- 1×1 Convolution
- Global Average Pooling

---

## 8.4 GoogLeNet

- Inception Module
- Multi-Branch Architecture
- 계산량 감소

---

## 8.5 Batch Normalization

- Internal Covariate Shift
- Batch Normalization Layer
- 빠르고 안정적인 학습

---

## 8.6 ResNet & ResNeXt

- Residual Learning
- Skip Connection
- Deep Network Training

---

## 8.7 DenseNet

- Dense Connection
- Feature Reuse
- Gradient 전달 개선

---

## 8.8 Designing Convolution Network Architectures

- CNN Architecture Design
- Design Space
- RegNet

---

# 이 장에서 중요한 흐름

Modern CNN은 단순히 Layer를 깊게 쌓는 과정이 아니라, **깊은 네트워크를 안정적으로 학습하고 계산 효율을 높이기 위한 다양한 아이디어의 발전 과정**이다.

각 모델은 다음과 같은 문제를 해결하기 위해 등장하였다.

| Model | 해결하려는 문제 |
|--------|----------------|
| AlexNet | Deep CNN 학습 가능성 |
| VGG | 더 깊은 Network 설계 |
| NiN | Fully Connected Layer의 한계 |
| GoogLeNet | 계산량과 Parameter 감소 |
| Batch Normalization | 학습 안정화 |
| ResNet | Gradient Vanishing |
| DenseNet | Feature 재사용 및 정보 전달 |
| RegNet | 체계적인 Network 설계 |

