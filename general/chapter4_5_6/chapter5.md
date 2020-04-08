## 교차검증

데이터를 여러번 반복해서 나누고 여러 모델을 학습한다. 많이 사용되는 교차 검증 방법은 K-flod cross-vaildation으로 데이터를 K 개의 집합으로 나눈다음 모델들을 만든다.

첫 번째 모델은 첫 번째 폴드를 테스트 세트로 사용하고 나머지 폴드를 훈련세트를 사용하여 학습한다. 이 방법으로 반복한 뒤 다섯 개의 정확도를 측정하여 다섯개의 정확도 값을 얻을 수 있다.

#### 장점

1. 테스트 세트에 각 샘플이 정확하게 한 번씩 들어가고 각 샘플은 폴드 중 하나에 속하며 각 폴드는 한 번씩 테스트 세트가 됩니다. 그렇기 떄문에 교차 검증의 점수를 높이기 위해서는 데이터셋에 있는 모든 샘플에 대한 모델이 잘 일반화되어야 한다.

2. 데이터를 여러개로 나누면 모델이 훈련 데이터에 얼마나 민감한지 알 수 있다.
3. 분할을 한 번 했을 때보다 데이터를 더 효과적으로 사용할 수 있다.

#### 단점

연산 비용이 늘어난다는 것. 모델을 K개 만들어야 하므로 데이터를 한 번 나눴을 때보다 대략 K배 더 느립니다.

교차 검증은 새로운 데이터에 적용할 모델을 만드는 방법이 아니다. 교차 검증의 목적은 단지 주어진 데이터셋에 학습된 알고리즘이 얼마나 잘 일반화될지 평가하는 것이다.

분류일 경우 **계층별 K-겹 교차 검증**을 사용한다. Ex) 클래스 A가 90프로 클래스 B가 10프로 일때 샘플에 들어가는 개수는 A가 90프로 B가 10프로가 되게 한다. 분할할 때 클래스의 비율대로 나눠진다는 말이다.

**LOOCV 폴드 하나에 샘플 하나만 들어 있는 K fold cross validation** 작은 데이터셋에 사용

**임의 분할 교차 검증** 부분 샘플링 하는 방식은 대규모 데이터셋으로 작업할 때 도움됨.( 옵션에 따라 미선택 세트가 존재할 수 있다. )

**그룹별 교차검증 ** 그룹배열을 생성해 훈련세트와 테스트 세트를 만들 때 분리되지 않아야 할 그룹을 지정하는 것이다.

**그리드 서치** 매게변수들을 대상으로 가능한 모든 조합을 시도해보는 것이다. 교차검증을 사용해서 각 매개변수 조합의 성능의 평가할 수 있다.

p339 검증세트에서 매개변수 선택 이유

**평가 지표와 측정** 

특정 알고리즘을 선택하여 나타난 결과를 **비지니스 임팩트** 라고 한다.

모델을 선택하고 매개변수를 조정 할 때 이런 비지니스 지표에 긍정적인 영향을 주는 모델과 매개변수를 선택해야 한다.

**불균형 데이터셋** 광고를 예를 들때 보통 100개의 광고나 글을 보여줄때 한번 클릭한다. 이럴때 모든 결과를 클릭 안함으로 했을 때 정확도는 99%지만 좋은 성능이라고 말할 수 없다.

**오차행렬** TN FP FN TP 

정확도 = TP + TN / 나머지 전체

정밀도 = TP / TP + FP

재현율 = TP / TP + FN

정밀도와 재현율의 조화 평균 F-feature

F = 2 * (정밀도 * 재현율)/(정밀도 + 재현율)

정밀도가 높아져도 재현율이 높게 유지될수록 좋은 모델.

이진 분류 평가

ROC -> 임계값을 고르기 위해 테스트세트를 사용해서는 안되고 𖤐도의 검증 세트를 활용해야 합니다.

AUC -> 불균형한 데이터셋에서는 정확도보다 AUC가 훨씬 좋은 지표입니다. AUC가 높은 모델에서 좋은 분류 결과를 얻으려면 결정 임계값을 조정해야 합니다.

교차검증, 그리드서치, 평가지표, 개선하기 위한 사항

첫째 교차검증을 해야한다. 테스트 세트나 교차겸증을 모델이나 모델의 매개변수 선택에 사용하면 테스트 데이터로 미래 성능을 평가했을 때 매우 낙관적인 예측치르 얻게된다. 그러므로 모델 학습에는 훈련데이터로, 모델과 매개변수 선택에는 검증 데이터로, 모델 평가에는 테스트  데이터로 분리해서 사용해야 합니다. 

거짓양성(FP)과 거짓음성(FN)이 매우 큰 영향을 미칩니다.