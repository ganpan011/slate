# 로그인/로그아웃 및 Token 체크/갱신

## 현장관제 로그인

> 요청 전문

```json
{
  "mb_id": "아이디",
  "mb_pwd": "패스워드"
}
```

>  응답 전문. 전문 상세 정보는 [TokenInfo](#tokeninfo) 참고

```json
{
  "return_code": 0,
  "return_message": "string",
  "context": {
    "access_token": "string",
    "authorities": [
      "string"
    ],
    "authorities_info": {},
    "expires_in": 0,
    "former_member": true,
    "jti": "string",
    "member_info": {},
    "refresh_token": "string",
    "scope": "string",
    "token_type": "string"
  }
}
```

현장관제 로그인을 위한 API 입니다.

Token 획득 후 localStorage 에 저장하여 브라우저 새로고침 및 브라우저 재기동시에도 
로그인 상태가 지속될 수 있도록 하여야 합니다. 

<aside class="notice">
HTTP Basic 인증 필요 
</aside>

기존 API 사용. [Swagger](https://ras.hulandev.co.kr/hma/swagger-ui/index.html#/OAuth%20API%20(%20%EB%A1%9C%EA%B7%B8%EC%9D%B8%20%ED%8F%AC%ED%95%A8%20)%20/imosLoginMemberUsingPOST)


### HTTP Request

`POST /hma/api/oauth/login/imos`

### Request Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
mb_id | M          | String | 사용자 계정
mb_pwd | M       | String | 사용자 패스워드

### Response Body

응답 전문 상세내용은 [TokenInfo](#tokeninfo) 참고


## 로그아웃

> 응답 전문 예시

```json
{
  "context": true,
  "return_code": 0,
  "return_message": "SUCCESS"
}
```

사용자 로그아웃을 위한 API 입니다.

처리 결과와 상관없이 Client 는 자체적으로 저장된 Token 정보를 삭제하고 로그아웃 처리하여야 합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요
</aside>

기존 API 사용. [Swagger](https://ras.hulandev.co.kr/hma/swagger-ui/index.html#/%EC%82%AC%EC%9A%A9%EC%9E%90%20%EA%B4%80%EB%A6%AC/logoutMemberUsingGET)

### HTTP Request

`DELETE /hma/api/member/logout`

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
context | M          | boolean | 정상적으로 로그아웃된 경우 true

## Check Token

>  응답 전문.

```json
{
  "return_code" : 0,
  "return_message" : "String",
  "context" : {
    "active" : true,
    "user_name" : "String",
    "jti" : "String",
    "exp" : 1738054301,
    "scope" : [ "web" ],
    "authorities" : [],
    "authorities_info" : { },
    "member_info" : {}
  }
}
```

Token 유효성 검사를 위한 API 입니다. 

Token 자동 갱신은 관리자 사이트의 경우 명시적으로 사용자가 연장을 하여야 하지만
현장관제와 통합관제는 Token 만료시간이 지정된 시간(12시간) 이내인 경우 Refresh Token 을 이용하여 갱신하여야 한다.

<aside class="notice">
HTTP Basic 인증 필요 
</aside>

기존 API 사용. [Swagger](https://ras.hulandev.co.kr/hma/swagger-ui/index.html#/OAuth%20API%20(%20%EB%A1%9C%EA%B7%B8%EC%9D%B8%20%ED%8F%AC%ED%95%A8%20)%20/checkTokenUsingGET)

### HTTP Request

`POST /hma/api/oauth/check_token`

### Request Parameter

항목 | 필수 여부(M/O) | 데이터 타입 | 설명설명
--------- |------------| -----------| -----------
token | M          | String | access token

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명설명
--------- |------------| -----------| -----------
active | M          | boolean | 유효사용자 여부
user_name | M          | Number | 사용자 관리번호
exp | M          | Number |  만료시간 
member_info | M          | MemberInfo | 로그인 사용자의 기본 정보. 상세내용은 [MemberInfo](#memberinfo) 참고
authorities | M          | List<String> |  사용자 권한 리스트
authorities_info | M          | Map | 특정 권한과 관련된 상세 권한 정보

## Refresh Token

>  Refresh Token 응답 전문은 아래와 같다.

```json
{
  "return_code": 0,
  "return_message": "string",
  "context": {
    "access_token": "string",
    "authorities": [
      "string"
    ],
    "authorities_info": {},
    "expires_in": 0,
    "former_member": true,
    "jti": "string",
    "member_info": {},
    "refresh_token": "string",
    "scope": "string",
    "token_type": "string"
  }
}
```

Refresh Token 정보를 이용하여 신규 Token 정보를 획득하기 위한 API 입니다.

<aside class="notice">
HTTP Basic 인증 필요 
</aside>

기존 API 사용. [Swagger](https://ras.hulandev.co.kr/hma/swagger-ui/index.html#/OAuth%20API%20(%20%EB%A1%9C%EA%B7%B8%EC%9D%B8%20%ED%8F%AC%ED%95%A8%20)%20/refreshTokenUsingGET)

### HTTP Request

`POST /hma/api/oauth/refresh_token`

### Request Parameter

항목 | 필수 여부(M/O) | 데이터 타입 | 설명설명
--------- |------------| -----------| -----------
refresh_token | M          | String | refresh token

### Response Body

응답 전문 상세내용은 [TokenInfo](#tokeninfo) 참고
