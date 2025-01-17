# Spring-Security-Example

Spring Security를 이용한 Jwt 토큰 생성 및 관리에 대한 예제입니다.

아래 블로그에 진행과정이 설명되어있습니다.

[SpringBoot 로그인 구현하기 (with. SpringSecurity, JWT)](https://velog.io/@junho5336/SpringBoot-%EB%A1%9C%EA%B7%B8%EC%9D%B8-%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0-with.-SpringSecurity-JWT)

[토큰 탈취 고려하기 (Refresh Token)](https://velog.io/@junho5336/%ED%86%A0%ED%81%B0-%ED%83%88%EC%B7%A8-%EA%B3%A0%EB%A0%A4%ED%95%98%EA%B8%B0-Refresh-Token)

소스파일 테스트
mariaDB 또는 mysql 설치 되어 있어야 함 
PostMan 이용하여야 함

<회원 가입>
POST
http://localhost:8080/register
body 체크
raw 체크 후 JSON으로 변경
{
    "account":"abc123",
    "password":"password",
    "nickname":"junho",
    "name":"junho",
    "email":"junho5336@gmail.com"
}

<로그인>
POST
http://localhost:8080/login
body 체크

<사용자 정보 가져오기1 >
GET
http://localhost:8080/user/get?account=abc123
---> 토큰을 넣지않고 접속하면 " 인증되지 않은 사용자입니다."  라고 리턴된다

<사용자 정보 가져오기1 >
GET
http://localhost:8080/user/get?account=abc123
Postman에서 'Authorization - Type - BearerToken을 선택하고 로그인을 했을 때 발급받은 토큰값을 넣어준다.
---> 토큰을 넣고 접속하면 정상적으로 사용자 정보을 가져온다

<admin 접속하여 정보 가져오기1 >
GET
http://localhost:8080/admin/get?account=abc123
---> 토큰을 넣지않고 접속하면 " 인증되지 않은 사용자입니다."  라고 리턴된다

<admin 접속하여 정보 가져오기1 >
GET
http://localhost:8080/admin/get?account=abc123
Postman에서 'Authorization - Type - BearerToken을 선택하고 로그인을 했을 때 발급받은 토큰값을 넣어준다.
---> 토큰을 넣고 접속하면 '권한이 없는 사용자입니다."라는 값이 리턴 된다

테스트 완료