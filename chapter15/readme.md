# 15장 let, const 키워드와 블록 레벨 스코프

## 15.1 var 키워드로 선언한 변수의 문제점

1. 변수 중복 선언 허용
2. 함수 레벨 스코프
3. 변수 호이스팅(이것은 전부 발생한다. const와 let에서는 다른 방식으로 에러 표출)

## 15.2 let 키워드

var 와의 차이점이 아래와 같다.

1. 변주 중복 선언 금지
   * 크롬 콘솔에서는 에러가 나지 않는다!!!
2. 블록 레벨 스코프
3. 변수 호이스팅
   * let과 const 키워드로 선언한 변수의 경우 선언 단계와 초기화 단계가 분리되어 진행된다.
   * 임시적 사각 지대가 형성된다.(임시적 사각 지대란 스코프의 시작 지점부터 초기화 단계 시작 지점까지 변수를 참조할 수 없는 지역이다. 즉 스코프의 시작 지점부터 초기화 시작 지점까지 변수를 참조할 수 없는 구간을 말하며 이 구간에서 변수를 사용할 경우 에러가 발생한다.)
4. 전역 객체와 let
   * var로 선언한 전역 변수와 함수는 암묵적으로 전역 객체 window의 프로퍼티가 된다.(web의 경우)
   * let이나 const 키워드로 선언한 전역 변수는 전역 객체의 프로퍼티가 아니고 보이지 않는 블록(전역 레시컬 환경의 선언적 환경 레코드)내에 존재한다.

## 15.3 const 키워드

* 대부분의 특징은 let 키워드와 같다.
* 차이점은 재할당이 되지 않는다라는 것이다.
* 재할당이 되지 않기 떄문에 선언과 동시에 초기화를 해야 한다.
* 재할당을 할 수 없다는 의미지 변경을 할 수 없다는 의미는 아니다.

## 15.4 var vs let vs const

* const 부터 우선 고려
* let 은 진짜로 재할당이 필요한 경우에만 사용(for문 정도인데 실제로는 거의 없다.)
* var 는 아젠 놔주자.(안녕)



