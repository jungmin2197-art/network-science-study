# 7.2 Convolutions for Images

> **핵심 키워드:** Cross-Correlation · Convolution Layer · Kernel · Feature Map · Edge Detection · Receptive Field

---

## 등장 배경

앞 절에서는 Fully Connected Layer가 이미지 데이터를 처리하기에 비효율적이며, 이를 해결하기 위해 Convolution을 사용하는 이유를 학습하였다.

하지만 아직 Convolution이 실제로 어떻게 이미지를 처리하는지는 알지 못한다.

이번 절에서는 **Convolution 연산의 실제 계산 과정**을 이해하고, Kernel(Filter)이 이미지에서 어떤 특징을 추출하는지 학습한다. 또한 CNN이 Edge와 같은 중요한 특징을 어떻게 자동으로 학습하는지, 그리고 Feature Map과 Receptive Field가 어떤 의미를 가지는지도 함께 살펴본다.

---

## 핵심 아이디어

> **Kernel(Filter)이 이미지를 조금씩 이동하면서 지역적인 특징(Local Feature)을 추출하고, 이를 Feature Map으로 표현한다.**

Convolution의 전체 과정은 다음과 같다.

```
Input Image
      │
      ▼
Kernel(Filter)
      │
      ▼
Cross-Correlation
      │
      ▼
Feature Map
      │
      ▼
Next Convolution Layer
```

즉,

이미지 전체를 한 번에 처리하는 것이 아니라

작은 영역(Local Region)을 반복적으로 탐색하며 특징을 추출한다.

---

## 주요 개념

### 1. Cross-Correlation Operation

CNN에서 실제 사용하는 연산은 엄밀히 말하면 **Convolution**이 아니라 **Cross-Correlation**이다.

Kernel을 뒤집지 않고 그대로 이미지 위를 이동하면서

각 위치에서

- Element-wise Multiplication
- Sum

을 계산한다.

```
Image

1 2 3
4 5 6
7 8 9

Kernel

1 0
0 1

↓

1×1 + 2×0 + 4×0 + 5×1
```

이 계산을 모든 위치에서 반복하여 새로운 Feature Map을 생성한다.

#### 왜 사용하는가?

- 이미지의 중요한 특징을 추출하기 위해
- 계산이 단순하고 효율적이기 때문이다.

---

### 2. Convolutional Layer

Convolution Layer는 여러 개의 Kernel을 이용하여 다양한 특징을 추출하는 Layer이다.

하나의 Kernel은 하나의 Feature Map을 생성한다.

예를 들어

```
Input

↓

Kernel 1 → Edge

Kernel 2 → Texture

Kernel 3 → Corner

↓

Multiple Feature Maps
```

처럼 서로 다른 특징을 동시에 학습할 수 있다.

#### 왜 사용하는가?

- 다양한 특징을 동시에 추출하기 위해
- 이미지 표현력을 높이기 위해

---

### 3. Object Edge Detection

Edge는 이미지에서 가장 중요한 특징 중 하나이다.

Kernel을 적절히 설계하면

- 세로 Edge
- 가로 Edge
- 대각선 Edge

등을 쉽게 검출할 수 있다.

예를 들어

```
0 1

0 1
```

과 같은 Kernel은 세로 방향의 변화를 강조한다.

#### 왜 중요한가?

- Edge는 객체의 윤곽을 나타낸다.
- 대부분의 고수준 특징은 Edge로부터 시작된다.
- CNN의 초기 Layer는 Edge를 주로 학습한다.

---

### 4. Learning a Kernel

초기 CNN에서는 Edge Detection Kernel을 사람이 직접 설계하기도 했다.

하지만 현대 CNN에서는 Kernel을 사람이 만드는 것이 아니라

**Backpropagation을 통해 자동으로 학습한다.**

즉,

```
Random Kernel

↓

Training

↓

Useful Kernel
```

으로 변화한다.

#### 왜 중요한가?

- 사람이 특징을 직접 설계할 필요가 없다.
- 데이터에 맞는 최적의 Feature를 자동으로 학습할 수 있다.

---

### 5. Cross-Correlation vs Convolution

수학적인 Convolution은 Kernel을 180° 회전시켜 계산한다.

하지만 CNN에서는 Kernel을 회전하지 않는다.

즉,

```
Mathematics

Kernel Flip

↓

Convolution
```

```
Deep Learning

No Flip

↓

Cross-Correlation
```

을 사용한다.

#### 왜 Convolution이라고 부르는가?

역사적으로 CNN 논문에서 Convolution이라는 용어가 사용되었고,

현재도 관례적으로 그대로 사용한다.

---

### 6. Feature Map

Feature Map은 Kernel이 추출한 특징을 저장한 결과이다.

```
Input

↓

Kernel

↓

Feature Map
```

Layer가 깊어질수록

Feature Map은

- Edge
- Texture
- Object Parts
- Object

순으로 더욱 추상적인 정보를 표현한다.

#### 왜 중요한가?

- 다음 Layer의 입력이 된다.
- 이미지의 중요한 특징만 전달한다.

---

### 7. Receptive Field

Receptive Field는 하나의 출력값이

입력 이미지의 어느 영역을 참고하여 계산되었는지를 의미한다.

초기 Layer에서는 작은 영역만 보지만,

Layer가 깊어질수록

```
3×3

↓

5×5

↓

9×9

↓

전체 이미지
```

처럼 점점 넓은 영역을 바라보게 된다.

#### 왜 중요한가?

- 객체 전체를 이해하기 위해
- 더 복잡한 특징을 학습하기 위해
- Deep CNN의 표현력을 높이기 위해

---

## 장점

- 이미지의 지역적인 특징을 효과적으로 추출할 수 있다.
- Kernel을 공유하여 Parameter 수를 크게 줄일 수 있다.
- 다양한 Feature Map을 동시에 생성할 수 있다.
- Layer가 깊어질수록 더욱 추상적인 특징을 학습할 수 있다.

---

## 한계

- Kernel 크기에 따라 추출 가능한 특징이 제한된다.
- 초기 Layer는 작은 영역만 관찰한다.
- 깊은 Layer가 필요할수록 계산량이 증가한다.

---

## 핵심 개념 정리

| 개념 | 역할 |
|------|------|
| Cross-Correlation | Kernel과 이미지를 계산하여 특징 추출 |
| Kernel(Filter) | 특징을 추출하는 작은 행렬 |
| Convolution Layer | 여러 Kernel을 이용하여 다양한 특징 추출 |
| Feature Map | 추출된 특징을 저장 |
| Receptive Field | 출력이 참고한 입력 이미지의 영역 |

---

## 다음 절과의 연결

7.2에서는 Convolution 연산과 Kernel이 이미지를 처리하는 원리를 학습하고, Feature Map과 Receptive Field의 개념을 이해하였다.

하지만 Convolution을 수행하면 Feature Map의 크기가 계속 감소하며, Kernel의 이동 방식에 따라 출력 크기가 달라진다.

다음 절에서는 **Padding과 Stride**를 이용하여 출력 크기를 조절하고, Convolution Layer를 더욱 효율적으로 사용하는 방법을 학습한다.
