# AP Sensor

AP Sensor 검색 및 정보 조회를 제공합니다.


## AP Sensor 리스트 검색

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
    "si_idx" : 1,
    "si_type" : "AP 센서 유형",
    "si_code" : "센서 코드",
    "sd_name" : "센서 구역명",
    "si_place1" : "위치1",
    "si_place2" : "위치2",
    "major" : 1,
    "minor" : 50001
  } ]
}
```

AP Sensor 리스트 검색을 제공합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20AP%20Sensor%20API%20/qrstickerListUsingGET)

### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/apsensor`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입      | 설명
--------- |------------|-------------| -----------
si_idx | M          | number      | AP 센서 관리번호
si_type | M          | string      | AP 센서 유형
si_code | M          | string      | AP 센서 코드
sd_name | M          | string      | AP 센서 구역명
si_place1  | M          | string      | 위치1
si_place2  | M          | string      | 위치2         
major  | M          | number | AP 센서 major 
minor | M          | number | AP 센서 minor 


## AP Sensor 정보 조회

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success",
  "context" : {
    "si_idx" : 1,
    "si_type" : "AP 센서 유형",
    "si_code" : "센서 코드",
    "sd_name" : "센서 구역명",
    "si_place1" : "위치1",
    "si_place2" : "위치2",
    "major" : 1,
    "minor" : 50001
  } 
}
```

AP Sensor 정보를 제공합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20AP%20Sensor%20API%20/qrstickerDetailUsingGET)

### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/apsensor/{si_idx}`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호
si_idx | M          | number | AP 센서 관리번호


### Response Body

항목 | 필수 여부(M/O) | 데이터 타입      | 설명
--------- |------------|-------------| -----------
si_idx | M          | number      | AP 센서 관리번호
si_type | M          | string      | AP 센서 유형
si_code | M          | string      | AP 센서 코드
sd_name | M          | string      | AP 센서 구역명
si_place1  | M          | string      | 위치1
si_place2  | M          | string      | 위치2
major  | M          | number | AP 센서 major
minor | M          | number | AP 센서 minor 


## AP 센서 감지 근로자 검색

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success",
  "context" : [{
    "wp_no" : 1,
    "wp_name" : "string",
    "cstrt_no" : 1,
    "cstrt_name" : "string",
    "coop_no" : 1,
    "coop_name" : "string",
    "mb_no" : 1,
    "mb_name" : "string",
    "telephone" : "string",
    "si_idx" : 1,
    "si_type" : "string",
    "sd_name" : "string",
    "si_place1" : "string",
    "si_place2" : "string",
    "in_out_type" : 1,
    "slr_datetime" : 12313213213
  }]
}
```

AP 센서 감지된 근로자를 검색한다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20AP%20Sensor%20API%20/findBleUserUsingPOST)

기존 API Deprecated ( 사용 불가 )

1. /imoa/api/monitor/4.1/workplace/{wpNo}/ble/user [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.1%5D%20IMOS%20%EC%9D%BC%EB%B0%98%20%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81%20%EA%B4%80%EB%A6%AC/searchBleUserUsingGET)


### HTTP Request

`POST /imoa/api/monitor/4.3/workplace/{wp_no}/apsensor/user/export`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호

### Request Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명설명
--------- |------------|--------| -----------
search_name | O          | string | 검색대상. 'COMPLEX' : 전체
search_value | O          | string | 검색값 ( 근로자명 )

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
wp_no | M          | number | 현장 관리번호
wp_name | M          | string | 현장명
cstrt_no | M          | number | 공사구간 관리번호
cstrt_name | M          | string | 공사구간명
full_Name | M          | string | 공사구간 fullname
coop_no | M          | number | 협력사 관리번호
coop_name | M          | string | 협력사명
mb_no | M          | number | 사용자 관리번호
mb_name | M          | string | 사용자명
telephone | M          | string | 전화번호
si_idx | M          | number | AP 센서 관리번호
si_type | O          | string | AP 센서 유형
sd_name | M         | string | AP 센서 구역 이름
si_place1 | O          | string | 위치1
si_place2 | O          | string | 위치2
in_out_type | O          | string | 센서 접근 상태 구분
equipment_icon_url | O          | string | 감지자가 장비기사일 경우 해당 장비 아이콘 URL
slr_datetime | O          | number | 센서 접근 시간



## 특정 AP 센서 감지 근로자 조회

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success",
  "context" : [{
    "wp_no" : 1,
    "wp_name" : "string",
    "cstrt_no" : 1,
    "cstrt_name" : "string",
    "full_Name" :  "string",
    "coop_no" : 1,
    "coop_name" : "string",
    "mb_no" : 1,
    "mb_name" : "string",
    "telephone" : "string",
    "si_idx" : 1,
    "si_type" : "string",
    "sd_name" : "string",
    "si_place1" : "string",
    "si_place2" : "string",
    "in_out_type" : 1,
    "equipment_icon_url" : "string",,
    "slr_datetime" : 12313213213
  }]
}
```

특정 AP 센서에 감지된 근로자를 조회한다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20현장관제%20AP%20Sensor%20API%20/monitorForWorkerUsingPOST)

기존 API Deprecated ( 사용 불가 )

1. 특정 Sensor 내 접근자 검색 [Swagger](http://127.0.0.1:32380/swagger-ui/index.html#/BLS%20%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81/monitorForWorkerUsingPOST_1)


### HTTP Request

`GET /api/monitor/4.3/workplace/{wpNo}/apsensor/{si_idx}/user`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호
si_idx | M          | number | AP 센서 관리번호


### Response Body

AP 센서 감지 근로자 항목 참고


## AP 센서 감지 근로자 위치 조회

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success",
  "context" : {
    "wp_no" : 1,
    "wp_name" : "string",
    "cstrt_no" : 1,
    "cstrt_name" : "string",
    "coop_no" : 1,
    "coop_name" : "string",
    "mb_no" : 1,
    "mb_name" : "string",
    "telephone" : "string",
    "si_idx" : 1,
    "si_type" : "string",
    "sd_name" : "string",
    "si_place1" : "string",
    "si_place2" : "string",
    "in_out_type" : 1,
    "slr_datetime" : 12313213213
  }
}
```

AP 센서 감지된 특정 근로자의 AP 센서 위치 정보를 제공한다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20AP%20Sensor%20API%20/findBleUserLocationUsingGET)

기존 API Deprecated ( 사용 불가 )

1. BLE 스마트 안전모니터 근로자 위치 검색 [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20AP%20Sensor%20API%20/findBleUserLocationUsingGET)


### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/apsensor/user/{mb_no}`

### Path Variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호
mb_no | M          | number | 사용자 관리번호

### Response Body

AP 센서 감지 근로자 항목 참고
