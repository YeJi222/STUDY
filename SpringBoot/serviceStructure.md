## [ 2023.01.27.금 ] (Modified on 2023.05.27.토)

<img src="https://ifh.cc/g/xrdSk4.jpg" width="80%"> 

- Entity
    - 데이터베이스에 쓰일 컬럼과 여러 엔티티 간의 연관관계를 정의
    - 데이터베이스의 테이블을 하나의 엔티티로 생각해도 무방하다
    - 실제 데이터베이스의 테이블과 1:1로 매핑되는 db와 가장 가까운 객체
    - entity 객체를 만든 후, dao에 보낸다
    - 이 클래스의 필드는 각 테이블 내부의 컬럼(Column)을 의미한다
- Repository
    - Entity에 의해 생성된 데이터베이스에 접근하는 메소드를 사용하기 위한 인터페이스
    - Service와 DB를 연결하는 고리의 역할을 수행
    - 데이터베이스에 적용하고자 하는 CRUD를 정의하는 영역
    - JpaRepository를 사용할 것 -> db에 접근할 수 있는 기본 메소드를 제공해줌
    - JpaRepository에서 save, getById 같은 기본적인 메소드들을 제공해준다
- DAO (Data Access Object)
    - 데이터베이스에 접근하는 객체를 의미 (Persistance Layer)
    - spring boot 코드를 작성하는 영역
    - Service가 DB에 연결할 수 있게 해주는 역할
    - DB를 사용하여 데이터를 조회하거나 조작하는 기능을 전담
    - DAO는 db와 직접 통신하는 영역이므로, entity 값을 저장하거나 가져오는 작업들을 수행한다 
    - repository를 활용해서 사용하기 때문에, 접근하는 본질은 repository가 가지고 있고, 메소드들을 활용해주는게 DAO -> 직접적으로 사용하는 것은 DAO
    - DAO에서 repository를 활용해서 코드를 작성하므로 Repository import 필요 
- DTO (Data Transfer Object)
    - DTO는 VO(Value Object)로 불리기도 하며, 계층간 데이터 교환을 위한 객체를 의미
    - VO의 경우 Read Only의 개념을 가지고 있다

@Autowired : 자동으로 연결시켜 객체를 주입받음

Service vs. Handler
스프링 부트에서 Handler와 Service는 서로 다른 역할을 수행하는 구성 요소
- Handler
    - Handler는 클라이언트의 요청을 처리하고 응답을 반환하는 역할을 한다
    - 주로 컨트롤러(Controller)라고도 불리며, HTTP 요청을 받아 처리하고, 비즈니스 로직을 호출하거나 다른 컴포넌트와의 상호작용을 조정
    - Handler는 클라이언트와의 인터페이스 역할을 하며, 요청을 분석하고 해당 요청에 대한 적절한 응답을 생성
- Service:
    - Service는 비즈니스 로직을 수행하는 역할
    - 주로 비즈니스 로직을 구현한 클래스로, 데이터베이스 조작, 외부 시스템과의 통신, 알고리즘 등을 처리
    - Service는 Handler나 다른 Service와의 협업을 통해 요청을 처리하고 결과를 반환
    - Service는 일반적으로 트랜잭션 관리, 데이터 유효성 검증 등을 담당하며, Handler나 다른 컴포넌트들이 비즈니스 로직에 직접 접근하는 것을 방지하기 위해 중간 계층으로 사용된다

- 일반적인 흐름은 클라이언트의 요청이 Handler에 도달하고, Handler는 요청을 검증하고 적절한 Service를 호출하여 비즈니스 로직을 처리
- Service는 필요한 데이터를 조작하고 처리한 결과를 다시 Handler로 반환
- Handler는 최종적으로 클라이언트에게 응답을 전달
- 이렇게 구성된 Handler와 Service는 역할과 책임이 분리되어 코드의 유지 보수성과 가독성을 향상시킨다
- Handler는 주로 클라이언트와의 인터페이스 역할을 하며, Service는 비즈니스 로직을 담당하는 구성 요소로 사용된다
