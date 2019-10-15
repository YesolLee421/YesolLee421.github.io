---
title: "[Reactive Programming] 프로그래밍 패러다임과 Reactive Programming"
categories: [Reactive Programming]

comments : true
---

현재 코틀린으로 RESTful한 안드로이드 앱을 만들기 위해 Retrofit 등을 찾아보았는데, 안드로이드에서 웹 통신을 위해 RxJava라는 것이 자주 같이 사용되는 것을 알게 되었다. RxJava란 자바 언어로 Reactive Programming을 할 수 있게 해 주는 API같은 것이라고 해서, 반응형 프로그래밍에 대해 조사할 필요를 느꼈다.

그런데 반응형 프로그래밍은 '프로그래밍 패러다임' 중 하나로, 이것을 이해하기 위해서는 다른 패러다임에 대해 간략히 알고 비교해야 될 것 같아서 먼저 여러 프로그래밍 패러다임에 대해 조사하였다.<br>

# 프로그래밍 패러다임(Programming Paradigm)이란?
- 프로그래밍을 하는 관점 및 방법론
- 예를 들어 `OOP(Object-Oriented Prgramming, 객체 지향)`, `FP(Functional Programming, 함수형)`, `RP(Reactive Programming, 반응형)` 등이 있다.
- 프로그래밍 언어 별로 지원하는 프로그래밍 패러다임이 다르다.

## 1. 명령형(Imperative) 프로그래밍
- 시간 순서대로 명령해서 문제를 해결하는 방식
- 선언형 프로그래밍의 반대 개념

## 2. 객체지향(OOP, Object-Oriented) 프로그래밍
- 데이터와 그 데이터를 처리할 메소드를 한데 묶어 객체를 만들고 객체를 조립하는 것을 목표로 함
- 특징
    - `추상화`: 외부 인터페이스만 제공하고 객체 내부를 숨겨서 어떻게 일을 하는지 모르게 결과를 내보낸다.
    - `캡슐화`: 객체 내부에 필요한 데이터를 묶어서 한 번에 관리한다.
    - `상속성`: 모객체를 상속 받아 추가 기능을 더 붙이거나 약간의 수정을 가한 객체를 만들 수 있다.
    - `다형성`: 메소드 이름이 같아도 타입에 따라 다른 메소드를 실행할 수 있다.

## 3. 선언형(Declarative) 프로그래밍
- 명령형 프로그래밍의 반대 개념
- 내가 원하는 것을 선언 후-> *"이제 어떻게 할 것인가?"*\
- 함수형, 논리형 프로그래밍이 여기에 속한다.

### 3-1. 함수형(Functional) 프로그래밍
> 자료 처리를 수학적 함수의 계산으로 취급하고 상태와 가변데이터를 멀리하는 프로그래밍 패러다임 (위키백과)
- 수학의 '함수' 개념을 프로그래밍 언어 설계에 적극적으로 반영: 입력이 같으면 출력도 같다!
- `destructive update`(한번 정의한 변수 값 변경) 불허용 = `immutable data`(불변하는 데이터) 사용
-  일반적인 명령형 언어에서 a=a+1라고 하면 변수 a의 값이 변경되어 저장됨
- 하지만 함수형 언어에서는 a는 '자기 자신보다 1만큼 더한 수'라는 의미만 가짐
- 순수함수(Pure Functions): 함수의 실행이 외부에 영향을 주지 않는, 닫힌 함수. 즉 부작용(Side Effect)가 없다.
```java
// 외부에 영향을 주는 함수
int a = 10, b = 20;
public int plus(int value){
    a = a + value;
    return a;
}
plus(15); //  = 25
plus(15); //  = 40
// a = 40; 외부 변수 a의 값을 계속 바꾼다.
```

```java
// 순수함수
int a = 10, b = 20;
public int plus(int a, int b){
    return a+b;
}
plus(a, b); // = 30
plus(a, b); // = 30
// 외부 변수 값 바꾸지 않음 + 입력이 같으면 출력도 같다.
```
- 장점
    1. `메모이제이션(Memoization)`가능: 함수 호출 시 파라미터 x를 알고 수행할 결과를 한 번 알면 다음엔 그냥 메모해 둔 결과값 리턴 가능(캐싱)->피보나치 재귀함수 구현 등에 적용하면 극단적으로 속도 빨라짐
    2. 멀티스레드 병렬화 쉽게 가능: 멀티스레드 버그 발생 원인이 스레드 간 공유되는 메모리를 변경하는 것인데, 언어 차원에서 메모리 불변을 보장해 멀티스레드 안정성을 보장한다.
    3. 함수 자체가 first-class datatype으로 분류해서 함수를 그냥 보통 변수 다루듯 할 수 있다. 즉 함수를 다른 함수에 인수로 넘겨주거나 함수를 반환하는(만드는) 함수를 정의할 수도 있으며 생산성이 뛰어나다. 코드가 간결해지고 버그가 잘 생기지 않는 견고한 코드가 나오는 경향이 있다.

