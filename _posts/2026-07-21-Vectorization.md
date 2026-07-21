---
title: "Vectorization"
date: 2026-07-21 15:50:00 +0900
categories: [Andrwng Lecture]
tags: [Machine_Learning, Deep_Learning, Study]
---

# Vectorization

벡터화

---

딥러닝의 핵심은 데이터세트이다.
모델을 학습시키다보면 매우 큰 데이터 세트를 학습시킬 경우가 있다.
큰 데이터를 학습시키다보면 결과를 내기까지 정말 오래걸리는데 그럴수록 코드가 빠르게 실행되는 것이 매우 중요하다.

그 방법 중 하나가 벡터화다!

---

## 벡터화란

로지스틱 회귀에서는 z = (w^T * x )+ b를 계산해야 한다.

![image.png](/assets/images/vectorization/image.png)

위 이미지 속 의사코드는 벡터화 되지 않는 구현이다.
벡터화가 되지않으면 위 z 수식을 계산하기 위해 for문을 돌려야한다. 코드도 길어지고 굉장히 느리다..

![image.png](/assets/images/vectorization/image1.png)

반면에 벡터화가 된 코드는 numpy 하나만으로 코드를 간결하게 작성할 수 있고, 시간이 오래걸리는 for문을 생략시킬 수 있다!

코드만 봤을 때도 벡터화된 구조가 더 빠르다는걸 알 수 있다.

## Vectorization 연산 속도

```python
import numpy as np

a = np.array([1, 2, 3, 4])
print(a)
```

a를 위와 같은 하나의 배열로 지정해보았다. 이제 time 모듈을 통해서 벡터화의 연산이 얼마나 걸리는지 확인해보자!

```python
import time

a = np.random.rand(1000000)
b = np.random.rand(1000000)

tic = time.time()
c = np.dot(a, b)
toc = time.time()
print(c)
print("Vectorized version: " + str(1000 * (toc-tic)) + "ms")

c = 0
tic = time.time()
for i in range(1000000):
    c += a[i] * b[i]
toc = time.time()

print(c)
print("for loop: " + str(1000 * (toc-tic)) + "ms")
```

![image.png](/assets/images/vectorization/image2.png)

결과적으로 벡터화된 코드의 연산속도는 0.6초, 벡터화되지 않은 코드(for loop)는 138초가 걸리는걸 볼 수 있다.

코드를 벡터화한다면 딥러닝을 구현할 때 결과를 훨씬 빨리 얻을 수 있다는 점이다!

## SIMD(Single Instruction Multiple Data)

위에서 실행한 연산 속도 코드는 모두 CPU에서 계산이 되었다. 

GPU와 CPU는 SIMD라는 병렬 프로세서가 있다.
이는 하나의 명령어로 여러 개의 값을 동시에 계산하는 방식을 의미한다. 쉽게 말해 벡터화 연산을 가능케 한다고 이해하면 쉽다.
따라서 for문으로 하나의 연산을 하는 것 보다, 벡터로 만들어서 연산하는 것이 더 효율적이라는 것이다.

GPU는 SIMD 계산을 매우 훌륭하게 수행하지만 CPU 또한 그렇게까지 나쁘지는 않다.