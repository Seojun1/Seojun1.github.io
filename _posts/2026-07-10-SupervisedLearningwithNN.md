---
title: "Supervised-Learning with NN?"
date: 2026-07-11 23:50:00 +0900
categories: [Andrwng Lecture]
tags: [Machine_Learning, Deep_Learning, Study]
---

# Supervised Learning with NN

신경망을 이용한 지도학습

---

지도학습은 입력 X와 출력 Y에 매핑하는 함수를 학습하는 것이 목적이다

![image.png](/assets/images/what_is_deeplearning_taking_off/01.png)

위 이미지처럼 입력(input)은 예측하고자하는 값(y)에 관한 특성, 정보들이다
따라서 Output(y)는 input(x)를 통해 학습해서 최종적인 결과물이 된다.

각각 사용하는 모델은 다음과 같다.

- Home features, Ad, user info와 같이 평범한 지도학습의 경우 → Standard NN(신경망)을 사용
- Image의 경우 → CNN이라고 불리는 합성곱 신경망을 사용한다
- Audio 음성은 시간에 흐름에 따라 재생되기에 1차원 시계열 데이터로 나타나는 시퀀스 데이터를 사용한다. 따라서 RNN이 사용됨
- Radar(레이더)의 경우 → 더 복잡한 하이브리드 신경망 구조를 사용한다

![image.png](/assets/images/supervised-learning-with-nn/02.png)

왼쪽부터 차례대로 표준 신경망, CNN(합성곱 신경망), RNN이다.
각각 모델의 형태가 다르다는 것을 알 수 있다.

![image.png](/assets/images/supervised-learning-with-nn/03.png)

지도학습에는 구조적, 비구조적 데이터로 나뉜다.

- 구조적 : 방의 사이즈, 침실 개수, 사용자 나이, 아이디 등 특성을 표현할 수 있음
- 비구조적 : 오디오, 사진, 텍스트 등 특성을 표현하기 어려움