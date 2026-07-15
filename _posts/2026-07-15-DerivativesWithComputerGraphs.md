---
title: "Derivatives With Computer Graphs"
date: 2026-07-15 19:50:00 +0900
categories: [Andrwng Lecture]
tags: [Machine_Learning, Deep_Learning, Study]
---

# Derivatives With Computer Graphs

계산 그래프로 미분하기

---

## 순전파

![image.png](/assets/images/Derivatives_With_Computer_Graphs/image.png)

**J(a, b, c) = 3(a + bc)**에 대한 계산을 해본다고 하자.

먼저 단계를 나눠서 풀어보자

1. u = b * c
b=3, c=2 이니까 u의 값은 b*c인 6이 된다.
2. v = a + u
a = 5, u에는 1번에서 구했던 값인 6을 넣어주자. 그럼 v의 값은 5 + 6 = 11이 된다.
3. J = 3 * v
v는 2번에서 구한 값 11을 대입해주면 된다. 따라서 J의 값은 3 * v(11) = 33이 된다.

위 방식처럼 왼쪽에서 오른쪽 즉, 순방향 방식대로 함숫값을 구하는 방법이 순전파다.

## 역전파

역전파는 보통 역방향 계산을 통해 미분 값을 구할 때 사용한다.

![image.png](/assets/images/Derivatives_With_Computer_Graphs/image1.png)

순전파는 왼쪽 → 오른쪽 방향대로 함숫값을 구했다면 역전파는 오른쪽 → 왼쪽 순으로 계산한다.

![image.png](/assets/images/Derivatives_With_Computer_Graphs/image2.png)

가장 오른쪽인 J의 값부터 계산해보자.
v에 대해 미분해보면, dJ / dv = 3 이 된다.

![image.png](/assets/images/Derivatives_With_Computer_Graphs/image3.png)

a는 v를 통해서 J에 영향을 준다.
따라서 J에 대해 a를 미분해보자.
dJ/da = dJ/dv * dv/da가 되고, dJ/dv는 위에서 이미 우리가 구했으니 3을 대입해 넣어주자.
그럼 수식은 3 * dv/da가 된다. v에 대해 a를 미분한 결과는 1이 나오니까 최종 값은 3 * 1 = 3이 된다.

---

![image.png](/assets/images/Derivatives_With_Computer_Graphs/image4.png)

b와 c도 한번 구해보자

1. dJ/db

b는 u를 거치고 다시 v를 거쳐 J에 영향을 준다. 연쇄법칙을 적용하면 다음과 같다.

**dJ/db = dJ/dv * dv/du * du/db**

- dJ/dv : 위에서 구했던 3이니 대입해주자
- dv/du : v = a + u를 u에 대해 미분한 값이 되니 결과는 1이 된다
du/db : u = b * c를  b에 대해 미분하는거니까 상수 값인 c만 남는다.

따라서 이를 정리하면 다음과 같이 수식이 정리된다. 3 * 1 * 2 = 6 

1. dJ/dc

c역시 u와 v를 거쳐 J에 영향을 준다. c 또한 수식을 나열해보자.

**dJ/dc = dJ/dv * dv/du * du/dc**

- dJ/dv : 3 (위에서 구한 값)
- dv/du : 1 (위에서 구한 값)
- du/dc : u = b * c를 c에 대해 미분하면 상수 값인 b만 남는다.

c 또한 수식을 정리해보면 아래와 같다.

3 * 1 * 3 = 9

따라서 b는 변화량 6을 가지고, c는 변화량 9를 가지게 된다!

![image.png](/assets/images/Derivatives_With_Computer_Graphs/image5.png)