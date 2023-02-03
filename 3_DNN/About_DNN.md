# DNN

## 1. About DNN

DNN = Deep Neural Network (심층신경망)

즉, 은닉 계층을 많이 쌓아서 만든 인공지능 기술.

기존 ANN은 은닉 계층 하나를 포함하였으나, DNN은 수십 수백개의 은닉 계층으로 구성되기도함.

때문에 더 우수한 성능을 낼수 있으며 적용 분야도 훨씬더 다양하다.

## 2. Principle of DNN

### 2.1. DNN Notion with structure

DNN은 은닉 계층이 여러개이기 때문에 당연하게도 제 1 은닉계층의 결과는 제 2 은닉계층으로 전달되며 최종 출력까지 이런식으로 전달되게 됨.

한가지 의문이 들수도 있음. 무조건 Hidden Layer만 더 늘리면 좋은게 아닌가라고 생각하지만 오히려 `과적합`이 발생할수있기에 이 또한 최적으로 방지하는게 DNN의 성능을 최대로 끌어올릴수있다.

### 2.2 Gradient Vanishing & ReLU Activation Function

경사도 소실문제에 대한 이해부터 하자 -> Question.md를 참고

경사도 소실 문제에 대해서 피드백하기 위해 ReLU를 활성화 함수로 사용한다는게 핵심임. 그러나 ReLU가 경사도 소실 문제에 대해서 완벽한 대응책은 아니라는것.

### 2.3 How to implement DNN

DNN을 구성하기 위해서 총 4단계가 필요함.

- 1. 기본 매개변수 설정
- 2. 분류 DNN 모델 구현
- 3. 데이터 준비
- 4. DNN의 학습 및 성능 평가

이제 코드로 넘어가자

- 필기체 분류 예제 (DNN_Classification1.ipynb)




