---
layout: post
title: 백준 단계별 문제풀이 스터디 2주차
subtitle:
author: 정우빈
categories: Study
tags: [python]
---

## 2869번 달팽이는 올라가고 싶다
### 링크
[https://www.acmicpc.net/problem/2869][1]
### 문제
땅 위에 달팽이가 있다. 이 달팽이는 높이가 V미터인 나무 막대를 올라갈 것이다.

달팽이는 낮에 A미터 올라갈 수 있다. 하지만, 밤에 잠을 자는 동안 B미터 미끄러진다. 또, 정상에 올라간 후에는 미끄러지지 않는다.

달팽이가 나무 막대를 모두 올라가려면, 며칠이 걸리는지 구하는 프로그램을 작성하시오.
### 입력
첫째 줄에 세 정수 A, B, V가 공백으로 구분되어서 주어진다. (1 ≤ B < A ≤ V ≤ 1,000,000,000)
### 출력
첫째 줄에 달팽이가 나무 막대를 모두 올라가는데 며칠이 걸리는지 출력한다.
### 코드
```python
#입력을 각 변수에 저장
intArr_input=list(map(int,input().split(" ")))
int_ClimbDistance=intArr_input[0]
int_SlipDistance=intArr_input[1]
int_HeightOfTree=intArr_input[2]

#날짜 카운터와 현위치를 저장할 변수 초기화
int_DayCount=0
int_CurrentHeight=0

#무한히 반복
while True:
  # n일차 카운팅
  int_DayCount+=1
  # 등반 후 높이 도달 비교
  int_CurrentHeight+=int_ClimbDistance
  # 높이에 도달했다면 break
  if int_CurrentHeight>=int_HeightOfTree:
    break
  # 자는동안 미끄러지는 높이
  int_CurrentHeight-=int_SlipDistance

#걸린 날짜를 출력
print(int_DayCount)
```
위의 방법이 가장 직관적인 방법이다. 하지만 문제에 0.15초라는 시간제한이 존재하기 때문에 위 과정을 수식으로 표현해 간단하게 계산해낼 필요가 있다.  
문제에서처럼 오르는거리를 A, 미끄러지는거리를 B, 나무높이를 V, 총걸리는 일수를 n이라고 하고 식을 정리하면

$An-B(n-1) \geq V$

$A+(A-B)(n-1) \geq V$

$(A-B)(n-1) \geq V-A$

$n-1 \geq (V-A)/(A-B)$

$n \geq (V-A)/(A-B)+1$

위와 같이 나타낼 수 있다.  
이때 n은 일 수에 해당하기 때문에 정수형태로 밖에 나타낼 수 없다.  
예를들어, $n \geq 5.5$일경우 $n=6$으로 $n \geq 3.3$일경우 $n=4$로 나타나야 한다.  
이 과정은 소숫점을 올림 처리하는것과 같다.  
이를 적용해 코드를 작성하면 아래와 같이 작성할 수 있다.
```python
import math
#입력을 각 변수에 저장
intArr_input=list(map(int,input().split(" ")))
int_ClimbDistance=intArr_input[0]
int_SlipDistance=intArr_input[1]
int_HeightOfTree=intArr_input[2]

#수식을 작성한 후 올림을 적용
int_DaysTaken=math.ceil(((int_HeightOfTree-int_ClimbDistance)/(int_ClimbDistance-int_SlipDistance))+1)

#걸린 날짜를 출력
print(int_DaysTaken)
```

## 3003번 킹, 퀸, 룩, 비숍, 나이트, 폰
### 링크
[https://www.acmicpc.net/problem/3003][2]
### 문제
동혁이는 오래된 창고를 뒤지다가 낡은 체스판과 피스를 발견했다.

체스판의 먼지를 털어내고 걸레로 닦으니 그럭저럭 쓸만한 체스판이 되었다. 하지만, 검정색 피스는 모두 있었으나, 흰색 피스는 개수가 올바르지 않았다.

체스는 총 16개의 피스를 사용하며, 킹 1개, 퀸 1개, 룩 2개, 비숍 2개, 나이트 2개, 폰 8개로 구성되어 있다.

동혁이가 발견한 흰색 피스의 개수가 주어졌을 때, 몇 개를 더하거나 빼야 올바른 세트가 되는지 구하는 프로그램을 작성하시오.
### 입력
첫째 줄에 동혁이가 찾은 흰색 킹, 퀸, 룩, 비숍, 나이트, 폰의 개수가 주어진다. 이 값은 0보다 크거나 같고 10보다 작거나 같은 정수이다.
### 출력
첫째 줄에 입력에서 주어진 순서대로 몇 개의 피스를 더하거나 빼야 되는지를 출력한다. 만약 수가 양수라면 동혁이는 그 개수 만큼 피스를 더해야 하는 것이고, 음수라면 제거해야 하는 것이다.
### 코드
```python
#입력을 각 변수에 저장
intArr_input=list(map(int,input().split(" ")))

#모든 피스의 본 구성을 입력한 배열 생성
intArr_FullPiece=[1,1,2,2,2,8]

#입력받은 피스와의 차를 계산
strArr_MissingPiece=[str(intArr_FullPiece[i]-intArr_input[i]) for i in range(len(intArr_input))]

#계산된 맞지않는 피스의 수 리스트를 출력
print(" ".join(strArr_MissingPiece))
```
입력받은 피스와 본구성의 차를 계산하는 과정에서 list comprehension을 사용하였다.

참고 : [https://shoark7.github.io/programming/python/about-list-comprehension-python][3]

## 25304번 영수증
### 링크
[https://www.acmicpc.net/problem/25304][4]
### 문제
준원이는 저번 주에 살면서 처음으로 코스트코를 가 봤다. 정말 멋졌다. 그런데, 몇 개 담지도 않았는데 수상하게 높은 금액이 나오는 것이다! 준원이는 영수증을 보면서 정확하게 계산된 것이 맞는지 확인해보려 한다.

영수증에 적힌,

구매한 각 물건의 가격과 개수 구매한 물건들의 총 금액 을 보고, 구매한 물건의 가격과 개수로 계산한 총 금액이 영수증에 적힌 총 금액과 일치하는지 검사해보자.
### 입력
첫째 줄에는 영수증에 적힌 총 금액  X 가 주어진다.

둘째 줄에는 영수증에 적힌 구매한 물건의 종류의 수  N 이 주어진다.

이후  N 개의 줄에는 각 물건의 가격  a 와 개수  b 가 공백을 사이에 두고 주어진다.
### 출력
구매한 물건의 가격과 개수로 계산한 총 금액이 영수증에 적힌 총 금액과 일치하면 Yes를 출력한다. 일치하지 않는다면 No를 출력한다.
### 제한
● 1 ≤ X ≤ 1,000,000,000  
● 1 ≤ N ≤ 100  
● 1 ≤ a ≤ 1,000,000  
● 1 ≤ b ≤ 10  
### 코드
```python
#입력을 각 변수에 저장
int_TotalPrice=int(input())
int_KindOfThings=int(input())
#각 물품의 가격과 갯수를 저장할 리스트 생성
list_PriceNAmount=[]
for i in range(int_KindOfThings):
  list_PriceNAmount.append(list(map(int,input().split(" "))))

#총합계 계산
int_CalculatedTotalPrice=0
for item in list_PriceNAmount:
  int_CalculatedTotalPrice+=item[0]*item[1]

#기존 총합계와 일치 여부 확인
if int_TotalPrice==int_CalculatedTotalPrice:
  print("Yes")
else:
  print("No")
```

[1]:https://www.acmicpc.net/problem/2869
[2]:https://www.acmicpc.net/problem/3003
[3]:https://shoark7.github.io/programming/python/about-list-comprehension-python
[4]:https://www.acmicpc.net/problem/25304