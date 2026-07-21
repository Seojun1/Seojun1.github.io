---
title: "Vectorizing Logistic Regression's Gradient Computation"
date: 2026-07-21 15:50:00 +0900
categories: [Andrwng Lecture]
tags: [Machine_Learning, Deep_Learning, Study]
---

# Vectorizing Logistic Regression's Gradient Computation

**로지스틱 회귀의 경사 계산을 벡터화 하기**

---

경사 계산을 위해 첫 샘플( dz^(1), dx^(2), …, dx^(m) )의 계산은 다음과 같다. 

![image.png](/assets/images/vectorizing-logistic-regressions-gradient-computation/image.png)

dz는 값들이 가로로 쌓여있는 벡터로 구성되며, (1 x m) 행렬이다.

![image.png](/assets/images/vectorizing-logistic-regressions-gradient-computation/image1.png)

A와 Y 또한 (1 x m) 행렬이며 dz는 A와 Y를 서로 뺀 값이다. 추가로 처음에 위에서 계산한 샘플의 값들(dz^(1), dz^(2), …)이 dz에 담겨있음을 알 수 있다.

![image.png](/assets/images/vectorizing-logistic-regressions-gradient-computation/image2.png)

따라서 아래 식까지가 지난번에 했던 (벡터화를 통해 for문 없애기) 내용이다.

![image.png](/assets/images/vectorizing-logistic-regressions-gradient-computation/image3.png)

---

## db에 대한 벡터화

![image.png](/assets/images/vectorizing-logistic-regressions-gradient-computation/image4.png)

db는 dz(i)의 모든 합을 m으로 나눈 값이다.
파이썬으로는 1/m * np.sum(dz)라고 표현

## dw에 대한 벡터화

![image.png](/assets/images/vectorizing-logistic-regressions-gradient-computation/image5.png)

dw는 (X * dz의 전치)에 1/m을 한 값이다.
X와 dz의 전치를 서로 곱하면 (m x 1)의 행렬이 되며 해당 행렬에 1/m을 한 값이 최종적인 dw의 값이 된다.

위와 같은 벡터화된 계산을 통해 for문 없이 변수의 갱신값을 계산할 수 있게 된다.

---

## 로지스틱 회귀 구현

![image.png](/assets/images/vectorizing-logistic-regressions-gradient-computation/image6.png)

경사하강법 갱신은 아래와 같다 (a : alpha → learning-rate).

- w = w - a(alpha)dw
- b = b - a(alpha)db

경사 하강법을 반복하고 싶다면 어쩔 수 없이 for문이 필요하다.