### 3-2. 반응형 (Reactive) 프로그래밍
- 데이터 중심 사고 방식: 그러나 OOP와 다르게 데이터의 흐름(Data flow)에 더 집중
- `비동기(Asynchronous) 데이터처리`: 이벤트나 변화(클릭 이벤트 뿐만아니라 변수, 유저 입력, 캐시 등 다양한 것에 대해 데이터 흐름 생성 가능)에 반응하기 위한 비동기적 데이터 처리 및 흐름 기반 프로그래밍 패러다임
- 예를 들어 트위터 피드도 하나의 데이터 흐름으로 만들어 그에 따라 반응하는 프로그램 생성 가능
- 동기식(Synchronous) 비효율적 처리로 인한 병목현상 해결, 생산성 증대
- **함수형 프로그래밍을 기반**으로 '불변식' 개념에 기초한다.
- 반응형 프로그래밍에서 변수 값을 바꾸면 해당 변수를 참조하는 모든 식들이 연쇄적으로 재평가되면서 스스로의 값을 갱신한다.(즉 직접 재계산명령 필요 없음)<br>

- 반응형 프로그래밍 코드 사례: 명령형 프로그래밍은 변수 a에 계산식을 할당하면 결과값이 저장되지만 반응형은 계산식이 저장 (예시: 엑셀)
```java
// 명령형 프로그래밍
int a=10, b=20;
int c = a+b;
System.out.println(c)); // c = 30;
a = 20;
System.out.println(c)); // c = 30; c에 계산식의 결과값 30만 저장됨
```

```java
// 반응형 프로그래밍
int a=10, b=20;
int c = a+b;
System.out.println(c)); // c = 30;
a = 20;
System.out.println(c)); // c = 40; c에 계산식 자체가 저장되어 사용하는 변수 a의 값이 바뀐 것이 반영됨
```
- 단점: 언제 변할지 모르는 수많은 변수를 일일히 추적하다보니 성능을 많이 잡아먹음->지연평가 개념 등 사용해도 고속처리는 힘들다->속도 느린 사용자 입력 반응 UI등에 사용<br>

- 데이터 흐름을 처리하는 여러 함수
    - merge(): 말 그대로 두 흐름을 하나로 합친다.
    - filter(): 데이터 흐름에서 내가 관심있는 이벤트들만 추출한 다른 흐름 제작 가능
    - map(): 데이터 흐름의 값에 따라 다른 값을 가지는 새로운 데이터 흐름 제작 가능 (예시: click이벤트 있을 때마다 숫자 1 반환하는 흐름 등) / `immutable` 한 특성살려 기존 흐름 값이 영향 주지 않음<br>

- Stream: sequence of ongoing events ordered in time (계속 실행되고 있는 연속 상의 이벤트들이 시간 순으로 정리된 것)
- value(값), error, completed signal(완료 신호) 등 들어온 이벤트 종류별로 함수를 따로 만들어서 비동기적으로 처리하는 것이 가능하다.<br>

- 구성요소
    - Observable(관찰대상)
    - Operator(연산자)
    - Subscribe(구독)



<br><br>

### 참고자료
- https://zeddios.tistory.com/303 [ZeddiOS]
- [프로그래밍 패러다임 위키백과] https://ko.wikipedia.org/wiki/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D_%ED%8C%A8%EB%9F%AC%EB%8B%A4%EC%9E%84
- [나무위키 프로그래밍 언어] https://namu.wiki/w/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D%20%EC%96%B8%EC%96%B4#s-4.4
- [The introduction to Reactive Programming you've been missing} https://gist.github.com/staltz/868e7e9bc2a7b8c1f754
- [반응형 프로그래밍 (Reactive Programming)] http://blog.skby.net/%EB%B0%98%EC%9D%91%ED%98%95-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-reactive-programming/





