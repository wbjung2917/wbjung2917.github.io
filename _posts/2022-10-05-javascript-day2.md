---
layout: post
title: JavaScript 강의 2일차
subtitle:
author: 정우빈
categories: Lecture
tags: [JavaScript]
---

## 자료형

---

### JavaScript에서의 자료형 확인
```javascript
let typesArray=[undefined,0,10n,true,"foo",Symbol("id"),Math,null,alert];
for(i=0;i<typesArray.length;i++){
    console.log(typeof typesArray[i]);
}
/*
실행결과
"undefined"
"number"
"bigint"
"boolean"
"string"
"symbol"
"object"
"object"
"function"
*/
```

### JavaScript에서의 형변환
```javascript
console.log("123"+456); // 456이 string으로 자동형변환 되어서 123456이 됨
console.log(parseInt("123")+456); // 579
```
이 외에 여러 형변환 함수들이 있다.
- parseFloat(x)
- Number(x)
- x.toString(진법)
- x.toFixed(소숫점자리수) - 기본은 0자리
- String(x)

## 연산

---

### JavaScript에서의 숫자연산
```javascript
let a=10, b=2;
console.log(a+b); //12
console.log(a-b); // 8
console.log(a*b); // 20
console.log(a/b); // 5
console.log(a%b); // 0
console.log(a++); // 10
console.log(a); // 11
console.log(--a); // 10
console.log(a); // 10
```

### JavaScript에서의 문자연산
```javascript
let [a,b,c]=["나는", "정우빈", "입니다."];
console.log(a+b+c);
```

### JavaScript에서의 비트연산
```javascript
//and연산
console.log(true & true);//1
console.log(true & false);//0
console.log(false & true);//0
console.log(false & false);//0
//or연산
console.log(true | true);//1
console.log(true | false);//1
console.log(false | true);//1
console.log(false | false);//0
//xor연산
console.log(true ^ true);//0
console.log(true ^ false);//1
console.log(false ^ true);//1
console.log(false ^ false);//0
//기타연산
console.log(4 << 1);//8
console.log(4 >> 1);//2
console.log(~4);//-5 ~~~ 1111 1111 1111 1011
console.log(~-5);//4 ~~~ 0000 0000 0000 0100
console.log(5&4); //101 & 100 = 100 그러므로 4
```

### JavaScript에서의 비교연산
```javascript
console.log(4>1);//True
console.log(4<1);//False
console.log(4==1);//False
console.log(4=='4');//True
console.log(4===4);//True
console.log(true&&false);//false
console.log(true||false);//True
```
## 함수

---

### Javascript에서의 함수
```javascript
    function 함수명(매개변수){
        함수내용
    }

    let 함수명 = (매개변수) => {
        함수내용
    }
```

### 콜백함수
```javascript
    function 함수명(매개변수, 콜백함수){
        함수내용
    }

    함수명(매개변수값, function (매개변수) {함수내용});
```

## JavaScript실습

---

### 예제 1
```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>예제1</title>
  </head>
  <body>
    <table>
      <tr id="name"></tr>
      <tr id="age"></tr>
    </table>
    <script>
      let nameArray=["이름1","이름2","이름3","이름4"];
      let ageArray=[11,23,45,67];
      for(i=0;i<nameArray.length;i++){
        console.log(`이름 : ${nameArray[i]}, 나이 : ${ageArray[i]}`);
        let nameTd=document.createElement("td"), ageTd=document.createElement("td");
        nameTd.innerHTML=nameArray[i];
        ageTd.innerHTML=ageArray[i];
        document.getElementById("name").append(nameTd);
        document.getElementById("age").append(ageTd);
      }
    </script>
  </body>
</html>
```

### 예제 2
```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>예제1</title>
  </head>
  <body>
    <table>
      <tr id="name"></tr>
      <tr id="age"></tr>
    </table>    
    <script>
      //i가 0~2까지반복
      for(let i=0;i<3;i++){
        //j가 0~2까지반복
        for(let j=0;j<3;j++){
          //콘솔에 i and j 출력
          console.log(`${i} and ${j}`);
          //j가 1이면 alert로 알림창 출력하고 break
          if(j==1){        
            alert(`${i} and ${j}`);
            break;
          }
        }//break로 여기만 빠져나옴
      }
    </script>
  </body>
</html>
```

### 예제 3
```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>예제1</title>
  </head>
  <body>
    <table>
      <tr id="name"></tr>
      <tr id="age"></tr>
    </table>    
    <script>
      function xnor(bool1,bool2){
        if((bool1==true && bool2==true)||(bool1==false && bool2==false)){
            return 1;
        }
        else{
            return 0;
        }
      }
      console.log(xnor(0,0)); //1
      console.log(xnor(1,0)); //0
      console.log(xnor(0,1)); //0
      console.log(xnor(1,1)); //1
    </script>
  </body>
</html>
```
### 예제 4
```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>예제1</title>
  </head>
  <body>
    <table>
      <tr id="name"></tr>
      <tr id="age"></tr>
    </table>    
    <script>
      let xnor = (bool1,bool2)=>{
        if((bool1==true && bool2==true)||(bool1==false && bool2==false)){
            return 1;
        }
        else{
            return 0;
        }
      }
      console.log(xnor(0,0)); //1
      console.log(xnor(1,0)); //0
      console.log(xnor(0,1)); //0
      console.log(xnor(1,1)); //1
    </script>
  </body>
</html>
```