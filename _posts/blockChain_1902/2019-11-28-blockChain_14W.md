---
title: "[블록체인] 13주차_블록체인의 미래"
categories:
  - BlockChain
tags:
  - BlockChain
  - 블록체인
  - K-MOOC

comments : true
---
*이 내용은 K-MOOC [알기쉬운블록체인] 강의를 듣고 정리한 내용입니다.*
<br>

[알기쉬운블록체인]: http://www.kmooc.kr/courses/course-v1:SJCU+SJCU01+2019_2/courseware/145ba5714d1246c1b65fe1b081d52db0/e1af1659e74343579fe5727acdfcfbc7/?child=last

<br>

# 2세대 암호화폐, 이더리움(Ethereum)
## 2세대 암호화폐, 이더리움(1)
### 1. 비트코인(1세대) vs 이더리움(2세대)

| Bitcoin | Ethereum |
| --- | --- |
| 블록체인에 화폐 거래내역만 저장 | 프로그램 코드가 돌아감 |
| 화폐 대체제(=금) | 다른 것을 만들어내기 위한 인프라, 플랫폼(=석유) |

### 2. 이더리움이란?
- 2013년 비탈릭 부테린이 개발
- 계기) 왜 블록체인에 비트코인의 거래 기록만 기록해야 하나? 좀 더 발전적인 것을 기록하면 어떨까?
- 결론) 블록체인에 우리가 만든 프로그램 자체를 등록하자!
- __작동방식__
    1. 유저 A가 프로그램 A를 블록체인에 등록함
    2. 프로그램 A를 누군가 실행할 때마다 A가 비트코인을 지급하겠다고 조건을 검 = __스마트 컨트랙트__
    3. 다른 유저들이 프로그램 A를 대신 실행하고, 그에 대한 보상으로 유저 A가 보상 지급
    4. __이더리움 = 월드 컴퓨터__: 이더리움에 등록되어 있는 프로그램은 누구든 대신 실행시켜줄 수 있다.
- 비트코인 vs 이더리움 상 블록체인의 차이
    - 비트코인: 각 블록에 거래 정보가 저장됨
    - 이더리움: 각 사용자들의 상태 정보 저장됨
- __스마트 컨트랙트(Smart contracts)__: 1996년 닉스 자보가 처음 사용한 개념<br>

### 3. 이더리움의 프로그래밍 언어: 솔리디티(Solidity)
- 이더리움 블록체인 상에 등록된 프로그램을 짜는(스마트 컨트랙트를 정의하는) 프로그래밍 언어 = 대표적으로 __솔리디티(Solidity)__
- 자바스크립트 문법과 유사하나 정적 타입 언어라서 자료형 명시해 주어야 한다. (출처: 프로그래머스 솔리디티 실습 튜토리얼 참고)
- 자바로 짠 프로그램이 JVM상에서 구동되듯이, 솔리디티로 짠 프로그램은 이더리움 버추얼 머신(Ethereum VM) 위에서 동작함
- __'튜링 컴플리트(Turing-Complete)'__: 일반적인 컴퓨터에서 할 수 있는 모든 프로그램은 이더리움 상에서도 프로그램 할 수 있다는 뜻
- 비트코인 상에서도 일부 프로그래밍 가능하지만 제한적임<br>


## 2세대 암호화폐, 이더리움(2)
---
### 1. 비트코인(1세대) vs 이더리움(2세대) 차이점
- 사용 목적: 비트코인 거래정보 기록(비트코인) vs 프로그램 자체 실행시키는 플랫폼(이더리움)
- 투표 조작 방지 방식
    - 비트코인: 작업증명(PoW)-> 과도한 에너지 소모, 속도 저하 등의 부작용
    - 이더리움
        - 캐스퍼 프로토콜 내 지분증명(PoS)-> PoW 방식의 부작용 많이 개선됨
        - 고스트 프로토콜(Greedy Heavies Observed Subtree, GHOST)<br>

