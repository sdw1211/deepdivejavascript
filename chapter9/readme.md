# 9장 타입 변환과 단축 평가

## 9.1 타입 변환이란?

* 명시적 타입 변환(explicit coercion)또는 타입 캐스팅(type casting): 개발자가 의도적으로 값의 타입을 변환하는 것

```javascript
var x = 10;

var str = x.toString();         //명시적 타입 변환
console.log(typeof str, str);   //string 10
console.log(typeof x, x);       //number 10
```

* 암묵적 타입 변환(implicit coercion) 또는 타입 강제 변환(type coercion): 개발자의 의도와는 상관없이 표현식을 평가하는 도중에 자바스크립트 엔진에 의해 암묵적으로 타입이 자동으로 변환

```javascript
var x = 10;

var str = x + '';       //암묵적으로 x의 타입이 문자열로 변환
console.log(typeof str, str);   //string 10
console.log(typeof x, x);       //number 10
```

* 명시적 타입 변환이나 암묵적 타입 변환이 기존 원시 값을 직접 변경하는 것이 아니고 기존 원시 값을 이용해 다른 타입의 새로운 원시 값을 생성하는 것이다.
* 자신이 작성한 코드에서 암묵적 타입 변환이 발생하는지, 발생한다면 어떤 타입의 어떤 값으로 변환되는지, 그리고 타입 변환된 값으로 표현식이 어떻게 평가될 것인지 예측 가능하도록 프로그램을 작성하는 것이 중요하다.

## 9.2 암묵적 타입 변환

* 암묵적 타입 변환이 발생하면 문자열, 숫자, 불리언과 같은 원시 타입 중 하나로 타입을 자동 변환한다.

### 9.2.1 문자열 타입으로 변환

```javascript
1 + '2' // "12"
```

* `+`연산자는 피연산자 중 하나 이상의 문자열인 경우 문자열 연결 연산자로 동작한다.
* 문자열 연결 연산자인 경우 문자열끼리 연결해야 하기 때문에 피연산자 중 문자열이 아닌 경우에 자바스크립트 엔진에서 문자열로 암묵적인 타입 변환을 시도한다.

### 9.2.2 숫자 타입으로 변환

* 산술 연산자는 모든 피연산자가 숫자여야 하기 때문에, 암묵적으로 숫자 타입으로 변환을 시킨다.
* 비교 연산자의 역할은 불리언 값을 만드는 것이다. > 비교 연산자는 피연산자의 크기를 비교하므로 모든 피연산자는 코드의 문맥상 모두 숫자 타입이어야 한다.

```javascript
1 - '1'  //0
1 * '10' //10
1 / 'one' //NaN

'1' > 0     //true
+''         //0
+'0'        //0
+'1'        //1
+'string'   //NaN

+true       //1
+false      //0

+null       //0
+undefined  //NaN

+{}         //NaN
+[]         //0
+[10, 20]   //NaN
+(function() {})    //NaN
```

### 9.2.3 불리언 타입으로 변환

* if문이나 for문과 같은 제어문 또는 삼항 조건 연산자의 조건식은 불리언 값, 즉 논리적 참/거짓으로 평가되어야 하는 표현식이다, 이런 조건식의 평가 결과를 암묵적으로 불리언 타입으로 변환시켜준다.

```javascript
if ('') console.log('1');   //false
if (true) console.log('2'); //true
if (0)  console.log('3');   //false
if ('str') console.log('4');  //true
if (null) console.log('5'); //false
```

* 자바스크립트에서 Falsy 값은 아래와 같다.
   * false
   * undefined
   * null
   * 0, -0
   * ''
   * NaN
* 위 Falsy 값을 제외하고는 전두 Truthy 값이다.

## 9.3 명시적 타입 변환

### 9.3.1 문자열 타입으로 변환

