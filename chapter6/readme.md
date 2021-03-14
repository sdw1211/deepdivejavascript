# 6장 데이터 타입

* 자바스크립트에는 7개의 데이터 타입을 제공, 7개의 타입은 원시 타입(primitive type)과 객체 타입(object/refrence type)으로 구분
   * 원시타입
       * 숫자 타입
       * 문자열 타입
       * 불리언 타입
       * undefined 타입
       * null 타입
       * 심벌 타입
    * 객체 타입
       * 객체
       * 배열
       * 함수 등등


## 6.1 숫자 타입

* 배정밀도 64비트 부동소수점 형식만 취급
* 즉 모든 소수는 실수로 처리되고, 정수만을 표현하기 위한 데이터 타입이 존재하지 않는다.
* 3가지의 특별한 값
   * Infinity:양의 무한대
   * -Infinity: 음의 무한대
   * NaN: 산술 연산 불가(not a number)

> [배정밀도 64비트 부동소수점 형식이란](https://vanillaani.tistory.com/6)

## 6.2 문자열 타입

* 0개 이상의 16비트 유니코드 문자(UTF-16)의 집합으로 전 세계 대부분의 문자를 표현할 수 있다.
* 문자열은 작음따음표(''), 큰따음표(""), 백틱(``)으로 텍스트를 감싸서 표현한다.
* 가장 일반적인 표기법은 작음따음표('')를 사용하는 것이다.

## 6.3 템플릿 리터럴

* ES6부터 생긴 새로운 문자열 표기법
* 백틱(``)을 사용해서 표현

### 6.3.1 멀티라인 문자열
```javascript
var template = `<ul>
    <li <a href="">HOME</a></li>
</ul>
`;

console.log(template);
```

### 6.3.2 표현식 삽입
```javascript
var first = 'Dongwoo';
var last = 'Seo';

console.log(`My name is ${first} ${last}`)
```

*`${}` 는 표현식을 감쌀 수 있다.

## 6.4 불리언 타입

* 논리적 참, 거짓을 나타내는 `ture`, `false` 값 뿐이다.

## 6.5 undefined 타입

* `undefined` 값이 유일
* 개발자가 의도적으로 할당하기 위한 값이 아니라 자바스크립트 엔진이 변수를 초기화할 떄 사용하는 값

## 6.6 null 타입

* `null` 값이 유일
* 변수가 이전에 참조하던 값을 더 이상 참조하지 않겠다는 의미로 사용

## 6.7 심벌 타입

* ES6에서 추가된 7번쨰 타입으로, 변경 불가능한 원시 타입의 값이다.
* 이 세상에서 유일 무이하다.
* 자세한 것은 뒤에서 배운다고 한다.

## 6.8 객체 타입

* 원시 타입을 빼고 나머지는 모두 객체 타입
* 이것도 자세한 것은 뒤애..

## 6.9  데이터 타입의 필요성

### 6.9.1 데이터 타입에 의한 메모리 공간의 확보와 참조

* 메모리에 값을 저장하려면 먼저 확보해야 할 메모리 공간의 크기를 결정해야 한다.
* 자바스크립트 엔진은 데이터 타입을 통해서 정해진 크기의 메모리 공간을 확보 한다.
* 값을 참조할 때 데이터 타입을 통해서 메모리 셀의 개수를 알아내서 그 만큼 값을 참조해온다.

### 6.9.2 데이터 타입에 의한 값의 해석

* 메모리에는 모든 값이 2진수로 되어 있는데 이것을 해석하는 규칙을 정하는 것이 데이터 타입
* 만약 메모리에 `0100 0001`이라는 값이 있고 데이터 타입이 숫자라면 `65`로 해석이 될 것이고, 문자 타입이라는 `A`로 해석이 될 것이다.

## 6.10 동적 타이핑

### 6.10.1 동적 타입 언어와 정적 타입 언어

* 정적 타입 언어는 변수를 선언할 떄 타입을 선언한다. 그리고 컴파일 시점에서 타입 체크를 수행하여 타입의 일관성을 강제함으로써 더욱 안정적인 코드의 구현을 통해 런타임에 발생하는 에러를 줄인다. 대표적인 언어로 C, C++, JAVA, Kotlin, Go 등등
* 동적 타입 언어는 변수를 선언할 때 타입을 선언하는 것이 아니고 런타임 시 값이 할당될 때 타입이 결정(타입 추론)된다. 그래서 해당 변수에는 여러가지의 데이터 타입의 값을 할당할 수 있다. 대표적인 언어로 파이썬, PHP, 루비 등

### 6.10.2 동적 타입 언어와 변수

* 동적타입의 언어의 경우 변수 값이 언제든지 변경될 수 있기 때문에 복잡한 프로그램에서는 변화하는 변수 값을 추적하기 어려울 수 있다.
* 개발자의 의도와는 상관없이 자바스크립트 엔진에 의해 암묵적으로 타입이 자동으로 변환되기도 한다. 이런 점으로 봤을 때 동적 타입의 언어는 유연성은 높지만 신뢰성은 떨어진다. 신뢰성을 키우기 위해서 변수 사용 이전에 데이터 타입을 체크해햐 하는 로직이 추가되는데 상당히 번거럽고 코드의 양도 증가한다.
* 변수 사용 시 주의 사항
   1. 변수는 꼭 필요한 경우에 한해 제한적으로 사용
   2. 변수의 유효 범위(스코프)는 최대한 좁게 만들어 변수의 부작용을 억제해야 한다.
   3. 전역 변수는 최대한 사용하지 않도록 한다.
   4. 변수보다는 상수를 사용해 값이 변경을 억제한다.
   5. 변수 이름은 변수의 목적이나 의미를 파악할 수 있도록 네이밍한다.
   