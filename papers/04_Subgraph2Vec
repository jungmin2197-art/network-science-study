# subgraph2vec: Learning Distributed Representations of Rooted Subgraphs from Large Graphs

CoRR (arXiv) 2016

# 왜 등장?

앞서 정리한 그래프 임베딩 방법인
- DeepWalk
- LINE
- node2vec
모두 **Node Embedding**을 학습하는 방법

즉, 그래프에서 개별 노드만 벡터로 표현하였음.
하지만 실제 그래프 분석에는 ** 노드 하나보다 주변 구조(SubGraph) 가 더 중요한 경우가 많다 **

예시 - 분자 그래프, 프로그램 분석 , 지식그래프
에서는 노드 자체보다 주변 구조가 더 많은 정보를 담는다.

subgraph2vec은 이러한 문제를 해결하기 위해
**Subgraph 자체를 Embedding으로 학습하는 방법**을 제안

# 핵심 아이디어
subgraph2vec의 목표는 ** Rooted Subgraph를 하나의 단어처럼 학습하는 것 **
Deep Walk 가 Node-> Word 로 생각했다면 subghraph2vec 는 Subgraph -> word 로 생각한다.

구조 자체를 하나의 표현으로 학습

# 왜 중요
많은 그래프 문제에서 노드 하나만 보는 것 보다 주변 구조(Local Structure)를 함께 보는 것이 더 중요
구조 정보를 직접 Embedding에 반영
# Rooted Subgraph

Rooted Subgraph란
특정 노드를 중심(Root)으로 일정 거리(k-hop)까지 포함한 부분 그래프를 의미한다.

예를 들어

```
      A
      |
B --- C --- D
      |
      E
```

Root가 C이고
1-hop을 선택하면

```
 A
 |
 C
/|\
B D
|
E
```

가 하나의 Rooted Subgraph가 된다

# 핵심 아이디어: Weisfeiler-Lehman Relabeling
subgraph2vec은 Rooted Subgraph를 생성하기 위해 Weisfeiler-Lehman(WL) Relabeling을 사용한다.
WL 알고리즘을 이용하여 각 노드 주변의 구조를 고유한 Label로 변환한다.
이 Label을 이용하여 Subgraph를 생성

# Skip-Gram 학습
생성된 Rooted Subgraph를 Word2vec의 skip-Gram 방식으로 학습
즉, 비슷한 Context에서 등장하는 Subgraph는 비슷한 Emedding 을 갖도록 학습

# 얻을 수 있는 이점
1. 구조 정보 보존
Node 하나가 아닌 Local Structure 전체를 학습 할 수있다.
2. 그래프 분류에 유리
Subgraph 정보를 활용하기 때문에 Graph Classification 성능 향상에 도움이 된다.
3. 분자(Molecule) 분석에 적합
분자는 원자 하나보다 주변 구조가 더 중요하고 subgraph2vec 는 이러한 특성을 잘 반영한다.

# 한계
1. 계산 비용 증가 
Subgraph 생성 과정이 복잡하고 그래프가 커질수록 계산량 크게 증가
2. Node Feature 활용 불가 
마찬가지로 그래프 구조만 사용 Node Attribute 는 반영하지 못함
3. End-to-End Learning 아님
먼저 Embedding 을 학습한 후 Downstream Task를 수행한다.

# 후속 연구 영향
그래프에서 노드뿐 아니라 부분 그래프를 표현하는 연구의 기반이 되었다.
이후 
- Graph Classification
- Graph Kernel
- GraphRAG
등에서 부분 구조를 활용하는 연구에 영향을 줌

# 이해 및 느낀점

Node2vec와 비슷한 논문이라 생각했으나 핵심은 뭐를 Embedding 할 것인가 라는점
기존은 노드를 임베딩 했다면 subgraph2vec 는 노드 주변의 구조 전체를 하나의 표현으로 학습
부분구조가 중요한 문제에서는 노드 임베딩 보다 더 많은 정보를 표현 할 수 있다는 점



