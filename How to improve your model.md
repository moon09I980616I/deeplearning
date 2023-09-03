
### 과대적합(Over-fitting)의 개념

- 제한된 훈련 데이터 세트가 지나치게 특화되어 새로운 데이터에 대한 오차가 매우 커지는 현상
- 모델의 매개변수 수가 많거나, 훈련 데이터 세트의 양이 부족한 경우 발생

![](https://velog.velcdn.com/images/moon0_/post/de811dea-4305-45a5-ba2d-bd72670c17e1/image.png)


- 과소 적합 (Under-fitting) : 모델이 너무 단순하여 데이터의 내재된 구조를 학습하지 못할 때 발생
- 일반화 (Generalization) : 테스트 데이터에 대한 높은 성능을 갖춤, 과대적합, 과소 적합을 피하고 정상추정함
- 과대 적합 (Over-fitting) : 모델이 훈련 데이터에 너무 잘 맞지만, 일반화가 떨어짐

### 과대적합 발생 원인

- 훈련 데이터는 실제 데이터의 부분 집합이라서 실제 데이터의 모든 특성을 가지고 있지 않을 수 있다.( 과대 적합 등의 문제가 발생할 수 있는 원인 제공)
- 과대 적합의 발생 원인은 실제 데이터에서 편향된 부분만을 가지고 있거나 오류가 포함된 값을 가지고 있을 경우 발생할 수 있다.
- 모델이 과도하게 복잡하거나, 변수가 지나치게 많을 때도 과대 적합이 발생할 수 있다.

### 과대적합 방지 기법

- 데이터 증강(Data Augmentation)
    - 모델은 훈련 데이터 세트의 양이 적을 경우, 해당 데이터의 특정 패턴이나 노이즈까지 분석되어 과대 적합 현상이 발생할 확률이 높으므로 충분한 데이터 세트를 확보해야 한다.
    - 데이터의 양이 적을 경우, 데이터를 변형해서 늘릴 수 있다.
- 모델의 복잡도 감소
    - 인공신경망의 복잡도는 은닉층의 수나 모델의 수용력 등으로 결정된다.
    - 과대 적합 현상이 발생할 때 인공 신경망의 은닉층의 수를 감소하거나 모델의 수용력을 낮추어 복잡도를 줄일 수 있다.
- 가중치 규제 적용
    - 개별 가중치 값을 제한하여 복잡한 모델을 간단하게 만드는 방법
    - 복잡한 모델은 많은 수의 매개변수를 가진 모델로 과대 적합될 가능성이 큼
- 드롭아웃
    - 학습 과정에서 신경망 일부를 사용하지 않는 방법
    ex) 드롭아웃의 비율을 0.5로 한다면 학습 과정마다 랜덤으로 절반의 뉴런을 사용하지 않고, 절반의 뉴런만을 사용
        ![](https://velog.velcdn.com/images/moon0_/post/30788489-8413-4688-9414-4c85befc13ff/image.png)

    - 드롭아웃은 신경망 학습 시에만 사용하고, 예측 시에는 사용하지 않는다.
    - 학습 시에 인공신경망이 특정 뉴런 또는 특정 조합에 너무 의존적으로 되는 것을 방지해준다.
    - 서로 다른 신경망들을 앙상블하여 사용하는 것 같은 효과를 내어 과대 적합을 방지한다.
    - 초기 드롭아웃 : 학습 과정에서 노드들을 P의 확률(일반적으로 0.5)로 학습 횟수마다 임의로 생략하고, 남은 노드들과 연결 선들만을 이용하여 추론 및 학습을 수행하는 기법으로 DNN(Deep Neural Network; 심층 신경망) 알고리즘에 사용
    - 공간적 드롭아웃 : 합성곱(Convolution) 계층에서의 드롭아웃, 특징 맵 내의 노드 전체에 대해 드롭아웃의 적용 여부를 결정하는 기법으로 CNN(Convolution Neural Network; 합성곱 신경망) 알고리즘에 사용
    - 시간적 드롭아웃 : 노드들을 생략하는 방식이 아니라 연결선 일부를 생략하는 방식으로, Drop Connection 방식의 개선 기법으로 RNN(Recurrent Neural Network; 순환 신경망) 알고리즘에 사용

### 매개변수 최적화

- 매개변수(Parameter)는 주어진 데이터로부터 학습을 통해 모델 내부에서 결정되는 변수이다.
- 매개변수 최적화(Parameter Optimization)
    - 학습 모델과 실제 레이블과 차이는 손실함수(Loss Function)로 표현되며, 학습의 목적은 오차, 손실 함수의 값을 최대한 작게 하도록 하는 매개변수(가중치, 편향)를 찾는 것
    - 매개변수의 최적값을 찾는 문제이며, 이러한 문제를 푸는 것을 최적화라 한다.
- 매개변수 종류
    - 가중치(Weight) : 각 입력값에 각기 다르게 곱해지는 수치, y=ax+b라고 하면 a가 가중치
    - 편향(Bias) : 하나의 뉴런에 입력된 모든 값을 다 더한 값(가중합)에 더해주는 상수 y=ax+b라고 하면 b가 편향
- 매개변수 최적화 과정 : x축에는 가중치, y축에는 손실값을 갖는 2차원 손실 함수 그래프를 이용하여 최적화를 한다.
- 매개변수 최적화 기법 - 확률적 경사 하강법
    
    - 학습률이 적은 경우
      
    <img src ="https://velog.velcdn.com/images/moon0_/post/50db00c8-e492-4c4c-8e69-45210b647d3a/image.png" width=500px>
      
    오래걸림
        
    
    - 학습률이 높은 경우
    <img src ="https://velog.velcdn.com/images/moon0_/post/72ae1dee-c527-4402-a34c-db3a0dc54ca9/image.png" width=500px>
    
    기울기 0을 지나치게되어 최적화가 되지 못함
        
    
    - 학습률이 적절한 경우
    <img src ="https://velog.velcdn.com/images/moon0_/post/92e1ccb8-55f5-4b0f-925b-9ad642041f1b/image.png" width=500px>

    기울기 0을 찾아 최적화가 됨
        

![](https://velog.velcdn.com/images/moon0_/post/f38f2651-1f49-4c8c-8862-6b4cf46f9b0c/image.png)


### 확률적 경사 하강법

- 확률정 경사하강법(SGD;Stochastic Gradient Descent)이란 손실 함수의 기울기를 구하여 그 기울기를 따라 조금씩 아래로 내려가 최종적으로는 손실 함수가 가장 작은 지점에 도달하도록 하는 알고리즘으로 기울기를 구하는데 학습 1회에 필요한 한 개의 데이터가 무작위로 선택이 되어 확률적이라고 한다. 손실 함수 그래프에서 지역 극소점에 갇혀 전역 극소점을 찾지 못하는 경우가 많고, 손실 함수가 비등방성 함수일 때에서는 최적화에 있어 매우 비효율적이고 오래 걸리는 탐색 경로를 보여준다. 확률적 경사 하강법의 단점을 개선해주는 기법으로 모멘텀, AdaGrad, Adam이 있다.
- 확률정 경사 하강법은 기울기가 줄어드는 최적점 근처에서 느리게 진행하며, 탐색 경로가 지그재그로 크게 변한다.

![](https://velog.velcdn.com/images/moon0_/post/05e3c062-3f66-47b9-8495-7c7c262de254/image.png)


### 모멘텀

- 모멘텀(Momentum)이란 기울기 방향으로 힘을 받으면 물체가 가속된다는 물리 법칙을 적용한 알고리즘이다. 모멘텀은 운동량을 뜻하며 확률적 경사 하강법(SGD)에 속도라는 개념을 적용한다. 기울기가 줄어들더라도 누적된 기울기 값으로 인해 빠르게 최적점으로 수렴하게 된다.
- 모멘텀 알고리즘의 최적점 탐색 경로를 보면 알 수 있듯이, 공이 구르는 듯한 모습을 보여준다. 관성의 방향을 고려해 진동과 폭을 줄이는 효과가 있다. 탐색 경로의 변위가 줄어들어 빠르게 최적점으로 수렴한다. 모멘텀의 갱신 경로는 공이 그릇 바닥을 구르듯 움직인다. 확률적 경사 하강법과 비교하면 지그재그 정도가 덜하다. x의 한방향으로 일정하게 가속하고, y축 방향의 속도는 일정하지 않다.

![](https://velog.velcdn.com/images/moon0_/post/d2285ccc-0f0c-4d74-b131-67a8bc2bb377/image.png)


### AdaGrad

- AdaGrad(Adaptive Gradient Algorithm)는 손실 함수의 기울기가 큰 첫 부분에서는 크게 학습하다가, 최적점에 가까워질수록 학습률을 줄여 조금씩 적게 학습하는 방식이다. 학습을 진행하면서 학습률을 점차 줄여나가는 학습률 감소 기법을 적용한 최적화 알고리즘이다. 매개변수 전체의 학습률 값을 일괄적으로 낮추는 것이 아니라 각각의 매개변수에 맞는 학습률 값을 만들어주는 방식이다.
- AdaGrade 기법의 최적점 탐색 경로를 보면, 최적점을 향해 매우 효율적으로 움직인다. 처음에는 큰 폭으로 움직이지만, 그 큰 움직임에 비례하여 갱신 정도도 큰 폭으로 작아진다. 갱신 강도가 빠르게 약해지고, 지그재그 움직임이 눈에 띄게 줄어들어 빠르게 최적점으로 수행한다. 최솟값을 향해 효율적으로 움직인다. y축 방향은 기울기가 커서 처음에는 크게 움직이지만 큰 움직임에 비례해 갱신 정도도 큰 폭으로 작아지도록 조정된다. y축 방향으로 갱신 강도가 빠르게 약해지고 지그재그 움직임이 줄어든다.

![](https://velog.velcdn.com/images/moon0_/post/b12d42c1-edf4-419c-aa99-15095dcf0588/image.png)


### Adam

- Adam(Adaptive Moment Estimation)은 모멘텀 방식과 AdaGrad 방식의 장점을 합친 알고리즘이다. 최적점 탐색 경로 또한 이 두 방식을 합친 것과 비슷한 양상으로 나타난다.
- 탐색 경로의 전체적인 경향은 모멘텀 방식처럼 공이 굴러가는 듯하고, AdaGrad로 인해 갱신 강도가 조정되므로 모멘텀 방식보다 좌우 흔들림이 덜 한 것을 볼 수 있다.Adam의 갱신 과정은 그릇 바닥을 구르듯 움직인다. 모멘텀과 비슷한 패턴이지만, 모멘텀보다 공의 좌우 흔들림이 적다.