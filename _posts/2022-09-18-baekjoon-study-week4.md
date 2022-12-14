---
layout: post
title: 백준 단계별 문제풀이 스터디 4주차
subtitle:
author: 정우빈
categories: Study
tags: [python]
---

## 11729번 하노이 탑 이동 순서
### 링크
[https://www.acmicpc.net/problem/11729][1]
### 문제
세 개의 장대가 있고 첫 번째 장대에는 반경이 서로 다른 n개의 원판이 쌓여 있다.
각 원판은 반경이 큰 순서대로 쌓여있다. 이제 수도승들이 다음 규칙에 따라 첫 번째 장대에서 세 번째 장대로 옮기려 한다.

한 번에 한 개의 원판만을 다른 탑으로 옮길 수 있다.
쌓아 놓은 원판은 항상 위의 것이 아래의 것보다 작아야 한다.
이 작업을 수행하는데 필요한 이동 순서를 출력하는 프로그램을 작성하라. 단, 이동 횟수는 최소가 되어야 한다.
### 입력
첫째 줄에 첫 번째 장대에 쌓인 원판의 개수 N (1 ≤ N ≤ 20)이 주어진다.
### 출력
첫째 줄에 옮긴 횟수 K를 출력한다.
두 번째 줄부터 수행 과정을 출력한다. 두 번째 줄부터 K개의 줄에 걸쳐 두 정수 A B를 빈칸을 사이에 두고 출력하는데, 이는 A번째 탑의 가장 위에 있는 원판을 B번째 탑의 가장 위로 옮긴다는 뜻이다.
### 코드
```python
def hanoi(move_list,num,start,middle,end):
  # 판이 한개일때의 처리
  if num==1:
    # 시작점에서 끝점으로 판을 이동
    move_list.append(start+" "+end)
  else:
    #num개 짜리 문제를 풀기전에
    #num-1개 짜리 하노이탑을 시작점에서 중간점으로 옮기는 문제를 풀어야한다.
    hanoi(move_list,num-1,start,end,middle)
    #맨밑에 있던 판을 시작점에서 끝점으로 옮긴다.
    move_list.append(start+" "+end)
    #num-1개 짜리 하노이탑을 중간점에서 끝점으로 옮기는 문제를 풀어야한다.
    hanoi(move_list,num-1,middle,start,end)

# 판의 갯수 입력받기
Int_NumberOfDiscs=int(input())
# 판의 이동을 저장할 빈 리스트 생성
move_list=[]
# 하노이탑 문제 풀기
hanoi(move_list,Int_NumberOfDiscs,"1","2","3")

# 이동횟수 출력
print(len(move_list))
# 이동내역 출력
for item in move_list:
  print(item)
```

## 1004번 어린왕자
### 링크
[https://www.acmicpc.net/problem/1004][2]
### 문제
어린 왕자는 소혹성 B-664에서 자신이 사랑하는 한 송이 장미를 위해 살아간다. 어느 날 장미가 위험에 빠지게 된 것을 알게 된 어린 왕자는, 장미를 구하기 위해 은하수를 따라 긴 여행을 하기 시작했다. 하지만 어린 왕자의 우주선은 그렇게 좋지 않아서 행성계 간의 이동을 최대한 피해서 여행해야 한다. 아래의 그림은 어린 왕자가 펼쳐본 은하수 지도의 일부이다.

![이미지][3]

빨간 실선은 어린 왕자가 출발점에서 도착점까지 도달하는데 있어서 필요한 행성계 진입/이탈 횟수를 최소화하는 경로이며, 원은 행성계의 경계를 의미한다. 이러한 경로는 여러 개 존재할 수 있지만 적어도 3번의 행성계 진입/이탈이 필요하다는 것을 알 수 있다.


위와 같은 은하수 지도, 출발점, 도착점이 주어졌을 때 어린 왕자에게 필요한 최소의 행성계 진입/이탈 횟수를 구하는 프로그램을 작성해 보자. 행성계의 경계가 맞닿거나 서로 교차하는 경우는 없다. 또한, 출발점이나 도착점이 행성계 경계에 걸쳐진 경우 역시 입력으로 주어지지 않는다.
### 입력
입력의 첫 줄에는 테스트 케이스의 개수 T가 주어진다. 그 다음 줄부터 각각의 테스트케이스에 대해 첫째 줄에 출발점 (x1, y1)과 도착점 (x2, y2)이 주어진다. 두 번째 줄에는 행성계의 개수 n이 주어지며, 세 번째 줄부터 n줄에 걸쳐 행성계의 중점과 반지름 (cx, cy, r)이 주어진다.
### 출력
각 테스트 케이스에 대해 어린 왕자가 거쳐야 할 최소의 행성계 진입/이탈 횟수를 출력한다.
### 코드
```python
# 출발점 O 도착점 O False
# 출발점 1 도착점 O True
# 출발점 O 도착점 1 True
# 출발점 1 도착점 1 False

#boolA와 boolB간의 xor연산을 하는 함수
def xor(boolA,boolB):
  if boolA==False and boolB==False:
    return False
  elif boolA==True and boolB==True:
    return False
  else:
    return True

#점A(ax,ay)와 점B(bx,by)사이의 거리를 구하는 함수
def distance(ax,ay,bx,by):
  return((bx-ax)**2+(by-ay)**2)**(1/2)

Int_NumberOfTestCases=int(input())
for i in range(Int_NumberOfTestCases):
  # 진입 이탈 횟수 카운터 만들기
  count=0
  # 시작점 도착점 좌표 받기
  list_startNend=list(map(int,input().split(" ")))
  # 앞에 두개 시작점에 저장
  start_point=list_startNend[:2]
  # 뒤에 두개 도착점에 저장
  end_point=list_startNend[2:]
  # 행성계 갯수 입력 받기
  Int_NumberOfPlanet=int(input())
  # 행성계 갯수 만큼 반복
  for j in range(Int_NumberOfPlanet):
    # 행성계 좌표와 반지름 받기 0,1 은 좌표 2는 반지름
    planet_info=list(map(int,input().split(" ")))
    # xor 조건을 위한 Boolean 값 설정
    #시작점을 포함하는지 True or False
    contains_start_point=distance(start_point[0],start_point[1],planet_info[0],planet_info[1])<planet_info[2]
    #도착점을 포함하는지 True or False
    contains_end_point=distance(end_point[0],end_point[1],planet_info[0],planet_info[1])<planet_info[2]
    # 둘중하나만 True면 카운터 늘리기
    if xor(contains_start_point,contains_end_point):
      count+=1
  # 카운터 출력
  print(count)
```
[1]:https://www.acmicpc.net/problem/11729
[2]:https://www.acmicpc.net/problem/1004
[3]:https://onlinejudgeimages.s3-ap-northeast-1.amazonaws.com/upload/201003/dfcmhrjj_113gw6bcng2_b.gif