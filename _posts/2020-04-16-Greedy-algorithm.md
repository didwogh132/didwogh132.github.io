---
layout : single
title : "Greedy algorithm"
date : 2020-04-16 19:22:00 +0900
author : jaeho
comments : true
---

# Greedy algorithm

- 그리디 알고리즘이란

그리디 알고리즘이란 매 상황에서 기대치 중 최솟값 또는 최댓값을 선택해 결과를 산출하는 방법이다.



- 조건

1. 근시안적 선택을 하기 때문에 입력을 받아 최선의 선택을 하면서 결과값을 도출하기 때문에 앞선 선택이 후의 선택에 영향을 미치면 안된다.
2. 매 상황에서의 최선의 선택이 결과적으로 최적해여야 한다.



- 책에 나와있는 그리디 알고리즘

동전 거스름돈, 최소 신장 트리, 최단 경로 찾기, 부분 배낭 문제, 집합 커버 문제, 작업 스케줄링, 허프만 압축



### 그리디 알고리즘 문제

N자리 숫자가 주어졌을 때, 여기서 숫자 K개를 지워서 얻을 수 있는 가장 큰 수를 구하시오. (1<=K<N<=500,000)



##### 입력

1. 첫째 줄에 N과 K를 입력 받는다.
2. 둘째 줄에 N자리 숫자를 받는다.

**접근 방법**

1. N번 자리부터 1번까지 순서대로 비교하며 N자리<(N-1)자리이면 스텍에 N-1을 넣어준다.
2. N번 자리 숫자를 없앤다.
3. 



``` c
#include<stdio.h>
void main() {
	int n, k, top = 0; char c, stack[500000]; 	
    scanf("%d%d", &n, &k);
	while (n--) { 
		do {
			scanf("%c", &c);
		} while (c < 48 || 57 < c);
		while (k > 0 && top > 0 && stack[top - 1] < c) { 
            top--; k--;
        }
		stack[top++] = c;
	}
	top -= k; stack[top] = 0; puts(stack);
}
```

while (n--) {
		do {
			scanf("%c", &c);
		} while (c < 48 || 57 < c);
		while (k > 0 && top > 0 && stack[top - 1] < c) { 
            top--; k--;
        }
		stack[top++] = c;
	}



scanf("%c", &c); 는 N자리의 숫자를 받는것이다.

while (c < 48 || 57 < c); 48~57('0'~'9")까지의 ASCII 값이다. 그 외의 값을 받게 되면 다시 입력을 받아야한다.



while (k > 0 && top > 0 && stack[top - 1] < c) { 
            top--; k--;

 } : N-1번째자리가 N번째자리보다 클 때 N번째 숫자를 삭제하고 N-1번째 숫자를 저장한다.

