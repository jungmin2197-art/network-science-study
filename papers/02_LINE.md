# LINE: Large-scale Information Network Embedding

WWW 2015

# 왜 등장했는가

DeepWalk는 Random Walk를 이용하여 그래프를 문장처럼 생성한 후 Word2Vec를 통해 Node Embedding을 학습. 하지만 DeepWalk에는 다음과 같은 한계가 존재
- Random Walk 생성 비용 큼.
- 그래프 커질수록 학습속도 느려짐.
- 가까운 노드(Local Structure)는 잘 학습하지만 다양한 관계 반영은 못함

LINE은 > ** Random Walk 없이 그래프의 연결 관계를 직접 학습하는 방법 **

# 핵심 아이디어
LINE 핵심은 > **그래프에서 중요한 관계(Proximity)를 직접 보존하는 것**

LINE은 그래프의 구조를 두 가지 관점에서 학습한다.

- First-order Proximity 1차 근접성 ( 직접 연결 되어있으면 비슷하다, 가장 직관적) 즉, Edge가 존재하는 두 노드는 Embedding 공간에서도 가까워져야 한다.
- Second-order Proximity 2차 근접성 ( 직접 연결은 안되어있지만 이웃이 비슷하면 비슷한 노드다) A와 B는 연결되어 있지 않지만 같은 이웃(C)을 가지므로 비슷한 Embedding을 갖도록 학습
DeepWalk는 RandomWalk를 통해 암묵적으로 학습하려했으나 LINE은 애당초 따로 정의하자라고 학습
이 두 정보를 각각 학습한 후 하나의 Embedding으로 결합

# 왜 중요?

DeepWalk는 Random Walk를 통해 간접적으로 그래프 구조를 학습한다.
반면 LINE은 그래프의 연결 관계 자체를 직접 최적화한다.
그래서
- Random Walk가 필요 없고
- 대규모 그래프에서도 효율적으로 학습할 수 있다.

# 주요 수식
First-order Proximity, Second-order Proximity 는 다음 목적 함수를 최소화한다.
즉 노드의 Neighborhood Distribution이 비슷하도록 학습

# 얻을 수 있는 이점

1. Random Walk 불필요
DeepWalk 보다 학습과정 단순

2. 대규모 그래프 처리 가능

3. Local Structure 보존
직접 연결 관계를 효과적으로 학습

4. Neighborhood Information 활용
비슷한 이웃 구조를 가진 노드도 비슷하게 표현

# 한계
1. Node Feature 사용 불가
여전히 그래프 구조만 이용한다.
노드의 Attribute는 활용하지 못함

2. Higher-order Structure 표현 부족
1-hop, 2-hop 관계 중심으로 학습하므로 복잡한 그래프 구조를 표현하는 데는 한계가 있다

3. End-to-End Learning 불가능
Embedding을 먼저 생성한 후 Classification 등을 수행

# 끼친 영향
대규모 그래프에서도 효율적인 그래프 임베딩이 가능함 보여줌
이후 에서 Neighborhood Information 의 중요성을 이해하는 기반
특히 First-order Proximity와 Second-order Proximity 개념은 Graph Representation Learning에서 알고있자

# 이해 및 느낀점
LINE은 DeepWalk보다 단순? 하다고 생각했으나 핵심은 Ranod Walk를 제거한 것이 아니라 그래프에서 어떤 관계를 보존할 것인가를 명확하게 정의한 것
직접 연결된 노드의  관계를 비슷한 이웃을 가진 노드의 관계를 학습한다는 점이 중요 아이디어
문장을 생성하지 않아서 대규모 그래프 효율적 사용가능
