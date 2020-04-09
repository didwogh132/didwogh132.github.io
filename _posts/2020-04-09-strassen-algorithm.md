---
layout : single
title : "strassen algorithm"
date : 2020-04-09 18:19:00 +0900
---

# Strassen algorithm

- 배경

  슈트라센 알고리즘은 독일의 수학자 폴커 슈트라센이 1969년에 개발한 행렬 곱셈 알고리즘이다. 

- 목적

  *n*×*n* 크기의 두 행렬을 곱하면 [O](https://ko.wikipedia.org/wiki/점근_표기법)(n^3)의 시간이 소요되지만 이 알고리즘은 대략 O(n^2.807)의 시간이 소요된다.

- 알고리즘

A와 B를 F에 포함되는 정사각행렬이라고 하자. 두 행렬의 곱을 C라고 하면 밑에 식과 같다.

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/f4c680ec4a32379114e0326ba69b179881b69e8e)

만약 A와 B가 2^n × 2^n 꼴의 크기가 아니라면 모자라는 행과 열을 0으로 채운다. 이 경우 행렬 곱셈이 끝난 뒤 행렬에서 필요한 부분만 다시 잘라 내야한다. A, B, C를 같은 크기의 정사각행렬 네 개로 나눈다.

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/41c6337190684aff7b69f124226d6e62d79ebca5)

이 때,

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/e2948b2c6caf12770b217310b956b23abdc80380)

다음이 성립한다.

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/8d91fa79d27697a5c6551698c1a83a3d5837c57b)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/a08bea24eec9422cda82e6e04af1d96fc6822038)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/7adffe97db091ce8ba231352b3721bbe261985ca)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/8b40ed74cf54465d8e54d09b8492e50689928313)

이 과정에서는 필요한 연산의 수가 줄어 들지 않는다. 모든 *C(i,j)* 행렬을 계산하려면 8번의 곱셈과 4번의 덧셈이 필요하다.

이번엔 행렬을 이렇게 정의해본다.

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/1e9e6268d824de7ad5010a32a1921452b264f7ee)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d40beeba8019e378fa0ed4b6e549c44a140a9ec)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/45e8e9679d33f2c66e24bd812e1e554f95bb1571)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/c12df2bb70f8f09f33f1ca4b8c2d577d5850a2ee)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/715adfa757b74b3ad6b4eea545c24762e4079161)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/30107b9c9c99494bf75f23e84b505e5921cee46e)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/9e93ef1c265be8be96209dde36230d56e139fc72)

이렇게 정의한 M 행렬들을 *C(i,j)* 행렬을 표현하는 데 쓰면 *C(i,j)* 행렬은 다음과 같이 표현된다.

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/26875b8ca1815e2c322c798faeecabe1d7836798)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/e71779a8ecc64f3e1268485cf389a05cdd3e6bf8)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/5853fa11f016df7eee4eb2a7ceb6137d3b3296de)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/b7d7d4ee9e67e0c23f1a522787d4829072542dbb)

이 행렬들을 계산하는 데는 M 행렬에서 총 7번의 곱셈과 10번의 덧셈이 필요하다. 그리고 *C(i,j)*를 구하는 과정에서는 8번의 덧셈이 필요하므로 전체적으로는 7번의 곱셈과 18번의 덧셈이 필요하다. 



그리고 이 과정을 재귀적으로 반복할 경우 ![](https://wikimedia.org/api/rest_v1/media/math/render/svg/586e85e6ba93daf1db18e144da90a79af278e9a9)번의 연산이 필요하다.  ![](https://wikimedia.org/api/rest_v1/media/math/render/svg/ce05babfc0fc45343915cfe440346e34e8442bfe)이므로 전체 수행 시간은 약 O(n^2.807)이다. 