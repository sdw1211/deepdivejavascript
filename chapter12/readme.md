# 12장 함수

## 12.1 함수란?

* 일련의 과정을 문으로 구현하고 코드 블록으로 감싸서 하나의 실행 단위로 정의하는 것

```javascript
//함수 정의
function add(x, y) {        //x,y 를 매개변수(parameter)
    return x + y;           //반환값(return value)
}

//함수 호출
console.log(add(10, 11));   //10, 11을 인수(argument)
```

## 12.2 함수를 사용하는 이유

* 함수는 필요할 때 여러 번 호출할 수 있다.(코드의 재사용성)
* 유지보수의 편의성을 높이고 실수를 줄여 코드의 신뢰성을 높이는 효과가 있다.
* 함수는 객체 타입의 값이기 때문에 식별자(이름)을 붙일 수 있다. 이는 이 함수의 역할을 알 수 있기 때문에(물론 잘 지어야 가능하겠지만) 코드의 가독성을 향상시킬 수 있다.
* 코드는 개발자를 위한 문서이기 때문에, 사람이 이해할 수 있는 코드로 작성해야 한다. 사람이 이해하지 못하면 기계도 이해하지 못한다!!!

## 12.3 함수 리터럴

* 리터럴이란 사람이 이해할 수 있는 문자 또는 약속된 기호를 사용해 값을 생성하는 표기 방식을 말한다. 즉 값을 생성하기 위한 표기법이다.(5.2절 참고)
* 자바스크립트 함수는 객체 타입의 값이다. 따라서 함수도 함수 리터럴로 생성할 수 있다.
* 함수를 호출이 가능한 객체다.

```javascript
var f = function add(x,y) { //add는 생략할 수 있다.
    return x + y;
};
```

## 12.4 함수 정의

* 4가지 방법으로 함수를 정의할 수 있다.

```javascript
//함수 선언문
function add(x,y) {
    return x + y;
}

//함수 표현식
var add = function(x,y) {
    return x + y;
};

//Function 생성자 함수
var add = new Function('x', 'y', 'return x+y;');

//화살표 함수
var add = (x,y) => x + y;
```

## 12.4.1 함수 선언문

* 함수 이름 생략이 불가능
* 함수 선언문은 표현식이 아니고 문이다. 그래서 변수 할당이 불가능하다.
* 자바스크립트 엔진은 생성된 함수를 호출하기 위해 함수 이름과 동일한 이름의 식별자를 암묵적으로 생성하고, 거기에 함수 객체를 할당한다.

```javascript
function add(x,y) {
    return x + y;
}

console.log(add);       //  add(x,y)
console.log(add(2,5));  //  7
```

## 12.4.2 함수 표현식

* 일급 객체: 일급 객체가 되기 위해서는 3가지 조건이 있다.
   1. 변수나 데이터에 할당 할 수 있어야 한다.
   2. 객체의 인자로 넘길 수 있어야 한다.
   3. 객체의 리턴값으로 리턴 할 수 있어야 한다.
* 자바스크립트에서 함수는 일급 객체이다.
* 함수는 일급 객체이기 때문에 특정 변수에 할당을 할 수 있다. 이 때 함수를 함수 표현식이라고 부른다.
* 함수 리터럴의 경우 함수 이름 생략이 가능하다. 이런 함수를 익명함수라고 부른다.

```javascript
var add = function (x,y) {
    return x + y;
}
```

## 12.4.3 함수 생성 시점과 함수 호이스팅

```javascript
console.log(add);           //add(x,y)
console.log(sub);           //undefined

console.log(add(1,2));      //3
console.log(sub(2,1));      //함수 아니다 라는 에러

function add(x,y) {
    return x + y;
}

var sub = function(x,y) {
    return x + y;
};
```

* 함수 선언문의 정의한 함수와 함수 표현식으로 정의한 함수의 생성 시점이 다르기 때문이다.
* 함수 선언문이 코드의 선두로 끌어 올리진 것처럼 동작하는 자바스크립트 고유의 특징을 함수 호이스팅이라고 한다.
* 변수 할당문의 값은 할당문이 실행되는 시점, 즉 런타임에 평가되므로 함수 표현시의 함수 리터럴로 할당문이 실행되는 시점에 평가되어 함수 객체가 된다.

