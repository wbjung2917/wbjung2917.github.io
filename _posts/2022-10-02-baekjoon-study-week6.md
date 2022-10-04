---
layout: post
title: 백준 단계별 문제풀이 스터디 6주차
subtitle:
author: 정우빈
categories: Study
tags: [python]
---

## 10828번 스택

### 링크
[https://www.acmicpc.net/problem/10828][1]

### 문제
정수를 저장하는 스택을 구현한 다음, 입력으로 주어지는 명령을 처리하는 프로그램을 작성하시오.

명령은 총 다섯 가지이다.

push X: 정수 X를 스택에 넣는 연산이다.  
pop: 스택에서 가장 위에 있는 정수를 빼고, 그 수를 출력한다. 만약 스택에 들어있는 정수가 없는 경우에는 -1을 출력한다.  
size: 스택에 들어있는 정수의 개수를 출력한다.  
empty: 스택이 비어있으면 1, 아니면 0을 출력한다.  
top: 스택의 가장 위에 있는 정수를 출력한다. 만약 스택에 들어있는 정수가 없는 경우에는 -1을 출력한다.  

### 입력
첫째 줄에 주어지는 명령의 수 N (1 ≤ N ≤ 10,000)이 주어진다. 둘째 줄부터 N개의 줄에는 명령이 하나씩 주어진다. 주어지는 정수는 1보다 크거나 같고, 100,000보다 작거나 같다. 문제에 나와있지 않은 명령이 주어지는 경우는 없다.

### 출력
출력해야하는 명령이 주어질 때마다, 한 줄에 하나씩 출력한다.
### 코드
```python
#list를 활용한 구현
import sys

class Stack:

  #Stack 생성시 초기화 stack_values에 빈리스트를 할당
  def __init__(self):
    self.stack_values = []

  #stack_values에 item을 append
  def push(self,item):
    self.stack_values.append(item)

  #stack_values의 맨 끝 항목을 리턴하고 삭제 
  def pop(self):
    if self.stack_values:
      pop_value=self.stack_values[-1]
      del self.stack_values[-1]
      return pop_value
      #return self.stack_values.pop() 팝으로 구현하는법

    #만약 stack_values가 빈리스트이면 -1리턴
    else:
      return -1

  #stack_values의 길이를 출력
  def size(self):
    return len(self.stack_values)

  #stack_values가 비었으면 1 아니면 0
  def empty(self):
    if self.stack_values:
      return 0
    else:
      return 1

  #stack_values의 맨 뒤 요소를 리턴
  def top(self):
    if self.stack_values:
      return self.stack_values[-1]
    #만약 stack_values가 비었으면 -1리턴
    else:
      return -1

#명령 갯수를 입력받는다.
NumberOfLines=int(sys.stdin.readline())
#스택을 하나 만든다.
My_Stack=Stack()
#명령 갯수만큼 반복하며 명령을 실행한다.
for i in range(NumberOfLines):
  #명령을 공백으로 split
  command=sys.stdin.readline().strip().split(" ")
  #명령이 push일때 명령의 숫자를 push
  if command[0]=="push":
    My_Stack.push(int(command[1]))
  #명령이 pop일때 pop
  elif command[0]=="pop":
    print(My_Stack.pop())
  #명령이 size일때 size
  elif command[0]=="size":
    print(My_Stack.size())
  #명령이 empty일때 empty
  elif command[0]=="empty":
    print(My_Stack.empty())
  #명령이 top일때 top
  elif command[0]=="top":
    print(My_Stack.top())
```

## 18258번 큐 2

### 링크
[https://www.acmicpc.net/problem/18258][2]

### 문제
정수를 저장하는 큐를 구현한 다음, 입력으로 주어지는 명령을 처리하는 프로그램을 작성하시오.

명령은 총 여섯 가지이다.

push X: 정수 X를 큐에 넣는 연산이다.  
pop: 큐에서 가장 앞에 있는 정수를 빼고, 그 수를 출력한다. 만약 큐에 들어있는 정수가 없는 경우에는 -1을 출력한다.  
size: 큐에 들어있는 정수의 개수를 출력한다.  
empty: 큐가 비어있으면 1, 아니면 0을 출력한다.  
front: 큐의 가장 앞에 있는 정수를 출력한다. 만약 큐에 들어있는 정수가 없는 경우에는 -1을 출력한다.  
back: 큐의 가장 뒤에 있는 정수를 출력한다. 만약 큐에 들어있는 정수가 없는 경우에는 -1을 출력한다.  

### 입력
첫째 줄에 주어지는 명령의 수 N (1 ≤ N ≤ 2,000,000)이 주어진다. 둘째 줄부터 N개의 줄에는 명령이 하나씩 주어진다. 주어지는 정수는 1보다 크거나 같고, 100,000보다 작거나 같다. 문제에 나와있지 않은 명령이 주어지는 경우는 없다.

### 출력
출력해야하는 명령이 주어질 때마다, 한 줄에 하나씩 출력한다.
### 코드1
```python
#linked_list를 사용해 구현하는 방법
import sys

#Node를 구현한다.
class Node:
  def __init__(self,data):
    #data를 저장할 공간
    self.data=data
    #다음노드를 가리킬 공간
    self.next=None

#Queue를 구현한다.
class Queue:
  #Queue초기화
  def __init__(self):
    #맨 앞 요소를 가리키는 포인터
    self.head=None
    #맨 뒤 요소를 가리키는 포인터
    self.tail=None
    #linked_list의 길이를 나타내는 변수
    self.length=0

  #push
  def push(self,item):
    #기존 길이가 0개일 때
    if self.length==0:
      #새 노드를 생성
      new_node=Node(item)
      # head랑 tail을 모두 새 노드를 가리키게 한다.
      self.head=new_node
      self.tail=new_node
      # length를 1늘인다.
      self.length+=1
    #기존 길이가 0개보다 클때(작을때는 없으므로)
    else:
      #새 노드를 생성
      new_node=Node(item)
      #tail이 가리키는 노드의 next에 새노드를 저장
      self.tail.next=new_node
      #tail이 가리키는 노드를 새 노드로 바꿈
      self.tail=new_node
      # length를 1늘인다.
      self.length+=1

  #pop
  def pop(self):
    #길이가 0일때는 -1을 리턴
    if self.length==0:
      return -1
    #길이가 존재하면
    else:
      #pop_value에 맨앞의 값을 저장
      pop_value=self.head.data
      #head가 가리키는 노드를 head의 next노드로 변경
      self.head=self.head.next
      #없앤 head가 마지막 요소였을때 tail도 None으로 변경
      if self.head==None:
        self.tail=None
      #length를 1줄인다.
      self.length-=1
      #아까 저장해둔 pop_value를 리턴
      return pop_value

  #size 
  def size(self):
    #length를 리턴
    return self.length

  #empty
  def empty(self):
    #큐가 비었으면 1 아니면 0
    if self.head==None:
      return 1
    else:
      return 0

  #front
  def front(self):
    #큐가 비었으면 -1  리턴 아니면 head의 data 리턴
    if self.head==None:
      return -1
    else:
      return self.head.data

  #back
  def back(self):
    #큐가 비었으면 -1  리턴 아니면 tail의 data  리턴
    if self.head==None:
      return -1
    else:
      return self.tail.data

#명령의 갯수 저장
NumberOfLines=int(sys.stdin.readline())
#큐 생성
My_Queue=Queue()
#명령의 갯수만큼 반복
for i in range(NumberOfLines):
  #명령을 공백으로 split
  command=sys.stdin.readline().strip().split(" ")
  #명령이 push일때 명령의 숫자를 push
  if command[0]=="push":
    My_Queue.push(int(command[1]))
  #명령이 pop일때 pop
  elif command[0]=="pop":
    print(My_Queue.pop())
  #명령이 size일때 size
  elif command[0]=="size":
    print(My_Queue.size())
  #명령이 empty일때 empty
  elif command[0]=="empty":
    print(My_Queue.empty())
  #명령이 front일때 front
  elif command[0]=="front":
    print(My_Queue.front())
  #명령이 back일때 back
  elif command[0]=="back":
    print(My_Queue.back())
```

### 코드2
```python
#deque를 사용해 구현하는 방법
from collections import deque
import sys

#Queue를 구현
class Queue:
  #Queue초기화
  def __init__(self):
    #deque객체인 queue_list를 생성
    self.queue_list=deque()

  #push
  def push(self,item):
    #queue_list에 item을 append
    self.queue_list.append(item)

  #pop
  def pop(self):
    #queue_list가 비어있지 않다면 popleft()로 맨 앞 요소를 제거하며 리턴
    if self.queue_list:
      return self.queue_list.popleft()
    #queue_list가 비어있다면 -1을 리턴
    else:
      return -1

  #size
  def size(self):
    #queue_list의 길이를 리턴
    return len(self.queue_list)

  #empty
  def empty(self):
    #queue_list가 비어있지 않다면 0 리턴
    if self.queue_list:
      return 0
    #queue_list가 비어있다면 1 리턴
    else:
      return 1

  #front
  def front(self):
    #queue_list가 비어있지 않다면 맨앞의 요소를 리턴
    if self.queue_list:
      return self.queue_list[0]
    #queue_list가 비어있다면 -1 리턴
    else:
      return -1

  #back
  def back(self):
    #queue_list가 비어있지 않다면 맨 뒤의 요소를 리턴
    if self.queue_list:
      return self.queue_list[-1]
    #queue_list가 비어있다면 -1 리턴
    else:
      return -1

#명령의 갯수 저장
NumberOfLines=int(sys.stdin.readline())
#큐 생성
My_Queue=Queue()
#명령의 갯수만큼 반복
for i in range(NumberOfLines):
  #명령을 공백으로 split
  command=sys.stdin.readline().strip().split(" ")
  #명령이 push일때 명령의 숫자를 push
  if command[0]=="push":
    My_Queue.push(int(command[1]))
  #명령이 pop일때 pop
  elif command[0]=="pop":
    print(My_Queue.pop())
  #명령이 size일때 size
  elif command[0]=="size":
    print(My_Queue.size())
  #명령이 empty일때 empty
  elif command[0]=="empty":
    print(My_Queue.empty())
  #명령이 front일때 front
  elif command[0]=="front":
    print(My_Queue.front())
  #명령이 back일때 back
  elif command[0]=="back":
    print(My_Queue.back())
```

## 당면한 문제
### 시간초과
#### input() vs sys.stdin.readline()
- **input()**  
input()은 prompt에 문자열을 화면에 출력한다.  
input()은 하나씩 누를 때마다 대응하는 데이터가 버퍼에 쌓인다.  
입력 우측에 붙는 개행 문자를 제거한다.  

- **sys.stdin.readline()**  
sys.stdin.readline()은 prompt에 출력하지 않는다.  
sys.stdin.readline()은 입력을 한번에 읽어 한번에 버퍼로 집어넣는다.  
입력 우측에 붙는 개행 문자가 포함된다. 그래서 strip()이나 rstrip()과 함께 쓰인다.

#### list와 linked list, deque
list는 맨 앞 요소의 pop연산 실행 시 맨 앞 요소를 지우고 나머지 요소를 앞으로 한 칸씩 이동하는 과정을 거친다. 때문에 시간복잡도가 $ O(n) $이다.  
반면 linked list와 deque는 head가 가리키는 노드만 한칸 옮겨주는 연산으로 이를 해결할 수 있으므로 시간복잡도가  $ O(1) $이 된다.  
이 과정에서 시간적으로 차이가 발생한다. 그렇기 때문에 popleft연산을 사용하는 자료구조를 만들 때에는 linked list형태나 deque를 활용한 코드의 사용이 좋다.

[1]:https://www.acmicpc.net/problem/10828
[2]:https://www.acmicpc.net/problem/18258