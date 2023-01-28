## [ 2023.01.25.수 ]

- Get API
    - @RequestMapping : value와 method로 정의하여 API를 개발하는 방식
        
        ```java
        @RequestMapping(value = "/hello", method = RequestMethod.GET)
        public String getHello(){
        	return "Hello World!";
        }
        ```
        
    
    - @GetMapping (without Param)
    : 별도의 파라미터 없이 GET API를 호출하는 경우 사용되는 방법
        
        ```java
        @GetMapping(value = "/name")
        	public String getName() {
        	return "Flature";
        }
        ```
        
    
    - @PathVariable
        
        : GET 형식의 요청에서 파라미터를 전달하기 위해 URL에 값을 담아 요청하는 방법
        🌱 아래 방식은 @GetMapping에서 사용된 변수의 이름과 메소드의 매개변수와 일치시켜야 한다
        
        ```java
        @GetMapping(value="/variable1/{**variable**}")
        	public String getVariable1(@PathVariable String **variable**) {
        	return variable;
        }
        ```
        
        🌱 아래 방식은 @GetMapping에서 사용된 변수의 이름과 메소드의 매개변수를 다를 경우 사용하는 방식 (변수의 관리의 용이를 위해 사용되는 방식)
        
        ```java
        @GetMapping(value="/variable2/{**variable**}")
        public String getVariable2(@PathVariable("**variable**") String var){
        	return var;
        }
        ```
        
    
    - @RequestParam
        
        : GET 형식의 요청에서 쿼리 문자열을 전달하기 위해 사용되는 방법
        
        : ‘?'를 기준으로 우측에 {키}={값}의 형태로 전달되며, 복수 형태로 전달할 경우 & 를 사용한다
        
        ```
        http://localhost:8080/api/v1/get-api/request1?name=flature&email=thinkground.flature@gmail.com&organization=thinkground
        ```
        
        ```java
        @GetMapping(value = "/request1")
         public String getRequestParam1(
          @RequestParam String name,
          @RequestParam String email,
          @RequestParam String organization) {
         return name + " " + email + " " + organization;
        }
        ```
        
        🌱 아래 예시 코드는 어떤 요청 값이 들어올지 모를 경우 사용하는 방식
        
        ```
        http://localhost:8080/api/v1/get-api/request2?name=flature&email=thinkground.flature@gmail.com&organization=thinkground
        ```
        
        ```
        @GetMapping(value="/request2")
          public String getRequestParam2(@RequestParam Map param) {
            StringBuilder sb = new StringBuilder();
        
            param.entrySet().forEach(map -> {
            	sb.append(map.getKey() + " : " + map.getValue() + "\n");
          	});
        
            return sb.toString();
        }
        ```
        
    
    - DTO 사용
        
        : GET 형식의 요청에서 쿼리 문자열을 전달하기 위해 사용되는 방법
        
        : key와 value가 정해져있지만, 받아야할 파라미터가 많을 경우 DTO 객체를 사용한 방식
        
        ```
        @GetMapping(value="/request3")
        public String getRequest Param3(MemberDTO memberDTO){
          //return memberDTO.getName()+""+ memberDTO.getEmail() + + memberDTO.getOrganization();
          return memberDTO.toString();
        }
        
        public class MemberDTO {
          private String name;
          private String email;
          private String organization;
        }
        ```
        
        - DTO 작성
            - generate → getter and setter
            - generater → toString()