### 2. 이더리움의 GHOST Protocol(Greedy Heavies Observed Subtree)
- 기존 비트코인: 1블록 생성(채굴)에 약 10분 소모
- 이더리움: 1블록 생성에 약 15초 소모
- 장점: 더 빠른 트랜잭션 처리
- 단점: 굉장히 많은 블록 생성됨->경쟁 상태의 블록 더 많이 생김 -> '고스트 프로토콜' 사용
- __<고스트 프로토콜>__ 이란?
    - 기존 비트코인: 가장 긴 줄에 위치한 블록들만 '권위 체인'으로 인정하고 인센티브 지급
    - 고스트 프로토콜: 가장 긴 줄에 위치한 블록 및 해당 체인에서 옆으로 이어진 블록들에 대해서도 보상을 지급함. 이 때 권위 체인에 옆으로 이어진 블록들을 __'엉클 체인'__ 이라고 한다.
    - 장점: 경쟁 상태에 있는 블록체인 네트워크를 빠른 시간 안에 안정화함
    - 단점: 인센티브 남발->그래서 메인블록의 보상(Full Block Reward)이 엉클 블록의 보상(Uncle Block Reward)보다 큼 & 엉클 블록 7개까지만 보상 지급
    - 특징: 가장 긴 체인보다 엉클 블록을 포함해 가장 많은 블록이 달려있는 체인을 __'헤비하다(heavy chain)'__ 이라고 표현하며 메인 블록으로 인정함<br>


## 2세대 암호화폐, 이더리움(3)
---
### 1. 이더리움 예시: 크립토키티(CryptoKitties, 2017)
- 기존 게임: 게임 관련 정보가 게임회사의 중앙 서버에 저장됨. 따라서 서비스 종료 시 모든 정보 사라짐
- DApp: 게임 정보가 블록체인 상에 저장되어 영원히 사라지지 않음. 즉 게임 아이템이 진정한 재산이 됨.
- __DApp(Decentralized App)이란?__ 데이터를 블록체인에 저장하는 탈중앙화된 앱을 기존 앱과 차별지어 DApp(혹은 댑)이라고 부름
- 크립토키티: DApp 고양이 육성 게임
    - 2017년 '액시엄 젠' 회사에서 개발함
    - 경제규모 약 4천만 달러로 평가됨
    - 출시 초기: 이더리움 네트워크 트래픽의 25%가 크립토키티에서 거래됨->이더리움 네트워크 처리속도 해결이 관건
    - 특징: 다른 블록체인 프로젝트와 달리 ICO(Initial Coin Offering)를 통해 투자금 모으지않고 지속가능한 수익모델 개발
    - ICO(Initial Coin Offering): 암호화폐, 블록체인 산업의 크라우드 펀딩과 비슷한 개념으로 새로운 암호화폐를 출시할 때, 크라우드 펀딩 방식으로 해당 토큰의 일부를 공개하여 비트코인, 혹은 기타 자금으로 교환하는 것<br>

### 2. Smart Contract vs DApp
- DApp: 블록체인을 가능하게 하는 웹사이트와 같은 것
- Smart Contracts: DApp과 블록체인을 연결시켜주는 기능을 함
- 전통적인 웹사이트: FrontEnd -> API -> 서버 데이터베이스에 접근
- DApp: FrontEnd -> 스마트컨트랙트 -> 블록체인에 접근<br>


### 3. 이더리움 상 스마트컨트랙트의 문제점
- 한 번 블록체인에 등록하면 업데이트하기 쉽지 않다.
- 블록체인의 불변성 -> 프로그램 업데이트 쉽지 않아서 처음부터 잘 만들지 않으면 오류가 그대로 남아있게 됨
- 특히 해당 프로그램을 수행할 때마다 돈이 거래되기 때문에 작은 실수로 인해 큰 금전적 손해를 볼 수 있음
- 예시) 이더리움 상 프로그램 'DAO'<br>

# 3세대 암호화폐들
## 3세대 암호화폐들(1)
### IOTA & Tangle(2015)
- IOTA: `블록체인` 이 아닌 **DAG 기반의 Tangle** 이라는 자료구조 체계를 사용하는 IoT 환경에 특화된 암호화폐
![14_2_tangle](https://user-images.githubusercontent.com/54266900/69862913-dc858900-12de-11ea-994a-283408446cff.PNG)

| 비교 | BlockChain | DAG - Tangle |
| --- | --- | --- |
| 구조 | 10분 단위로 만든 장부 일렬로 연결 | 수많은 장부(블록)이 불규칙하게 연결됨 (Directed Acyclic Graph) |
| 블록 등록 | 거래기록 + 해시퍼즐 풀기 + 가장 빠르게 회람 + 검증해야 인센티브 얻음 | 탱글의 임의의 블록 2개를 컨펌하면 새 블록 생성 가능 | 
| 특징 | 처리 속도 느리고 에너지 소모 심함 | IoT기계에서도 사용 가능하지만 각 블록의 신뢰도 떨어짐 | 
<br>

## 3세대 암호화폐들(2)
---
### 1. IOTA
1. IOTA의 특징
    - `Tangle`구조: 기존 블록들 중 임의의 블록 2개만 골라서 컨펌하면 새 블록 생성 가능
    - 언제 어디서든지 블록 생성 및 컨펌 활동이 자유롭게 일어남<br>

2. IOTA의 필요성
    - 4차 산업시대: IoT 기기가 주변에 산재해있음
    - IoT 기기들이 사람의 손을 거치지 않고 직접 암호화폐를 사용할 수 있도록 하기 위해 만들어짐
    - 예시) 무인배달 드론: 배터리 충전 후 내장된 암호화폐 기능으로 결제를 알아서 함<br>

