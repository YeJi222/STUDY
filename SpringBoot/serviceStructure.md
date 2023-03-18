## [ 2023.01.27.금 ] (Modified on 2023.03.18.토)

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
