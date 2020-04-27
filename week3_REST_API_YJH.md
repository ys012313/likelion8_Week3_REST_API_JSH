# Rest API

Created: Apr 26, 2020 2:00 PM
Created By: Jihyun Yeom
Last Edited Time: Apr 26, 2020 2:41 PM

# 🧐Rest API

## REST(REpresentational State Transfer)

### : HPPT 기반으로 필요한 자원(DBMS, 이미/동영상/문서(PDF)와 같은 파일, 서비스(이메일 전송, PUSH 메시지 등))에 접근하는 방식을 정해놓은 아키텍쳐

## REST의 속성

1. **서버에 있는 모든 resource는 각 resource 당 클라이언트가 바로 접근할 수 있는 고유 URI가 존재한다.**
2. **서비스에 자유도가 높고 유연한 아키텍쳐 적응이 가능하다.
→모든 요청은 클라이어느탁 요청할 때마다 필요한 정보를 주기 때문에 서버에서는 세션 정보를 보관할 필요가 없기 때문이다.**
3. **HTTP 메소드를 사용한다.
→ 모든 resource는 일번적으로 http 인터페이스인 GET, POST,PUT,DELETE 4개의 메소드로 접근 되어야 한다.**
4. **서비스 내에 하나의 resource가 주변에 연관된 resource들과 연결되어 표현이 되어야 한다.**

## REST의 구성 요소

### : 자원(resource), method, message

### 1. Resource

**1. REST에서는 URI(Uniform Resource Identifier)를 통해 자원에 접근한다.**

**2. '/'의 쓰임새**

**(1) 슬래시 구분자(/)는 계층 관계를 나타낸다.**

**ex) [https://github.com/yeomja99/likelion8_github_assignment](https://github.com/yeomja99/likelion8_github_assignment)**

**'github'부터 하위 소속들을 거쳐 '[likelion8_github_assignment](https://github.com/yeomja99/likelion8_github_assignment)' 까지 도달하는 구조임을 알 수 있다.**

**(2) URI 마지막 문자로 슬래시(/)를 포함하지 않는다.**

**3. resource 간의 관계를 표현하는 방법**

```html
**/리소스명/리소스 ID/관계까 있는 다른 리소스명

ex)
GET : /users/{userid}/devices (일반적으로 소유 'has'의 관계를 표현할 떄)
GET : /users/{userid{/likes/devices (관계명이 애매하거나 구체적 표현이 필요할 때)**
```

**4. URI에서는 '_'보다 '-'을 권장한다.**

**5. URI 경로에서는 소문자가 적합하다. (대소문자에 따라 다른 리소스로 인식)**

**6. 파일 확장자는 URI에 포함시키지 않는다. → Accept header 사용**

### 2. HTTP 메소드

[HTTP 메소드](https://www.notion.so/b03bd4cd7dcb4124bd6d4695b7ccf86e)

### 3. Message

1. **구성 : HTTP header와 body, 응답상태코드**
    1. **Body : 자원에 대한 정보를 전달**
    2. **Header : HTTP 바디에 어떤 포맷으로 데이터가 담겼는지 정의**
    3. **응답 상태 코드 : 응답 상태 코드를 통해 리소스 요청에 대한 응답을 할 수 있음.** 

## REST의 장단점

- **장점**
    1. **언어와 플랫폼에 독립적이다.**
    2. **SOAP(다른 통신 방식)보다 개발이 쉽고 단순하다.**
    3. **REST가 지원하는 Framework나 언어 등 도구들이 없어도 구현이 가능하다.**
    4. **기존 웹 인프라를 사용가능하다. 
    → HTTP를 그대로 사용하기 때문**
- **단점**
    1. **HTTP 프로토콜만 사용이 가능하다.**
    2. **P2P 통신 모델을 가정했기 때문에 둘 이상을 대상으로 하는 분산환경에는 유용하지 않다.**
    3. **보안, 정책 등에 대한 표준이 없기 때문에 관리가 어렵고 이러한 부분까지 고려해서 구현할 경우 설계나 구현에서 비교적 어려움을 갖는다.**

## REST가 API로써는 어떻게 사용될까?

### API는 한 프로그램과 다른 프로그램을 이어주는 접착제 역할이다. 즉, REST API는 내가 원하는 API를 가져와 사용할 때 REST 방식(URI 형식으로 request) 해당 데이터베이스에 요청하는 식으로 작동한다고 생각하면 될 것 같다!