# 공사구간 및 현황 정보

## 공사구간 정보 리스트 조회

> 요청 전문 예시

```JSON
{
  "search_name" : "검색대상",
  "search_value" : "검색값",
  "construct_in_progress" : 1
}

```

> 응답 전문 예시

```JSON
{
  "return_code": 0,
  "return_message": "Success",
  "context":  [
    {
      "cstrt_no": 1,
      "cstrt_name": "상단",
      "full_name": "암센터/상단"
    }
  ]
}
```

공사구간 정보 검색을 제공합니다.

라벨, 아이콘 등록/수정시 사용.
진행현황바 내 진행현황(구성요소) 등록시 공사 진행정보가 존재하는 공사구간만을 선택하여야 한다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20%EA%B3%B5%EC%82%AC%20%EA%B5%AC%EA%B0%84%20API%20/constructSectionExportUsingPOST)


### HTTP Request

`POST /imoa/api/monitor/4.3/workplace/{wp_no}/construct_section/export`

### Path variable

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
wp_no | M          | 현장 관리번호

### Request BODY

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
search_name | M          | 검색대상. 'COMPLEX' : 전체, 'cstrt_name' : '공사구간명'
search_value | M          | 검색값
construct_in_progress | O          | 공사 진행정보 존재 유무. 값 없으면 전체. 0: 미존재, 1: 존재


### Response Body

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
cstrt_no | M          | 공사구간 관리번호
cstrt_name | M          | 공사구간명
full_name | M          | 공사구간 전체명 ( 상위 공사구간이 있을 경우 상위공사구간명 + '/' + 공사구간명



## 전체 공사진행 현황 조회

> 응답 전문 예시

```JSON
{
  "return_code": 0,
  "return_message": "Success",
  "context": {
    "total_progress": 33,
    "total_construct_distance" : 1444,
    "total_progress_distance" : 185,
    "list": [
      {
        "cstrt_no": 1,
        "cstrt_name": "상단",
        "construct_distance" : 1444,
        "progress_distance" : 185,
        "depth" : 3.984
      }
    ]
  }
}
```

전체 공사진행 현황 및 개별 공사진행현황 리스트를 제공합니다. ( 공사 현황 컴포넌트 )

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20%EA%B3%B5%EC%82%AC%20%EA%B5%AC%EA%B0%84%20API%20/constructSectionProgressUsingGET)

### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/construct_section/progress`

### Path variable

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
wp_no | M          | 현장 관리번호

### Response Body

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
total_progress | M          | 전체 진행율
total_construct_distance | M          | 전체 공사거리(단위는 m)
total_progress_distance | M          | 전체 진행거리(단위는 m)
list.cstrt_no | M          | 공사구간 관리번호
list.cstrt_name | M          | 공사구간명
list.construct_distance | M          | 총 공사거리(단위는 m)
list.progress_distance | M          | 진행거리(단위는 m)
list.depth | O          | 심도(단위는 m)



## 공사 진행현황 정보 조회

> 응답 전문 예시

```JSON
{
  "return_code": 0,
  "return_message": "Success",
  "context": {
    "cstrt_no": 1,
    "cstrt_name": "공사구간명",
    "construct_distance": 1080,
    "progress_distance": 81,
    "depth": 80.230
  }
}
```

특정 공사구간의 진행현황 정보를 조회합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20%EA%B3%B5%EC%82%AC%20%EA%B5%AC%EA%B0%84%20API%20/updateConstructSectionProgressUsingPUT)


### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/construct_section/progress/{cstrt_no}`

### Path variable

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
wp_no | M          | 현장 관리번호
cstrt_no | M          | 공사구간 관리번호

### Response Body

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
cstrt_no | M          | 공사구간 관리번호
cstrt_name | M          | 공사구간명
construct_distance | M          | 총 공사거리(단위는 m)
progress_distance | M          | 진행거리(단위는 m)
depth | O          | 심도(단위는 m)


## 공사현황 정보 수정


> 요청 전문 예시

```JSON
{
  "progress_distance": 205,
  "depth": 4.184
}
```

> 응답 전문 예시

```JSON
{
  "return_code": 0,
  "return_message": "Success"
}
```

공사진행 정보를 수정합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20%EA%B3%B5%EC%82%AC%20%EA%B5%AC%EA%B0%84%20API%20/updateConstructSectionProgressUsingPUT)


### HTTP Request

`PUT /imoa/api/monitor/4.3/workplace/{wp_no}/construct_section/progress/{cstrt_no}`

### Path variable

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
wp_no | M          | 현장 관리번호
cstrt_no | M          | 공사구간 관리번호

### Request Body

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
progress_distance | M          | 진행거리(단위는 m)
depth | O          |  심도(단위는 m)
