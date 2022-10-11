---
layout: post
title: JavaScript 강의 3일차
subtitle:
author: 정우빈
categories: Lecture
tags: [JavaScript]
---

## Array, Dictionary

---

### Array
```javascript
let arrExample=[];
let arrExample=new Array();
let arrExample=[1,2,3,"히틀러","잔다르크"];
```

### Dictionary
```javascript
let dictExample={};

let dictExample={
    a: "apple",
    b: "banana",
    c: "cat",
    d: "dog"
};

let a="apple",b="banana";
let dictExample={a,b}
```

## 클래스와 객체

### 클래스 예제1
```javascript
class Car{
    constructor(wheel,sit) {
        this.numberOfWheels=wheel;
        this.numberOfSits=sit;
    }
    getNumberOfWheels(){
        return this.numberOfWheels;
    }
    setNumberOfWheels(num){
        this.numberOfWheels=num;
    }
    getNumberOfSits(){
        return this.numberOfSits;
    }
    setNumberOfSits(num){
        this.numberOfSits=num;
    }
    printCarInfo(){
        console.log(`바퀴수 : ${this.numberOfWheels}, 좌석수 : ${this.numberOfSits} 입니다.`)
    }
}

let car1=new Car(4,5);
car1.printCarInfo();
car1.setNumberOfSits(5);
car1.setNumberOfWheels(6);
console.log(car1.getNumberOfSits());
console.log(car1.getNumberOfWheels());
```

### 클래스 예제2
```javascript
const Car={
    numberOfWheels: 4,
    numberOfSits: 4,
    getNumberOfWheels: ()=>{
        return this.numberOfWheels;
    }
    setNumberOfWheels: (num)=>{
        this.numberOfWheels=num;
    }
    getNumberOfSits: ()=>{
        return this.numberOfSits;
    }
    setNumberOfSits: (num)=>{
        this.numberOfSits=num;
    }
    printCarInfo: ()=>{
        console.log(`바퀴수 : ${this.numberOfWheels}, 좌석수 : ${this.numberOfSits} 입니다.`)
    }
}

let car1=new Car();
car1.printCarInfo();
car1.setNumberOfSits(5);
car1.setNumberOfWheels(6);
console.log(car1.getNumberOfSits());
console.log(car1.getNumberOfWheels());
```