3. IOTA의 문제점
    - 34%(1/3 이상 담합) 공격: 전체 사용자의 1/3이상이 담합하면 전체 시스템에 영향 미칠 수 있음
    - 완벽한 탈중앙화가 아님
        - 응집력이 약해 수많은 의견이 산만하게 제시되는 구조
        - 이를 보완하기 위해 `코디네이터`라는 중앙 프로그램 있음
        - '코디네이터': 블록이 일정하게 한쪽으로 성장할 수 있도록 유도하는 기능 / 소스코드 미공개
    - 기술 상의 결함
        - '컬 해시함수' 암호화: 이미 발견된 취약점인데 해결하지 않은 채로 출시<br>

### 2. 다른 3세대 암호화폐들
1. **NEO** (2015): 중국판 이더리움<br>

2. **Cardano** (2017)
    - 학계에서 엄밀하게 검증된 기술만 사용함 -> '가장 과학적인 암호화폐'
    - 응용서비스) 학위증명서, 졸업증명서 등 학교에 방문하지 않고도 확인 가능<br>

3. **익명성 극대화** 한 암호화폐들
    - 모네로, 제트캐시, 제트 코인 등<br>


# 암호화폐의 가치와 블록체인의 미래
## 암호화폐 관련 정의 및 정책
### 1. 코인 vs 토큰
- 암호화폐: 코인, 토큰
- 코인(Coin): 비트코인, 이더리움, 리플, 아이오타 등 자체 블록체인 시스템을 가진 암호화폐
- 토큰(Token): 이더리움 플랫폼 상에서 만든 서비스, 프로그램 내에서 사용하는 암호화폐. 즉 이더리움 상에서 작동하는 일종의 약식 코인
- 예시) 네이버페이: 온라인 쇼핑몰에서 쉽게 결제 시스템 구축할 수 있도록 네이버페이 시스템을 제공함(=이더리움)
- `이더리움 토큰`: `ERC20` 표준->이더리움 플랫폼 상에서 구동되는 프로그램에서 쉽게 암호화폐 만들도록 설계함
- 토큰->코인: 이더리움 플랫폼에서 운영하다가 자체 블록체인 시스템을 만들어서 운영하게 되면 **'메인넷 서비스를 시작했다'** 라고 하고 토큰이던게 정식 코인이 됨<br>

### 2. 코인 투자 방식: ICO (Initial Coin Offering)
- __IPO(기업 공개)__: _기업 설립 후 처음으로 외부투자자에게 주식을 공개하고, 이를 매도하는 업무를 의미한다. 주식을 공개하는 방법으로는 자신의 회사주를 주식시장에 등록(주식 상장)하는 작업을 들 수 있다._ (출처: 위키백과)
- IPO 과정은 까다롭다: 자본->시제품->시장 판매->3년 간 매출액 분석->기업 평가 후 주식 상장(IPO)
- __ICO(가상화폐 공개)__: _블록체인 기술을 기반으로 새로운 암호화폐를 만들기 위해 불특정 다수의 투자자들로부터 초기 개발 자금을 모금하는 과정을 말한다._ 이때 투자금은 암호화폐로 받기 때문에 국격 제약이 없다. (출처: 위키백과)
- ICO 에서 투자자의 이득은? 해당 코인의 미래 가치를 담보해서 다른 암호화폐로 해당 코인을 사는 것: 크라우드 펀딩과 비슷한 듯
- ICO의 문제? 만들어진 제품(코인) 없이 사업계획서만 보고 해당 사업, 코인의 성공 가능성을 평가해서 투자해야 함. 따라서 실패 확률이 90%로 매우 높고 사기성 스캠도 굉장히 많다.<br>

### 3. 토큰에 대한 분류

| 지불형(Payment) 토큰 | 기능형(Utility)토큰 | 자산형(Asset)토큰 | 
| --- | --- | --- |
| 지불수단 외 다른 기능 없음 | 앱 혹은 서비스 이용 목적 | 배당금, 이자, 수익에 대한 권리<br>또는 수익 흐름에 참여할 권리 부여 | 
| `Bitcoin`, `Ethereum` | `Bat`, `Steem`, `Storj` | ? | 
| 증권 취급[x]<br>자금세탁규정 준수 | 증권 취급[x] | 증권 취급[o] | 

