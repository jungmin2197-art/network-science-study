# Cluster-GCN: An Efficient Algorithm for Training Deep and Large Graph Convolutional Networks

KDD 2019

# 왜 등장?
GCN 은 모든 이웃의 정보를 aggregation 하기 때문에 그래프가 커질수록 메모리 사용량과 계산량이 급격히 증가
GraphSAGE는 Neighbor Sampling 을 이용하야 이러한 문제를 완화하였지만,
Sampling 과정에서 일부 Neighbor만 사용하기 때문에 정보 손실(Information Loss)이 발생하며, Sampling으로 인한 분산(Variance) 문제도 존재한다.

Cluster-GCN은 이러한 문제를 해결하기 위해
 **그래프를 여러 개의 Cluster(Subgraph)로 분할한 뒤, Cluster 단위로 Mini-batch 학습을 수행하는 방법**

# 핵심 아이디어
Cluster-GCN의 핵심은
**Node를 Sampling하는 것이 아니라 Graph를 먼저 Partition한 후 Cluster 단위로 학습하는 것**

기존 방법은 Graph -> Neighbor Sampling -> Mini-batch 를 수행
반면 Cluster-GCN 은 Graph -> Graph Partition -> Cluster -> Mini-batch 를 수행

Sampling 대신 Graph Partition을 이용하여 메모리 사용량을 줄이고 Neighborhood 정보를 최대한 유지

# 왜 중요?
GraphSAGE에서는 Neighbor를 Sampling하기 때문에 중요한 Neighbor가 제외될 수 있다.
하지만 Cluster-GCN은 같은 Cluster 안의 Node들을 함께 학습하기 때문에 Neighbor 정보가 더 잘 보존
또한 Mini-batch 학습이 가능하여 대규모 그래프에서도 효율적으로 학습 가능

# Graph Partition
Cluster-GCN은

METIS와 같은 Graph Partition 알고리즘을 이용하여 그래프를 여러 개의 Cluster로 나눈다.

예를 들어
Large Graph

↓

Cluster 1

Cluster 2

Cluster 3

...

Cluster N
```

각 Cluster는 하나의 Mini-batch처럼 사용

# Mini-batch Training
학습 과정에서는 하나 또는 여러 개의 Cluster를 선택하여 Forward와 Backpropagation을 수행
즉,전체 그래프를 GPU에 올릴 필요가 없다.
필요한 Cluster만 메모리에 올려 학습을 진행

# 주요 수식
Cluster-GCN 자체는 새로운 Graph Convolution 연산을 제안한 논문가 아니다.
GCN의 Message Passing 연산은 그대로 사용하며, 학습에 사용하는 Adjacency Matrix를 Cluster 단위의 부분 그래프로 제한

# 이점
1. Mini-batch Learning
전체 그래프를 사용하지 않고 Cluster 단위로 학습 가능

2. 메모리 사용량 감소
필요한 Cluster만 GPU 메모리에 올리기 때문에 대규모 그래프에서도 학습이 가능

3. Sampling Error 감소
Neighbor Sampling 대신 Graph Partition을 사용하므로 Neighborhood 정보를 더 잘 유지 가능

4. 학습 속도 향상
sampling 기반 방법보다 더 빠른학습이 가능

# 한계
1. Graph Partition 필요
학습 전에 Graph Partition을 수행해야 한다.
그래프가 자주 변경되는 Dynamic Graph에서는 빡셀 수 있음

2. Cluster 간 정보 손실
서로 다른 Cluster에 존재하는 Neighbor는 동일한 Mini-batch에서 함께 학습되지 않을 수 있음

3. Partition 품질에 의존
Cluster를 어떻게 분할하느냐에 따라 성능 차이가 발생 가능

# 후속 영향
Cluster GCN은 대규모 그래프 학습(scalable GNN)의 대표 방법 중 하나
이후
- GraphSAINT
- ShaDow-GNN
- Quiver
- PyTorch Geometric NeighborLoader
등 다양한 대규모 GNN 학습 기법에 영향
현재 대부분의 GNN Framework에서도 Mini-batch 기반 학습의 대표적인 방법으로 사용

# 이해 및 느낀점
sampling 개선 뿐 아니라, Graph 를 먼저 여러개의 Cluster 로 분할한뒤 cluster 단위로 학습한다는게 메인
SAGE는 노드를 샘플링하는 방식이고 Cluster-GCN 은 그래프 자체를 Partition 하여 미니베치를 구성한다
정보 손실을 줄이면서 대규모 그래프를 학습할 수 있다는게 키 포인트



