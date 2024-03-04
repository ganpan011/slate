# CCTV API

CCTV 검색, CCTV Play 를 위한 필요 정보 API 를 제공합니다.


## CCTV 리스트 검색

> 요청 전문 예시

```JSON
{
  "search_name" : "검색대상",
  "search_value" : "검색값",
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
    "install_type" : 0
  } ]
}
```

CCTV 리스트 검색을 제공합니다.
기본적으로 EMStone NVR 이용하는 CCTV 리스트만 제공합니다. ( 타 연동방식은 BLE 화면에서 현재는 제공 불가 )

마커 CCTV 관련하여 install_type 을 지정하여 리스트 검색하여야 합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20CCTV%20API%20/exportUsingPOST)

### HTTP Request

`POST /imoa/api/monitor/4.3/workplace/{wp_no}/cctv/export`


### Path variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호

### Request BODY

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
search_name | O          | string | 검색대상. 'COMPLEX' : 전체
search_value | O          | string | 검색값
install_type | O          | number | 설치 유형. 0: 고정형, 1: 이동형


### Response Body

항목 | 필수 여부(M/O) | 데이터 타입   | 설명
--------- |------------|----------| -----------
cctv_no | M          | number  | CCTV 관리번호
cctv_name | M          | string | CCTV명                                        
cctv_kind | M          | number | CCTV 유형. 0: 일반, 1: IntelliVix, 2: Emstone    
cctv_url | M          | string | CCTV 연동을 위한 URL. ( MJPEG 방식 플레이 필요 정보 )      
conn_type | M          | string | CCTV 연동 방식                                   
install_type | M          | number | 설치 유형. 0: 고정형, 1: 이동형                        


## CCTV Play 를 위한 정보 조회 ( NVR 방식 )

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

EMStone NVR 이용하는 CCTV Play 를 위한 정보를 제공합니다. ( conn_type 이 NVR 방식 )

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20CCTV%20API%20/viewUsingGET) 

<aside class="notice">
BLE Mode 에서 CCTV Play 는 BLE Monitor API 내 CCTV 플로팅 팝업 관련 API 를 이용하여주세요.    
</aside>


### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/cctv/preview/nvr/{cctvNo}`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호
cctv_no | M          | number | CCTV 관리번호


### Response Body

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
cctv_url | M          | CCTV 연동을 위한 URL. ( MJPEG 방식 플레이 필요 정보 )
id  | M          | NVR 연동을 위한 아이디
pw  | M          | NVR 연동을 위한 패스워드


## CCTV Play 를 위한 정보 조회 ( NVRV 방식 )

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

Intellivix NVR 이용하는 CCTV Play 를 위한 정보를 제공합니다. ( conn_type 이 NVRV 방식 )

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20CCTV%20API%20/previewUsingGET)

### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/cctv/preview/nvrv/{cctvNo}`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호
cctv_no | M          | number | CCTV 관리번호


### Response Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
ip | M          | string | NVR 연동 IP
uid  | M          | number | NVR 에 따른 채널(정수형) 아이디
streamer_ip  | M          | string | NVR Stream IP
streamer_port  | M          | string | NVR Stream Port
streamer_src_port  | M          | string | NVR Stream source Port
auth_key  | M          | string | NVR Stream 접속을 위한 키
access_key  | M          | string | NVR Stream access key
