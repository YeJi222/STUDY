## [ 2023.01.27.금 ]

- Lombok
    - 반복되는 메소드를 Annotation을 사용하여 자동으로 작성해주는 라이브러리
    - 일반적으로 VO, DTO, Model, Entity 등의 데이터 클래스에서 주로 사용된다
    - 대표적으로 많이 사용되는 Annotation
    - @Getter
    - @Setter
    - @NoArgConstructor
    - @AllArgConstructor
    - @Data
    - @ToString
- Lombok 사용법
    - 라이브러리 의존성 설정
        
        ```xml
        <dependency>
        	<groupId>org.projectlombok</groupId>
        	<artifactId>lombok</artifactId>
        	<optional>true</optional>
        </dependency>
        ```
        
- Lombok의 대표적인 annotation
    - @Getter
    - @Setter
    - 해당 클래스에 선언되어 있는 필드를 기반으로 'getField', 'setField' 와 같은 식으로 자동으로 메소드를 생성
        
        ```java
        @Getter
        @Setter
        public class MemberDTO {
        	private String name;
        	private String email;
        	private String organization;
        }
        ```
        
        👇🏻 아래와 같은 역할 (getter와 setter를 별도로 따로 작성할 필요가 없다)
        
        ```java
        public String getName() {
        	return name;
        }
        public void setName(String name) {
        	this.name = name;
        }
        public String getEmail() {
        	return email;
        }
        public void setEmail (String email) {
        	this.email = email;
        }
        public String getOrganization() {
        	return organization;
        }
        public void setOrganization(String organization) {
        	this.organization = organization;
        }
        ```
        
    - @NoArgsConstructor
        
        : 파라미터가 없는 생성자를 생성
        
    - @AllArgsConstructor
        
        : 모든 필드값을 파라미터로 갖는 생성자를 생성
        
    - @RequiredArgsConstructor
        
        : 필드값 중 final이나 @NotNull인 값을 갖는 생성자를 생성
        
        ```java
        @NoArgsConstructor
        @RequiredArgsConstructor
        @AllArgsConstructor
        public class MemberDTO {
        	private String name;
        	private String email;
        	private String organization;
        }
        ```
        
    - @ToString
        - toString 메소드를 자동으로 생성해주는 기능
        - @ToString 어노테이션에 exclude 속성을 사용하여 특정 필드를 toString에서 제외시킬 수 있다
        
        ```java
        @ToString
        public class MemberDTO {
        	private String name;
        	private String email;
        	private String organization;
        }
        ```
        
        ```java
        @ToString(exclude = "email")
        public class MemberDTO {
        	private String name;
        	private String email;
        	private String organization;
        }
        ```
        
        ```java
        @Override
        public String toString() {
        	return "MemberDTO{"+
        		"name='" + name + '\" +
        		", email='" + email + '\" +
        		", organization='" + organization + '\" +
        		'}';
        }
        ```
        
    - @EqualsAndHashCode
        - equals, hashCode 메소드를 자동으로 생성
        - equals : 두 객체의 내용이 같은지 동등성(equality)를 비교하는 연산자
        - hashCode : 두 객체가 같은 객체인지 동일성(identity)를 비교하는 연산자
        - callSuper 속성을 통해 메소드 생성시 부모 클래스의 필드까지 고려할지 여부 설정 가능
            - callSuper = true → 부모 클래스 필드 값들도 동일한지 체크
    - @Data
        - 해당 어노테이션을 사용하면, 앞서 나온 기능들을 한번에 추가해줌
        - @Getter
        - @Setter
        - @RequiredArgsConstructor
        - @ToString
        - EqualsAndHashCode
- Getter 사용법
    - @Getter 선언 → 마우스 오른쪽 -> Refactor -> Delombok -> @Getter
        
        : 메소드를 만들어준다
        
        ```java
        import lombok.Getter;
        import lombok.Setter;
        import lombok.ToString;
        
        @Getter
        @Setter
        @ToString
        public class MemberDTO {
            private String name;
            private String email;
            private String organization;
        }
        ```
        
        → @Getter, @Setter, @ToString로 코드 단축
