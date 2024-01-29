# QRSticker

AP Sensor 검색 및 정보 조회를 제공합니다.


## QRSticker 리스트 검색

> 요청 전문 예시

```JSON
{
  "search_name" : "검색대상",
  "search_value" : "검색값",
  "wp_no" : 1
}

```

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success",
  "context" : [ {
    "qr_stk_no" : 1,
    "qr_stk_name" : "QR 스티커명",
    "qr_type" : "qr 유형. 1: 출/퇴근, 2: 진/출입",
    "inout_type" : "진/출입유형. 1: 진입, 2: 진출, 3: 진/출입 선택"
  } ]
}
```

QRSticker 리스트 검색을 제공합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

### HTTP Request

`POST /imoa/api/qrsticker/export`

### Request BODY

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
search_name | M          | 검색대상. COMPLEX : 전체
search_value | M          | 검색값
wp_no | M          | 현장 관리번호

### Response Body

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
qr_stk_no | M          | QR 스티커 관리번호
qr_stk_name | M          | QR 스티커명
qr_type | M          | QR 스티커 유형. 1: 출/퇴근, 2: 진/출입
inout_type | M          | 진/출입유형. 1: 진입, 2: 진출, 3: 진/출입 선택


## QRSticker 정보 조회

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success",
  "context" : {
    "qr_stk_no" : 1,
    "qr_stk_name" : "QR 스티커명",
    "qr_type" : "qr 유형. 1: 출/퇴근, 2: 진/출입",
    "inout_type" : "진/출입유형. 1: 진입, 2: 진출, 3: 진/출입 선택"
  }
}
```

QRSticker 정보를 제공합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

### HTTP Request

`GET /imoa/api/qrsticker/{qr_stk_no}`

### Path variable

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
qr_stk_no | M          | QR 스티커 관리번호


### Response Body

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
qr_stk_no | M          | QR 스티커 관리번호
qr_stk_name | M          | QR 스티커명
qr_type | M          | QR 스티커 유형. 1: 출/퇴근, 2: 진/출입
inout_type | M          | 진/출입유형. 1: 진입, 2: 진출, 3: 진/출입 선택

