# QRSticker

QR ( QrSticker ) 검색 및 정보 조회 및 진출/입 이력 조회 API 를 제공합니다.

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


## QRSticker 진출/입 이력 검색

> 요청 전문 예시

```JSON
{
    "page" : 1,
    "page_size" : 10,
    "search_name" : "검색대상",
    "search_value" : "검색값",
    "qr_stk_no" : 8,
    "inout_type" : 1,
    "target_date" : "2024-02-23"
}
```

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success",
  "context": {
    "current_page": 1,
    "page_size": 10,
    "total_count": 0,
    "list": [
      {
        
      }
    ]
  }
}
```

QRSticker 진출/입 이력 검색을 제공합니다.

마커 메뉴에서 QR 코드 클릭시 나오는 진출/입 이력 팝업을 위한 API 입니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

TODO
 
신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20QR%20Sticker%20API%20/searchUsingPOST_10)

### HTTP Request

`POST /imoa/api/monitor/4.3/workplace/{wp_no}/qrsticker/log/search`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호


### Request Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
page | M          | number | 검색 페이지
page_size | M          | number | 페이지당 건수
search_name | O          | string | 검색대상. 'COMPLEX' : 전체, qrStkName: QR 명
search_value | O          | string | 검색값
qr_stk_no | O          | string | QR 스티커 관리번호. 없으면 해당 현장 전체 스티커 대상
inout_type | O          | number | 진/출입유형. 1: 진입, 2: 진출. 없으면 전체
target_date | O          | string | 검색일. 'YYYY-MM-DD' 날짜 포맷. 없으면 디폴트 당일

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
mb_no | M          | number | 사용자 관리번호
mb_name | M          | string | 사용자명
telephone | M          | string | 전화번호
grd_name | M          | string | 사용자 등급명
qr_stk_no | M          | number | QR 스티커 관리번호
qr_stk_name | M          | string | QR 스티커명
qr_type | M          | number | QR 스티커 유형. 1: 출/퇴근, 2: 진/출입 
inout_type | M          | number | 진/출입유형. 1: 진입, 2: 진출, 3: 진/출입 선택
wp_name | M          | string | 현장명
coop_name | O          | string | 협력사명



## QRSticker 진출/입 이력 Data export

> 요청 전문 예시

```JSON
{
    "search_name" : "검색대상",
    "search_value" : "검색값",
    "qr_stk_no" : 8,
    "inout_type" : 1,
    "target_date" : "2024-02-23"
}
```

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success",
  "context": [
    {

    }
  ]
}
```

QRSticker 진출/입 이력 Data export 제공합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20QR%20Sticker%20API%20/exportUsingPOST_6)

### HTTP Request

`POST /imoa/api/monitor/4.3/workplace/{wp_no}/qrsticker/log/export`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호


### Request Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
search_name | O          | string | 검색대상. 'COMPLEX' : 전체, qrStkName: QR 명
search_value | O          | string | 검색값
qr_stk_no | O          | string | QR 스티커 관리번호. 없으면 해당 현장 전체 스티커 대상
inout_type | O          | number | 진/출입유형. 1: 진입, 2: 진출. 없으면 전체
target_date | O          | string | 검색일. 'YYYY-MM-DD' 날짜 포맷. 없으면 디폴트 당일


### Response Body

QRSticker 진출/입 이력 검색 응답 항목 참고
