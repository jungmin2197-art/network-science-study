GNN의 이론적인 표현력(Expressive Power)분석

# How Powerful are Graph Neural Networks? (GIN)

ICLR 2019

# 왜 등장?
GCN, GraphSAGE, GAT는 모두 Message Passing 기반 Graph Neural Network이다.
이들은 이웃 노드의 정보를 Aggregation하여 Node Representation을 학습하지만,
다음과 같은 중요한 질문이 남아 있었다.

** "현재의 GNN이 서로 다른 그래프 구조를 정말 구별할 수 있을까?" **
즉,성능이 좋은 모델을 만드는 것이 아니라  **Graph Neural Network의 표현력(Expressive Power)** 자체를 분석하는 것이 이 논문의 목표이다.

# 핵심 아이디어
GIN 의 핵심은 ** GNN 의 표현력은 Aggregation Function 에 의해 결정된다 **
즉, Neighbor를 어떻게 Aggregation하는지가 그래프를 얼마나 잘 구별할 수 있는지를 결정
논문에서는 Sum Aggregation이 가장 강력한 표현력을 가진다는 것을 증명

# 왜 중요한가
기존 GNN들은 Mean Max Attention 등 다양한 Aggregation을 사용
하지만 어떤 Aggregation이 가장 좋은지 이론적으로 설명하지 못함.
GIN은 Weisfeiler-Lehman(WL) Graph Isomorphism Test와 비교하여 GNN의 표현력을 분석

# Weisfeiler-Lehman (WL) Test
WL Test는 두 그래프가 같은 구조인지(Isomorphic) 판단하는 대표적인 알고리즘
과정은 매우 간단하다.
각 Node는 자신과 Neighbor의 Label을 이용하여
새로운 Label을 반복적으로 생성
만약 두 그래프의 Label이 달라지면 두 그래프는 다른 그래프라고 판단
--> WL Test 수준의 표현력을 가지는 GNN이 가장 강력한 GNN이다. 라고 주장

# Aggregation Function
GIN은 Aggregation Function의 표현력을 비교
### Mean Aggregation Neighbor 평균을 사용한다.
GCN GraphSAGE에서 사용된다.
서로 다른 구조가 같은 평균을 가지면 구별하지 못한다.

### Max Aggregation
가장 큰 값만 사용. 중요한 정보가 손실될 수 있다.

## Sum Aggregation
Neighbor Feature를 모두 더한다. Node의 개수와 구조 정보를 가장 잘 보존
GIN은 Sum Aggregation이 WL Test와 동일한 표현력을 가질 수 있음을 증명

GIN의 업데이트 식은
h_v^{(k)} = MLP^{(k)}\left((1+\epsilon)h_v^{(k-1)}+\sum_{u\in N(v)}h_u^{(k-1)}\right)

여기서

- h_v^{(k)} : k번째 Layer의 Node Representation
- N(v) : Neighbor Node
- \epsilon : 자신의 Feature 비중
- MLP : Multi-Layer Perceptron
을 의미한다.
GCN과 가장 큰 차이는 Aggregation 이후
단순 Linear Layer가 아니라 MLP를 사용한다는 점

# 왜 MLP를 사용?
GCN은 Linear Transformation을 사용한다.
하지만 Linear Model은 복잡한 함수를 충분히 표현하지 못한다.

GIN은 MLP를 사용하여 비선형 표현력을 크게 향상

# 이점
1. 높은 표현력
WL Test 수준의 표현력을 가질수있다.
2. 구조 정보 보존
Mean이나 Max보다 그래프 구조를 더 잘 구별
3. 강력한 Graph 분류 성능
4. GNN 이론 정립
GNN의 표현력을 수학적으로 분석 

# 한계
1. Oversmoothing
GCN과 마찬가지로 Layer가 깊어질수록 Representation이 비슷해질 수 있다.
2. Homophily 가정
비슷한 Node가 연결되어 있다는 가정
3. 계산량 증가
MLP를 사용하기 때문에
GCN보다 연산량이 증가

# 후속 영향
GIN은 Graph Neural Network의 표현력을
처음으로 이론적으로 분석한 연구
이후

- Graph Isomorphism 연구
- Graph Transformer
- GraphGPS
- Expressive GNN
등 다양한 연구에서
기준 모델(Baseline)로 사용

# 이해한 내용 및 느낀점
성능향상 목적보단 GNN이 얼마나 그래프 구조를 구별할수있는가를 분석한 논문
WL Test를 사용하여 GNN 의 표현력을 분석
또한 GCN이나 GraphSAGE의 Mean Aggregation보다
Sum Aggregation이 그래프 구조를 더 잘 보존할 수 있다는 점이

GIN의 가장 큰 기여


