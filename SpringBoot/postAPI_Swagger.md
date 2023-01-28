## [ 2023.01.26.목 ]

- Post API : 리소스를 추가하기 위해 사용되는 API
    - @PostMapping:POST API를 제작하기 위해 사용되는 어노테이션(Annotation)
    - @RequestMapping + POST method 의 조합
    : 일반적으로 추가하고자 하는 Resource를 http body에 추가하여 서버에 요청
    : 그렇기 때문에 @RequestBody를 이용하여 body에 담겨있는 값을 받아야함
    
    ```java
    // http://localhost:8080/api/v1/post-api/member
    @PostMapping(value = "/member")
    public String postMember(@RequestBody Map postData) {
    	StringBuilder sb = new StringBuilder();
    
    	postData.entrySet().forEach(map -> {
    		sb.append(map.getKey() + " : " + map.getValue() + "\n");
    	});
    
    	return sb.toString();
    }
    ```
    
- DTO 사용
    - key와 value가 정해져있지만, 받아야할 파라미터가 많을 경우 DTO 객체를 사용한 방식
    
    ```java
    // http://localhost:8080/api/v1/post-api/member2
    @PostMapping(value = "/member2")
    	public String postMember Dto(@RequestBody MemberDTO memberDTO) {
    	return memberDTO.toString();
    }
    ```
    
    - @RequestBody 꼭 필요
        
        → 안붙이면 MemberDTO의 객체 값들이 들어오지 않아서 null로 된다
        
- Swagger
    - 서버로 요청되는 API 리스트를 HTML 화면으로 문서화하여 테스트 할 수 있는 라이브러리
    - 이 라이브러리는 서버가 가동되면서 @RestController를 읽어 API를 분석하여 HTML 문서를 작성한다
    - Swagger가 필요한 이유
        - REST API의 스펙을 문서화 하는 것은 매우 중요
        - API를 변경할 때마다 Reference 문서를 계속 바꿔야하는 불편함이 있음
    - Swagger 설정 방법
        - @Configuration : 어노테이션 기반의 환경 구성을 돕는 어노테이션
        - loC Container에게 해당 클래스를 Bean 구성 Class 임을 알려줌
        - @Bean : 개발자가 직접 제어가 불가능한 외부 라이브러리 등을 Bean으로 만들 경우에 사용