1. String 생성자 함수를 new 연산자 없이 호출하는 방법
2. Object.prototype.toString 메서드를 사용하는 방법
3. 문자열 연결 연산자를 이용하는 방법 - 이건 암묵적으로 봐야 하지 않나?

```javascript
String(1);          //"1"
(1).toString();     //"1"
1 + '';             //"1"
```

### 9.3.2 숫자 타입으로 변환

1. Number 생성자 함수를 new 연산자 없이 호출하는 방법
2. parseInt, parseFloat 함수를 사용하는 방법(문자열만 가능)
3. + 단항 산술 연산자를 이용하는 방법
4. * 산술 연산자를 사용하는 방법

```javascript
Number('1');            //1
Number('10.53');        //10.53

parseInt('1');          //1
parseFloat('10.53');    //10.53

+'1';                   //1
+'10.53';               //10.53

'1' * 1;                //1
'10.53' * 1;            //10.53
```

### 9.3.3 불리언 타입으로 변환

1. Boolean 생성자 함수를 new 연산자 없이 호출하는 방법
2. !부정 논리 연산자를 두 번 사용하는 방법

```javascript
Boolean('x');           //true
Boolean('');            //false

Boolean(0);             //false
Boolean(1);             //true

!!'x';                  //true
!!'';                   //false

!!0;                    //false
!!1;                    //true
```

## 9.4 단축 평가

### 9.4.1 논리 연산자를 사용한 단축 평가

* 논리합(||)또는 논리곱(&&) 연산자 표현식의 평가 결과는 불리언 값이 아닐 수도 있다. 논리합(||) 또는 논리곱(&&) 연산자 표현식은 언제나 2개의 피연산자 중 어느 한쪽으로 평가된다.

```javascript
'Cat' && 'Dog'  // Dog
'Cat' && 'Dog'  // Cat

var elem = null;
elem && elem.id;    //elem이 Truthy 값인 경우 elem.id 값을 처리한다.

value || '111';     //value 값이 Falsy 값이면 111 값으로 대체한다.
```

* 논리 연산의 결과를 결정하는 피연산자를 타입 변환하지 않고 그대로 반환한다. 
* 단축 평가: 표현식을 평가하는 도중에 평가 결과가 확정된 경우 나머지 평가 과정을 생략하는 것을 말한다.
* 함수 매개변수에 기본값을 설정할 때 : || 사용
* 객체를 가리키기를 기대하는 변수가 null 또는 undefined가 아닌지 확인하고 프로퍼티를 참조 할 때: && 사용

### 9.4.2 옵셔널 체이닝 연산자

* ECMAScript 2020에서 도입된 옵셔널 체이닝 연산자 ?. 는 좌항의 피연산자가 null 또는 undefined 인 경우 undefined 를 반환하고, 그렇지 않으면 우항의 프로퍼티를 참조를 이어간다.

```javascript
var elem = null;

var value = elem?.value;
var value2 = elem && elem.value;

console.log(value); //undefined
console.log(value2); //null


var elem2 = '';

var value3 = elem2?.length;      
var value4 = elem2 && elem2.length;

console.log(value3); //0  elem2가 null이나 undefined가 아니기 때문에 length 속성값을 value3에 할당한다.
console.log(value4); //'' elem2가 falsy 값이기 때문에 elem2 값을 value4에 할당한다.
```

### 9.4.3 null 병합 연산자
* ECMAScript 2020에서 도입된 null 병합 연산자는 ??는 좌항의 피연산자가 null 또는 undefined 인 경우 우항의 피연산자를 반환하고, 그렇지 않으면 좌항의 피연산자를 반환한다.

```javascript
var foo = null ?? 'default string';
console.log(foo);       //default string

var foo2 = '' || 'default string';
console.log(foo2);      //default string    ''는 Falsy 값이기 때문에 'default string'이 foo2에 할당
var foo3 = '' ?? 'default string';
console.log(foo3);      //'' ''는 undefined 또는 null이 아니기 때문에 '' 값이 foo3에 할당
```









