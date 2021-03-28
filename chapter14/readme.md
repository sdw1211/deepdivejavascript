# 14장 전역 변수의 문제점

* 결론은 될 수 있으면 전역 변수를 사용하지 말자!!!

## 14.1 변수의 생명 주기

### 14.1.1 지역 변수의 생명 주기

* 모든 변수는 생성되고 소멸이 되는 생명 주기를 갖는다.
* 변수는 자신이 선언된 위치에서 생성되고 소멸한다.
* 지역 변수의 생명 주기는 보통 함수의 생명 주기와 일치한다. 예외로 클로저가 있는데 이것은 뒤에 다시 배운다.
* 호이스팅은 스코프 단위로 발생

### 14.1.2 전역 변수의 생명 주기

* 프로그램이 시작되고 종료될 때까지 주기를 가진다.
* var 키워드로 선언된 전역 변수의 생명 주기는 전역 객체의 생명 주기와 일치한다.


## 14.2 전역 변수의 문제점

1. 암묵적 결합
   * 모든 코드가 전역 변수를 참조하고 변경할 수 있다는 점
   * 코드 가독성이 않좋아지고 의도하지 않는 결과가 나올 수 있다.
2. 긴 생명 주기
3. 스코프 체인 상에서 종점에 존재
4. 네임스페이스 오염

## 14.3 전역 변수의 사용을 억제하는 방법

### 14.3.1 즉시 실행 함수

* 모든 코드를 즉시 실행 함수로 감싸면 모든 변수는 즉시 실행 함수의 지역 변수가 된다.

### 14.3.2 네임스페이스 객체

* 전역에 네임스페이스 역할을 담당할 객체를 생성하고 전역 변수처럼 사용하고 싶은 변수를 프로퍼티로 추가하는 방법이다.
* 식별자 충돌에만 효과적

### 14.3.3 모듈 패턴

* 클래스를 모방해서 관련이 있는 변수와 함수를 모아 즉시 실행 함수로 감싸 하나의 모듈을 만든다. 모듈 패턴은 자바스크립트의 강력한 기능인 클로저를 기반으로 동작한다. 전역 변수의 억제는 물론 캡슐화까지 구현할 수 있다는 것이다.
* 클로저랑 관련이 있기 때문에 뒤에서 자세하게 배운다.

### 14.3.4 ES6 모듈

* ES6 모듈을 사용하면 더는 전역 변수를 사용할 수 없다. ES6 모듈은 파일 자체의 독자적인 모듈 스코프를 제공한다. 
* 최근 브라우저에서만 지원
