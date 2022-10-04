---
layout: post
title: JavaScript 강의 1일차
subtitle:
author: 정우빈
categories: Lecture
tags: [JavaScript]
---

## 환경설정

---

### Node Js설치

https://nodejs.org/ko/download/


### 익스프레스 설치

npm i -g express-generator

### 프로젝트 생성

express jsproject --view=pug 

### node_modules등 기타 파일생성

npm install

### 프로젝트 실행

npm start

npm start 후 브라우저 주소창 : http://localhost:3000 or http://127.0.0.1:3000

### vscode 확장 설치

1. prettier
2. javascript 첫번째
3. auto close tag
4. live server

## JavaScript

---

### JavaScript란? 

특정 웹에 생동감을 불어넣어 동적인 페이지로 만들어주는 아이

### JavaScript의 강점

html안에서 스크립트라는 키워드로 js, css등의 작업을 동시에 할 수 있다.(통합성)

### JavaScript의 단점

### JavaScript 엔진의 종류

크롬, 오페라 - V8  
파이어폭스 - 스파이더몽키  
익스플로러 - 트라이던트, 샤크라  
엣지 - 샤크라코어  
사파리 - 시퀴럴피쉬

### JavaScript 엔진의 역할

 - 파싱
 - V8이 스크립트를 읽어들여서 기계어로 변환(컴파일)
 - 엔진 최적화
 - 언어종류
 - 가비지 컬렉션

### JavaScript가 브라우저에서 할 수 있는 일

지금 배우는것은 모던 JavaScript이지만 과거의 문법이 남아있다.  
(why? for 하위 호환성 유지를 위해)  
예전의 JavaScript는 low level을 직접 조작하지 못해 안전한 코드였다.  
Node Js가 등장하며 상황이 약간 달라졌다.

- JavaScript는 웹조작, 클라이언트, 서버간의 상호작용 등을 주로 담당할 수 있다.
- 이벤트 조작 또한 가능하다.(ajax활용)
- 쿠키(브라우저) 값을 가져오거나 설정, 사용자에게 메시지 전송

### JavaScript가 브라우저에서 할 수 없는 일

- 서버측 작업을 할 수 없었는데 Node Js로 어느정도 가능해 짐
- 브라우저 탭 간에 상호 독립적이기 때문에 제약이 있다.
- (보안)정책상 제약이 있을 수 있다.

이런 부분을 extension등으로 우회할 방법이 있긴하다.

### HTML에 스크립트 적용법
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta http-equiv="X-UA-Compatible" content="IE=edge" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Hello Wrold</title>
        <!-- 외부스크립트 -->
        <script src="padth/to/script.js"></script>
        <script src="https://urltoscript.com"></script>
    </head>
    <body>
        <!-- 내부스크립트 -->
        <script>
            console.log("hello world! console.log")
            alert("hello world! alert");
        </script>
        <h1>hello world! h1</h1>
    </body>
</html>
```

### BootStrap 적용 실습
```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Bootstrap demo</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-Zenh87qX5JnK2Jl0vWa8Ck2rdkQ2Bzep5IDxbcnCeuOxjzrPF/et3URy9Bv1WTRi" crossorigin="anonymous">
  </head>
  <body>
    <h1>Hello, world!</h1>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-OERcA2EqjJCMA+/3y+gxIOqMEjwtxJY7qPCqsdltbNJuaOe923+mo//f6V8Qbsw3" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.6/dist/umd/popper.min.js" integrity="sha384-oBqDVmMz9ATKxIep9tiCxS/Z9fNfEXiDAYTujMAeBAsjFuCZSmKbSSUnQlmh/jp3" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.2/dist/js/bootstrap.min.js" integrity="sha384-IDwe1+LCz02ROU9k972gdyvl+AESN10+x7tBKgc9I5HFtuNz0wWnPclzo6p9vxnk" crossorigin="anonymous"></script>
  </body>
</html>
```

## JavaScript문법

---

### JavaScript에서의 변수선언
```javascript
// 중복선언 O, 재할당 O
var a=0;
// 중복선언 X, 재할당 O
let b=1;
// 중복선언 X, 재할당 X, 반드시 선언과 동시에 초기화
const c=3;
```
- **호이스팅, 스코프**  
참고 : [https://www.howdy-mj.me/javascript/var-let-const/][1]

### JavaScript에서의 자료형
- Boolean(True or False)
- null(빈 값)
- undefined(값을 할당하지 않은 변수)
- Number(정수, 부동소수점, Infinity, NaN)
- String(문자열)

### JavaScript에서의 for문
```javascript
for(i=0;i<n;i++){
    console.log(i);
}
```

### JavaScript에서의 if문
```javascript
if(a>0){
    console.log("Positive");
} 
else if(a<0){
    console.log("Negative");
}
else{
    console.log("Zero");
}
```

### JavaScript에서의 주석처리
```javascript
// 이것은 한줄주석 입니다.
/* 
이것은 여러줄 주석입니다.
한번에 여러줄을 주석처리할 수 있습니다.
단축키는 Alt+Shift+A입니다.
*/
```

### use strict
```javascript
"use strict";
//선언없이 할당을 했으므로 에러가 남
//원래는 암묵적으로 이해해주지만 use strict가 에러를 유발
x=3.14;
```

[1]:https://www.howdy-mj.me/javascript/var-let-const/