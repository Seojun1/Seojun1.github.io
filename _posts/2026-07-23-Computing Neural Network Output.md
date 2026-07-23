---
title: "Computing Neural Network Output"
date: 2026-07-23 17:30:00 +0900
categories: [Andrwng Lecture]
tags: [Machine_Learning, Deep_Learning, Study]
---

# Computing Neural Network Output

신경망 네트워크 출력의 계산

---

![image.png](/assets/images/Computin-Neural-Network-Output/image.png)

로지스틱 회귀는 위 이미지 과정대로 학습을 진행한다.

반면에 신경망에서는 은닉층이 여러 개인 네트워크 형식으로 학습을 진행하는데 각 노드들이 어떻게 계산을 하는지 알아보자.

---

![image.png](/assets/images/Computin-Neural-Network-Output/image1.png)

첫 번째 노드인 a~1~^[1]^의 경우, w^T^ * x + b의 결과인 z와 시그모이드 함수를 거친 a를 계산하는 총 두 개의 연산을 한다.

각 노드의 연산에서 사용되는 표기법은 아래와 같다.

- a~i~^[l]^
    - l : 몇 번째 층인지 의미한다
    - i : 해당 층에서의 몇 번째 노드인지 의미한다.

예시로 a~2~^[1]^인 경우, 첫번째 층의 2번째 노드를 의미하게 된다.

![image.png](/assets/images/Computin-Neural-Network-Output/image2.png)

a~2~^[1]^ 노드 또한 z~2~^[1]^과 a~2~^[1]^을 로지스틱 회귀와 동일한 방식으로 구한다.

이렇게 쭉 마지막인 네 번째 노드까지 구한 식을 나열하면 아래와 같은 수식이 나오게 된다.

![image.png](/assets/images/Computin-Neural-Network-Output/image3.png)

이걸 코드로 구하려면 for문을 써야하는데 되도록이면 for문을 작성하지 않는 것이 좋다고 했다.

따라서 해당 수식들을 벡터화 해야한다.

---

먼저 w와 x 그리고 b를 벡터화해서 행렬처럼 나열하면 다음과 같다.

![image.png](/assets/images/Computin-Neural-Network-Output/image4.png)

즉 벡터화한 결과들이 전부 z~1~^[1]^ ~ z~4~^[1]^의 값과 같다는걸 알 수 있다.

그럼 이제 이 결과를 z라는 행렬 안에 담으면 최종 수식은 아래와 같다.

![image.png](/assets/images/Computin-Neural-Network-Output/image5.png)

이제 마지막인 a의 값도 벡터화 해보자.

![image.png](/assets/images/Computin-Neural-Network-Output/image6.png)

위에서 z 라는 행렬안에 w * x + b의 값 전부를 담았으니, 시그모이드 함수에 z행렬만 넣어주면 된다.

시그모이드까지 통과한 a~1~^[1]^ ~ a~4~^[1]^까지 벡터들을 a^[1]^ 행렬 안에 쌓아 정의하면 된다.

---

![image.png](/assets/images/Computin-Neural-Network-Output/image7.png)

정리하면 신경망의 출력값을 계산하는데에는 위 네 등식만이 필요하다.