## [ 2023.01.27.금 ]

- Put API
    - 해당 리소스가 존재하면 갱신하고, 리소스가 없을 경우에는 새로 생성해주는 API
    - 업데이트를 위한 메소드
    - 기본적인 동작 방식은 Post API와 동일
- Delete API
    - 서버를 통해 리소스를 삭제 하기 위해 사용되는 API
    - 일반적으로 @PathVariable을 통해 리소스 ID 등을 받아 처리
    - ex) 회원탈퇴
- ResponseEntity
    - Spring Framework에서 제공하는 클래스 중 HttpEntity라는 클래스를 상속받아 사용하는 클래스
    - 사용자의 HttpRequest에 대한 응답 데이터를 포함하는 클래스
    - HttpStatus
    - HttpHeaders
    - HttpBody

