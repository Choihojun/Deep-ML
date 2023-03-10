# Reinforcement Learning

강화학습은 행동에 대한 정책을 학습하는 인공신경망이다.

앞의 내용들은 지도학습망이 행동 자체를 직접학습시켰다면, 강화학습은 행동을 직접 학습하는 대신 행동에 따라 보상이 좋아지는 방향으로 학습을 수행함.

## 1. Principle of Reinforcement Learning

강화학습은 환경에서 보상을 통해 행동의 정책을 결정하는 인공지능 학습 방법.

필요 요소

### 1.1. 상태 (State) - S

에이전트가 explore를 해야할 공간을 의미

### 1.2. 행동 (Action) - A

에이전트가 특정 state에서  

### 1.3. 행동을 결정하는 정책 (Policy) 

기호로는 pi(A | S)

-> S라는 상태에서 A라는 액션을 선택할 확률 (만약 선택할수있는 행동이 2가지라면 0.5, 0.5씩을 가짐)

### 1.4. 그에 따른 보상 (Reward) - R

### 1.5. 반환값 (Return Value): 에이전트의 행동은 바로

$$G_k = R_{k+1} + \gamma R_{k+2} + ... + \gamma^{L-1}R_{k+L}$$

여기서 k는 행동을 한 현재 시간을 의미함. $\gamma$는 0과 1 사잇값을 가지는 감가상각 비율을 의미함 (1에 가까울수록 미래 보상이 현재 행동에 많은 영향을 받는 것을 의미함)

### 1.6. 가치함수 (Value function)

확률적 정책이 고려된다면 같은 상태에서도 때에 따라서 다른 행동을 할수있게됨. 그리고 행동의 결과에 따라서 보상이나 반환값도 때에 따라 확률적으로 달라질수있음.

따라서 확률적 상황을 고려한 특정 상태에서 반환값의 평균을 가치함수로 정의하고 V[s]로 표시함

$$V[s] = E[G_{k}|S_{k}=s]$$

### 1.7. 행동가치함수

동일한 상태에서 행동이 달라지면 평균 반환값이 달라질수 있음.

가치함수는 상태에 따른 행동에 따른 리턴을 평균한것.

그러나 행동가치함수는 행동별 반환값을 평균한 값.

$$Q[s, a] = E[G_{k}|S_{k}=s, A_k = a]$$

이때 가치함수의 식은 행동가치함수에 행동별 정책을 고려한 평균값으로 표현 가능함

$$V[s] = \sum_a \pi(a|s)Q[s, a]$$

### 1.8. 벨만 기대 방정식

벨만 기대 방정식은 $G_k = R_{k+1} + \gamma G_{k+1}$의 특성을 이용하여 가치함수를 다이나믹한 형태로 표현한 방정식.

$$V[s] = E[G_{k}|S_{k}=s] (변경전)$$

$$V(s) = E[R_{k+1} + \gamma V[S_{k+1}]|S_k = s] (적용후) $$

마찬가지로 벨만 기대 방정식은 행동가치함수에도 적용이 가능함.

$$Q[s, a] = E[R_{k+1} + \gamma Q[S_{k+1}, A_{k+1}]|S_{k}=s, A_k = a]$$

위의 관계들을 이용한다면 다이내믹 프로그래밍을 통해서 각각 수렴 가치함수와 수렴 행동가치함수를 구할수있게됨.

여기서 수렴 가치함수와 수렴 행동가치함수란 벨만 기대 방정식을 통해서 정책에 대해 가치함수와 행동가치함수가 더 변하지 않는 값으로 수렴된 경우를 의미함.

## 2. The standard Reinforcement Learning optimization method

MDP (Markov Decision Process)는 마르코프 결정 과정이며 이를 강화학습의 최적화에 기반을 두고 있음.

### 2.1. MDP 상태 변환 확률

MDP는 다음 상태가 현재 상태와 행동에 의해서 정의되고 과거 상태와 행동과는 연관이 되지 않는 프로세스임.

이를 이용하여 MDP의 상태 변환 확률 정의하면 다음과 같음.

$$P_{s, s'}^a=P[S_{k+1}|(S_k, A_k)]$$

여기서 S, A는 각각 s, a 상태와 액션이다. 확률은 미래 상태인 s'이 현재 상태와 행동인 s와 a에 의해서 정해질 확률을 나타내는 것을 알수있음.

### 2.2. Average Reward value in MDP

MDP 모델에서 s 상태에서 a라는 행동을 했을 때 받게 되는 평균 보상값을 다음과 같이 정의함.

$$R_{s}^a=E[R_{k+1]}]$$


### 2.3. Policy Iteration (정책 반복법)

MDP 최적화의 기본적인 방법으로 기대 방정식을 이용한 정책 반복법이 있음.

순서는 다음과 같다.

- 1 step) 밸만 기대 방정식 (output: 수렴 행동 가치함수)
- 2 step) 정책 계산 (output: 정책)
- 3 step) 정책 수렴 검사 (최적 정책)
- 4 step) 최적 정책이 안나왔다면 다시 밸만 기대 방정식

### 2.4. MDP 모델 정보를 이용한 수렴 행동가치함수 계산

행동가치함수를 효과적으로 수렴시키기 위해서 벨만 기대 방정식을 사용.

MDP 모델 정보인 상태 변환 확률인 P와 평균 보상값 R을 이용해 다음과 같이 시간에 대한 것으로 변환함.

$$Q_k[s, a]=R_{s}^a + \gamma \sum_{s'\in S}P_{s, s'}^a \sum_{a' \in A}Q_{k-1}[s', a'] $$

$Q_k[s, a]$와 $Q_{k-1}[s, a]$는 시간 k와 시간 k-1에서 구한 행동가치 함수를 의미함.

MDP 모델에 대한 정보를 알고 있다는 가정하에 과거 행동가치함수를 이용하여 현재 행동가치함수를 반복해서 계산하는 방식임.

시간 k가 커짐에 따라서 행동가치함수는 일정한 값으로 수렴하게 됨.

### 2.5. 수렴 행동가치함수를 이용한 정책 계산

$$\pi(a|s)=argmax Q_{\pi}[s,a]$$

수렴 행동가치함수를 구하게 되면 그에 맞는 최적 정책을 새롭게 구합니다.

$Q_{\pi}[s,a]$는 수렴 행동가치함수입니다. 새롭게 구한 정책은 새로운 최적화를 통해서 이전 정책보다 더 나은 가치를 제공합니다. 이전 정책은 수렴 행동가치함수를 구하기 위해 사용되었으며, 구해진 수렴 행동가치함수를 이용해 한 단계 더 나아진 정책을 구하게 된다.

고도화된 정책이 나왔을때 이를 이용하여 다시 수렴 행동가치함수를 구하게 되고 반복적으로 계산 과정을 수행함으로서 정책이 수렴되도록 만듬.

## 3. RL Example using Policy Iteration method.

Check Example (Frozen Lake)

- (install gym) pip install gym

*gym은 강화학습 실습을 위한 환경임 (OpenAI가 운영하는 강화학습 알고리즘을 개발하고 검증할수있는 예제 환경을 제공하는 툴킷임)