# metapath2vec: Scalable Representation Learning for Heterogeneous Networks

KDD 2017

# Heterogeneous Graph
Heterogeneous Graph란 노드와 Edge의 종류가 여러 개인 그래프를 의미

# 왜 등장
기존 Graph Embedding 방법인
-DeepWalk
- LINE
- node2vec
- struc2vec
은 모두 **동종 그래프(Homogeneous Graph)** 를 대상으로 설계

즉, 모든 노드와 Edge가 같은 종류라는 가정

하지만 실제 그래프는 다양한 종류의 노드와 관계를 포함하는 경우가 많다.
기존 Random Walk를 그대로 적용하면 의미 없는 경로가 생성되어 좋은 Embedding을 학습하기 어려움.

metapath2vec은 이러한 문제를 해결하기 위해 ** Meta-path **를 이용한 Random Walk를 제안

# 핵심 아이디어
metapath2vec 목표는
** Heterogeneous Graph에서 의미 있는 Random Walk를 생성하는 것 ** 

이를 위해 Random Walk 의 이동경로를 Meta-path 로 제한한다.
즉, 그래프의 의미(Semantics)를 유지하면서 노드 임베딩을 학습

# 왜 중요
기존 node2vec 는 Node-> Node -> Node 만 고려
하지만  Heterogeneous Graph에서는 노드마다 의미가 다름.
Meta-path를 사용하면 의미있는 관계만 따라가며 Embedding 을 학습 할 수 있음
Heterogeneous Graph 는 노드의 타입이 다르므로 단순 Random Walk 보다 관계의 의미를 고려하는 것이 더 중요

# Meta-path
Meta-path는 노드 타입과 관계 타입을 이용하여 Random Walk의 경로를 정의
예시
Author → Paper → Author
는 공동 연구자를 찾는 Meta-path
Author → Paper → Venue → Paper → Author
같은 학회에 논문를 발표한 연구자를 찾는 Meta-path

Meta-path를 이용하면 Random Walk가 그래프의 의미를 유지하도록 제한

# 학습
Meta-path 를 따라 생성된 Random Walk를 Word2vec 의 Skip-gram 모델에 입력
즉, 비슷한 Context 에서 등장하는 노드는 비슷한 Embedding 을 갖도록 학습
기본적인 Skip-Gram 목적 함수는 DeepWalk와 유사하지만,Context를 생성하는 방식이 Meta-path 기반이라는 점이 가장 큰 차이

# 이점
1. 의미 있는 Random Walk
Meta-path를 이용하여 그래프의 의미를 유지할 수 있다.
2. Heterogeneous Graph 활용 가능
다양한 타입의 노드와 Edge를 효과적으로 학습
3. Semantic Relationship 학습
단순 연결 관계가 아니라 의미 있는 관계를 Embedding에 반영
4. 대규모 그래프 적용 가능
지식 그래프, 추천시스템 분야 활용 가능

# 한계
1. Meta-path를 사람이 설계 해야한다가 가장 큰 한계
좋은 Meta-path 를 직접 정의

2. 마찬가지로 Node Feature 사용 불가
그래프 구조만 사용하고 Node Attribute는 반영 못함

3. End-to-End Learning은 지원 X

# 후속 연구 영향
metapath2vec은 Heterogeneous Graph Representation Learning의 대표적인 시작점
이후
- HAN (Heterogeneous Graph Attention Network)
- MAGNN
- HGT (Heterogeneous Graph Transformer)

등 다양한 Heterogeneous GNN 연구의 기반

# 이해 및 느낀점

Heterogeneous Graph에 적용한 논문 정도로 생각 
핵심 Random Walk 자체가 아니라 어떤 경로를 따라 이동할 것인가 라는 점
Meta-path 를 이용하면 의미를 유지하면서 Embedding 학습 가능 하니깐
지식 그래프 처럼 노드 종류 다양한 그래프에서 효과적 일듯
근데 사람이 직접 설계 어차피 한계는 존재

