# 5장 표현식과 문

* 개념을 이해한다는 것은 바로 용어를 정확히 이해하고 설명할 수 있다는 것

## 5.1 값

* 값(value): (표현)식(express)이 평가(evaluate)되어 생성된 결과를 말한다.
* 모든 값은 데이터 타입을 가지며, 가진 데이터 타입에 따라서 다르게 해석된다.

## 5.2 리터럴

* 리터럴(literal): 사람이 이해할 수 있는 문자 또는 약속된 기회를 사용해 값을 생성하는 표기법(notation)
```javascript
//리터럴의 예
3                                           //숫자 리터럴
'hello'                                     //문자 리터럴
true, false                                 //불리언 리터럴
null                                        //null 리터럴
undefined                                   //undefined 리터럴
{name: 'lee', address: 'Seoul'}             //객체 리터럴
[1,2,3]                                     //배열 리터럴
function() {}                               //함수리터럴
/[A-Z]+/g                                   //정규 표현식 리터럴
```

## 5.3 표현식

* 표현식(expression): 값으로 평가될 수 있는 문(statement)이다. 즉, 표현식이 평가되면 새로운 값을 생성하거나 기존 값을 참조한다.
* 리터럴도 표현식의 한 종류이다.
* 동치(equivalent): 표현식과 표현식이 평가된 값이 동등한 관계일 경우

```javascript
//표현식의 예
var score = 100;
var score = 50 + 50;
score;
```

## 5.4 문

* 문(statement): 프로그램을 구성하는 기본단위이자 최소 실행 단위로 문의 집합으로 이뤄진 것이 바로 프로그램이며, 문을 작성하고 순서에 맞게 나열하는 것이 프로그래밍
* 문을 여러 토큰으로 구성되는데, 여기서 토큰(token)이란 문법적인 의미를 가지며, 문법적으로 더 이상 나눌 수 없는 코드의 기본 요소를 의미
* 문을 컴퓨터에 내리는 명령이라는 의미로 명령문이라고도 함

## 5.5 세미콜론과 세미콜론 자동 삽입 기능

* 세미콜론(;)은 문의 종료를 나타낸다.
* 코드블록({...}) 뒤에는 세미콜론을 붙이지 않는다. 이러한 코드 불록은 언제나 문의 종료를 의미하는 자체 종결성을 갖기 떄문
* 세미콜론을 생략할 경우 자바스크립트 엔진에서 문의 끝이라고 예측되는 지점에 자동으로 세미콜론을 붙여주는 기능을 수행한다.
* 하지만 몇몇 경우에 개발자가 예측한 결과와 다른 결과가 나올 수 있는 때문에 세미콜론은 될 수 있으면 쓰자는 분위기
* 하지만 위 의견은 세미콜론 자동 삽입(ASI: automatic semicolon insertion)의 동작원리를 제대로 이해 못하고 쓰기 때문에 발생하는 것이기 때문에 ASI를 제대로 이해하고 세미콜론을 빼는 것이 더 좋다는 의견이 최근에 많이 나옴([관련 링크](https://bakyeono.net/post/2018-01-19-javascript-use-semicolon-or-not.html))
* 결론은 규칙을 정해서 통일성있게 사용하자.(개인적으로는 쓰는데 익숙혀져서 쓰는 것을 추천)

## 5.6 표현식인 문과 표현식이 아닌 문

* 표현식은 문의 일부일 수도 있고, 구 자체로 문이 될 수도 있다.
* 푠현식인 문과 표현식이 아는 문을 구별하는 가장 간단하고 명료한 방법은 변수에 할당해 보는 것
* 변수에 할당이 되면 표현식인 문이고 그렇지 않은 경우는 표현식이 아는 문이다.






