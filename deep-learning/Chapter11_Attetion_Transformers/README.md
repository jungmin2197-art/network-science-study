# CH11. Attention Mechanisms and Transformers

## Overview

기존 RNN 기반 Seq2Seq 모델은 입력 문장을 하나의 Context Vector에 압축해야 하기 때문에 긴 문장에서 정보 손실(Information Bottleneck)이 발생하였다.

Attention Mechanism은 Decoder가 필요한 순간마다 Encoder의 모든 Hidden State를 직접 참고할 수 있도록 하여 이러한 문제를 해결하였다.

이후 Self-Attention을 기반으로 하는 Transformer가 등장하면서 RNN 없이도 Sequence를 효율적으로 처리할 수 있게 되었으며, 현대의 GPT, BERT, Vision Transformer(ViT), 대규모 언어 모델(LLM)의 기반이 되었다.

---

# 학습 목표

이 장에서는 다음 내용을 중심으로 학습한다.

- Attention의 기본 개념 이해
- Query, Key, Value의 역할 이해
- Attention Score 계산 방법 이해
- Bahdanau Attention 이해
- Multi-Head Attention 이해
- Self-Attention 이해
- Positional Encoding 이해
- Transformer 구조 이해
- Vision Transformer(ViT) 이해
- 대규모 사전학습 모델(BERT, GPT, T5) 이해

---

# 발전 과정

```text
RNN
    │
    ▼
LSTM / GRU
    │
    ▼
Encoder-Decoder
    │
    ▼
Seq2Seq
    │
    ▼
Attention
    │
    ▼
Bahdanau Attention
    │
    ▼
Self-Attention
    │
    ▼
Transformer
    │
    ▼
Vision Transformer
    │
    ▼
BERT / GPT / T5
    │
    ▼
Large Language Models
```

---

# Chapter Contents

## 11.1 Queries, Keys, and Values

- Query
- Key
- Value
- Information Retrieval

---

## 11.2 Attention Pooling

- Similarity
- Kernel
- Nadaraya-Watson Regression

---

## 11.3 Attention Scoring Functions

- Dot Product Attention
- Scaled Dot Product Attention
- Additive Attention

---

## 11.4 Bahdanau Attention

- Seq2Seq with Attention
- Dynamic Context Vector

---

## 11.5 Multi-Head Attention

- Multiple Attention Heads
- Parallel Representation Learning

---

## 11.6 Self-Attention and Positional Encoding

- Self-Attention
- Positional Encoding
- CNN vs RNN vs Transformer

---

## 11.7 Transformer

- Encoder
- Decoder
- Feed Forward Network
- Residual Connection
- LayerNorm

---

## 11.8 Vision Transformer

- Patch Embedding
- Transformer Encoder
- Image Classification

---

## 11.9 Large-Scale Pretraining

- BERT
- T5
- GPT
- Large Language Models

---

# 이 장에서 중요한 흐름

Seq2Seq는 입력 문장을 하나의 Context Vector에 압축해야 했기 때문에 긴 문장에서 성능이 저하되는 문제가 있었다.

Attention은 Decoder가 필요한 순간마다 Encoder의 모든 Hidden State를 참고하도록 하여 이러한 문제를 해결하였다.

이후 Self-Attention은 입력 Sequence 내부의 모든 Token 관계를 동시에 학습할 수 있게 만들었고, Transformer는 RNN을 완전히 제거하면서 병렬 연산과 장거리 의존성(Long-range Dependency) 학습을 가능하게 하였다.

현재의 GPT, BERT, ViT, LLaMA 등 대부분의 최신 AI 모델은 모두 Transformer를 기반으로 한다.

---

