# Graph Attention Networks (GAT)

ICLR 2018

# 왜 등장?
GCN은 이웃노드의 정보를 Aggregation 하여 Node Representation을 학습하는 Graph Neural Network이다.
이후 GraphSAGE는 Neighbor Sampling을 이용하여 대규모 그래프에서도 효율적으로 학습할 수 있도록 개선
하지만 두 모델 모두 공통적 한계가 존재
- 모든 Neighbor를 동일한 중요도로 Aggregation
- 어떤 Neighbor가 중요한지 학습하지 못함
- 불필요한 Neighbor도 같은 비중으로 반영

GAT는 이러한 문제를 해결하기 위해 ** Attention Mechanism ** 을 이용하여
중요한 Neighbor에 더 큰 가중치를 부여하는 Graph Neural Netwokr 를 제안

# 핵심 아이디어
** Neighbor 마다 서로 다른 Attention Score 를 학습하는 것 **
모든 Neighbor를 동일하게 평균내는 것이 아니라 중요한 Neighbor는 크게 반영하고 덜 중요한 Neighbor는 작게 반영

# 왜 중요?
GCN 에서는 모든 Neighbor 가 동일한 Weight를 가진다.
예를 들어
      A

      |

B ---- C ---- D

      |

      E
Node C를 업데이트 할때 
A,B,D,E 모두 같은 비중으로 사용
하지만 실제 그래프에서는 모든 Neighbor가 동일하게 중요한 것은 아님.
GAT는 Attention을 이용하여 각 Neighbor의 중요도를 학습

# Attention Mechanism
Attention은 현재 Node와 Neighbor Node의 관계를 이용하여 Importance Score를 계산하는 방법
Neighbor -> Attention Score 계산 -> Weighted Sum -> 새로운 Representation 생성

# Attention Coefficient
두 노드의 Attention Score는 다음과 같이 계산
e_{ij}=a(Wh_i,Wh_j)
- h_i : 현재 Node Feature
- h_j : Neighbor Feature
- W : Weight Matrix
- a: Attention Function
현재 Node 와 Neighbor의 관계를 이용하여 중요도를 계산

# Softmax Normalization
Attention Score를 확률처럼 사용하기 위해 Softmax를 적용

\alpha_{ij}=\frac{\exp(e_{ij})}{\sum_{k\in N(i)}\exp(e_{ik})}
여기서 alpha_{ij}는 Neighbor j가 Node i 에게 주는 중요도를 의미
Attention Score의 합은 1이된다.

# Node update
Neighbor Feature를 Attention Score로 가중합하여 새로운 Representation을 생성

# Multi-head Attention
GAT는 Attention을 여러 번 독립적으로 수행
이를 Multi-head Attention 이라고 한다.
예를 들어 8개의 Head를 사용하면 8개의 서로 다른 Attention을 학습
장점은
- 학습 안정성 증가
- 다양한 관계 학습
- 일반화 성능 향상

# 얻을 수 있는 이점
1. Neighbor Importance 학습
모든 Neighbor를 동일하게 보지 않는다. 중요한 Neighbor를 자동으로 선택

2. Parameter Sharing
Attention Function을 모든 Node가 공유

3. End-to-End Learning
Attention Score도 학습 과정에서 자동으로 최적화

4. 높은 표현력
GCN보다 더 풍부한 Neighborhood 정보를 학습

# 한계
1. 계산량 증가
모든 Edge마다 Attention을 계산 GCN보다 연산량이 크다.

2. 대규모 그래프 비효율
이웃 수가 많을수록 Attention 계산 비용이 증가

3. Overfitting 가능성
Attention Parameter가 증가하면서 복잡한 모델이 될 수 있다.

# 후속 영향
GAT는 Attention Mechanism을 Graph Neural Network에 처음 성공적으로 적용한 연구
이후
- GATv2
- Heterogeneous GAT
- Graph Transformer
등 다양한 Attention 기반 GNN 연구의 기반.
특히 Graph Transformer는 GAT의 Attention 개념을 더욱 확장한 모델

# 이해 내용 및 느낀점
Neighbor 를 동일하게 사용하는 것이 아니라 Neighbor 마다 서로 다른 중요도를 학습한다는 점
중요한 Neighbor 의 의견을 더 많이 반영하는 모델이라고 이해
Attention Mechanism 덕분에 Node Representation이 더 중요한 이웃의 정보를 중심으로 학습된다는 점이 GAT의 가장 큰 기여
