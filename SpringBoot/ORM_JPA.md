## [ 2023.01.27.금 ]

- ORM (Object Relational Mapping)
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2dc67ccf-2b19-4205-bb2d-57657550ec41/Untitled.png)
    
    - 어플리케이션의 객체와 관계형 데이터베이스의 데이터를 자동으로 매핑해주는 것을 의미
        - Java의 데이터 클래스와 관계형 데이터베이스의 테이블을 매핑
    - 객체지향 프로그래밍과 관계형 데이터베이스의 차이로 발생하는 제약사항을 해결해주는 역할을 수행
    - 대표적으로 JPA, Hibernate 등이 있다 (Persistent API)
- ORM의 장점
    - SQL 쿼리가 아닌 직관적인 코드로 데이터를 조작할 수 있다
        - 개발자가 보다 비즈니스 로직에 집중할 수 있다
    - 재사용 및 유지보수가 편리
        - ORM은 독립적으로 작성되어 있어 재사용이 가능
        - 매핑정보를 명확하게 설계하기 때문에 따로 데이터베이스를 볼 필요가 없다
    - DBMS에 대한 종속성이 줄어든다
        - DBMS를 교체하는 작업을 비교적 적은 리스크로 수행 가능
- ORM의 단점
    - 복잡성이 커질 경우 ORM만으로 구현하기 어렵다
        - 직접 쿼리를 구현하지 않아 복잡한 설계가 어려움
    - 잘못 구현할 경우 속도 저하 발생
    - 대형 쿼리는 별도의 튜닝이 필요할 수 있다
- JPA (Java Persistance API)
    
    ![https://slid-users-assets-v1-seoul.s3.ap-northeast-2.amazonaws.com/public/capture_images/095286546e6140c597500755a86160f6/b4bfa8c3-ed7d-44e4-9307-858704c9ea3d.png](https://slid-users-assets-v1-seoul.s3.ap-northeast-2.amazonaws.com/public/capture_images/095286546e6140c597500755a86160f6/b4bfa8c3-ed7d-44e4-9307-858704c9ea3d.png)
    
    - JPA는 Java Persistance API의 줄임말이며, ORM과 관련된 인터페이스의 모음
    - Java 진영에서 표준 ORM으로 채택되어 있다
    - ORM이 큰 개념이라고 하면, JPA는 더 구체화 시킨 스펙을 포함한다
- Hibernate
    - ORM Framework 중 하나
    - JPA의 실제 구현체 중 하나이며, 현재 JPA 구현체 중 가장 많이 사용된다
- Spring Data JPA
    - Spring Framework에서 JPA를 편리하게 사용할 수 있게 지원하는 라이브러리
        - CRUD 처리용 인터페이스 제공
        - Repository 개발 시 인터페이스만 작성하면 구현 객체를 동적으로 생성해서 주입
        - 데이터 접근 계층 개발시 인터페이스만 작성해도 된다
    - Hibernate에서 자주 사용되는 기능을 조금 더 쉽게 사용할 수 있게 구현
