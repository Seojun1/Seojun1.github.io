---
title: "Logistic Regression"
date: 2026-07-11 23:50:00 +0900
categories: [Andrwng Lecture]
tags: [Machine_Learning, Deep_Learning, Study]
---

# Logistic Regression Loss & Cost function

로지스틱 회귀 손실함수 & 비용함수

---

![image.png](/assets/images/logistic-cost/image.png)

![image.png](/assets/images/logistic-cost/image1.png)

예측값인 y-hat은 시그모이드(Transpose W * x + b) 라는 것을 저번 페이지에서 배웠다
시그모이드 수식은 1/1+e^-z이다.

---

![image.png](/assets/images/logistic-cost/image2.png)

로지스틱 회귀를 통해서 결국엔 실제값과 동일한 예측값을 갖기를 바란다 (loss = 0)
그치만 기계를 통한 예측은 실제 결과와 아예 똑같을 순 없다. 그래서 예측값 - 실제값인 손실함수가 존재한다.

---

## Loss Function

손실 함수는 하나의 특성(x)에 대한 실제값(y)과 예측값(y-hat)의 오차를 계산하는 함수다.

![image.png](/assets/images/logistic-cost/image3.png)

m개의 오차를 제곱해서 최소 하는 방식을 주로 사용한다
하지만 해당 방식을 로지스틱 회귀에서 사용하면 지역 최소값에 빠져 경사하강법 적용을 못하게 만들기 때문에 다른 방식의 Error Function이 필요하다

![image.png](/assets/images/logistic-cost/image4.png)

해당 L(y-hat, y) 함수를 쉽게 풀어 설명하면 아래와 같다

- y = 0 : L(y-hat, y) = -log(1 - y-hat)가 0에 가까워지도록 y-hat이 0에 수렴하게 됨
- y = 1 : L(y-hat, y) = -log(y-hat)가 0에 가까워지도록 y-hat은 1에 수렴하게 됨

---

## Cost Function

비용함수는 모든 입력에 대한 오차를 계산하는 함수다.

![image.png](/assets/images/logistic-cost/image5.png)

이는 weight, bias를 매개변수로 사용한다. 
데이터 전체 개수(m개)의 오차 총합을 구해 이를 다시 m으로 나누어 오차의 평균치를 구한다.

---

## Conclusion

로지스틱 회귀의 핵심은 아래와 같다.

- Loss Funtion(J)를 최소화 시키며 학습함
- 최적의 parameters(w, b)를 찾는다