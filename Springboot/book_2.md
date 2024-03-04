2.1 서버 간 통신

MSA (Microserice Architecture)
서비스 규모를 작게 나누어 구성한 아키텍처  

서버 간 통신  
한 서버가 다른 서버에 통신을 요청하는 것으로 한 대는 서버, 한 대는 클라이언트가 되는 구조

Servlet
클라이언트 요청을 처리하고 결과를 반환하는 자바 웹 프로그래밍 기술  
서블릿 컨테이너(Servlet Contatiner)에서 관리한다.  
톰캣은 WAS의 역할과 서블릿 컨테이너 역할을 수행하는 대표적인 컨테이너이다.  

스프링 부트의 동작 구조  
![image](https://github.com/wonlog/TIL/assets/149459170/d9aae0bf-7f42-4411-983f-981011805499)  

2.4 디자인 패턴: GoF 패턴 정리  
![image](https://github.com/wonlog/TIL/assets/149459170/361d5419-aed2-42ad-8fc0-e47ec91fa99a)  

생성 패턴
> 객체 생성에 사용되는 패턴으로, 객체를 수정해도 호출부가 영향을 받지 않는다.

구조 패턴  
> 객체를 조합해서 더 큰 구조를 만든다.

행위 패턴  
> 객체 간의 알고리즘이나 책임 분배에 관한 패턴
> 객체 하나로는 수행할 수 없는 작업을 여러 객체를 이용해 작업을 분배한다. 결합도 최소화를 고려할 필요가 있다.

2.5 REST API  
REST란? (REST: Representational State Transfer)  
> 월드 와이드 웹(WWW)과 같은 분산 하이퍼미디어 시스템 아키텍처의 한 형식
> 주고받는 자원(resource)에 이름을 규정하고 URI에 명시해 HTTP 메서드를 통해 해당 자원의 상태를 주고받는 것

REST API란? (API: Application Programming Interface)  
> 애플리케이션에서 제공하는 인터페이스
> API를 통해 서버 또는 프로그램 사이를 연결할 수 있다.
