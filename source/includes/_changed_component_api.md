# ChangedComponent ( 기존 API 변경 )

마커 및 진행현황바 설정을 통한 위치 지정으로 인해 영향을 받는 기존 컴포넌트 및 API 의 변경 적용

## 위험지역접근현황 컴포넌트 변경

위험지역 컴포넌트 API 교체

기존 "[4.2]IMOS 위험 센서(AP) 감지 현황" - 출입금지접근 컴포넌트 API 을 폐기하고 "[4.3]위험지역접근현황 컴포넌트 (DangerAp) API" 신규로 추가

신규 API [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%EC%9C%84%ED%97%98%EC%A7%80%EC%97%AD%EC%A0%91%EA%B7%BC%ED%98%84%ED%99%A9%20%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8%20(DangerAp)%20API)


### 위험지역 접근 현황 

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success",
  "context" : {
    "total_cnt" : 1,
    "status_list" : [{
      "cstrt_no" : 1,
      "full_name" : "공사구간 fullname",
      "cnt" : 10,
      "authorized_cnt" : 5,
    }]
  } 
}
```

위험지역 접근 현황 컴포넌트 메인 API

위험지역은 공사구간명(full_name) 표출하도록 변경 필요

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>


#### HTTP Request

`/api/monitor/4.2/workplace/{wpNo}/status` -> `/api/monitor/4.3/workplace/{wpNo}/status`


#### Response Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
total_cnt | M          | number | 전체 수
status_list.cstrt_no | M          | number |  공사구간 관리번호
status_list.full_name | M          | string | 공사구간 full 명 ( 상위 공사구간이 있을 경우 상위공사구간명 + '/' + 공사구간명 )
status_list.cnt | M          | number | 감지수
status_list.authorized_cnt | M          | number | 인가자수


### 위험지역 접근자 현황

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success",
  "context" : [{
    "cstrt_no" : 1,
    "cstrt_name" : "string",
    "full_name" : "string",
    "coop_no" : 1,
    "coop_name" : "string",
    "mb_no" : 1,
    "mb_name" : "string",
    "coop_section_name" : "string",
    "worker_section_name" : "string",
    "slr_datetime" : 12313213213
  }]
}
```

공사구간 선택시 해당 공사구간 내 위험 AP 센서에 감지된 근로자 리스트 제공
위치는 공사구간명(full_name) 표출하도록 변경 필요

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>


#### HTTP Request

`/api/monitor/4.2/workplace/{wpNo}/status/building/{building_no}/floor/{floor}` -> `/api/monitor/4.3/workplace/{wpNo}/status/{cstrtNo}`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입          | 설명
--------- |------------|-----------------| -----------
wp_no | M          | number | 현장 관리번호
cstrt_no | M          | number | 공사구간 관리번호


#### Response Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
cstrt_no | M          | number | 공사구간 관리번호
cstrt_name | M          | string | 공사구간명
full_Name | M          | string | 공사구간 fullname
coop_no | M          | number | 협력사 관리번호
coop_name | M          | string | 협력사명
mb_no | M          | number | 사용자 관리번호
mb_name | M          | string | 사용자명
authorized | M | number | 인가자 여부. 0: 미인가, 1: 인가
coop_section_name | M          | string | 협력사 공종 ( work_section_name_a )
worker_section_name | M          | string | 근로자 공종 ( work_section_name_b )
slr_datetime | O          | number | 센서 접근 시간



### 위험지역 접근 보고서(공종/협력사/공사구간별 감지수) 데이터 페이징 리스트 제공


> 요청 전문 예시

```JSON
{
  "page":1,
  "page_size":5,
  "start_date":"20241219",
  "end_date":"20241224"
}
```

> 응답 전문 예시

```JSON
{
  "context" : {
    "current_page" : 1,
    "page_size" : 5,
    "total_count" : 2,
    "list" : [ 
      {
        "coop_section_name" : "기타공사",
        "work_section_name_a" : "기타공사",
        "coop_name" : "(주)휴랜 협력사",
        "full_name" : "string",
        "cnt" : 2438,
        "authorized_cnt" : 0
      }, 
      ......
      ......
    ]
  },
  "return_code" : 0,
  "return_message" : "Success"
}
```

위험지역접근 보고서 검색 API

위험지역은 공사구간명(full_name) 표출하도록 변경 필요


#### HTTP Request

`/api/monitor/4.2/workplace/{wpNo}/dangerAp/report/search` -> `/api/monitor/4.3/workplace/{wpNo}/dangerAp/report/search`

#### Path variable

항목 | 필수 여부(M/O) | 데이터 타입          | 설명
--------- |------------|-----------------| -----------
wp_no | M          | number | 현장 관리번호


#### Request Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
page | M          | number | 검색 페이지
page_size | M          | number | 페이지당 건수
start_date | M          | string | 검색시작일
end_date | M          | string | 검색종료일


#### Response Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
full_Name | M          | string | 공사구간 fullname
coop_name | M          | string | 협력사명
coop_section_name | M          | string | 협력사 공종 ( work_section_name_a )
worker_section_name_a | M          | string | 근로자 공종 ( work_section_name_b )
slr_datetime | O          | number | 센서 접근 시간
cnt | M          | number | 감지수
authorized_cnt | M          | number | 인가자수


### 위험지역 접근 보고서 Excel 다운로드

> 요청 전문 예시

```JSON
{
  "start_date":"20241219",
  "end_date":"20241224"
}
```

엑셀 댜운로드 API


#### HTTP Request

`/api/monitor/4.2/workplace/{wpNo}/dangerAp/report/download` -> `/api/monitor/4.3/workplace/{wpNo}/dangerAp/report/download`


#### Path variable

항목 | 필수 여부(M/O) | 데이터 타입          | 설명
--------- |------------|-----------------| -----------
wp_no | M          | number | 현장 관리번호


#### Request Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
start_date | M          | string | 검색시작일
end_date | M          | string | 검색종료일



## 근로자 보건관리 컴포넌트 API 변경


### IMOS 보건관리 현황 근로자 위치 조회

응답값에 cstrt_no 추가

'/api/monitor/4.2/workplace/{wpNo}/health/worker/location/{mbNo}'

변경 API [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.2%5DIMOS%20%EA%B7%BC%EB%A1%9C%EC%9E%90%20%EB%B3%B4%EA%B1%B4%EA%B4%80%EB%A6%AC%20%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8%20API/workerLocationUsingGET)


