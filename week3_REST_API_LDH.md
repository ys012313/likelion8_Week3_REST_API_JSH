과거에는 브라우저가 웹서버에 웹페이지를 요청하여 클라이언트를 제공하여 웹페이지가 작동하였지만, 최근에는 SPA(Signle-Page-Application)를 이용하여 클라이언트(대표적으로 React, Vue, Angular)를 구현하며, 클라이언트를 서버와 분리하여 클라이언트 로직을 분명히 한다. 또한 서버에 API를 요청하므로써 웹 어플리케이션을 개발한다.

---

## REST(Representational State Transfer) 아키텍쳐 스타일을 따르는 API

### REST? →분산 하이퍼미디어 시스템(예: 웹)을 위한 아키텍쳐 스타일

### 아키텍쳐 스타일 → 제약조건의 집합

---

### REST API는 다음의 구성으로 이루어져있다.

- 자원 (Resource) - URL
- 행위 (Verb) - Http method
- 표현 (Representations)

---

제약조건을 모두 지켜야 "REST를 따른다" 라고 말하는 게 가능하다. 그렇다면 REST는 어떤 제약조건들로 구성되어있을까?

1. client-server
    - 클라이언트는 유저와 관련된 처리를, 서버는 REST api를 제공함으로써 각각의 역활이 확실하게 구분되고 일관적인 인터페이스로 분리되어 작동할 수 있게 한다.
2. stateless
    - REST는 HTTP의 특성을 이용하기 때문에 무상태성을 갖는다. 즉 서버에서 어떤 작업을 하기 위해 상태정보를 기억할 필요가 없고 들어온 요청에 대해 처리만 해주면 되기 때문에 구현이 쉽고 단순해진다.
3. cache
    - HTTP라는 기존 웹표준을 사용하는 REST의 특징 덕분에 기본 웹에서 사용하는 인프라를 그대로 사용 가능하다.
4. **uniform interface**
    - Uniform Interface는 Http 표준에만 따른다면 모든 플랫폼에서 사용이 가능하며, URI로 지정한 리소스에 대한 조작을 가능하게 하는 아키텍처 스타일을 말한다.
5. layered system
    - 클라이언트와 서버가 분리되어 있기 때문에 중간에 프록시 서버, 암호화 계층등 중간매체를 사용할 수 있어 자유도가 높다.
6. code-on-demand (optional)
    - 서버에서 코드를 client로 보내서 실행할 수 있어야한다.(JavaScript)

사실 REST는 이키텍쳐 스타일이면서 동시에 하이브리드 아키텍쳐 스타일이라고도 말하는데, 그 이유는 아키텍쳐 스타일인 동시에 아키텍쳐 스타일의 집합이기 때문이다. 

이미 HTTP만 따라도 대체로 오늘날 REST API를 굴리는 것들은 대체로 잘 지킨다고 할 수 있다. 그러나 uniform interface는 잘 만족을 못한다. 그렇다면 uniform interface를 살펴보자

---

### Uniform Interface의 제약조건

- identification of resources : 리소스가 URI로 식별되면 된다.
- manipulation of resources through representations : representation 전송을 통해서 resource를 조작해야 된다.(리소스를 만들거나 수정하거나 삭제할 때 http 메시지에 표현을 담아 전송하는 것)
- **self-descriptive messages : Json을 이용한 메세지 포멧을 이용하여 직관적으로 이해할 수 있고 REST api 메세지만으로 그 요청이 어떤 행위를 하는지 알 수 있다.**
- **hypermedia as the engine of application state(HATEOAS)**

마지막 두가지 제약조건은 REST API로 오늘날 알려져있는 거의 모든것들이 지키지 못한다.  

---

## REST API를 설계하는 법

### URL는 정보의 자원을 표현한다.

제목 대로 URL는 정보의 자원을 표현해야하기 때문에 설계 할때 몇 가지 지켜야 할 것들이 있다.

**1) 소문자를 사용한다.**

- 대소문자에 차이를 두기 떄문에(foo.com과 FOo.com은 서로 다르다) 혼란을 줄 수 있기 때문에 지양하는 것이 좋다.

**2) 하이픈( - )을 사용한다.**

**3) 확장자를 사용하지 않는다.**

```
http://foo.com/world.txt
http://foo.com/world.png
```

위와 같이 했을 때, 확장자에 때른 url을 만들어야 하기 떄문에 비효울적일 수 있다.

**4) 밑줄( __ )은 사용하지 않는다.**

### 자원에 대한 행위는 HTTP Method로 표현한다

아래가 대표적으로 사용하는 4가지 Mehtod이다.

[Untitled](https://www.notion.so/10ed25e0124e4d4b81e4cbd8a5538ac8)

예를 들어 글을 수정하기 위해선 아래와 같이 할 수 있다.

```
POST /posts/put/:id (X)
POST /posts/update/:id (X)

PUT /posts/:id (O)
```

참고 자료

- “[HTTP] REST API 란.” 개인 블로그. 2019년 10월 28일 수정, 2019년 4월 29일 접속, [https://velog.io/@wlsdud2194/HTTP-REST-API-란](https://velog.io/@wlsdud2194/HTTP-REST-API-%EB%9E%80).
- “그런 REST API로 괜찮은가.” YouTube. 2017년 11월 20일 수정, 2020년 4월 29일 접속, [https://www.youtube.com/watch?v=RP_f5dMoHFc&t=29s](https://www.youtube.com/watch?v=RP_f5dMoHFc&t=29s).