### 4. 각국의 ICO 정책
1. __한국: 금지__
    - 모든 형태의 ICO 금지
2. __중국: 금지__
    - 암호화폐의 익명성으로 인해 자국 위안화를 외국으로 빼돌리거나 상속 시 추적 불가능한 문제
    - 홍콩은 ICO 허용
3. __스위스: 육성__
    - 2018년 2월 연방금융감독청: ICO 가이드라인 발표
    - 자산형 토큰만 증권법 적용
    - 주크(Zug) 시에 크립토밸리 조성
    - 암호화폐 허브국가로 육성 방침
    - 세계 ICO 5위 (147건), 인구 100만 명 당 ICO 4위
    - 전통적으로 비밀금고 운영-> 비밀금고 시장의 기득권을 지키기 위해 암호화폐도 적극 수용
4. __에스토니아: 육성__
    - 전자 영주권(e-Residency)제도로 외국인 창업지원
    - ICO 적극 장려
    - 인구 100만 명 당 ICO 1위
    - 작은 도시형 국가: ICO, 암호화폐 등 다양한 IT 기술에 대해 빠른 도입 및 시행착오
5. __싱가포르: 육성__
    - 2017년 11월 중앙은행: ICO 가이드라인 발표
    - 증권형 ICO: 증권선물법(SFA) 적용
    - 세계 ICO 4위(233건), 인구 100만 명 당 ICO 2위
6. 기타 허용국가
    - 미국, 일본, 프랑스, 독일, 영국, 러시아 등
    - 고위험도 상품 + 증권과 유사한 성질: 일정 부분 규제하는 방향
    - 2018년 11월 미국 SEC: ICO에 증권법 적용 본격과->사기성 ICO 집중단속<br>


## 암호화폐의 가치와 블록체인의 미래
---
### 1. 암호화폐의 가치는?
1. 암호화폐와 블록체인
    - 퍼블릭 블록체인의 경우: `비트코인`, `이더리움` 등
    - 중앙관리기관 없음->중복사용 방지를 위해 `블록체인` 사용->`블록체인` 사용을 위해 인센티브 필요->인센티브를 다시 암호화폐로 지급
2. 암호화폐를 이용한 비즈니스 모델
    - `크립토키티` 등 블록체인의 고유 특징을 이용한 비즈니스 모델
3. 암호화폐 가치 측정 시 고려할 사항
    - 해당 화폐의 기반이 되는 블록체인의 기술적 가치 평가
    - 해당 암호화폐를 이용하는 비즈니스 모델에 대한 평가
    - 대안) 외국 중심으로 이런 ICO의 건전성 확보해주는 전문 사이트 증가 중<br>


### 2. 암호화폐와 블록체인의 미래는?    

![14_3_2_가트너하이프사이클](https://user-images.githubusercontent.com/54266900/69937553-74bd8100-151e-11ea-999c-4496ceedee31.PNG)

- **가트너 하이프 사이클(Gartner Hype Cycle)이란?** '기술 성장 곡선'으로 처음 어떤 기술이 나온 후 해당 기술의 가치 변화 그래프
    - 초기: 해당 기술의 기대가치가 상승해 거품이 끼게 됨
    - 정점: 거품이 정점에 이르면 사람들이 그 기술의 본질을 알게 되어 관심도 추락
    - 안정기: 거품이 꺼져도 해당 기술이 가치가 있다면 응용 분야를 찾아 가치가 안정됨<br>

- **블록체인의 기술 성장 곡선, Gartner Hype Cycle(가트너 하이프 사이클)**
    - 영상) '거품 꺼지기 직전 단계'로 평가함 (아마 영상은 2018년에 만들어진 듯)
    - 최근 오프라인 강의) '거품 꺼진 직후'로 평가함. (2019.11.30 기준)

- 암호화폐와 블록체인의 미래는?
    - 거품이 꺼져도 '블록체인'은 고유의 가치가 있음
    - 그러나 2, 3년 내에 급격히 세상 바꾸기는 힘들 듯
    - 여전히 기술적 난제 많음: 프라이버시 보호, 속도 문제 등
    - 추후 응용 분야: _암호화폐, 크라우드 펀딩, 에너지 트레이딩, 에너지 카 충전 등_ (향후 3~5년 내)

    ![14_3_2_미래블록체인응용분야](https://user-images.githubusercontent.com/54266900/69937856-2361c180-151f-11ea-8056-5f276f00e3b5.PNG)
<br><br>


<마인드맵>
![알기쉬운블록체인_마인드맵_14주차](https://user-images.githubusercontent.com/54266900/69938928-e77c2b80-1521-11ea-9141-6f6b7efd5e9a.jpg)



