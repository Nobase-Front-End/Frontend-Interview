# CORS(Cross Origin Resource Sharing)

## 문제 1. CORS란 무엇인가요?

CORS는 출처가 다른 리소스 공유에 관한 정책입니다.
보안 상의 이유로 모든 웹사이트는 기본적으로 SOP(Same-Origin Policy)를 따르는데요, 다시 말해 같은 출처에 대한 데이터 요청은 항상 허락되지만, 다른 출처로 데이터를 요청할 경우 특별한 규칙에 따라 허락을 받아야 합니다.
해당 규칙이 CORS로, 다른 출처에 데이터를 요청할 때 CORS 정책을 지키지 않으면 브라우저가 서버의 응답을 파기시키고, 클라이언트는 CORS에러를 만나게 됩니다.

## 문제 2. 그렇다면 CORS에서 이야기하는 출처란 무엇인가요?

CORS에서 이야기하는 출처는 URI를 구성하는 요소 중 Scheme, Host, Port를 말합니다.
3가지 중 하나라도 다른 경우 다른 출처로 간주하며, 그 중 포트 번호는 따로 명시되지 않은 경우 HTTP/HTTPS의 기본 포트번호를 기준으로 합니다.

**출처의 구성 요소**

- Scheme
  - `http://` , `https://`와 같은 프로토콜. http와 https는 다른 프로토콜이기 때문에, 호스트가 같더라도 서로 다른 출처로 인식하여 CORS에러가 발생할 수 있다.
- Host
  - `www.naver.com`과 같이, 다른 웹사이트와 구분되는 독립적인 이름. 우리가 흔히 주소라고 부르는 부분을 말하며, 뒷부분의 파라미터와 쿼리스트링 등은 포함하지 않는다.
  - 예: `www.pereng.com`과 `api.pereng.com`은 다른 출처
- Port
  - 생략되는 경우가 많으며, 명시할 경우 호스트 뒤에 붙는다.
    - 예: `https://www.pereng.com:8000`
  - http의 기본 포트번호는 `:80`, https의 기본 포트번호는 `:443` 이다.

## 문제 3. CORS 이슈를 해결하는 방법은 무엇인가요?

### 서버에서 해결하는 방법

- 응답 헤더에 `Access-Control-Allow-Origin` 을 설정합니다.
  `Access-Control-Allow-Origin`는 서버에서 허용할 출처의 URI를 담는 부분으로,
  `*`로 모든 출처를 허용하는 것보다는 `https://www.pereng.com`과 같이 구체적인 출처를 명시하는 것이 보안상 권장됩니다.
- 추가적으로, 클라이언트에서 요청 헤더에 `Credentials: include`옵션을 사용한 경우
  1. `Access-Control-Allow-Origin`에 `*` 를 사용 하면 CORS 에러가 발생합니다.
  2. 서버측 응답 헤더에 `Access-Control-Allow-Credentials: true` 를 설정해야 합니다.

### 클라이언트에서 해결하는 방법

Proxy를 설정하여 요청을 우회할 수 있습니다. proxy를 거치게 할 주소와 요청을 받을 서버의 주소를 이용하여, 마치 같은 주소에서 요청을 주고받는 것처럼 눈속임하여
CORS를 피해갈 수 있습니다.

이때, proxy 설정은 개발 단계에서만 적용된다는 점에 유의해야 합니다. 만약 개발 단계에서 서버 측 작업 없이 proxy만으로 CORS를 해결했을 경우, 배포 이후 출처에
따라 CORS 이슈가 다시 발생할 수 있습니다.

- 예시:

  ```jsx
  //  `/api`로 시작하는 요청의 주소를 원래 클라이언트 주소가 아닌 target에서 설정한 주소로 우회해준다.

  // 따라서 target의 주소와 요청을 받을 서버의 주소를 일치시키면, 동일한 출처로 판단하여 CORS 정책 위반을 피해갈 수 있다

  proxy: {
        '/api': {
          target: 'https://api.evan.com',
          changeOrigin: true,
          pathRewrite: { '^/api': '' },
        },
      }

  ```

#### 추가자료

답변을 작성하기 위해 정리한 내용입니다. 이해를 돕기 위해 첨부합니다.
[노션 링크](https://phase-dryosaurus-8ac.notion.site/CORS-9f5a68d44a8f4b46bbb647a9b50c2638)

#### 참고자료

[CORS는 왜 이렇게 우리를 힘들게 하는걸까?](https://evan-moon.github.io/2020/05/21/about-cors/#cors%EB%A5%BC-%ED%95%B4%EA%B2%B0%ED%95%A0-%EC%88%98-%EC%9E%88%EB%8A%94-%EB%B0%A9%EB%B2%95)
[MDN CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)
