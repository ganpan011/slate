# CCTV API

CCTV 검색, CCTV Play 를 위한 필요 정보 API 를 제공합니다.

## CCTV List 검색

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
  "cctv_no": 385,
  "cctv_name": "생활가압장 테스트",
  "cctv_kind": 0,
  "conn_type": "NVR",
  "cctv_url": "https://nvr64-1.hulandev.co.kr/live/video1.mjpg",
  "install_type": 0,
  "ptz_status": 1,
  "channel_id": "1",
  "nvr_manufacture": 1,
  "mjpeg_support": 1,
  "mjpeg_url": "https://nvr64-1.hulandev.co.kr/live/video1.mjpg",
  "camera_info_support": 1
}
```

CCTV 리스트 검색을 제공합니다.

* 마커 CCTV 관련하여 install_type 을 지정하여 리스트 검색하여야 합니다.

* CCTV 현장관제를 위해서는 install_type 을 지정하지 않고 리스트 검색하여야 합니다.
 - camera_info_support 가 1 인 경우 10분 간격으로 CCTV signal 상태를 위한 API 를 조회하여 CCTV 상태를 표시하여야 한다.

* 2024-09-03 API 변경
 - 응답값 : nvr_no, nvr_manufacture, mjpeg_support, mjpeg_url, camera_info_support 추가


<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 

<pre>
CCTV Play 를 위한 정보 수신
1. conn_type 이 NVR 이거나 MJPEG 인 경우 MJPEG OVER HTTP 방식으로 Play 를 하여야 한다.
 - Play 전 'CCTV Play 를 위한 정보 조회 ( NVR 방식 )' 를 통해 정보를 받아 Play 시도
2. conn_type 이 NVRV 인 경우 
 - Play 전 'CCTV Play 를 위한 정보 조회 ( NVRV 방식 )' 를 통해 정보를 받아 Play 시도
</pre>

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

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
cctv_no | M          | number | CCTV 관리번호
cctv_name | M          | string | CCTV명                                        
cctv_kind | M          | number | CCTV 유형. 0: 일반, 1: IntelliVix, 2: Emstone    
cctv_url | M          | string | CCTV 연동을 위한 URL. ( MJPEG 방식 플레이 필요 정보 ) - mjpeg_url 이용      
conn_type | M          | string | CCTV 연동 방식.  NVR, NVRV, MJPEG, RTSP ( 미지원 ), ONVIF ( 미지원 )                                  
install_type | M          | number | 설치 유형. 0: 고정형, 1: 이동형                        
ptz_status | M          | number | PTZ 지원 여부. 0: 미지원, 1: 지원
nvr_no | O          | number | NVR 관리번호
nvr_manufacture | O          | number | NVR 제조사 코드. 1: EMStone, 2: Intellivix
channel_id | O          | string | 채널 번호 ( NVR 내 채널 번호 )
mjpeg_support| M          | string | MJPEG 지원 여부
mjpeg_url| M          | string | MJPEG URL ( MJPEG 지원시 )
camera_info_support| M          | string | 카메라 정보 지원 여부


## CCTV Play 를 위한 정보 조회 ( NVR 방식 )

> 응답 전문 예시

```JSON
{
  "cctv_url": "https://nvr64-1.hulandev.co.kr/live/video1.mjpg",
  "nvr_manufacture": 1,
  "mjpeg_support": 1,
  "mjpeg_url": "https://nvr64-1.hulandev.co.kr/live/video1.mjpg",
  "camera_info_support": 1,
  "conn_type": "NVR",
  "port_type": null,
  "rstp_port": null,
  "port": null,
  "id": "admin",
  "pw": "XXXXXXXX"
}
```

MJPEG Over HTTP 를 이용하는 CCTV 관련 정보를 제공합니다. ( conn_type 이 NVR 방식 )
* 
* cctv_url 이 아닌 mjpeg_url 을 이용하여 주세요.

* 2024-09-03 API 변경

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

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
cctv_url | M          | CCTV 연동을 위한 URL. ( X )
id  | M          | NVR 연동을 위한 아이디
pw  | M          | NVR 연동을 위한 패스워드
nvr_manufacture | O          | number | NVR 제조사 코드. 1: EMStone, 2: Intellivix
mjpeg_support| M          | string | MJPEG 지원 여부
mjpeg_url| M          | string | MJPEG URL ( MJPEG 지원시 )
camera_info_support| M          | string | 카메라 정보 지원 여부
conn_type | M          | string | CCTV 연동 방식.  NVR, NVRV, MJPEG, RTSP ( 미지원 ), ONVIF ( 미지원 )
port_type | O          | string | 현재 미사용 ( X )
rstp_port | O          | string | 현재 미사용 ( X )
port | O          | string | 현재 미사용 ( X )


## CCTV Play 를 위한 정보 조회 ( NVRV 방식 )

> 응답 전문 예시

```JSON
{
  "context": {
    "ip": "nvrv.hulandev.co.kr",
    "uid": 3,
    "streamer_ip": "nvrv.hulandev.co.kr",
    "streamer_port": "9200",
    "streamer_src_port": "9200",
    "auth_key": "XXXXXX",
    "access_key": "AXXXXXX"
  },
  "return_code": 0,
  "return_message": "Success"
}
```

Intellivix NVR 이용하는 CCTV Play 를 위한 정보를 제공합니다. ( conn_type 이 NVRV 방식 )

CCTV Play 는 기존 웹 소스 참고.

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


## CCTV signal 상태 조회

> 응답 전문 예시

```JSON
{
  "context": {
    "signal_status_name": "정상",
    "signal_status": 1
  },
  "return_code": 0,
  "return_message": "Success"
}
```

CCTV signal 상태를 조회하는 API 입니다.
signal 이 OFF 인 경우 "CCTV 가 꺼져있습니다" 문구 내지는 관련 아이콘 표시. 
CCTV Play 를 지속하는 경우 10분마다 호출하여 signal 상태 체크하고 OFF -> ON 으로 바뀐 경우 다시 Play 시도를 하여야 한다. 

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20CCTV%20API%20/signalStatusUsingGET)

### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/cctv/signal/{cctvNo}`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호
cctv_no | M          | number | CCTV 관리번호


### Response Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
signal_status | M          | Number | signal 상태. 0: OFF, 1: 정상, 2: 상태 미지원, 99: 오류
signal_status_name | M          | string | signal 상태명

