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

- Swagger 통한 실습
    - [http://localhost:9090/swagger-ui/index.html](http://localhost:9090/swagger-ui/index.html#/delete-controller/DeleteVariableUsingDELETE)
    - put-controller
        - member   
        <img src="https://ifh.cc/g/RLdbqm.jpg" width="80%">
            
            {
                "name" : "yeji",
                "phone-number" : "010-1234-5678"
            }
        <img src="https://ifh.cc/g/3vFZD4.jpg" width="80%"> 
    
        
        - member1
        <img src="https://ifh.cc/g/ywm4Lv.jpg" width="80%"> 
            <br>
            - DTO 클래스 정해져 있는 값으로 전달해 주어야 한다  
           
            {
                "email": "21900806@handong.ac.kr",
                "name": "HongYeJi",
                "organization": "Handong"
            }
                
            - member1은 toString()에서 return한 형태로 response
                
                
        - member2
            - member2는 json 형태로 response
                
                ![https://slid-users-assets-v1-seoul.s3.ap-northeast-2.amazonaws.com/public/image_upload/74d499a23b8243008e0d7dac2359dc9b/23476583-d03b-4419-9fb7-eb47cc966fec.png](https://slid-users-assets-v1-seoul.s3.ap-northeast-2.amazonaws.com/public/image_upload/74d499a23b8243008e0d7dac2359dc9b/23476583-d03b-4419-9fb7-eb47cc966fec.png)
                
        - member3
            
            ![https://slid-users-assets-v1-seoul.s3.ap-northeast-2.amazonaws.com/public/image_upload/74d499a23b8243008e0d7dac2359dc9b/96e51240-b99c-4d09-8f73-f82e7cf76620.png](https://slid-users-assets-v1-seoul.s3.ap-northeast-2.amazonaws.com/public/image_upload/74d499a23b8243008e0d7dac2359dc9b/96e51240-b99c-4d09-8f73-f82e7cf76620.png)
            
            - member3은 response body가 json 형태
                
                : body(memberDTO)니까 memberTDO 형식 즉 json 형태를 return
                
            - code값이 변경된 것을 확인할 수 있다 (200 코드가 아닌 202)
                
                cf) 202 -> Accepted 값이 202
                
                ![https://slid-users-assets-v1-seoul.s3.ap-northeast-2.amazonaws.com/public/image_upload/74d499a23b8243008e0d7dac2359dc9b/ea33c31d-1876-4258-903f-42decf480291.png](https://slid-users-assets-v1-seoul.s3.ap-northeast-2.amazonaws.com/public/image_upload/74d499a23b8243008e0d7dac2359dc9b/ea33c31d-1876-4258-903f-42decf480291.png)
                
    - delete controller
        
        : 아이디를 받고 db에서 삭제하는 작업을 주로 한다
