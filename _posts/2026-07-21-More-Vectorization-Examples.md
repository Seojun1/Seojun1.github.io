---
title: "More Vectorization Examples"
date: 2026-07-21 15:50:00 +0900
categories: [Andrwng Lecture]
tags: [Machine_Learning, Deep_Learning, Study]
---

# More Vectorization Examples

더 많은 벡터화 예제

---

## 로지스틱 회귀와 경사하강법에서의 벡터

![image.png](/assets/images/more-vectorization-examples/image.png)

위는 로지스틱 회귀에서의 비용함수의 의사코드이다.

위 코드에서는 특성의 개수(dw)를 2개(dw_1, dw_2)로 가정하였지만, 만약 특성의 개수가 늘어난다면, dw_1, dw_2에서 더 나아가 dw_3, …, dw_n이 될 것이다. 따라서 이 부분 또한 for문을 이용해 처리해야한다. 그렇게 되면 이중 for문을 사용하게 되므로 계산속도가 현저히 느려지게 된다.

그럼 이제 특성이 여러개라고 가정하고, 이중 for문인 환경에서 벡터를 적용해서 하나의 for문 구조로 바꿔보자!

---

![image.png](/assets/images/more-vectorization-examples/image1.png)

위 이미지에서 m을 카운트하는 for문 1개, dw_1, dw_2 등의 특성을 카운트하는 for문해서 총 2개의 for문이 있다.

![image.png](/assets/images/more-vectorization-examples/image2.png)

먼저 선언부분에 있는 dw1, dw2를 n_x 차원의 벡터인 dw를 생성해 하나로 통합할 수 있다.

![image.png](/assets/images/more-vectorization-examples/image3.png)

그러면 자연스레 dw_1, dw_2와 같이 특성을 카운트해줬던 for문을 대신해서 오른쪽에 적혀있는 수식처럼 벡터 연산을 사용할 수 있다.

![image.png](/assets/images/more-vectorization-examples/image4.png)

dw_1, dw_2를 m으로 나눠주던 아래쪽에 있는 수식 또한 dw /= m 으로 간단하게 변경할 수 있다.

결과적으로 두개였던 for문을 벡터연산을 통해 하나로 줄였다 !