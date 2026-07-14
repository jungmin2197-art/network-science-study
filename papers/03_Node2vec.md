# node2vec: Scalable Feature Learning for Networks
( KDD 2016)
용어 정리
Homophily graph: 커뮤니티에 기반하고 동일 커뮤니티 속한 노드들이 서로 유사 ex: u와 s1 s2 s3 s4 유사
Structural Equivalence: 구조적 기능이나 역할 동일 ex: u s6
Randomwalk: 그래프의 특정 노드에서 시작하여, 현재 노드와 연결된 이웃 노드 중 하나를 무작위로 선택해 이동하는 과정
        장점: 계산 효율성, 유연성  단점: 정보 편향, 단순성

  Deep walk: 네트워크에서 랜덤워크를 통해 노드시퀀스를 생성, 이를 Word2vec로 학습시키는 그래프 임베딩 방법
        Rigid 경직된 이웃 정의: 구조적 동등성 포착 어려움

  Subgraph2vec: 노드 하나가 아닌, 특정 노드를 중심으로 한 부분 그래프(subgraph)의 구조 자체를 벡터화
        동형성 해결, 구조적 맥락 포착, 높은 계산 복잡도

  RoIX (역할추출): 노드가 어떤 커뮤니티에 속해있는지가 아니라, 네트워크 전체에서 허브, 브릿지 등 어떤 역할을 하는지 분석
       추출된 노드-특징 행렬을 노드-역할 행렬과 역할-특징 행렬로 분해
       행렬분해 의존 문제 유연성 부족


왜 등장?
기존 머신러닝은 그래프 데이터를 다루기 위해서 사람이 직접 feature 설계
단점: 비용이 많이 들고 일반화 어렵고 그래프 적용 어렵다 

아이디어: node2vec는 그래프의 노드를 벡터 공간으로 변환하는 것 = 노드 -> Embedding vector 변환 수행
비슷한 역할 하는 노드는 가까운 벡터로 학습
biased random walk 두개의 하이퍼파라미터를 사용하여 p(Return parameter) 이전 노드로 다시 돌아갈 확률 조절 p가 크면 쉽게 되돌아가지않고 p가 작으면 되돌아가기 쉬움
q( In-Out Parameter) 탐색범위 조절 q>1 BFS 성향 가까운 이웃 중심 탐색 구조적 유사도 학습 q<1 DFS 성향 멀리이동 Community 정보 학습

왜 중요?
Node2vec 이전에도 Deepwalk가 존재 but Randomwalk 방식이 고정되어있었음. 네트워크 이웃 정의방식이 경직-> 복잡한 연결에 둔감하게 반응, 정보 손실
node2vec는 BFS(너비우선)  DFS(깊이우선) 사이를 조절할 수 있는 biased random walk를 제안 -> 풍부한 구조 정보 학습 가능

이점
node2vec: 특정샘플링 전략에 얽매이지 않는 유연한 목적함수 설계 + 탐색공간 조정 위한 매개변수 제공
자동 feature learning -> 직접 feature engineering 불필요
확장성-> 대규모 그래프 처리 가능
노드분류 링크학습 등 다양한 활용, 구조 정보 학습

한계
Node feature 사용 불가: 그래프 구조만 사용해서
메시지 패싱 없음: 노드 간 정보 전달 과정이 없음( 초기모델이란는뜻)

요약
node2vec는 그래프를 딥러닝으로 처리하기 이전 세대의 대표적인 방법. 어떻게 randomwork를 수행할까 특히 p와 q를 통해 BFS 기반 구조 학습과 DFS 기반 커뮤니티 학습을 조절할 수 있다는 점




