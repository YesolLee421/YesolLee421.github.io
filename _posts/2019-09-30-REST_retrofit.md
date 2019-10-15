---
title: "[Android] REST, RESTful API, Retrofit 조사"
categories:
  - REST

comments : true
---

# REST (Representational State Transfer)
## REST의 정의
- 월드 와이드 웹과 같은 분산 하이퍼미디어 시스템을 위한 소프트웨어 아키텍처의 한 형식
- 분산 시스템 설계를 위한 아키텍처 스타일 (= 제약 조건의 집합)
- 로이 필딩(Roy Fielding)의 2000년 박사학위 논문에서 소개됨<br>

## RESTful?
- REST 아키텍처 스타일을 모두 만족하는 것<br>

## REST가 필요한 이유
1. 분산 시스템 구현: 거대 애플리케이션의 부분들을 모듈, 기능별로 쪼개어 각각 RESTful하게 개발하면 상호 통신 가능

2. 멀티 플랫폼: 웹 페이지를 위한 html 및 이미지를 직접 보내지 않고 json, xml 등의 형식을 지킨 데이터만 보내면 웹이나 모바일 등 플랫폼 상관없이 여러 클라이언트가 사용 가능<br>

## REST의 구성요소
1. HTTP URI: 자원(resource)
2. HTTP Method = 행위: GET, POST, PATCH, DELETE 등
3. MIME TYPE = 자원 표현방식 (json, xml 등)<br>

## REST 아키텍처의 6가지 제한 조건
### 1. 클라이언트 / 서버 구조

### 2. Stateless
- 각 요청(response)에 클라이언트의 context가 서버에 저장되지 않는다.<br>

### 3. Cacheable
- 클라이언트는 응답을 캐싱할 수 있어야 한다.<br>

### 4. Layered System(계층화)
- 클라이언트는 보통 대상 서버에 직접 연결되었는지, 또는 중간 서버(*Middleware, 미들웨어*)를 통해 연결되었는지를 알 수 없다.
- *미들웨어(middleware)*
    - 양 쪽을 연결하여 데이터를 주고 받을 수 있도록 중간에서 매개 역할을 하는 소프트웨어
    - 3계층 클라이언트/서버 구조에서 웹 브라우저의 데이터베이스로부터 데이터를 저장하거나 읽어올 수 있게 중간에 미들웨어가 존재
    - 클라이언트 종류에 상관 없이 표준화된 인터페이스 제공 가능<br>

### 5. Code on Demand(optional)
- 자바스크립트 코드 제공 등을 통해 서버가 클라이언트가 실행시킬 수 있는 로직을 전송하여 기능 확장 가능
- 서버에서 코드를 클라이언트에 보내서 실행할 수 있어야 한다.<br>

### 6. Uniform interface (인터페이스 일관성)
- 자원은 유일하게 식별 가능해야 한다.
- http method로 표현 담기
- 메시지로 리소스 조작: 클라이언트가 어떤 자원을 지칭하는 메시지와 특정 메타데이터만 있어도 서버 상의 해당 자원을 변경, 삭제할 수 있다.
- 메시지는 스스로 설명 가능해야 함(self-descriptive)
- 전이(HATEOAS, Hypermedia as the Engine of Application State): 하이퍼링크를 통해 애플리케이션 상태가 전이 = 해당 정보에서 다른 정보를 넘어갈 수 있는 하이퍼링크 명시<br>

## URI와 URL의 차이점
- URI (Uniform Resource Identifier) = 자원 식별자: 개별 자원을 유일하게 식별하는 값
- URL (Uniform Resource Location): 과거 웹에서 html 파일 주고 받음->파일 위치 가리치는 Locator사용 (자원 식별 필요성 없었음)
- 즉 URI가 파일 뿐만 아니라 여러 다른 자원들도 포함하는 개념<br>

## RESTful한 API를 만들기 위해서는?
- 마이크로소프트 REST 가이드라인 참고: URL 구조, 헤더 종류 등 세세한 것에 대한 가이드라인이 존재한다. 필요할 때 한 번씩 검색해서 봐야할 듯
- 안드로이드에서 REST를 만족하는 http통신을 하기 위해 별도의 라이브러리가 필요하다.<br>

# Retrofit?
## Retrofit이란?
- retrofit 사전적 의미: (기계 속에 원래 없던 부품 등을) 새로 장착하다/넣다/제공하다 (네이버 사전)
- 안드로이드에서 HTTP client, RESTful API 개발 위한 라이브러리 중 하나
- HTTP request를 위해 OkHttp라이브러리 사용
- HTTP API 를 자바(코틀린) 인터페이스 형태로 사용: 서비스 인터페이스 구현(GET 등 메소드 구현)
- Retrofit 클래스->빌더->create
- call: 서비스 인터페이스 통해서 동기 또는 비동기하는 http 요청을 원격 웹서버로 보냄<br>

## Response 메소드 필수 속성
- 상대 URL
- 요청 메소드 이름(어노테이션): GET, POST, PUT, DELETE, HEAD<br>

## URL
- 동적 부분 치환 가능 {id} -> 반드시 메소드 매개변수에 명시 @Path("id") int groupID<br>

## 요청 본문
- `@Body` 어노테이션으로 명시<br>

## 메소드 데이터 방식 2가지
1. `@formUrlEncoded`: form 형식 데이터 / @Field 로 매개변수 명시
2. `Multipart`: @Part / Retrofit 컨버터나 RequestBody를 통해 직렬화(serialization)가능한 객체 사용<br>

## 헤더 다루기
- 정적 헤더 @Headers
- 동적 헤더 @Header<br>

## 동기 vs 비동기
- call 인스턴스 각각 다른 방식 사용 가능
- 안드로이드 콜백은 메인스레드에서 실행됨<br>

## Retrofit 설정
- Retrofit은 API인터페이스를 호출 가능한 객체로 바꿔준다.
- `컨버터(Converter)`: 기본적으로는 http 요청 본문을 OkHttp의 ResponseBody형식과 `@Body`에 이용하는 RequestBody형식만 역직렬화 가능하지만, 컨버터가 이외의 형식을 변환해 준다.
- 인터페이스가 `Gson`등을 역직렬화 가능하게 하려면 `GsonConverterFactory`클래스로 컨버터 추가해서 사용하면 됨
- 주로 많이 사용하는 컨버터 라이브러리
    - JSON 관련: Gson, Jackson, Moshi
    - Protocol Buffers 관련: Protobuf, Wire
    - XML 관련: Simple XML
    - 이미지 관련: Glide
- Custom 컨버터도 만들 수 있음: `Converter.Factory` 클래스 상속 후 Retrofit 객체 만들 때 추가<br>





* 출처
    - [기본기를 쌓는 정아마추어 코딩블로그] https://jeong-pro.tistory.com/180 
    - [마이크로소프트 REST 가이드라인] https://github.com/Microsoft/api-guidelines/blob/vNext/Guidelines.md
    - [REST 위키피디아(eng)] https://en.wikipedia.org/wiki/Representational_state_transfer
    - [Retrofit 공식 한글문서] http://devflow.github.io/retrofit-kr/



