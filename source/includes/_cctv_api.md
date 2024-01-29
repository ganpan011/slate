# CCTV

CCTV 검색, CCTV Play 를 위한 필요 정보 API 를 제공합니다.


## CCTV 리스트 검색

> 요청 전문 예시

```JSON
{
  "search_name" : "검색대상",
  "search_value" : "검색값",
  "wp_no" : 1,
  "install_type": 0
}

```

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success",
  "context" : [ {
    "cctv_no" : 1,
    "cctv_name" : "CCTV명",
    "cctv_kind" : 0,
    "cctv_url" : "https://hulan.co.kr/mjpeg.cgi?snapshot=on&channel=62",
    "id" : "id",
    "pw" : "pw",
    "status" : 1,
    "ptz_status" : 1,
    "install_type" : 0
  } ]
}
```

CCTV 리스트 검색을 제공합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

### HTTP Request

`POST /imoa/api/device/cctv/export`

### Request BODY

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
search_name | M          | 검색대상. 'COMPLEX' : 전체, 'cstrt_name' : '공사구간명'
search_value | M          | 검색값
wp_no | M          | 현장 관리번호
install_type | O          | 설치 유형. 0: 고정형, 1: 이동형


### Response Body

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
cctv_no | M          | CCTV 관리번호
cctv_name | M          | CCTV명
cctv_kind | M          | CCTV 유형. 0: 일반, 1: IntelliVix, 2: Emstone
cctv_url | M          | CCTV 연동을 위한 URL. ( MJPEG 방식 플레이 필요 정보 )
id  | M          | NVR 연동을 위한 아이디
pw  | M          | NVR 연동을 위한 패스워드
install_type | M          | 설치 유형. 0: 고정형, 1: 이동형



## CCTV Play 를 위한 정보 조회

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success",
  "context" : {
    "cctv_url" : "https://hulan.co.kr/mjpeg.cgi?snapshot=on&channel=62",
    "id" : "id",
    "pw" : "pw"
  } 
}
```

CCTV Play 를 위한 정보를 제공합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

### HTTP Request

`POST /imoa/api/device/cctv/preview/nvr/{cctv_no}`

### Path variable

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
cctv_no | M          | CCTV 관리번호


### Response Body

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
cctv_url | M          | CCTV 연동을 위한 URL. ( MJPEG 방식 플레이 필요 정보 )
id  | M          | NVR 연동을 위한 아이디
pw  | M          | NVR 연동을 위한 패스워드

