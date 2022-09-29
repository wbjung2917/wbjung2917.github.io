---
layout: post
title: 백준 단계별 문제풀이 스터디 1주차
subtitle:
categories: Study
tags: [python]
---

## 10871번 X보다 작은수
### 링크
[https://www.acmicpc.net/problem/10871][1]

### 문제
정수 N개로 이루어진 수열 A와 정수 X가 주어진다. 이때, A에서 X보다 작은 수를 모두 출력하는 프로그램을 작성하시오.

### 입력
첫째 줄에 N과 X가 주어진다. (1 ≤ N, X ≤ 10,000)

둘째 줄에 수열 A를 이루는 정수 N개가 주어진다. 주어지는 정수는 모두 1보다 크거나 같고, 10,000보다 작거나 같은 정수이다.

### 출력
X보다 작은 수를 입력받은 순서대로 공백으로 구분해 출력한다. X보다 작은 수는 적어도 하나 존재한다.

### 코드
```python
# 첫번째줄 입력을 변수에 저장
strarr_input=input().split(" ")
int_LengthOfArray=int(strarr_input[0])
int_TargetNumber=int(strarr_input[1])

# 두번째줄 입력을 변수에 저장
intarr_ArrayOfNumbers=list(map(int,input().split(" ")))

# 비교 후 값을 저장할 리스트를 생성
num_list=[]
# 주어진 int array의 모든 값에 대하여 비교
for num in intarr_ArrayOfNumbers:
    # num 이 int_TargetNumber보다 작은지 비교 후 num_list에 append
    if num<int_TargetNumber:
    num_list.append(str(num))

# num_list를 공백으로 묶어 출력
print(" ".join(num_list))
#for num in num_list:
#    print(f"{num}",end=" ")
```

## 1110번 더하기 사이클
### 링크
[https://www.acmicpc.net/problem/1110][2]

### 문제
0보다 크거나 같고, 99보다 작거나 같은 정수가 주어질 때 다음과 같은 연산을 할 수 있다. 먼저 주어진 수가 10보다 작다면 앞에 0을 붙여 두 자리 수로 만들고, 각 자리의 숫자를 더한다. 그 다음, 주어진 수의 가장 오른쪽 자리 수와 앞에서 구한 합의 가장 오른쪽 자리 수를 이어 붙이면 새로운 수를 만들 수 있다. 다음 예를 보자.

26부터 시작한다. 2+6 = 8이다. 새로운 수는 68이다. 6+8 = 14이다. 새로운 수는 84이다. 8+4 = 12이다. 새로운 수는 42이다. 4+2 = 6이다. 새로운 수는 26이다.

위의 예는 4번만에 원래 수로 돌아올 수 있다. 따라서 26의 사이클의 길이는 4이다.

N이 주어졌을 때, N의 사이클의 길이를 구하는 프로그램을 작성하시오.

### 입력
첫째 줄에 N이 주어진다. N은 0보다 크거나 같고, 99보다 작거나 같은 정수이다.

### 출력
첫째 줄에 N의 사이클 길이를 출력한다.

### 코드
```python
#입력받은수를 저장하고 해당 수의 10의 자리수와 1의 자리수를 각각 저장
int_input=int(input())
int_FrontNumber=int_input//10
int_BackNumber=int_input%10

#사이클길이 카운터 0으로 초기화
counter=0

#무한히 반복
while True:
    #새로 생성되는 숫자의 앞자리와 뒷자리를 저장
    int_NewFront=int_BackNumber
    int_NewBack=(int_FrontNumber+int_BackNumber)%10
    #새로 생성된 숫자의 각 자릿수를 기존자리에 대체
    int_FrontNumber=int_NewFront
    int_BackNumber=int_NewBack
    #카운터 1 증가
    counter+=1
    #새로운 숫자계산
    int_NewNumber=10*int_NewFront+int_NewBack
    #새로운 숫자가 최초 숫자와 같다면 break
    if int_NewNumber==int_input:
        break

# 카운터 출력
print(counter)
```



[1]:https://www.acmicpc.net/problem/10871
[2]:https://www.acmicpc.net/problem/1110