# CH9. Recurrent Neural Networks (RNN)

## Overview

지금까지 CNN은 이미지처럼 입력과 출력의 크기가 고정된 데이터를 처리하는 방법을 학습하였다. 하지만 자연어, 음성, 시계열 데이터와 같이 순서(Sequence)가 중요한 데이터는 기존의 Feedforward Neural Network나 CNN만으로는 효과적으로 처리하기 어렵다.

Recurrent Neural Network(RNN)는 이전 시점의 정보를 기억(Hidden State)하면서 현재 입력을 처리하는 구조를 제안하여 순차 데이터(Sequential Data)를 효과적으로 학습할 수 있도록 설계된 신경망이다.

이 장에서는 Sequence Modeling의 기본 개념부터 Language Model, RNN의 동작 원리, Backpropagation Through Time(BPTT)까지 RNN의 핵심 내용을 학습한다.

---

# 학습 목표

이 장에서는 다음 내용을 중심으로 학습한다.

- Sequence Data의 특징 이해
- Language Model의 개념 이해
- RNN의 구조와 동작 원리 이해
- Hidden State의 역할 이해
- BPTT(Backpropagation Through Time) 이해
- Gradient Vanishing 문제와 해결 방법 이해

---

# RNN의 발전 흐름

```text
Sequence Data
        │
        ▼
Language Model
        │
        ▼
Recurrent Neural Network (RNN)
        │
        ▼
Backpropagation Through Time (BPTT)
        │
        ▼
Gradient Vanishing
        │
        ▼
LSTM / GRU (CH10)
```

---

# Chapter Contents

## 9.1 Working with Sequences

- Sequence Data
- Autoregressive Model
- Sequence Prediction

---

## 9.2 Text Preprocessing

- Tokenization
- Vocabulary
- Text to Sequence

---

## 9.3 Language Models

- N-gram
- Perplexity
- Sequence Sampling

---

## 9.4 Recurrent Neural Networks

- Hidden State
- RNN 구조
- Sequence Modeling

---

## 9.5 RNN From Scratch

- RNN 구현
- Gradient Clipping
- Language Model

---

## 9.6 Concise RNN Implementation

- PyTorch RNN
- 간결한 구현

---

## 9.7 Backpropagation Through Time

- BPTT
- Gradient Vanishing
- Gradient Exploding

---

# 이 장에서 중요한 흐름

RNN은 순차 데이터를 처리하기 위해 Hidden State를 도입한 신경망이다.

입력 데이터를 시간(Time Step)에 따라 순차적으로 처리하며, 이전 시점의 정보를 다음 시점으로 전달한다. 이러한 구조 덕분에 문장 생성, 번역, 음성 인식, 시계열 예측과 같은 Sequence Modeling 문제를 해결할 수 있다.

하지만 RNN은 긴 Sequence에서 Gradient Vanishing 문제가 발생하기 때문에 이후 LSTM과 GRU가 등장하게 된다.

---

# 공부하면서 집중할 내용

각 절을 공부할 때 다음 질문을 중심으로 이해하면 좋다.

1. Sequence Data는 일반 데이터와 무엇이 다른가?
2. Hidden State는 왜 필요한가?
3. RNN은 이전 정보를 어떻게 기억하는가?
4. BPTT는 일반 Backpropagation과 무엇이 다른가?
5. Gradient Vanishing은 왜 발생하는가?
6. LSTM과 GRU는 어떤 문제를 해결하기 위해 등장했는가?

---

# 내가 이해한 내용

RNN은 CNN처럼 공간(Spatial) 정보를 처리하는 모델이 아니라 **시간(Time) 또는 순서(Order) 정보를 학습하기 위해 만들어진 신경망**이다. 가장 큰 특징은 Hidden State를 이용하여 이전 입력의 정보를 현재 계산에 활용한다는 점이며, 이를 통해 문장, 음성, 시계열과 같은 Sequence 데이터를 효과적으로 처리할 수 있다. 또한 RNN의 한계인 Gradient Vanishing 문제를 이해하는 것은 이후 LSTM, GRU, Attention, Transformer를 학습하기 위한 중요한 기반이 된다.
