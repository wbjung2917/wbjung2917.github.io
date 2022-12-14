---
layout: post
title: 백준 단계별 문제풀이 스터디 3주차
subtitle:
author: 정우빈
categories: Study
tags: [python]
---

## 1546번 평균
### 링크
[https://www.acmicpc.net/problem/1546][1]
### 문제
세준이는 기말고사를 망쳤다. 세준이는 점수를 조작해서 집에 가져가기로 했다. 일단 세준이는 자기 점수 중에 최댓값을 골랐다. 이 값을 M이라고 한다. 그리고 나서 모든 점수를 점수/M*100으로 고쳤다.

예를 들어, 세준이의 최고점이 70이고, 수학점수가 50이었으면 수학점수는 50/70*100이 되어 71.43점이 된다.

세준이의 성적을 위의 방법대로 새로 계산했을 때, 새로운 평균을 구하는 프로그램을 작성하시오.
### 입력
첫째 줄에 시험 본 과목의 개수 N이 주어진다. 이 값은 1000보다 작거나 같다. 둘째 줄에 세준이의 현재 성적이 주어진다. 이 값은 100보다 작거나 같은 음이 아닌 정수이고, 적어도 하나의 값은 0보다 크다.
### 출력
첫째 줄에 새로운 평균을 출력한다. 실제 정답과 출력값의 절대오차 또는 상대오차가 10-2 이하이면 정답이다.
### 코드
```python
# 입력값 변수에 저장
Int_NumberOfScores=int(input())
IntArr_Scores=list(map(int,input().split(" ")))

# 점수 최댓값 저장
Int_MaxScore=max(IntArr_Scores)

# 조작점수 총계 계산
TotalScore=0
for score in IntArr_Scores:
    TotalScore+=(score/Int_MaxScore)*100

# 조작점수 평균 계산
print(TotalScore/Int_NumberOfScores)
```

## 4344번 평균은 넘겠지
### 링크
[https://www.acmicpc.net/problem/4344][2]
### 문제
대학생 새내기들의 90%는 자신이 반에서 평균은 넘는다고 생각한다. 당신은 그들에게 슬픈 진실을 알려줘야 한다.
### 입력
첫째 줄에는 테스트 케이스의 개수 C가 주어진다.

둘째 줄부터 각 테스트 케이스마다 학생의 수 N(1 ≤ N ≤ 1000, N은 정수)이 첫 수로 주어지고, 이어서 N명의 점수가 주어진다. 점수는 0보다 크거나 같고, 100보다 작거나 같은 정수이다.
### 출력
각 케이스마다 한 줄씩 평균을 넘는 학생들의 비율을 반올림하여 소수점 셋째 자리까지 출력한다.
### 코드
```python
# 입력값 변수에 저장
Int_NumberOfCases=int(input())
CaseList=[]
for i in range(Int_NumberOfCases):
    CaseList.append(list(map(int,input().split(" "))))

# 각 케이스에 대해 실행
for case in CaseList:
    # 카운트 초기화
    count=0
    # 케이스 평균 계산
    Int_Average=sum(case[1:])/case[0]
    # 케이스의 요소별로 평균과 비교
    for score in case[1:]:
        if score>Int_Average:
        count+=1
    # 결과출력
    print(f"{(count/case[0])*100:.3f}%")
```
## 1065번 한수
### 링크
[https://www.acmicpc.net/problem/1065][3]
### 문제
어떤 양의 정수 X의 각 자리가 등차수열을 이룬다면, 그 수를 한수라고 한다. 등차수열은 연속된 두 개의 수의 차이가 일정한 수열을 말한다. N이 주어졌을 때, 1보다 크거나 같고, N보다 작거나 같은 한수의 개수를 출력하는 프로그램을 작성하시오.
### 입력
첫째 줄에 1,000보다 작거나 같은 자연수 N이 주어진다.
### 출력
첫째 줄에 1보다 크거나 같고, N보다 작거나 같은 한수의 개수를 출력한다.
### 코드
```python
def isHanSu(number):
    # 자리수 파악을 용이하게 하기위해 스트링으로 만들기
    Str_Number=str(number)
    # 한자리 or 두자리수는 무조건 한수
    if len(Str_Number)==1 or len(Str_Number)==2:
        return True
    # 그게 아니면 한수인지 판별
    else:
        # 제일 윗자리수와 다음자리수의 차이를 저장
        diff=int(Str_Number[0])-int(Str_Number[1])
        # 자릿수별로 아랫자리와 비교하여 등차가 깨지면 False
        for i in range(1,len(Str_Number)-1):
        if diff!=int(Str_Number[i])-int(Str_Number[i+1]):
            return False
        # 끝까지 다돌았으면 등차라는 거니까 True
        return True

# 입력값 변수에 저장
Int_Number=int(input())

# 카운트 초기화
count=0
# 1~Int_Number까지 반복
for i in range(1,Int_Number+1):
    # i 가 한수이면 count에 +1
    if isHanSu(i):
        count+=1
# 결과 출력
print(count)
```

[1]:https://www.acmicpc.net/problem/1546
[2]:https://www.acmicpc.net/problem/4344
[3]:https://www.acmicpc.net/problem/1065