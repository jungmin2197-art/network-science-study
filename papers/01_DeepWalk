# DeepWalk: Online Learning of Social Representations
KDD 2014

# 왜 등장했나
기존 그래프 분석에서는 사람이 직접 그래프 feature 를 설계해야 했다.
예를 들어
- Degree
- Centrality
- Clustering Coefficient 등을 직접 계산하여 머신러닝 모델에 입력으로 사용

- Feature Engineering 비용이 크고
- 그래프마다 다른 Feature를 설계해야 하며
- 일반화가 어려움

DeepWalk는 이러한 문제를 해결하기 위해
> ** 그래프 구조로부터 자동으로 Node Representation(Embedding)을 학습하는 방법** 제안

# 핵심 아이디어
> ** 그래프를 문장(Sentence) 처럼 생각하는것 **

Word2vec에서는 문장 안에서 함께 등장하는 단어를 비슷한 의미로 학습
DeepWalk 는 RandomWalk를 이용하여 그래프에서 문장을 생성

Randomwalk를 하나의 문장으로 생각하고 Word2vec의 Skip-gram 모델을 그대로 적용하여 노드 임베딩을 학습

# 왜 중요할까
DeepWalk 이전에는 그래프 데이터를 위한 일반적인 Representation Learning 방법이 거의 존재하지 않았다.

DeepWalk는 NLP에서 성공한 Word2Vec을 그래프에 처음으로 성공적으로 적용

# ** Random Walk **
DeepWalk의 가장 중요한 과정 
현재 노드에서 이웃 노드중 하나를 무작위로 선택하여 이동하는 과정
랜덤워크를 여러번 반복하면 그래프의 지역적인 구조(Local Structure)를 반영하는 문장을 만들수있다.

# ** Skip-gram **
Random Walk로 생성한 문장을 Word2Vec의 Skip-Gram 모델에 입력한다.

Skip-Gram의 목표는 > **현재 노드를 이용하여 주변 노드를 예측하는 것**
이를 통해 비슷한 위치에 자주 등장하는 노드는 비슷한 Embedding을 가짐

# 이점
1. 자동으로 피쳐를 학습
2. 그래프 임베딩 생성 -> 각 노드를 고정 길이 벡터로 표현
3. 학습된 임베딩을 노드 분류, 링크 연결 등 다양한 활용

# 한계
1.Random Walk가 고정되어있어서 항상 동일한 랜덤워크  수행
탐색 전략 조절 불가 -->> node2vec 로 해결

2. Node Feature를 사용하지 않는다.
그래프의 연결 구조만 이용하고 노드의 Attribute 정보는 활용하지 못함

3. Tow-stage Learning 
먼저 임베딩을 학습한 후 다른 머신러닝 모델을 학습해야한다.
Embedding과 Classification이 함께 학습되지 않는다.
-->> GCN에서 해결

# 이해한 내용과 생각
DeepWalk는 랜덤워크를 수행하는 알고리즘 보다 Word2vec NLP쪽에서 많이 쓰던거를 그래프에 적용했다는 아이디어가 메인
그래프를 문장으로 표현하고 그 노드들을 단어처럼 학습한다는 발상
근데 Random Walk 방식이 고정되어있어서 그래프 다양한 구조 반영이 어렵겠다. 근본있는 방식 그래프 표현의 시초 정도

