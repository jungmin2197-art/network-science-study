# CH8. Modern Convolutional Neural Networks

## Overview

LeNet은 CNN(Convolutional Neural Network)의 가능성을 보여준 최초의 모델이었지만, 네트워크의 깊이와 표현력에는 한계가 있었다. 이후 ImageNet과 같은 대규모 데이터셋의 등장과 GPU 성능의 발전으로 더욱 깊고 강력한 CNN 구조가 요구되었으며, 이를 해결하기 위해 다양한 현대 CNN 아키텍처가 제안되었다.

이 장에서는 현대 CNN의 발전 과정을 대표하는 모델들을 살펴본다.

- **AlexNet (2012)** : Deep CNN의 시작과 ImageNet 우승
- **VGG (2014)** : 작은 Kernel을 이용한 깊은 네트워크
- **NiN (2014)** : MLP를 이용한 특징 표현 향상과 Global Average Pooling
- **GoogLeNet (2014)** : Inception Module을 이용한 Multi-Branch 구조
- **Batch Normalization (2015)** : 학습 안정화와 빠른 수렴
- **ResNet (2015)** : Residual Learning을 통한 초심층 네트워크
- **DenseNet (2017)** : Feature Reuse를 위한 Dense Connection
- **RegNet (2020)** : 체계적인 CNN Architecture Design

---

## 왜 Modern CNN이 등장했는가?

LeNet 이후 CNN은 이미지 분류 성능을 크게 향상시켰지만, 더 깊은 네트워크를 학습하는 과정에서 다양한 문제가 발생하였다.

- 더 복잡한 특징을 학습하기 어려움
- Gradient Vanishing 문제
- Overfitting
- 계산량 증가
- 비효율적인 네트워크 구조

Modern CNN은 이러한 문제들을 해결하면서 더 깊고, 더 효율적이며, 더 높은 성능을 갖는 모델로 발전하였다.

---

## Modern CNN의 발전 흐름

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
NiN (2014)
      │
      ▼
GoogLeNet (2014)
      │
      ▼
Batch Normalization (2015)
      │
      ▼
ResNet (2015)
      │
      ▼
DenseNet (2017)
      │
      ▼
RegNet (2020)
```

---

## 이 장에서 집중해야 할 내용

각 모델를 공부할 때 다음 내용을 중심으로 이해하는 것이 중요하다.

1. 왜 이 모델이 등장했는가?
2. 이전 모델의 어떤 한계를 해결했는가?
3. 핵심 아이디어는 무엇인가?
4. 대표적인 구조와 주요 구성 요소는 무엇인가?
5. 장점과 한계는 무엇인가?
6. 이후 어떤 모델에 영향을 주었는가?

---

## 학습 순서

- 8.1 AlexNet
- 8.2 VGG
- 8.3 Network in Network (NiN)
- 8.4 GoogLeNet
- 8.5 Batch Normalization
- 8.6 ResNet & ResNeXt
- 8.7 DenseNet
- 8.8 Designing CNN Architectures (RegNet)
