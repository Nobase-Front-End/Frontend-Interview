# REST-API

## 1. REST가 등장하게 된 배경

WEB은 정보들을 하이퍼텍스트로 연결하여 인터넷에서 공유한다. HTTP를 설계하던 사람 중 한 명이었던 로이필딩은 기존의 웹을 망가트리지 않으면서 HTTP를 개선하기 위한 방법을 생각하다가 REST를 만들었다. 즉, REST는 **독립적인 진화**를 목적으로 등장했다.
<br>
<br>

## 2. REST란?

REST는 분산하이퍼 미디어 시스템, 즉 **진화하는 웹**을 위한 **제약 조건의 집합**이다. 네트워크 리소스를 정의하고, 클라이언트와 서버가 데이터를 주고 받는 방식에 대한 원칙을 포함한다.

REST 제약 조건은 아래와 같다.

- client-server: 분산 컴퓨팅 구조로 자원을 제공하는 서버와 자원을 요청하는 클라이언트로 구분하는 것을 의미한다. 구조를 작은 단위로 분리함으로써 클라이언트와 서버가 각각 독립적으로 개선되도록 한다.
- stateless: 서버가 클라이언트의 이전 요청 상태를 갖고 있지 말아야 함을 의미한다. 즉, 클라이언트가 관련 상태를 서버에게 전송해서 매 요청이 독립적으로 이해되어야 한다.
- cacheable: 웹 캐시는 서버 지연을 줄이기 위해 웹 문서들을 임시 저장하는 기술이다. 클라이언트는 서버 응답을 캐싱할 수 있어야 한다. 잘 관리된 캐싱은 클라이언트와 서버의 상호작용을 제거하여 확장성과 성능을 향상시킬 수 있다.
- uniform interface
- layered system: 계층화 시스템의 낮은 계층은 상위 계층을 돕는 기능이나 서비스를 제공한다. 중간 서버는 로드밸런싱(컴퓨터의 중앙처리장치나 저장장치에게 작업을 나누는 것)이나 공유 캐시 기능을 제공한다.
- code on demand: 서버가 클라이언트에 코드를 보내서 실행할 수 있어야한다. 즉, 자바스크립트다!

HTTP만 잘 따르면 다음 조건들의 대부분을 만족할 수 있다. 하지만 uniform interface는 만족하기가 어렵다.
<br>
<br>

## 3. uniform interface란?

서버와 클라이언트는 동시에 진화를 하는 것이 아니라 독립적으로 진화한다. 그렇기 때문에 서버의 기능이 변경되어도 클라이언트를 업데이트할 필요가 없게 만들려면 uniform interface가 필요하다.

uniform interface의 제약조건은 아래와 같다.

- identification of resources: 리소스가 uri로 식별되어야 한다.
- manipulation of resources through representations: representation 전송을 통해서, 즉 HTTP 메세지에 표현을 담아서 리소스를 조작해야한다.
- self-descriptive messages: 메세지의 내용으로 온전히 해석이 가능해야 한다.
  ⇒ 서버나 클라이언트가 변경되더라도 전송되는 메세지는 언제나 해석 가능해진다.
- hypermedia as the engine of application state(HATEOAS): 애플리케이션의 상태는 하이퍼링크를 통해 전이되어야 한다.
  ⇒ 서버가 링크를 동적으로 바꿀 수 있다.

웹은 REST를 잘 만족하기 때문에

- 웹 페이지를 변경했다고 웹 브라우저를 업데이트할 필요가 없다.
- 웹 브라우저가 업데이트 됐다고 웹 페이지를 변경할 필요가 없다.
- HTTP, HTML 명세가 변경되어도 웹은 잘 동작한다.

특히, 웹은 버전업이 되더라도 하위 호환성을 깨뜨리지 않으려는 노력을 한다. 아래의 예시들이 하위 호환성을 깨뜨리지 않기 위한 노력이다.

- referer이 오타지만 아직까지 고치지 않았다.
- charset이 잘못된 표현이지만 (원래는 encoding이라고 해야하는데) 고치지 않고있다.
  <br>
  <br>

## 4. REST API란?

REST 아키텍쳐 스타일을 따르는 API다. REST API는 하이퍼텍스트(링크)를 포함한 self-descriptive한 메세지의 uniform interface를 통해 리소스에 접근한다.

웹 페이지는 media type이 HTML이고, HTTP API는 Json이다.

HTML은 하이퍼링크가 잘 정의되어 있고, html명세에 모든 태그가 정의되어 있어 self-descriptive하다. 하지만 Json은 하이퍼링크가 정의되어 있지 않고, 문법적인 해석은 가능하지만 의미를 해석하기 위해 별도의 문서가 필요하기 때문에 self-descriptive하지 않다.

따라서 REST API가 되게 하려면 self-descriptive와 HATEOAS를 만족시켜야 한다.

- self-descriptive는 custom media type을 정의하거나 profile link relation으로 만족시킬 수 있다.
- HATEOAS는 HTTP 헤더나 본문에 링크를 담아 만족시킬 수 있다.
  <br>
  <br>

## 참고 자료

[위키백과](https://ko.wikipedia.org/wiki/REST)

[그런 REST API로 괜찮은가](https://www.youtube.com/watch?v=RP_f5dMoHFc&t=284s)
