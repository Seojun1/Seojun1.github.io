---
title: "Binary Classification"
date: 2026-07-11 23:50:00 +0900
categories: [Andrwng Lecture]
tags: [Machine_Learning, Deep_Learning, Study]
---

# Binary Classification

카테고리: AI

이진 분류

---

![image.png](assets/images/binary-classification/image.png)

이진 분류는 그렇다 / 아니다 2개를 분류하는 것이다
예를 들어 위 고양이 사진이 입력으로 주어짐 → ‘고양이이다 / 아니다’ 를 분류하는 것이 이진 분류이다.

## Classification(분류), Regression(회귀)

![image.png](assets/images/binary-classification/image1.png)

Classification

- 데이터를 하나의 기준으로 2개로 분류하는 것 (ex: Yes / No)

Regression

- 연속적인 숫자나 수치를 예측하는 것 (과거 매출 데이터로 다음 달 매출액 예측)

## 고양이 데이터 처리 과정

![image.png](assets/images/binary-classification/image.png)

입력된 고양이 이미지의 크기가 64 x 64 라면 빨간색, 초록색, 파란색 세 행렬의 크기 또한 (64 x 64 x 3)으로 표현된다.
(위 이미지에서는 설명을 위해 5 x 4로 생략하여 표기했지만 실제로는 64 x 64 행렬이다)

추가로 Red, Green, Blue 세 픽셀에 적혀있는 각각의 숫자는 채도(밝기)를 의미한다.

이제 픽셀 값 하나하나를 합쳐서 세로로 세운 X를 차원 벡터(feature vector)라고 해보자.

세로로 세워진 차원 벡터 X의 차원 수는 
**64 x 64 x 3 = 12888**로 구할 수 있다.

![image.png](assets/images/binary-classification/image2.png)

![image.png](assets/images/binary-classification/image3.png)

---

![image.png](assets/images/binary-classification/image4.png)

![image.png](assets/images/binary-classification/image5.png)

한 쌍의 (x, y)가 있다고 해보자.
x는 차원 벡터이고, y는 0과 1 중 하나의 값만 가진다.

![image.png](assets/images/binary-classification/image6.png)

m 이라는 훈련 데이터가 있다고 하자 (Length : m개)
m 훈련 데이터를 열어보면 (x, y) 쌍으로 구성되어 있을 것이다. 

```bash
**{(x_1, y_1), (x_2, y_2), …, (x_m, y_m)}**
```

또한 M은 훈련 데이터 m을 테스트하기 위한 새로운 테스트 세트를 의미한다

이제 계산을 편리하게 하기 위해 차원 벡터인 x를 행렬의 형태로 바꾸어보자.

![image.png](assets/images/binary-classification/image7.png)

x_1 ~ x_m 까지를 행렬의 열로 구성해서 행렬 X를 만들면 위 이미지에 있는 X의 형태가 된다.

x_1 ~ x_m까지를 열이 아닌 행으로 구성하는 방법도 있지만, 딥러닝에서는 열 방식이 더 쉬워서 주로 열 방식을 사용한다

![image.png](assets/images/binary-classification/image8.png)

![image.png](assets/images/binary-classification/image9.png)

마지막으로 X는 n_x * m 차원이고, 해당 차원을 파이썬으로 구현하고자 한다면
X.shape()로 구할 수 있다.

![image.png](assets/images/binary-classification/image10.png)

Y 또한 위와 같은 구조를 통해 계산된다.