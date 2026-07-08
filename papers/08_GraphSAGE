# Inductive Representation Learning on Large Graphs (GraphSAGE)
NeurIPS 2017

# 왜 등장?
GCN은 Graph Structure와 Node Feature를 동시에 학습하는 최초의 Graph Neural Network
하지만 GCN에는 다음과 같은 한계가 존재
- 모든 노드의 이웃 정보를 사용해야 하므로 대규모 그래프에서 메모리 사용량이 쿰
- 학습 시 사용하지 않은 새로운(Node)에는 바로 적용할 수 없음
- 전체 그래프가 메모리에 존재해야함.
즉 GCN  **Transductive Learning(전이적 학습, 학습할 때 테스트 노드까지 그래프 안에 존재해야한다)**만 가능

GraphSAGE는 이러한 문제를 해결하기 위해
**이웃 노드를 Sampling하여 Inductive Learning이 가능한 GNN** 샘플링 개념을 도입

# 핵심 아이디어
GraphSAGE의 핵심은 모든 이웃을 사용하는 것이 아니라 일부 이웃만 Sampling 하여 Representation을 학습하는 것
또한 Node 자체를 임베딩으로 저장하는 것이 아니라 Aggregation Function 을 학습한다.
즉, 새로운 Node가 들어와도 이웃정보만 있으면 Representation을 생성 할 수 있음.

# 왜 중요?
GCN에서는 각 Node의 Representation을 직접 학습
하지만 새로운 Node가 추가되면 다시 학습
GraphSAGE는 Embedding 자체를 저장하는 것이 아니라
Aggregation 방법을 학습하기 때문에 새로운 Node도 바로 처리
이것이 GraphSAGE의 가장 큰 기여

# Inductive Learning
Inductive Learning이란 학습하지 않은 새로운 Node에 대해서도 Representation을 생성할 수 있는 능력을 의미한다.
예를 들어 학습 당시 존재하지 않았던 사용자가 새롭게 SNS에 가입하더라도 주변 이웃 정보를 이용하여 Embedding을 생성
반면 GCN은 새로운 Node가 추가되면 전체 모델을 다시 학습

#Neighbor Sampling
GraphSAGE는 모든 Neighbor 를 사용하는 대신 일부 Neighbor 만 샘플링한다.
예를들어 Node가 1000개의 Neighbor를 가지고 있다면 1000-> Random Sampling -> 25개 사용 처럼 일부 Neighbor만 이용
이를 통해 계산량과 메모리 사용량을 크게 줄일 수 있다.

# Aggregation
Sampling한 Neighbor들의 정보를 하나의 Representation으로 합친다.
GraphSAGE에서는 다양한 Aggregator를 제안

## 1. Mean Aggregator
가장 단순한 방법.Neighbor Feature의 평균을 계산한다.
GCN과 가장 유사한 방식

## 2. LSTM Aggregator
Neighbor들을 LSTM으로 Aggregation한다.
Neighbor 간 복잡한 관계를 학습

## 3.Pooling Aggregator
각 Neighbor Feature를 MLP에 통과시킨 후 Max Pooling을 수행
비선형 정보를 더 잘 학습

주요수식 체크
- $h_v^{k}$ : k번째 Layer의 Node Representation
- $N(v)$ : Neighbor Node
- AGGREGATE : Neighbor Aggregation Function
- CONCAT : 자신의 Feature와 Neighbor Feature 결합
- $W$ : Weight Matrix

# 이점
## 1. Inductive Learning
새로운 Node도 Embedding 생성 가능

## 2. Sampling 기반 학습
대규모 그래프에서도 효율적으로 학습 가능.

## 3. 다양한 Aggregator 사용 가능
평균뿐 아니라 LSTM Pooling 등 다양한 방식 사용 가능.

## 4. 확장성 우수

# 한계
## 1. Sampling 정보 손실
Neighbor를 일부만 선택하기 때문에 중요한 Neighbor가 제외될 수 있다.

## 2. Aggregator 선택 중요
어떤 Aggregator를 사용하는지에 따라 성능 차이가 크다.

## 3. 모든 Neighbor를 동일하게 처리
Neighbor Importance를 구분하지 않는다.
이 문제는 이후 GAT에서 Attention으로 해결

# 미친 영향
GraphSAGE는 샘플링 기반 GNN 연구의 시작이 되었다.
또한
- PinSAGE
- FastGCN
- ClusterGCN
등 대규모 그래프를 위한 다양한 GNN 연구에 큰 영향을 주었다.

또한 Inductive Learning 개념은 추천시스템과 Dynamic Graph 분야에서 널리 사용된다.

# 이해한 내용
GraphSAGE는 단순히 샘플링을 추가한 GCN 뿐만 아니라
임베딩을 학습하는 것이 아니라 Aggregation Function 을 학습한다는 점 이라는 것을 이해
즉, GraphSAGE 는 Node 자체를 기억하는 것이 아니라 주변 이웃으로부터 어떻게 Representation 을 만들것인가를 학습
그래서 새로운 Node가 추가되어도 다시 학습하지 않고 Representation을 생성하는게 큰 장점



