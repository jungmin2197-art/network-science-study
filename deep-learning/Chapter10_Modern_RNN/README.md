# CH10. Modern Recurrent Neural Networks

## Overview

기본 RNN은 순차 데이터를 처리할 수 있다는 장점이 있지만, Sequence가 길어질수록 Gradient Vanishing과 Long-term Dependency 문제가 발생한다.

이 장에서는 이러한 문제를 해결하기 위해 제안된 다양한 RNN 구조와 Sequence-to-Sequence(Seq2Seq) 모델을 학습한다.

또한 기계 번역(Machine Translation)을 예제로 Encoder-Decoder 구조와 Beam Search를 이용한 문장 생성 방법까지 살펴본다.

---

# 학습 목표

이 장에서는 다음 내용을 중심으로 학습한다.

- LSTM의 구조와 동작 원리 이해
- GRU의 구조와 LSTM과의 차이 이해
- Deep RNN 이해
- Bidirectional RNN 이해
- Machine Translation 데이터 처리 과정 이해
- Encoder-Decoder 구조 이해
- Sequence-to-Sequence(Seq2Seq) 학습 과정 이해
- Beam Search를 이용한 문장 생성 이해

---

# RNN의 발전 흐름

```text
Vanilla RNN
      │
      ▼
Gradient Vanishing
      │
      ▼
LSTM
      │
      ▼
GRU
      │
      ▼
Deep RNN
      │
      ▼
Bidirectional RNN
      │
      ▼
Encoder-Decoder
      │
      ▼
Seq2Seq
      │
      ▼
Beam Search
```

---

# Chapter Contents

## 10.1 Long Short-Term Memory (LSTM)

- Memory Cell
- Forget Gate
- Input Gate
- Output Gate

---

## 10.2 Gated Recurrent Unit (GRU)

- Reset Gate
- Update Gate
- Candidate Hidden State

---

## 10.3 Deep Recurrent Neural Networks

- Multi-layer RNN
- Hidden State Stacking

---

## 10.4 Bidirectional Recurrent Neural Networks

- Forward RNN
- Backward RNN
- Context Information

---

## 10.5 Machine Translation

- Parallel Corpus
- Tokenization
- Sequence Dataset

---

## 10.6 Encoder-Decoder

- Encoder
- Decoder
- Context Vector

---

## 10.7 Sequence-to-Sequence Learning

- Seq2Seq
- Teacher Forcing
- Masked Loss
- Prediction

---

## 10.8 Beam Search

- Greedy Search
- Exhaustive Search
- Beam Search

---

# 이 장에서 중요한 흐름

Vanilla RNN은 Sequence 데이터를 처리할 수 있지만 긴 문장을 기억하기 어렵다.

LSTM과 GRU는 Gate 구조를 이용하여 중요한 정보를 오래 기억할 수 있도록 개선하였다.

이후 Encoder-Decoder 구조가 등장하면서 입력 Sequence와 출력 Sequence의 길이가 다른 문제를 해결할 수 있게 되었고, Seq2Seq 모델은 기계 번역의 기반이 되었다.

마지막으로 Beam Search는 문장 생성 과정에서 더 자연스러운 결과를 선택하기 위한 탐색 기법이다.

---
