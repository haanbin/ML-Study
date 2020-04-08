# 데이터 표현과 특성 공학

- 특성공학 : 가장 적합한 데이터 표현을 찾는 것.

#### 범주형 변수

- 원-핫-인코딩 : 범주형 변수를 표현하는데 널리 쓰이는 방법
- 예를들어 남성이 male, man으로 사용될 수 있으므로 같은 범주로 인식해야 한다. Series에 있는 value_counts 메서드를 사용하여 유일한 삾이 몇번 나타나는지 확인해 보는것이 좋다.

**연속형 변수의 스케일을 조정하는 이유 P282**

트리 기반 모델은 특성의 순서에만 영향을 받지만 선형모델과 신경망은 각 특성의 스케일과 분포에 밀접하게 연관되어 있다. 그리고 특성과 타깃값 사이에 비선형성이 있다면 특히 선형 회귀에서는 모델을 만들기가 어렵다. log와 exp함수는 데이터의 스케일을 변경해 선형 모델과 신경망의 성능을 올리는데 도움을 준다.

대부분의 모델은 각특성이 정규분포와 비슷할 때 최고의 성능을 낸다.

구간분할, 다항식, 상호작용은 데이터가 주어진 상황에서 모델의 성능에 큰 영향을 줄 수 있다. 트리 기반 모델은 스스로 중요한 상호작용을 찾아낼 수 있어 대부분의 경우 데이터를 명시적으로 변환하지 않아도 된다.

지도학습에서 사용되는 전략 일변량통계, 모델기반선택, 반복적선택

일변량통계 : 다른 특성과 깊게 연관된 특성은 선택되지 않을 것이다.

모델기반특성선택 : 특성 중요도를 평가해서 가장 중요한 특성들만 선택한다. 

반복적 선택 : 특성을 하나도 선택하지 않은 상태에서 하나씩 추가하는 방법, 모든 특성을 가지고 시작해서 하나씩 제거해나가는 방법

렌덤포레스트는 데이터 전처리가 거의 필요하지 않아 맨 처름 시도해보기 좋은 모델이다

**연속성 변수는 예측에 안좋은 것인가 ? P313**

랜덤포레스트 외삽

**요일과 시간이 정수로 인코딩되어 연속형 변수로 해석 P318**

DataFragme을 Numpy 배열로 바꿀 수 있으며 P277

훈련데이터와 테스트데이터 포인트를 모두 포함하는 DataFragme을 사용해서 원핫인코딩

한 특성을 여러 특성으로 나누는 구간 분할

상호작용, 다항식

MinMaxScaler

다항식 특성 - 원본 특성에서 두 개를 뽑아 만들 수 있는 모든 곱을 얻을 수 있다. 

정규분포와 비슷할때 최고의 성능 로그나 exp사용

일변량 통계, 모델 기반 선택, 반복적 선택

일변량 각 특성이 독립적으로 평가된다는 점입니다.

임계값을 계싼하는 방법은 각각 다르며 가장 간단한 SelectKBest는 고정된 k개의 특성을 선택하고 SelectPercentile은 지정된 비율만큼 특성을 선택합니다. 그럼 cancer 데이터셋에 분류를 위한 특성 선택을 적용해보겠습니다. 




