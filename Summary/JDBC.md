JDBC(Java Database Connectivity)
Java 기반 애플리케이션의 데이터를 데이터베이스에 저장 및 업데이트하거나, 데이터베이스에 저장된 데이터를 Java에서 사용할 수 있도록 하는 자바 API
Java 애플리케이션에서 데이터베이스에 접근하기 위해 JDBC API를 사용하여 데이터베이스에 연동할 수 있으며, 데이터베이스에서 자료를 쿼리(Query)하거나 업데이트하는 방법을 제공


JDBC는 3가지 기능을 표준 인터페이스로 정의하여 제공한다.

java.sql.Connection - 연결
java.sql.Statement - SQL을 담은 내용
java.sql.ResultSet - SQL 요청 응답

 
Spring Data JDBC, Spring Data JPA 등과 같은 기술이 등장하면서 JDBC API를 직접적으로 사용하는 일은 줄어들었다.
하지만, Spring Data JDBC, Sprind Data JPA와 같은 기술도 데이터베이스와 연동하기 위해 내부적으로 JDBC를 이용하기 때문에 JDBC의 동작 흐름에 대해 알 필요가 있다.
![image](https://github.com/wonlog/TIL/assets/149459170/a74a811b-3671-42e8-895d-dd42b36f35f2)

JDBC 드라이버

데이터베이스와의 통신을 담당하는 인터페이스
Oracle, MS SQL, MySQL 등과 같은 데이터베이스에 알맞은 JDBC 드라이버를 구현하여 제공
JDBC 드라이버의 구현체를 이용해서 특정 벤더의 데이터베이스에 접근할 수 있음

JDBC API 사용 흐름
JDBC API의 구성 요소들의 동작 흐름은 다음과 같다.

![image](https://github.com/wonlog/TIL/assets/149459170/3245e193-ce5e-43cf-af62-5b82dc4f74f7)

JDBC 드라이버 로딩 : 사용하고자 하는 JDBC 드라이버를 로딩한다. JDBC 드라이버는 DriverManager 클래스를 통해 로딩된다.
Connection 객체 생성 : JDBC 드라이버가 정상적으로 로딩되면 DriverManager를 통해 데이터베이스와 연결되는 세션(Session)인 Connection 객체를 생성한다.
Statement 객체 생성 : Statement 객체는 작성된 SQL 쿼리문을 실행하기 위한 객체로 정적 SQL 쿼리 문자열을 입력으로 가진다.
Query 실행 : 생성된 Statement 객체를 이용하여 입력한 SQL 쿼리를 실행한다.
ResultSet 객체로부터 데이터 조회 : 실행된 SQL 쿼리문에 대한 결과 데이터 셋이다.
ResultSet, Statement, Connection 객체들의 Close : JDBC API를 통해 사용된 객체들은 생성된 객체들을 사용한 순서의 역순으로 Close 한다.

커넥션 풀(Connection Pool)
JDBC API를 사용하여 데이터베이스와 연결하기 위해 Connection 객체를 생성하는 작업은 비용이 많이 드는 작업 중 하나이다.
 
커넥션 객체를 생성하는 과정

애플리케이션에서 DB 드라이버를 통해 커넥션을 조회한다.
DB 드라이버는 DB와 TCP/IP 커넥션을 연결한다. (3 way handshake와 같은 네트워크 연결 동작 발생)
DB 드라이버는 TCP/IP 커넥션이 연결되면 아이디와 패스워드, 기타 부가 정보를 DB에 전달한다.
DB는 아이디, 패스워드를 통해 내부 인증을 거친 후 내부에 DB를 생성한다.
DB는 커넥션 생성이 완료되었다는 응답을 보낸다.
DB 드라이버는 커넥션 객체를 생성해서 클라이언트에 반환한다.

이처럼 커넥션을 새로 만드는 것은 비용이 많이 들며, 비효율적이다.
 
이러한 문제를 해결하기 위해 애플리케이션 로딩 시점에 Connection 객체를 미리 생성하고, 애플리케이션에서 데이터베이스에 연결이 필요할 경우 미리 준비된 Connection 객체를 사용하여 애플리케이션의 성능을 향상하는 커넥션 풀(Connection Pool)이 등장하게 된다.
 
Connection 객체를 미리 생성하여 보관하고 애플리케이션이 필요할 때 꺼내서 사용할 수 있도록 관리해 주는 것이 Connection Pool이다.
 
커넥션 풀 동작 구조
![image](https://github.com/wonlog/TIL/assets/149459170/44349df7-fa93-47de-9594-e0f147167b41)

애플리케이션을 시작하는 시점에 커넥션 풀은 필요한 만큼 커넥션을 미리 생성하여 보관한다.
서비스의 특징과 스펙에 따라 생성되는 Connection 객체의 개수는 다르지만 일반적으로 기본값으로 10개를 생성한다.
커넥션 풀에 들어있는 Connection 객체는 TCP/IP로 DB와 연결되어 있는 상태이기 때문에 즉시 SQL을 DB에 전달할 수 있다.
즉, DB 드라이버를 통해 새로운 커넥션을 획득하는 것이 아닌 이미 생성되어 있는 커넥션을 참조하여 사용하게 된다.
커넥션 풀에 있는 커넥션을 요청하면 커넥션 풀은 자신이 가지고 있는 커넥션 객체 중 하나를 반환한다.

 
따라서, DB 드라이버를 통해 커넥션을 조회, 연결, 인증, SQL을 실행하는 시간 등 커넥션 객체를 생성하기 위한 과정을 생략할 수 있게 된다.
 
Spring Boot 2.0 이전 버전에서는 Apache 재단의 오픈 소스인 Apache Commons DBCP를 주로 사용하였지만, 스프링 부트 2.0 이후 HikariCP를 기본 DBCP로 채택하여 사용되고 있다.




출처: https://ittrue.tistory.com/250 [IT is True:티스토리]
