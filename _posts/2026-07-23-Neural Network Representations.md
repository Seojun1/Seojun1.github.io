---
title: "Neural Network Representations"
date: 2026-07-23 17:30:00 +0900
categories: [Andrwng Lecture]
tags: [Machine_Learning, Deep_Learning, Study]
---


# Neural Network Representations

신경망 네트워크의 구성

---

신경망 네트워크에는 각 레이어들을 칭하는 표기법이 있다.

![image.png](/assets/images/Neural-Network-Representations/image.png)

- 입력층 : Input Layer
- 은닉층 : Hidden Layer (훈련 세트에서 볼 수 없음)
- 출력층 : Output Layer

지도학습으로 훈련시키는 신경망에서는 훈련 세트가 (입력값 X, 출력값 Y)로 구성되어있다.
은닉층의 실제 값은 훈련세트에 기록되어있지 않다.

## Input Layer

![image.png](/assets/images/Neural-Network-Representations/image1.png)

이전에는 입력 특성을 나타내기 위해 Vector X를 사용했지만 네트워크에서의 다른 표기법은 a^[0]^가 된다.
a는 활성값을 의미하며 신경망의 층들이 다음 층으로 전달해주는 역할을 한다.

즉, 입력층은 X를 은닉층(Hidden Layer)로 전달해준다

## Hidden Layer

은닉층에서는 a^[0]^의 다음 활성값인 a^[1]^을 만든다.

![image.png](/assets/images/Neural-Network-Representations/image2.png)

은닉층에는 총 4개의 노드가 있는데 각 노드들은 위에서부터 차례대로 a_1^[1]^, a_2^[1]^, a_3^[1]^, a_4^[1]^을 의미한다.
따라서 a^[1]^은 4차원 벡터가 된다. (해당 은닉층에 노드가 총 4개가 있기 때문)

## Output Layer

![image.png](/assets/images/Neural-Network-Representations/image3.png)

실숫값 a^[2]^를 만들어낸다. 즉, y-hat이 a^[2]^의 값을 가지게 된다!
로지스틱 회귀에서 y-hat이 a의 값을 가지는 것과 비슷하다.

로지스틱 회귀에서는 출력층이 하나만 있어서 대괄호 첨자를 쓰지 않았지만, 신경망에서는 위첨자를 사용해 어떤 층에서 만들어진건지 표기를 해준다.

## 가중치와 편향

그럼 은닉층부터 출력층까지의 가중치와 편향은 어떻게 계산이 되는지 알아보자.

### 은닉층

![image.png](/assets/images/Neural-Network-Representations/image4.png)

먼저 위 신경망에서의 가중치, 편향은 은닉층에 관련된 변수이기 때문에 위첨자를 붙여 w^[1]^, b^[1]^로 표기한다.
결과적으로 은닉층에서 w는 (4 x 3)행렬이 되고 b는 (4 x 1)행렬이 된다.

- 4는 해당 은닉층에 노드가 네 개가 있기 때문이고, 3은 입력 특성(x~1~, x~2~, x~3~)이 세 개이기 때문이다.

### 출력층

![image.png](/assets/images/Neural-Network-Representations/image5.png)

위와 같은 방식으로 출력층에서의 w는 (1 x 4)행렬, b는 (1 x 1) 행렬이 된다.

- 1은 출력층에 노드가 한 개가 있기 때문이고, 4는 은닉층에 은닉 노드가 네 개가 있기 때문이다.

---

![image.png](/assets/images/Neural-Network-Representations/image6.png)

신기한 점은 위 신경망은 3층 신경망이 아닌 2층 신경망이다.
신경망 층의 개수를 셀 때는 입력 층은 제외한다.

- 논문에서는 입력층을 0번째 층이라고 함. 따라서 위 신경망은 0층(입력층) → 1층(은닉층) → 2층(출력층)이 되어 2층 신경망이 된다.