## 12.4.4 Function 생성자 함수

```javascript
var add = new Function('x', 'y', 'return x + y');
```

* 쓰지 말자(없는 셈 치자..)

## 12.4.5 화살표 함수

```javascript
const add = (x,y) => x + y;
```

* ES2015에서 도입된 화살표 함수는 function 키워드 대신 화살표를 사용해 좀 더 간략한 방법으로 함수를 선언할 수 있다.
* 화살표 함수는 생성자 함수로 사용할 수 없으며, 기존 함수와 this 바인딩 방식이 다르고, prototype 프로퍼티가 없으며 arguments 객체를 생성하지 않는다. 
* 자세한 것은 뒤에..

## 12.5 함수 호출

### 12.5.1 매개변수와 인수

* 함수를 실행하기 위해 필요한 값을 함수 외부에서 내부로 전달할 필요가 있는 경우, 매개변수를 통해 인수를 전달한다.
* 매개변수는 함수 몸체 내부에서만(스코프) 사용 할 수 있다.
* 함수는 매개변수의 개수와 인수의 개수가 일치하는지 체크하지 않는다. 인수가 부족한 경우 할당되지 않는 매개변수는 `undefined` 값이 할당된다.
* 매개변수보다 인수가 많을 경우 초과된 인수는 무시된다.
* 모든 인수는 암묵적으로 `arguments` 객체의 프로퍼티에 보관된다.

```javascript
function add(x,y) {             //x,y 매개변수
    return x + y;
}

var c = add(1,2);               //1,2는 인수
var d = add(1);                 //NaN y는 undefined
var f = add(3,4,5);             //7 5는 무시
```

### 12.5.2 인수 확인

* 자바스크립트 함수는 매개변수와 인수의 개수가 일치하는 확인하지 않는다.
* 자바스크립트 동적 타입언어이다. 따라서 자바스크립트 함수는 매개변수의 타입을 사전에 지정할 수 없다.
* 수동으로 체크 관련 로직을 넣어줘야 한다.
* 타입스크립트를 사용하게 되는 원인 중 하나.

```javascript
function add(a,b) {
    if (typeof a === 'number' && typeof b === 'number') {
        return a + b;
    }

    throw new TypeError('a,b는 숫자타입만 가능합니다.');
}

//초기화를 통한 방법
function add(a,b,c) {
    a = a || 0;
    b = b || 0;
    c = c || 0;

    return a + b + c;
}

//기본값 기능 활용하기
function add(a=0,b=0,c=0) {
    return a + b + c;
}
```

### 12.5.3 매개변수의 최대 개수

* 될 수 있으면 작게 만드는 것이 좋다.(최대 3개이상 쓸 경우에는 이유가 있어야 한다. 클린코드 50page 9줄)
* 3개 이상일 경우에는 `object`로 만들자. 이럼 순서와 상관 없어진다.

### 12.5.4 반환문

* 함수는 `return` 키워드와 표현식으로 이뤄진 반환문을 사용해 실행 결과를 함수 외부로 반환할 수 있다.
* `return` 이라는 키워드를 통해 자바스크립트에서 사용하는 모든 값을 반환할 수 있다.(함수도 반환 가능)
* 반환문은 함수 내부에서만 사용 가능하다.
* 반환문의 역할
   1. 반환문은 함수의 실행을 중단하고 함수 몸체를 빠져나간다.
   2. `return` 키워드 뒤에 오는 표현식을 평가해 반환한다.

```javascript
function multiply(x,y) {
    return x * y;
}

console.log(multiply(3,4));     //12
```

### 12.6 참조에 의한 전달과 외부 상태의 변경

* 객체 타입을 인수로 받을 경우 참조에 의한 전달 방식으로 전달 되기 때문에 외부에서 객체 타입의 값을 변경할 경우 함수의 결과 값이 변경될 수 있는 상황이 발생할 수 있다.
* 이런 경우 디버깅이 힘들기 때문에 이런 부분을 방지하기 위해서 객체 타입을 인수로 받는 경우 해당 인수를 불편 객체로 변환해주거나 깊은 복사 등의 기능을 활용해서 인수의 객체를 복사해서 사용하는 방식을 활용해야 한다.

