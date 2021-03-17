# 10장 객체 리터럴

## 10.1 객체란?

* 자바스크립트는 객체 기반의 프로그래밍 언어이며, 자바스크립트를 구성하는 거의 "모든 것"이 객체다.
* 원시 값을 제외한 나머지 값(함수, 배열, 정규 표현식 등)은 모두 객체다.
* 원시 타입의 값, 즉 원시 값은 변경 불가능한 값이지만 객체 타입의 값, 즉 객체는 변경 가능한 값
* 객체는 0개 이상의 프로퍼티로 구성된 집합이며, 프로퍼티는 키와 값으로 구성
* 객체는 프로퍼티와 메서드로 구성된 집합체. 프로퍼티와 메서드의 역할은 다음과 같다.
   * 프로퍼티: 객체의 상태를 나타내는 값
   * 메서드: 프로퍼티를 참조하고 조작할 수 있는 동작
* 객체의 프로퍼티 값이 함수일 경우, 구분을 위해 메서드라 부른다.

## 10.2 객체 리터럴에 의한 객체 생성

* 프로토타입 기반 객체지향 언어로서 다양한 객체 생성 방법을 지원
   1. 객체 리터럴
   2. Object 생성자 함수
   3. 생성자 함수
   4. Object.create 메서드
   5. 클래스(ES6)

* 가장 일반적이고 간단한 방법은 객체 리터럴을 사용하는 방법이다.
* 객체 리터럴은 자바스크립트의 유연함과 강력함을 대표하는 객체 생성 방식이다.

```javascript
var person = {
    name: 'Lee',
    sayHello() {
        console.log(`Hello! My name is ${this.name}.`);
    },
};

console.log(typeof person); //object
console.log(person);        //{name: 'Lee', sayHello: f}, person.toString() 실행

//빈 객체를 생성하는 방법

var empty = {};
console.log(typeof empty);  //object
```

## 10.3 프로퍼티

* 객체는 프로퍼티의 집합이며, 프로퍼티의 키와 값으로 구성된다.
* 프로퍼티를 나열할 때는 쉼표(,)로 구분한다. 일반적으로 마지막 프로퍼티 뒤에는 쉼표를 사용하지 않으나 사용해도 좋다.(사용하는 것을 추천한다!!!)
   * [MDN 링크](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Trailing_commas)
   * [쓰면 좋은점](https://medium.com/@nikgraf/why-you-should-enforce-dangling-commas-for-multiline-statements-d034c98e36f8)
* 프로퍼티 키: 빈 문자열을 초함하는 모든 문자열 또는 심벌 값
* 프로퍼티 값: 자바스크립트에서 사용할 수 있는 모든 값
* 프로퍼티 키가 문자열안 경우 식별자 네이밍 규칙을 따르는 경우는 따옴표를 생략할 수 있다.

```javascript
var person = {
    firstName: 'Dongwoo',       //식별자 네이밍 규칙을 준수하는 프로퍼티 키
    'last-name': 'Seo',         //식별자 네이밍 규칙을 준수하지 않는 프로퍼티 키
};

var obj = {};
var key = 'hello';

obj[key] = 'world';             //키를 동적으로 생성하는 방법1
obj = {                         //키를 동적으로 생성하는 방법2
    [key]: 'world',
};
```

## 10.4 메서드

* 자바스크립트 함수는 일급 객체이다. 그렇기 때문에 프로퍼티의 값으로 사용 가능
* 메서드 내부에서 사용한 this 키워드는 객체 자신을 가리키는 참조 변수이다. 자세한 것은 뒤에..

```javascript
var circle = {
    radius: 5,
    getDiameter() {     //getDiameter: function() 을 줄여서 쓸 수 있다.
        return 2 * this.radius; //this는 circle을 가리킨다.
    }
}


console.log(circle.getDiameter());      //10
```

## 10.5 프로퍼티 접근

* 마침표 프로퍼티 접근 연산자(.)를 사용하는 마침표 표기법
* 대괄호 프로퍼티 접근 연산자([...])를 사영하는 대괄호 표기법
* 객체에 존재하지 않는 프로퍼티에 접근하면 undefined를 반환한다.

```javascript
var person = {
    name: 'Lee',
};

console.log(person.name);       //마침표 표기법
console.log(person['name']);    //대괄호 표기법

var person = {
    'last-name': 'Lee',
    1: 10,
};

person.'last-name';     //문법에러
person.last-name;       //NaN
person[last-name];      //문법에러
person['last-name'];    //Lee

person.1;               //에러
person.'1';             //에러
person[1];              //10
person['1'];            //10
```

## 10.6 프로퍼티 값 갱신

```javascript
var person = {
    name: 'Lee',
};

person.name = 'Seo';

console.log(person.name); // Seo
```

## 10.7 프로퍼티 동적 생성

```javascript
var person = {
    name: 'Lee',
};

person.age = 20;

console.log(person); // Seo {name: 'Lee', age: 20}
```

## 10.8 프로퍼티 삭제

```javascript
var person = {
    name: 'Lee',
};

person.age = 20;
delete person.age;

console.log(person);        //{name:'Lee'}
```

## 10.9 ES6에서 추가된 객체 리터럴의 확장 기능

### 10.9.1 프로퍼티 축약 표현

```javascript
//ES5

var x=1, y=2;
var obj = {
    x: x,
    y: y,
};

//es2015+
var obj = {
    x,
    y,
};
```

### 10.9.2  계산된 프로퍼티 이름

```javascript
//es5

var prefix = 'prop';
var i = 0;

var obj = {};

ojb[prefix + '-' + ++i] = i;
ojb[prefix + '-' + ++i] = i;
ojb[prefix + '-' + ++i] = i;


//es2015+
const obj = {
    [prefix + '-' + ++i]: i,
    [prefix + '-' + ++i]: i,
    [prefix + '-' + ++i]: i,
}
```

### 10.9.3 메소드 축약 표현

```javascript
//ES5
var obj = {
    name: 'Lee',
    sayHi: function() {
        
    }
}

//es2015+
const obj = {
    name: 'Lee',
    sayHi() {
        
    }
}

```
