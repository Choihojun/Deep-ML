# Question markdown

질문이 있거나 모르는 개념이 있을때 기술하는 페이지

## fit_transform vs transform function

둘의 차이에 대해서 정의하기

## Machine performance metric

mse, accuracy

## pr curve, ROC Curve


## Backpropagation


## Gradient Vanishing Problem

딥러닝에서 Layer를 많이 쌓을수록 데이터 표현력이 증가할꺼 같지만 실제로는 Layer가 증가할수록 학습이 잘 안된다 (표현력이 더 떨어지게 됨)

기울기 소실이란 역전파 과정에서 출력층에서 멀어질수록 Gradient값이 매우 작아지는 현상을 의미함.

원인은 다음과 같다. 활성화 함수를 미분하였을때 x값에 대응하는 y값이 점점 0으로 가기 때문이다. 0으로 가게 되면 역전파 과정에서 제대로된 가중치 업데이트가 되지 않기 때문이다. 

안되는 활성화 함수: Sigmoid, tanh

어느정도 극복이 가능한 함수: ReLU (미분을 수행하면 양수에서는 무조건 1, 음수에서는 0이다. 때문에 음수인 뉴런 같은 경우에는 다시 회생이 불가능해지는 문제가 있다 -> Dying ReLU)

좀더 개선된 함수: Leaky ReLU


## Loss는 커지는데 Accuracy는 감소하는 결과는 어떻게 해석?


## Dropout 함수

Dropout은 특정 feature에 대해서만 과도하게 학습되는 과대적합에 대해서 방지하기 위해 사용되는 방법임.

0.2를 Dropout의 매개변수로 적었을때 특정 layer의 모든 노드는 각각 0.2의 확률을 가지게 되고 0.2에 해당되엇을때 잠시 뉴런은 역할을 못하게 됨.

즉, 꺼진 뉴런에 대해서는 학습이 안되며 전체적으로 볼때 확률적으로 고르게 학습될수있도록 하는 전략을 의미함

## 이미지의 텐서

