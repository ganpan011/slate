# Device

디바이스 ( IOT 장치 및 BLE G/W ) 검색 및 정보 조회를 제공합니다. 


## 디바이스 리스트 검색

> 요청 전문 예시

```JSON
{
  "search_name" : "검색대상",
  "search_value" : "검색값",
  "wp_no" : 1,
  "device_type": 1,
  "device_category": 1
}

```

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success",
  "context" : [ {
    "idx" : 1,
    "device_type" : "디바이스 유형",
    "device_id" : "표시명",
    "mac_address_type" : 1,
    "mac_address" : "00:00:00:00:00:00",
    "gate_inout" : 1,
    "gate_manufacturer" : 1,
    "device_category" : 1
  } ]
}
```

디바이스 ( IOT 장치 및 BLE G/W ) 리스트 검색을 제공합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

### HTTP Request

`POST /imoa/api/device/export`

### Request BODY

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
search_name | M          | 검색대상. COMPLEX : 전체(공사명, 디바이스 식별자, macAddress), wpName : 공사명(현장명), deviceId : 표시명, macAddress: mac address
search_value | M          | 검색값
wp_no | M          | 현장 관리번호
device_type | O          | 디바이스 유형
device_category | O          | 디바이스 유형 카테고리. ( 1: IOT 장치, 2: 위치 센서, 99: 기타 )

### Response Body

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
idx | M          | 디바이스 관리번호
device_type | M          | 디바이스 유형
device_id | M          | 디바이스 표시명
mac_address_type | M          | 통신방식. 1: 일반, 2: LoRa
mac_address  | M          | mac address
gate_inout  | M          | 출입 유형. 0: 이탈(퇴근) ,  1: 진입(출근)
gate_manufacturer  | M          | 제조사 구분
device_category | M          | 디바이스 유형 카테고리. ( 1: IOT 장치, 2: 위치 센서, 99: 기타 )


## 디바이스 정보 조회

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success",
  "context" : {
    "idx" : 1,
    "device_type" : "디바이스 유형",
    "device_id" : "표시명",
    "mac_address_type" : 1,
    "mac_address" : "00:00:00:00:00:00",
    "gate_inout" : 1,
    "gate_manufacturer" : 1,
    "device_category" : 1
  } 
}
```

디바이스 정보를 제공합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

### HTTP Request

`GET /imoa/api/device/{idx}`

### Path variable

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
idx | M          | 디바이스 관리번호


### Response Body

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
idx | M          | 디바이스 관리번호
device_type | M          | 디바이스 유형
device_id | M          | 디바이스 표시명
mac_address_type | M          | 통신방식. 1: 일반, 2: LoRa
mac_address  | M          | mac address
gate_inout  | M          | 출입 유형. 0: 이탈(퇴근) ,  1: 진입(출근)
gate_manufacturer  | M          | 제조사 구분
device_category | M          | 디바이스 유형 카테고리. ( 1: IOT 장치, 2: 위치 센서, 99: 기타 )

