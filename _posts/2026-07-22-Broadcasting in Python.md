---
title: "Broadcasting in Python"
date: 2026-07-22 19:22:00 +0900
categories: [Andrwng Lecture]
tags: [Machine_Learning, Deep_Learning, Study]
---

# Broadcasting in Python

파이썬의 브로드캐스팅
---

브로드캐스팅은 크기(Shape)가 다른 배열 혹은 행렬 간의 산술 연산을 가능하게 해주는 기능을 의미한다.

![image.png](/assets/images/broadcasting/image.png)

예를 들어, 네가지 음식의 탄수화물, 단백질, 지방이 주는 칼로리의 백분율을 구해본다고 하자.
계산 과정은 아래와 같다.

- 각 과일에 맞는 탄수화물, 단백질, 지방의 합을 구한다
- 행렬 전체를 나눠서 네 가지 음식 안의 탄수화물, 단백질, 지방이 주는 칼로리의 백분율을 구한다

먼저 (3 x 4) 행렬 A에 있는 각 과일의 성분의 합을 구하면 총 칼로리를 얻을 수 있다.
위 과정을 for문 없이 한줄의 파이썬 코드만으로 구해보자.

## Code

```python
import numpy as np

A = np.array([[56.0, 0.0, 4.4, 68.0],
              [1.2, 104.0, 52.0, 8.0],
              [1.8, 135.0, 99.0, 0.9]])

print(A)
```

먼저 위 이미지에 있던 네 가지 음식 행렬을 A라는 변수에 담는다

```python
cal = A.sum(axis=0)
print(cal)

>>> [ 59.  239.  155.4  76.9]
```

A 행렬의 열을 더하라는 의미의 코드를 작성한다.
코드를 실행시켜보면 각 과일마다 (탄수화물 + 단백질 + 지방)의 값이 나온다!

+ axis의 0과 1은 서로 의미가 다르다.

![image.png](/assets/images/broadcasting/image1.png)

- sum(axis=0) : 열끼리 더함
- sum(axis=1) : 행끼리 더함

```python
percentage = 100*A / cal.reshape(1,4) # (3,4) -> (1,4)
print(percentage)

>>> [[94.91525424  0.          2.83140283 88.42652796]
 [ 2.03389831 43.51464435 33.46203346 10.40312094]
 [ 3.05084746 56.48535565 63.70656371  1.17035111]]
```

백분율을 구해보자.

cal(각 과일마다 탄수화물+단백질+지방 값)의 shape을 (1,4)로 바꿔주고 이를 100*A(백분율이니까 100을 곱함)와 서로 나눠주면 백분율의 값이 나온다.

![image.png](/assets/images/broadcasting/image2.png)

사실 첫번째 코드를 통해 cal의 shape은 (1,4)로 이미 변경된 상태다.
그래서  reshape 함수를 굳이 사용하지 않아도 되지만, 코드를 작성할 때 행렬의 차원이 확실하지 않다면 reshape 함수로 확실하게 행렬의 차원을 바꿔주는 것이 좋다.

---

![image.png](/assets/images/broadcasting/image3.png)

(m x n) 행렬에 (1 x n)을 연산할 때 → (1 x n) 행렬을 m번 복사하여 (m x n)으로 변환 후 계산

(m x n) 행렬에 (m x 1)을 연산할 때 → (m x 1) 행렬을 n번 복사하여 (m x n)으로 변환 후 계산

![image.png](/assets/images/broadcasting/image4.png)

(m x 1) 행렬에 (1 x 1) 행렬 즉, 실수를 연산할 때 → 실수를 m번 복사해 (m x 1)으로 변환 후 계산
(1 x m) 행렬에 (1 x 1) 실수를 연산할 때 → 실수를 m번 복사해 (1 x m)으로 변환 후 계산

![image.png](/assets/images/broadcasting/image5.png)

간단한 예시로 (4 x 1) 행렬과 실수 100을 서로 더한다고 하자.
그러면 실수 100을 m번(4번) 반복하여 똑같이 (4 x 1) 행렬로 만들면 된다.

![image.png](/assets/images/broadcasting/image6.png)

그럼 위에서 보는 것과 같이 각 행렬의 Shape이 같아지면서 서로 연산이 가능해진다.