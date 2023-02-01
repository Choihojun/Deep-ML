# Basic notion in Deep Learning

## 1. Machine Learning Data

1. Training data: 학습 데이터로서 모델을 학습할때 사용됨
2. Validation data: 검증 데이터, 검증 학습이 진행되는 동안 성능을 검증하는데 사용되는 데이터
3. Test data: 평가 데이터, 학습을 마치고 나서 모델의 성능을 최종적으로 평가하는 데 사용하는 데이터를 의미함

*tip: 검증 데이터는 일반적으로 학습 데이터에서 일정 비율로 추출해서 사용함. 때에 따라서 평가 데이터를 직접 사용하기도 함

## 2. Optimizer

옵티마이저의 역할은 손실함수를 빠르게 줄여나가면서 어떤 방향으로 가중치를 업데이트해야하는지 계산하는 역할을 한다.

옵티마이저 종류

### 2-1. 경사 하강법 (Gradient Descent)

한번 학습시 모든 데이터 셋을 이용하며, 최솟값을 찾기 위해 한칸한칸씩 전진하는 방식이기에 상당히 오래걸리는 특징을 지님

학습률이 클때 최솟값을 찾지 못하고 오히려 loss가 발산하는 방향으로 갈수도 있음

### 2-2. 확률적 경사하강법 (SGD, Stochastic Gradient Descent)

### 2-3. 모멘텀 (Momentum)

### 2-4. NAG (Nesterov Accelerated Gradient)

### 2-5. Adagrad

### 2-6. RMSProp

### 2-7. Adam (Adaptive Moment Estimation)

각 파라미터마다 다른 크기의 업데이트를 진행하는 방식임. minima의 탐색을 위해서 조심스럽게 속도를 줄이는 방법이며 

loss가 빠르게 줄어들고 Vanishing learning rate, high variance 문제를 해결한 방법. 

그러나 계산 비용이 든다는게 유일한 단점

