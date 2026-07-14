---
title: "Gradient Descent"
date: 2026-07-14 22:27:00 +0900
categories: [Andrwng Lecture]
tags: [Machine_Learning, Deep_Learning, Study]
---

# Gradient Descent
경사하강법

---

Loss, Cost Function에서 전체 데이터셋의 예측이 얼마나 잘 평가되었는지 보는 것이라면 경사하강법은 이를 가능케하는 parameter w, b를 찾아내는 방법이다.

w, b를 구하려면 비용함수 J(w, b)를 매우 작게 만드는 parameter인 w와 b를 찾아야한다.

## 경사하강법

![image.png](/assets/images/Gradient-Desecent/image.png)

먼저, 비용함수의 모양은 위 그림에 나와있는 J(w,b)처럼 Convex한 형태여야한다.

> 비용함수 모양이 Convex하지 않다면 경사하강법을 적용할 수 없다. (지역 최적값이 여러개이기 때문이다)
→ 따라서 Sigmoid 함수를 통해서 임의로 Convex할 수 있도록 한다. 그리고나서 최적의 w, b를 구하기 위해 경사하강법을 적용한다.
> 

![image.png](/assets/images/Gradient-Desecent/image1.png)

경사하강법의 초기에는 최소값을 모르기 때문에 임의의 점을 골라서 시작한다.

가장 가파른(steepest)방향으로 즉, 함수의 기울기를 따라서 최적의 값으로 한 step씩 업데이트를 하게 된다.
이를 반복하면 전역 최적값(Global) 혹은 그 근사치에 도달하게 된다

## 경사하강법 흐름

![image.png](/assets/images/Gradient-Desecent/image2.png)

![image.png](/assets/images/Gradient-Desecent/image3.png)

상수 $\alpha$는 Learning Rate를 의미하며 양의 정수이다.
$\frac{dJ(w)}{dw}$는 미분계수(함수의 기울기)를 의미한다.

즉, 알고리즘은 다음과 같다.

```scss
w := w - (Learning Rate * 미분계수)
```

w 위치에 따라 업데이트 방향 또한 다르다.

- dw > 0 라면, 파라미터 w는 기존의 w 값 보다 작은 방향으로 업데이트 된다
- dw < 0 이면, 파라미터 w는 기본의 w값 보다 큰 방향으로 업데이트 된다

### 수식

1. 미분계수가 양수라면 왼쪽으로 점차 하강하게 된다.

$$
w - \frac{dw}{dJ(w)} (양수)
$$

2. 미분계수가 음수가 되니까 오른쪽으로 더해지며 하강하게 된다.

$$
w - \frac{dw}{dJ(w)}(음수)
$$

## 미적분 표기법

![image.png](/assets/images/Gradient-Desecent/image4.png)

하나의 변수에 대한 도함수는 $dw = \frac{dJ(w,b)}{dw}$ 로 표현해도 되지만
두 개 이상의 변수가 있을 경우, 편미분 기호인 $\partial$을 사용한다.