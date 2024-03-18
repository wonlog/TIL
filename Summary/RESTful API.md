REST는 REpresentational State Transfer의 약어이다.  
클라이언트와 서버가 데이터를 주고 받는 방식에 대한 아키텍처 스타일이다.  
여섯가지 기본 원칙이 있고, 이 가이드를 준수한 인터페이스는 `RESTful` 하다고 표현한다.  

### RESTful API를 위한 6가지 원칙
- **Client-Server 구조**  
  클라이언트와 서버는 서로 독립적이어야 하며, 클라이언트는 오직 URLs 리소스만 알아야 한다.
  클라이언트와 서버의 인터페이스가 변경되지 않는 한, 이 둘은 독립적으로 개발되거나 대체될 수 있게 유지해야 한다.
  
- **Stateless**  
  클라이언트의 모든 요청에는 해당 요청을 이해할 수 있는 모든 정보가 포함되어야 한다.
  서버는 HTTP 요청에 대한 어떤 것도 저장하지 않는다.
  컨텍스트를 유지해야 하는 세션, 인증과 인가에 대한 정보 또한 클라이언트에만 보관되며, 각 요청 시 해당 정보를 모두 포함하여 서버에 요청한다.
  
- **Cacheable**  
  서버는 Response cache-control 헤더에 해당 요청이 캐싱이 가능한 지에 대한 여부를 제공해야 한다.
  
- **Uniform interface**  
  보편적인 소프트웨어 엔지니어링 원칙을 component interface에 적용하면, 전체적인 시스템 아키텍처는 단순화되고 각 상호작용에 대한 가시성이 개선된다.
  이름 그대로 일관된 인터페이스를 얻기 위해 REST에서는 4가지 인터페이스 규칙을 정의하였다.
    - identification of resources
    - manipulation of resources through representations
    - self-descriptive messages
    - hypermedia as the engine of application state
 
      
- **Layered system**  
  
- **Code on demand**

---

### RESTful API를 위한 네이밍 규칙

1. **리소스를 표현하기 위해 명사를 사용하라**

2. **일관성이 핵심이다**

3. **CRUD 함수명을 사용하지 마라**

4. **필터를 위해 쿼리 파라미터를 사용해라**

### 함께 읽은 글
[RESTful API를 위한 6가지 원칙과 네이밍 규칙](https://prohannah.tistory.com/156)
https://restfulapi.net
