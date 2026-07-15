# CH12. Optimization Algorithms

## Overview

딥러닝 모델은 손실 함수(Loss Function)를 최소화하도록 학습된다. 이를 위해 다양한 최적화(Optimization) 알고리즘이 사용된다.

이 장에서는 Gradient Descent를 시작으로 SGD, Mini-batch SGD, Momentum, AdaGrad, RMSProp, Adadelta, Adam까지 현대 딥러닝에서 가장 널리 사용되는 Optimizer들의 원리와 차이점을 학습한다.

또한 Convex Optimization, Learning Rate Scheduling 등 최적화의 이론적 배경도 함께 다룬다.

---

# 학습 목표

이 장에서는 다음 내용을 중심으로 학습한다.

- Optimization의 목적 이해
- Convex Optimization 이해
- Gradient Descent 이해
- Stochastic Gradient Descent(SGD) 이해
- Mini-batch SGD 이해
- Momentum 이해
- AdaGrad 이해
- RMSProp 이해
- Adadelta 이해
- Adam Optimizer 이해
- Learning Rate Scheduling 이해

---

# 발전 과정

```text
Loss Function
      │
      ▼
Gradient Descent
      │
      ▼
Stochastic Gradient Descent (SGD)
      │
      ▼
Mini-batch SGD
      │
      ▼
Momentum
      │
      ▼
AdaGrad
      │
      ▼
RMSProp
      │
      ▼
Adadelta
      │
      ▼
Adam
      │
      ▼
Learning Rate Scheduling
```

---

# Chapter Contents

## 12.1 Optimization and Deep Learning

- Optimization Goal
- Loss Function
- Optimization Challenges

---

## 12.2 Convexity

- Convex Set
- Convex Function
- Convex Optimization
- Constraints

---

## 12.3 Gradient Descent

- Gradient
- One-dimensional GD
- Multivariate GD
- Adaptive Methods

---

## 12.4 Stochastic Gradient Descent

- SGD
- Dynamic Learning Rate
- Convergence Analysis

---

## 12.5 Mini-batch SGD

- Vectorization
- Mini-batch
- GPU Efficiency

---

## 12.6 Momentum

- Velocity
- Exponential Moving Average
- Faster Convergence

---

## 12.7 AdaGrad

- Adaptive Learning Rate
- Sparse Features
- Preconditioning

---

## 12.8 RMSProp

- Exponential Moving Average
- Stable Learning Rate

---

## 12.9 Adadelta

- Adaptive Update
- Learning Rate-Free Optimization

---

## 12.10 Adam

- Momentum
- RMSProp
- Bias Correction
- Yogi

---

## 12.11 Learning Rate Scheduling

- Learning Rate Scheduler
- Cosine Annealing
- Warmup
- Decay Policy

---

# 이 장에서 중요한 흐름

딥러닝 학습은 손실 함수(Loss Function)를 최소화하는 방향으로 파라미터를 업데이트하는 과정이다.

가장 기본적인 Gradient Descent는 전체 데이터를 이용하여 기울기를 계산하지만 계산량이 크다는 단점이 있다.

이를 개선하기 위해 SGD와 Mini-batch SGD가 등장하였고, 이후 Momentum, AdaGrad, RMSProp, Adadelta, Adam과 같이 더 빠르고 안정적인 Optimizer들이 제안되었다.

마지막으로 Learning Rate Scheduling을 통해 학습 과정에서 Learning Rate를 조절하여 더욱 효율적인 학습을 수행한다.

---
