# QRSticker

QR ( QrSticker ) 검색 및 정보 조회를 제공합니다.

## QRSticker 리스트 검색

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

마커 메뉴에서 QR 코드 설정시 이용합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20QR%20Sticker%20API%20/qrstickerListUsingGET_2)

### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/qrsticker`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호


### Response Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
qr_stk_no | M          | number | QR 스티커 관리번호
qr_stk_name | M          | string | QR 스티커명
qr_type | M          | number | QR 스티커 유형. 1: 출/퇴근, 2: 진/출입
inout_type | M          | number | 진/출입유형. 1: 진입, 2: 진출, 3: 진/출입 선택


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

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20QR%20Sticker%20API%20/qrstickerDetailUsingGET_1)

### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/qrsticker/{qr_stk_no}`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호
qr_stk_no | M          | number | QR 스티커 관리번호


### Response Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
qr_stk_no | M          | number | QR 스티커 관리번호
qr_stk_name | M          | string | QR 스티커명
qr_type | M          | number | QR 스티커 유형. 1: 출/퇴근, 2: 진/출입
inout_type | M          | number | 진/출입유형. 1: 진입, 2: 진출, 3: 진/출입 선택

