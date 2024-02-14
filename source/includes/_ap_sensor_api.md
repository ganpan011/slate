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

