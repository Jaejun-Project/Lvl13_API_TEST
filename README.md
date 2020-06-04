# Lvl13 API (NodeJS & MongoDB)



## Prerequisites

You will need the following things properly installed on your computer.

* [Git](https://git-scm.com/)
* [Node.js](https://nodejs.org/) (with npm)
* [Postman](https://www.postman.com/)
* npm install

**Repository 들어가서 서버 실행**

* nodemon index.js

# Postman을 이용하여 API 테스트하기


## 코디 리스트

**코디 리스트 보기**

GET: localhost:3000/stylelists

**tag 된 코디 보기**

GET: localhost:3000/stylelists/tag

Body Raw에 태그 값을 입력하여 입력된 태그 리스트만 뽑아 보기

ex:
{
	  "tag": "봄"
}

##회원가입 및 로그인

**회원가입:**

POST: localhost:3000/users/register

ex)

  {
	"name": "Jaejun Min",
	"email": "test1.test.test",
	"username": "test1",
	"password": "123456"
}

**회원 인증토큰 받기:**

POST: localhost:3000/users/authenticate

ex):
{
	"username": "test1",
	"password": "123456"
}

결과 ex:

{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJmYXZvcml0ZXMiOltdLCJfaWQiOiI1ZWQ4ZTA2Yjk2Y2IyYjdlYTdlNTFjZjMiLCJuYW1lIjoiSmFlanVuIE1pbiIsImVtYWlsIjoidGVzdDEudGVzdC50ZXN0IiwidXNlcm5hbWUiOiJ0ZXN0MSIsInBhc3N3b3JkIjoiJDJiJDEwJEtsdVQ0bEJkbUZwM0NGUGVPMEZVSXVUQ0d6U2g1aFBTOVdZcGxwdDlmY2U3SVBVLnRYNVJlIiwiX192IjowLCJpYXQiOjE1OTEyNzIzOTYsImV4cCI6MTU5MTg3NzE5Nn0.H1BS-29IYcHQkF2YGGqG4dq03T8KhbEbuvdU_9LNF50"
}


**인증 승인 하는 방법:**

Postman auth에 들어가서 Type을 Bearer Token으로 변경 후 위에 받은 token 값을 복사 붙여넣기.

인증이 필요한 URL마다 같은 방식으로 인증을 진행.


**로그인 회원정보 보기 :**

GET: localhost:3000/users/profile


**로그인된 회원의 "좋아요"한 코디 출력하기**

* :id 값은 회원의 아이디이므로 회원정보 보기를 이용하여 로그인된 회원 아이디 복사하여 입력

ex) localhost:3000/stylelists/:id/favorites => localhost:3000/stylelists/5ed8e06b96cb2b7ea7e51cf3/favorites


GET: localhost:3000/stylelists/:id/favorites


**좋아요 추가하기**

POST: localhost:3000/stylelists/:id/favorites/add

ex): {
	"\_id": "5ed8e1fe96cb2b7ea7e51cf7"
 }

*  코디리스트의 아이디값을 입력하여 "좋아요" 추가

**좋아요 지우기**

POST: localhost:3000/stylelists/:id/favorites/remove

{
 "_id": "5ed8e1fe96cb2b7ea7e51cf7"
}

* 코디리스트의 아이디값을 입력하여 "좋아요" 제거

**기타 사항**
* 현재  "좋아요 지우기" 지워지기는 하나  </br>
  "ERR_HTTP_HEADERS_SENT" 에러 발생하면서 서버 중단 현상이 생겨서 수정 중입니다.