## 12.7 다양한 함수의 형태

### 12.7.1 즉시 실행 함수

* 함수 정의와 함께 바로 시작되는 함수를 즉시 실행 함수라고 한다.
* 함수 이름이 없는 익명 함수를 사용하는 것이 일반적이다.
* 반드시 () 연산자로 감싸야 한다.

```javascript
(function() {
    var a = 2;
    var b = 3;
    return a + b;
}());

// function() {}(); 이것은 에러인데
// (function() {})(); 야들은 될까? 
// (function() {}());

// 번외로 10.toString();    //에러인데
// 10..toString();        //왜 될까?
```

https://262.ecma-international.org/11.0/#sec-expression-statement
https://262.ecma-international.org/11.0/#sec-tonumber-applied-to-the-string-type

### 12.7.2 재귀 함수

* 함수가 자기 자신을 호출하는 것을 재귀 호출이라고 한다.
* 자기 자신을 호출하는 행위, 즉 재귀 호출을 수행하는 함수를 말한다.
* 탈출 조건을 무조건 만들어야 한다. 안그러면 스택오버플로우가 발생한다.
* 재귀 함수를 활용한 소스는 이해하기가 어렵기 때문에 최대한 사용하지 않는 것을 추천한다.


```javascript

function countdown(n) {
    if (n < 0) return;
    console.log(n);
    countdown(n - 1);       //재귀 호출
}

```

### 12.7.3 중첩 함수

* 함수 내부에 정의된 함수를 중첩 함수 또는 내부 함수라 한다.
* 중첩 함수를 포함하는 함수는 외부 함수라고 한다.
* 외부 함수를 돕는 핼퍼 함수의 역할
* 자세한 것은 뒤에 배웁시다.

```javascript
function outer() {
    var x = 1;

    function inner() {
        var y = 2;
        console.log(x + y);
    }

    inner();
}

outer();
```

### 12.7.4 콜백 함수

* 함수의 매개변수를 통해 다른 함수의 내부로 전달되는 함수를 콜백 함수
* 매개 변수를 통해 함수의 외부에서 콜백 함수를 전달받는 함수를 고차 함수
* 고차 함수는 콜백 함수를 자신의 일부분으로 합성한다.
* 고차 함수는 매개 변수를 통해 전달받은 콜백 함수의 호출 시점을 결정해서 호출한다.
* 콜백 함수는 고차 함수에 의해 호출되며 이때 고차 함수는 필요에 따라 콜백 함수에 인수를 전달할 수 있다.

```javascript

function repeat(n, f) {
    for(var i=0, i < n; i++) {
        f(i);
    }
}

function logAll(value) {
    console.log(value);
}

function logOdds = function(value) {
    if (value % 2) {
        console.log(value);
    }
}


repeat(10, logAll);     //DI?   
repeat(20, logOdds);    //DI

```

### 12.7.5 순수 함수와 비순수 함수

* 함수형 프로그래밍에서는 어떤 외부 상태에 의존하지도 않고 변경하지도 않는, 즉 부수 효과가 없는 함수를 순수 함수라고 하고, 그 반대를 비순수 함수라고 한다.
* 순수 함수의 조건
   1. 동일한 인수에 언제나 동일한 값을 반환하는 함수
   2. 외부 상태를 변경하지 않는다

```javascript
//순수 함수 예
function increase(n) {
    return ++n;
}

console.log(increase(1)); 
console.log(increase(1)); 
console.log(increase(1)); 

console.log(increase({})); 
console.log(increase('wdwqdwqdqwd')); 
console.log(increase([])); 


//비 순수 함수 예

var a =10;

function increase() {
    return ++a;
}

console.log(increase(1)); 
console.log(increase(1)); 
console.log(increase(1)); 

console.log(increase({})); 
console.log(increase('wdwqdwqdqwd')); 
console.log(increase([])); 

function test(a,b) {
    return a+b;
}

var a = [1,2];
var c = [3,5];

test(1,2);
test(a,c);

```



























