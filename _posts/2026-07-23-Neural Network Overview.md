---
title: "Neural Network Overview"
date: 2026-07-23 17:30:00 +0900
categories: [Andrwng Lecture]
tags: [Machine_Learning, Deep_Learning, Study]
---

# Neural Network Overview

신경망 네트워크 개요

---

![image.png](/assets/images/Neural-Network-Overview/image.png)

이전의 내용들은 위 이미지처럼 (w^T^ * x) + b인 z 하나를 사용해서 시그모이드를 통과시킨 a를 구하고 이를 통해 Loss Function의 값을 구했다.

![image.png](/assets/images/Neural-Network-Overview/image1.png)

신경망부터는 레이어가 여러 개로 되어있는 네트워크식의 학습 방법을 사용한다.

![image.png](/assets/images/Neural-Network-Overview/image2.png)

학습 과정은 이전과 크게 다르지 않다. z와 a를 구하는 과정을 두 번 더 반복한다고 생각하면 된다.
따라서 반복의 표시인 대괄호 첨자([1], [2] 등)가 z와 a에 사용된다. 
* 대괄호 위첨자와 각 훈련 샘플을 뜻하는 소괄호 위첨자를 헷갈리면 안됨 주의 

## Conclusion

- 네트워크식 학습 방법은 이전에 했던 로지스틱 회귀를 두번 반복해주는 것이라고 이해하면 편하다
- 네트워크식 학습 방법 또한 역방향 계산이 가능하다.