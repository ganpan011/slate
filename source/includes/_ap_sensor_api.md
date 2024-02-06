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

### HTTP Request

`POST /imoa/api/device/apsensor/export`

### Request BODY

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
search_name | M          | 검색대상. COMPLEX : 전체
search_value | M          | 검색값
wp_no | M          | 현장 관리번호

### Response Body

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
si_idx | M          | AP 센서 관리번호
si_type | M          | AP 센서 유형
si_code | M          | AP 센서 코드
sd_name | M          | AP 센서 구역명
si_place1  | M          | 위치1
si_place2  | M          | 위치2
major  | M          | AP 센서 major
minor | M          | AP 센서 minor

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

<aside class="warning">
API 미구현 
</aside>

### HTTP Request

`GET /imoa/api/device/apsensor/{si_idx}`

### Path variable

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
si_idx | M          | AP 센서 관리번호


### Response Body

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
si_idx | M          | AP 센서 관리번호
si_type | M          | AP 센서 유형
si_code | M          | AP 센서 코드
sd_name | M          | AP 센서 구역명
si_place1  | M          | 위치1
si_place2  | M          | 위치2
major  | M          | AP 센서 major
minor | M          | AP 센서 minor

