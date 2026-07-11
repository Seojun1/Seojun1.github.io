---
title: "Logistic Regression"
date: 2026-07-11 23:50:00 +0900
categories: [Andrwng Lecture]
tags: [Machine_Learning, Deep_Learning, Study]
---


# Logistic Regression

로지스틱 회귀

---

![image.png](assets/images/logistic-regression/image.png)

로지스틱 회귀는 0과 1사이의 확률 값으로 예측하여 이진 분류 문제를 해결하는 방법이다.

---

![image.png](assets/images/logistic-regression/image1.png)

input 데이터로 쓰일 x가 있다고 해보자.
그럼 input값 x를 토대로 로지스틱 회귀를 통해 결괏값 y-hat을 도출하게 되는데, 여기서 로지스틱 회귀를 거친 y-hat의 결과 값은  **0 ≤ y ≤ 1** 의 조건을 만족해야한다. 

y-hat을 통한 예측 방법 (input 이미지가 고양이 사진이라고 가정)

- 0 ≤ y-hat < 0.5 → 0(고양이가 아님)
- 0.5 ≤ y-hat ≤ 1 → 1(고양이가 맞음)

---

![image.png](assets/images/logistic-regression/image2.png)

로지스틱 회귀의 파라미터로 w와 b가 주어졌다 (w: 차원, b: 실수)
딥러닝에서 w는 가중치(weight), b는 편향(bias)를 의미함.

그럼 아래 수식이 성립이 된다.

![image.png](assets/images/logistic-regression/image3.png)

그치만 parameter w, b만을 가지고는 예측 값인 y-hat을 계산할 수 없다.
그래서 차원 w를 Transpose 시켜서 선형 함수인 것처럼 바꾸어서 계산해야한다

![image.png](assets/images/logistic-regression/image4.png)

사실 로지스틱 회귀는 0과 1 둘중에 하나가 나와야하는 이진 분류에서 자주 사용되진 않는다
(로지스틱 회귀는 0~1 사이의 확률값으로 나타나기 때문)
따라서 로지스틱 회귀에 사용되는 함수로, 시그모이드 함수도 함께 사용할 것이다!

![image.png](assets/images/logistic-regression/image5.png)

시그모이드 함수를 쓰면 결괏값이 반드시 0~1 사이의 값으로 나오게 된다
따라서 아래 조건에 맞게 0.5보다 작거나 같으면 0(고양이가 아니다), 크면 1(고양이가 맞다)로 판별하게 된다.

- 0 ≤ y < 0.5 → 0으로 결정
- 0.5 ≤ y ≤ 1 → 1로 결정

---

로지스틱 회귀의 주 목적은 y-hat이 잘 예측되도록 Parameter(weight, bias)를 잘 학습시키는 것이다!