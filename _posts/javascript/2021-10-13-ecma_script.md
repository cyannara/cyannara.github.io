---
title: "ecma script"
date: 2021-10-13
categories: javascript  
---

## 참고사이트

* [모질라 자바스크립 가이드](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide){:target="_blank"}
* [모던자바스크립트 Deep Dive(이웅모)](https://poiemaweb.com/js-introduction){:target="_blank"}
* [모던 JavaScript 튜토리얼](https://ko.javascript.info/){:target="_blank"}
* [w3schools](http://w3schools.com){:target="_blank"}
* [developer-readmap](https://github.com/kamranahmedse/developer-roadmap){:target="_blank"} [developer-readmap](https://roadmap.sh/)
* [ecma standard](https://www.ecma-international.org/publications-and-standards/standards/ecma-262/){:target="_blank"}
* [fetch 모질라](https://developer.mozilla.org/ko/docs/Web/API/Fetch_API/Using_Fetch){:target="_blank"}

## 자바스크립트 버전 [(참고사이트)](https://www.greycampus.com/blog/programming/java-script-versions){:target="_blank"}

* ES5    = ES5(2009년) : callback/JSON/getter,setter/Date.now() 
* ES2015 = ES6 : let/const/Arrow funtion/for~of/default,rest parameter/spread operator(...)/template literal/promise/Map/Set/Module/Symbol/class
* ES2016 = ES7 : **(연산자)/array includes()
* ES2017 = ES8 : async,await/str.padStart(),padEnd()/Object.values()/Object.entries()/ trailing commas
* ES2018 = ES9 : rest properties(...)
* ES2019 = ES10
* ES2020 = ES11
* 매년 6월에 새 버전이 나옴
* eclipse는 EcmaScript 6을 지원RRR
* `바벨(Babel)` : 자바스크립트 코드를 구 표준을 준수하는 코드로 바꿔줌. async/await를 지원하지 않는 브라우저를 만나면 Babel은 이전 브라우저에서 작동하는 polyfill를 자동으로 제공합니다.
* `폴리필(polyfill)` : 변경된 표준을 준수할 수 있게 기존 함수의 동작 방식을 수정하거나, 새롭게 구현한 함수의 스크립트를 폴리필이라 부름. 구현이 누락된 새로운 기능을 메꿔주는 역할.

## 예약어

arguments / await / break / case / catcl / class / const / debuffer / default / delete / do / else / enum / eval / export / extends / false / finally / for / function / if / implements / import / in / Infinity / instanceof / interface / let / NaN / null / package / private / protected / public / return / static / super / switch / this / /throw / true / typeof / undefined / var / void / while / with / yield

## 원시형 데이터 타입과 참조형 데이터 타입

* 원시형 데이터 타입 : 숫자형/문자형('')/불리언(true,false)/심볼형/null/undefined
* `심볼형` : 문자열 안지를 받아 고유한 키 값을 생성. 같은 인자를 넘겨도 다른 키 값이 생성. 객체의 속성 키로 사용함.Symbile('문자값') 
* 참조형 데이터 타입 : 객체(함수, 배열, 맵, 집합)


## 변수선언

* `const` : 상수선언. 값 변경불가. 객체나 배열의 원소값은 변경 가능 
* `let` : 변수가 사용되는 scope가 존재. 중복선언 방지.  hoisting 안됨
* `var` : 전역객체 속성이 생성되어 전역객체로 접근. hoisting됨
* `호이스팅` : 미선언변수 사용으로 인한 오류를 방지하기 위해서 선언하기 전에 사용한 변수는 호이스팅에 의해 위로 끌어 올려져 선언되지만 초기화는 하지 않음. (2장8절 참조)

```javascript
let cnt = 10;      // 중복선언 방지(err msg : Identifier 'XXX' has already been declared)
const init = 10;   // 상수선언. 값 변경불가(err msg : Assignment to constant variable)
const obj = { };   // 상수선언. 값(타입) 변경불가. 객체나 배열의 원소값은 변경 가능
```

![var](./img/var01.png)  

## 연산자
* 널 병합 연산자(??) : 왼쪽 피연산자가 null 또는 undefiened 일 때 오른쪽 피연산자를 반환하고 아니면 왼쪽 피연산자를 반환 ( nvl 함수와 같음)  
* 널 병합 할당 연산자(??=) : 위와 같음.  
   
```javascript
car.speed ??= 10;                 // car.speed 가 없으면 car.speed 속성에 10으로 할당
let speed = car.speed ?? 10;      // car.speed 가 없으면 speed 변수에 10으로 할당
```
* typeof : number, string, object, boolean, function, undefined, symbol, bigint, null
* 
```
  <script>

   let v1 = 10.5;   //number
   let v2 = "good"; //string
   let v3 = new String("morining");  //object
   let v4 = {};  //object
   let v5 = [];  //object
   let v6 = true; //boolean
   let v7 = ()=>{} ;  //function

   console.log(v1, typeof v1)
   console.log(v2, typeof v2)
   console.log(v3, typeof v3)
   console.log(v6, typeof v6)
   console.log(v7, typeof v7)
  
   console.log("변수선언안한경우", typeof num)
  </script>
```
  
## 모듈
* [참고사이트](https://velog.io/@jjunyjjuny/ES-Modules-%EC%A0%95%EB%A6%AC%ED%95%98%EA%B8%B0){:target="_blank"}
* `캡슐화` : 모듈 안의 모든 기능들은 모듈 안에서만 동작하며, 모듈 밖에서는 접근이 허용된 속성이나 메서드만 사용가능
* 모듈의 변수, 함수 클래스 등은 `export` 키워드로 노출하고 `import`로 가져다 사용한다.
* 파일 단위로 모듈이 구성되며 코드 묶음 단위이다.
* ES5에서는 모듈 개념이 없어서 즉시실행함수를 사용했음  
* 모듈은 순환참조할 수 없다.
* IE 브라우저는 지원안함.
* 테스트하려면 서버환경에서 필요함
* 모듈도 하나의 객체로서 임포트 시점에 모듈객체의 참조 주소를 변수에 할당

```js
//1. default 키워드로 모듈의 반환기본값 설정 (모듈 하나만 임포트) 
import defaultModule from './18_module.js'
```

```js
//2. 임포트할 모듈을 {}에 나열
import {moduleA, moduleB, moduleC} from './18_module.js'
console.log(moduleA)
moduleB('module run~~');
const modulec = new moduleC();
```

```js
//3. 모든 모듈을 불러올 경우 반드시 새 모듈 이름을 지정 
import * as myModule from './18_module.js'
console.log(myModule.moduleA)
myModule.moduleB('module run~~');
const modulec = new myModule.moduleC();
```

```js
export const moduleA = 'moduleA';
export function moduleB(msg){
    console.log('msg:'+ msg);
}
export class moduleC{
    constructor() {
        console.log('module C');
    }
}
```

```js
export {moduleA, moduleB, moduleC}
```
