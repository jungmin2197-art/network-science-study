# Linear Neural Networks for Classification

## 왜 사용하는가

Regression은 연속적인 값을 예측하지만,

Classification은:

- 고양이 / 강아지
- 정상 / 비정상
- 스팸 / 정상 메일

처럼 category를 예측하는 문제이다.

현실의 많은 AI 문제는 classification 문제에 해당한다.

딥러닝에서는 classification을 통해:

- probability modeling
- decision boundary
- classification loss
- optimization

개념을 학습한다.

---

# Softmax Regression

4장의 핵심 모델은 Softmax Regression이다.

Linear Regression을 classification 문제로 확장한 형태이다.

---

## 핵심 아이디어

입력 데이터를 각 클래스의 score로 변환한다.

$$
o = XW + b
$$

여기서:

- X : 입력
- W : weight
- o : 각 클래스 score(logit)

하지만 classification에서는 단순 score보다:

> "각 클래스일 확률"

이 중요하다.

그래서 softmax 함수를 사용한다.

---

# Softmax

Softmax는 score를 확률 형태로 변환한다.

$$
\hat{y}_i = \frac{e^{o_i}}{\sum_j e^{o_j}}
$$

특징:

- 모든 값이 0~1 사이
- 전체 합은 1
- 가장 높은 score가 높은 확률을 가짐

즉 모델의 출력을 probability distribution으로 바꾼다.

---

# 왜 Softmax를 사용하는가

Classification에서는:

> "이 데이터가 어떤 클래스에 속할 가능성이 높은가?"

를 알아야 한다.

Softmax는 이를 확률 형태로 표현 가능하게 만든다.

예:

```text
고양이 : 0.8
강아지 : 0.1
새 : 0.1
```

---

# Cross Entropy Loss

Classification에서는 squared loss보다 Cross Entropy를 더 많이 사용한다.

$$
L = -\sum_i y_i \log(\hat{y}_i)
$$

---

## 왜 사용하는가

확률 분포 차이를 측정하기 좋기 때문이다.

예측 확률이 실제 정답과 가까워질수록 loss가 감소한다.

---

## 장점

- classification에 적합
- gradient가 안정적
- softmax와 잘 결합됨

딥러닝 classification의 기본 loss function이다.

---

# 장점

## 1. Classification 문제 해결 가능

Linear Regression은 classification에 적합하지 않다.

Softmax Regression은 category 예측 가능.

---

## 2. 확률 기반 해석 가능

결과를 probability 형태로 표현 가능하다.

예측 confidence를 확인할 수 있다.

---

## 3. 구현이 단순함

구조가 간단하여 classification의 기본 개념 이해에 좋다.

---

## 4. 딥러닝 classifier의 기초

많은 neural network의 마지막 layer는 softmax 기반이다.

예:

- CNN classifier
- Transformer classifier
- BERT classification head

---

# 단점

## 1. 선형 decision boundary만 가능

가장 큰 한계.

복잡한 nonlinear 데이터 분리가 어렵다.

---

## 2. 표현력 부족

이미지나 자연어처럼 복잡한 데이터에서는 성능 한계 존재.

그래서 hidden layer를 추가한 MLP가 등장한다.

---

## 3. Feature engineering 의존성

좋은 feature를 직접 만들어야 하는 경우가 많다.

깊은 neural network는 representation learning을 자동 수행한다.

---

# Generalization

딥러닝에서 중요한 개념 중 하나.

훈련 데이터가 아니라:

> "보지 않은 데이터에서도 잘 동작하는가"

가 핵심이다.

---

## Training Error vs Generalization Error

### Training Error

훈련 데이터에서의 오차.

---

### Generalization Error

새로운 데이터에서의 오차.

실제 성능은 generalization 능력으로 판단한다.

---

# Underfitting과 Overfitting

## Underfitting

모델이 너무 단순해서 데이터 패턴 학습 실패.

---

## Overfitting

훈련 데이터를 과도하게 암기.

새 데이터 성능 감소.

---

# 해결 방법

## Weight Decay

weight 크기 제한.

---

## Dropout

일부 neuron 제거하며 학습.

---

## Early Stopping

validation 성능 감소 시 학습 중단.

---

# 중요한 흐름

Linear Regression은 연속값 예측,

Softmax Regression은 category classification으로 확장된 형태이다.

이후 neural network는:

- hidden layer
- nonlinear activation
- deeper architecture

를 추가하며 더 복잡한 문제를 해결하게 된다.

---

## 내가 이해한 내용

Softmax Regression은 딥러닝 classification의 가장 기본 구조이다.

특히:

- probability prediction
- softmax
- cross entropy
- overfitting
- generalization

개념을 처음 이해하는 데 중요하다.

많은 modern neural network 역시 마지막 출력 부분은 softmax classification 구조를 사용한다.
