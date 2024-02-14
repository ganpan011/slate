# Device

디바이스 ( IOT 장치 및 BLE G/W ) 검색 및 정보 조회를 제공합니다. 

## 디바이스(장치) 검색

> 요청 전문 예시

```JSON
{
  "search_name" : "검색대상",
  "search_value" : "검색값",
  "device_type": 1,
  "device_type_category": 1
}

```

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success",
  "context" : [ {
    "idx" : 1,
    "device_type" : 1,
    "device_type_category" : 1,
    "device_id" : "표시명",
    "mac_address" : "00:00:00:00:00:00"
  } ]
}
```

디바이스 ( IOT 장치 및 BLE G/W ) 리스트 검색을 제공합니다.

마커 센서 관련하여 IoT 센서와 BLE G/W 는 device_type 을 지정하여 리스트 검색하여야 합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger]()

### HTTP Request

`POST /imoa/api/monitor/4.3/workplace/{wp_no}/device/export`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호

### Request BODY

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
search_name | O          | string | 검색대상. COMPLEX : 전체(공사명, 디바이스 식별자, macAddress), wpName : 공사명(현장명), deviceId : 표시명, macAddress: mac address
search_value | O          | string | 검색값
device_type | O          | number | 디바이스 유형 ( 디바이스 유형 코드 참고 )
device_type_category | O          | number | 디바이스 유형 카테고리. ( 0: 미지정, 1: IOT 장치, 2: 위치 센서  )

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
idx | M          | number | 디바이스 관리번호
device_type | M          | number | 디바이스 유형
device_type_category | M          | number | 디바이스 유형 카테고리. ( 0: 미지정, 1: IOT 장치, 2: 위치 센서 )
device_id | M          | string | 디바이스 표시명
mac_address  | M          | string | mac address

## 디바이스(장치) 정보 조회

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success",
  "context" : {
    "idx" : 1,
    "device_type" : 1,
    "device_type_category" : 1,
    "device_id" : "표시명",
    "mac_address" : "00:00:00:00:00:00"
  } 
}
```

디바이스 정보를 제공합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger]()

### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/device/{idx}`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호
idx | M          | number | 디바이스 관리번호

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
idx | M          | number | 디바이스 관리번호
device_type | M          | number | 디바이스 유형
device_type_category | M          | number | 디바이스 유형 카테고리. ( 0: 미지정, 1: IOT 장치, 2: 위치 센서 )
device_id | M          | string | 디바이스 표시명
mac_address  | M          | string | mac address

