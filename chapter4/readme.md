# 4장 변수

## 4.1 변수란 무엇인가? 왜 필요한가?

* 변수는 프로그래밍 언어에서 데이터를 관리하기 위한 핵심 개념
* 변수는 하나의 갑을 저장하기 위해 확보한 메모리 공간 자체 또는 그 메모리 공간을 식별하기 위해 붙인 이름이다.
* 프로그래밍 언어에서 값을 저장하고 ㅊ마조하는 메커니즘으로 값의 위치를 가리키는 상징적인 이름이다.
* 변수 이름: 메모리 공간에 저장된 값을 식별할 수 있는 고유한 이름
* 변수 값: 변수에 저장된 값
* 할당(assignment): 변수에 값을 저장하는 것
* 참조(reference): 변수에 저장된 값을 읽어 들이는 것
* 사람이 이해할 수 있는 언어로 명명한 변수 이름을 통해 변수에 저장된 값의 의미를 명확하게 하는 것이 좋다.
* 하지만 변수명을 만드는 것음 참 어렵다. 그 이유로 영어..(개발자가 영어를 해야 하는 이유...)

```javascript
//result가 변수이름, 30(계산된 결과)가 변수 값 
//아래 문을 변수이름 result에 30이라는 변수 값을 할당했다 라는 의미로 사용된다.
var result = 10 + 20;

//아래 문은 면수이름 result2에 result 변수를 참조해서 20이라는 값을 더한 50이라는 변수 값을 할당했다.
var result2 = result + 20;
```

>* [영어 변수명을 잘 지어보자](https://www.youtube.com/watch?v=rbSnkiqPnJI)
>* [구글 자바스크립트 스타일 가이드](https://google.github.io/styleguide/jsguide.html)
>* [에어비앤비 스타일 가이드](https://github.com/airbnb/javascript)
>* [자바스크립트의 메모리 관리](https://developer.mozilla.org/ko/docs/Web/JavaScript/Memory_Management)
>* [자바스크립트는 어떻게 작동하는가](https://engineering.huiseoul.com/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%8A%94-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%9E%91%EB%8F%99%ED%95%98%EB%8A%94%EA%B0%80-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EA%B4%80%EB%A6%AC-4%EA%B0%80%EC%A7%80-%ED%9D%94%ED%95%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EB%88%84%EC%88%98-%EB%8C%80%EC%B2%98%EB%B2%95-5b0d217d788d)

## 4.2 식별자

* 식별자: 변수 이름
* 어떤 값을 구별해서 식별할 수 있는 고유한 이름
* 식별자는 값이 아니라 메모리 주소를 기억하고 있다.
* 식발자는 변수 이름 뿐만 아니라 함수, 클래스 등의 이름도 포함한다.

## 4.3 변수 선언

* 변수를 생성하는 것
* 값을 저장하기 위한 메모리 공간을 확보(allocate)하고 변수 이름과 확보된 메모리 공간의 주소를 연결(name binding)해서 값을 저장할 수 있게 준비하는 것
* 변수 선언에 의해 확보된 메모리 공간은 확보가 해제(release)되기 전까지는 누구도 확보된 메모리 공간을 사용할 수 없도록 보호되므로 안전하게 사용할 수 있다.
* **변수를 사용하기 위해서는 반드시 선언이 필요**
* var, let, const라는 키위도를 사용한다. ES6 이후에는 let, const 만을 사용하도록 권장한다.
* 자바스크립트는 하위호환성을 지원하기 때문에 모든 것이 없어지지 않는다..
* 키워드: 자바스크립트 코드를 해석하고 실행하는 자바스크립트 엔진이 수행할 동작을 규정한 일종의 명령어, 종류는 책을 참조
* 변수를 선언하고 값을 할당하지 않는 경우 기본적으로 `undefined` 가 할당
* 자바스크립트 엔진의 변수 선언 단계
   1. 선언 단계: 이름을 등록해서 자바스크립트 엔진에 변수의 존재를 알린다.
   2. 초기화 단계: 값을 저장하기 위한 메모리 공간을 확보하고 암묵적으로 undefined를 할당해 초기화한다.
* 모든 식별자는 실행 컨텍스트에 등록된다. 자세한 것은 뒤에 배운다.
* 선언하지 않은 변수를 사용할 경우 RefrenceError가 발생한다.

## 4.4 변수 선언의 실행 시점과 변수 호이스팅

```javascript
//구문
console.log(score);

var score;

//런타임 시
var score = undefined;  //런타임 이전에 변수 선언을 올려준다.
console.log(score);
score = undefined;
```
* 위와 같이 변수 선언은 런타임 시에 발생하는 것이 아니고 그 이전 단계에서 먼저 실행됩니다.
* 변수 선언이 소크코드의 어디에 위치하는지 상관없이  다른 코드보다 먼저 실행한다. 그래서 어떤 위치에 있던지 상관없지 변수를 참조할 수 있음
* 호이스팅: 변수 선언문이 코드의 선두로 끌어 올려진 것처럼 동작하는 자바스크립트 공유의 특징

>* [MDN var](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/var)
>* [호이스팅은 공식 문서에는 존재하지 않는다.](https://medium.com/nmc-techblog/what-is-hoisting-in-javascript-bf73980d9dac)

## 4.5 값의 할당

* 할당(assignemnt) 연사자(=)를 활용해서 우변의 값을 좌변의 변수에 할당하는 행위

```javascript
var score; //변수 선언
score = 80; //값을 할당
```

* 변수 선언과 값의 할당을 하나의 문으로 단축 표현할 수 있다.

```javascript
var score = 80;
```

```javascript
//런타임 이전
console.log(score);
score = 80;
var score;

console.log(score);

//런타임 시
var score = undefined;
console.log(score); //undefined
score = 80;         //80
score = undefined;  //undefined

console.log(score); //undefined
```

## 4.6 값의 재할당

* 이미 값이 할당되어 있는 변수에 새로운 값을 또다시 할당하는 것을 말한다.
* 재할당은 변수에 저장된 값을 다른 값으로 **변경**한다. 이 말은 메모리의 위치가 변경된다는 것을 의미한다.

## 4.7 식별자 네이밍 규칙

* 식별자는 특수문자를 제외한 문자, 숫자, 언더스코어(_), 달러 기호($)를 포함할 수 있다.
* 특수문자를 제외한 문자, 언더스코어(_), 달러 기호($)로 시작, 숫자로 시작하는 것은 허용하지 않는다.
* 예약어는 식별자로 사용할 수 없다.
* ES5부터는 식별자를 만들 때 유니코드 문자가 허용되었지만 안쓰는 것을 추천한다.
* 식별자 네이밍을 할 떄 의미가 있는 단어를 활용해서 네이미하는 것이 좋다.






