---
title: "Logistic Regression Gradient Descent"
date: 2026-07-15 19:50:00 +0900
categories: [Andrwng Lecture]
tags: [Machine_Learning, Deep_Learning, Study]
---

# Logistic Regression Gradient Descent

로지스틱 회귀의 경사하강법

---

로지스틱 회귀 수식에 대해 잠깐 복습하고 넘어갑시다

![image.png](/assets/images/Logistic-Regression-Gradient-Descent/image.png)

- z : weight inversed *  x_data + bais
- y-hat : 예측값
- L(a,y) : 하나의 샘플에 대한 Loss Function 
            (a : 로지스틱 회귀의 출력값, y : 참 값 Label)

---

![image.png](/assets/images/Logistic-Regression-Gradient-Descent/image1.png)

로지스틱 회귀의 실제 동작하는 흐름 다이어그램이다.
위 다이어그램을 보고 역전파 방식으로 계산을 해보자

먼저 손실함수의 수식은 다음과 같다.

![image.png](/assets/images/Logistic-Regression-Gradient-Descent/image2.png)

이제 위 손실함수 수식에서 a에 대한 미분을 하면 손실 함수 L(a,y)의 도함수를 다음과 같은 수식을 통해 구할 수 있다.
dL(a,y)/da = -y/a + l-y / l-a (da가 -y/a + 1-y / 1-a가 되는 과정을 오른쪽에 작성해놓았으니 참고)

![image.png](assets/images/Logistic-Regression-Gradient-Descent/image3.png)

다음으로 z에 대해 미분하면 다음과 같다.

![image.png](/assets/images/Logistic-Regression-Gradient-Descent/image8.png)

dz의 식으로 dL/dz와 dL(a,y)/dz 두 개가 있는데 둘 다 똑같은 식으로 같은 의미를 내포하니 편한 식으로 이해하면 된다.
(왼쪽 그림에서 dz가 a - y가 되는 과정을 오른쪽에 작성해놓았으니 참고)

![image.png](/assets/images/Logistic-Regression-Gradient-Descent/image6.png)

단일 샘플에 대해서만 경사하강법을 사용한다면 위 과정처럼 값을 구할 수 있다.
그럼 최종적인 dw_1, dw_2, db에 대한 값은 아래와 같이 계산할 수 있다.

dw_1 :  w1 * dz
dw_2 : w2 * dz
db : dz

![image.png](/assets/images/Logistic-Regression-Gradient-Descent/image7.png)

마지막으로 구한 dw_1, dw_2, db를 위 이미지와 같은 방식으로 반복 갱신함으로써 경사하강법이 수행된다