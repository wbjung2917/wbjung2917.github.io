---
layout: post
title: 백준 단계별 문제풀이 스터디 5주차
subtitle:
author: 정우빈
categories: Study
tags: [python]
---

## 14888번 연산자 끼워넣기
### 링크
[https://www.acmicpc.net/problem/14888][1]
### 문제
N개의 수로 이루어진 수열 A1, A2, ..., AN이 주어진다. 또, 수와 수 사이에 끼워넣을 수 있는 N-1개의 연산자가 주어진다. 연산자는 덧셈(+), 뺄셈(-), 곱셈(×), 나눗셈(÷)으로만 이루어져 있다.

우리는 수와 수 사이에 연산자를 하나씩 넣어서, 수식을 하나 만들 수 있다. 이때, 주어진 수의 순서를 바꾸면 안 된다.

예를 들어, 6개의 수로 이루어진 수열이 1, 2, 3, 4, 5, 6이고, 주어진 연산자가 덧셈(+) 2개, 뺄셈(-) 1개, 곱셈(×) 1개, 나눗셈(÷) 1개인 경우에는 총 60가지의 식을 만들 수 있다. 예를 들어, 아래와 같은 식을 만들 수 있다.

1+2+3-4×5÷6 1÷2+3+4-5×6 1+2÷3×4-5+6 1÷2×3-4+5+6 식의 계산은 연산자 우선 순위를 무시하고 앞에서부터 진행해야 한다. 또, 나눗셈은 정수 나눗셈으로 몫만 취한다. 음수를 양수로 나눌 때는 C++14의 기준을 따른다. 즉, 양수로 바꾼 뒤 몫을 취하고, 그 몫을 음수로 바꾼 것과 같다. 이에 따라서, 위의 식 4개의 결과를 계산해보면 아래와 같다.

1+2+3-4×5÷6 = 1 1÷2+3+4-5×6 = 12 1+2÷3×4-5+6 = 5 1÷2×3-4+5+6 = 7 N개의 수와 N-1개의 연산자가 주어졌을 때, 만들 수 있는 식의 결과가 최대인 것과 최소인 것을 구하는 프로그램을 작성하시오.
### 입력
첫째 줄에 수의 개수 N(2 ≤ N ≤ 11)가 주어진다. 둘째 줄에는 A1, A2, ..., AN이 주어진다. (1 ≤ Ai ≤ 100) 셋째 줄에는 합이 N-1인 4개의 정수가 주어지는데, 차례대로 덧셈(+)의 개수, 뺄셈(-)의 개수, 곱셈(×)의 개수, 나눗셈(÷)의 개수이다.
### 출력
첫째 줄에 만들 수 있는 식의 결과의 최댓값을, 둘째 줄에는 최솟값을 출력한다. 연산자를 어떻게 끼워넣어도 항상 -10억보다 크거나 같고, 10억보다 작거나 같은 결과가 나오는 입력만 주어진다. 또한, 앞에서부터 계산했을 때, 중간에 계산되는 식의 결과도 항상 -10억보다 크거나 같고, 10억보다 작거나 같다.
### 코드
```python
# 중복순열 구현
def product(list_of_elements,num):
  for i in range(len(list_of_elements)):
    # 한개 일 때 한 개 짜리 제너레이터 생성
    if num==1:
      yield [list_of_elements[i]]
    # 여러개 일 때 한 개 짜리+뒤에꺼 제너레이터 반복으로 추가
    else :
      for next in product(list_of_elements,num-1):
        yield [list_of_elements[i]]+next

# 사칙연산 구현
def calculator(num1,num2,op):
  if op=="+":
    return num1+num2
  elif op=="-":
    return num1-num2
  elif op=="*":
    return num1*num2
  elif op=="/":
    if num1<0:
      num1=-num1
      return -(num1//num2)
    else:
      return num1//num2

#입력값 저장
number_of_numbers=int(input())
list_of_numbers=list(map(int,input().split(" ")))
number_of_operators=list(map(int,input().split(" ")))
list_of_operators=["+","-","*","/"]

#연산자 목록을 저장할 리스트 생성
list_of_calculation=[]
#4가지 연산자를 number_of_numbers-1개 만큼 뽑은 중복순열들에 대해 반복
for i in product(list_of_operators,number_of_numbers-1):
  #연산자 갯수 저장할 리스트 생성
  count_operators=[]
  #모든 연산자에 대해 각 갯수를 append
  for op in list_of_operators:
    count_operators.append(i.count(op))
  #연산자 갯수 리스트와 주어진 연산자 갯수가 같으면 연산자 목록에 append
  if count_operators==number_of_operators:
    list_of_calculation.append(i)

#결과값 리스트 생성
result_list=[]
#연산자 목록 리스트에 대해 반복
for calc_list in list_of_calculation:
  #result에 주어진 첫번째수 저장
  result=list_of_numbers[0]
  #카운트 1로 초기화
  count=1
  #연산자리스트에 대해 반복
  for op in calc_list:
    #result에 순서대로 계산한 값을 저장
    result=calculator(result,list_of_numbers[count],op)
    #카운트증가
    count+=1
  #result값 결과값 리스트에 저장
  result_list.append(result)

#결과값 리스트 최댓값 출력
print(max(result_list))
#결과값 리스트 최솟값 출력
print(min(result_list))
```
중복순열 구현과정에서 yield를 사용하는 과정을 참고하였다.  
yield 개념 [https://www.daleseo.com/python-yield/][2]  
파이썬 순열조합 구현 [https://juhee-maeng.tistory.com/91][3]

[1]:https://www.acmicpc.net/problem/14888
[2]:https://www.daleseo.com/python-yield/
[3]:https://juhee-maeng.tistory.com/91