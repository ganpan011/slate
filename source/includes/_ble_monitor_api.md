# BLE Monitor API

BLE mode 화면 표시를 위한 구성 정보 조회 API 입니다.

> 전체 응답 전문 예시

```json
{
  "context": {
    "cstrt_no": 1,
    "cstrt_name": "상단",
    "image_url": "공사 구간 이미지 URL",
    "marker_list": [
      {  
        "mk_no": 1,
        "mk_name": "표시명(라벨 표시 텍스트)",
        "mk_type": 1,
        "grid_x": 10.12,
        "grid_y": 98.99,
        "label_text": "라벨 표시 텍스트",
        "lnk_cstrt_no": 1,
        "attached_target": 1,
        "ap_sensor_stat" : {
          "caution_count" : 3,
          "danger_worker_count" : 1,
          "worker_count" : 2
        },
        "option": {
        },
        "style": {
          "font_size": "font 사이즈",
          "font_color": "font 색상",
          "bg_color": "백그라운드 색상"
        }
      },
      {
        "mk_no": 2,
        "mk_name": "표시명(아이콘 유형명)",
        "mk_type": 2,
        "grid_x": 10.12,
        "grid_y": 98.99,
        "attached_target": 1,
        "lnk_cstrt_no": 3,
        "icon_type" : 1,
        "icon_info" : {
          "icon_type" : 1,
          "icon_usage" : 1,
          "icon_type_name" : "아이콘명",
          "icon_url" : "아이콘 URL"
        },
        "option": {
        },
        "style": {
          "icon_size" : 10
        }
      },
      {
        "mk_no": 3,
        "mk_name": "표시명(디바이스 표시명)",
        "mk_type": 3,
        "grid_x": 10.12,
        "grid_y": 98.99,
        "attached_target": 1,
        "ref_device_idx" : 14,
        "device_info" : {
          "idx" : 14,
          "display_name" : "디바이스명",
          "device_type" : 14,
          "device_type_name" : "디바이스 유형명",
          "status" : 1,
          "dv_status" : 1
        }, 
        "option": {
          "show_name" : 1
        },
        "style": {
        }
      },
      {
        "mk_no": 4,
        "mk_type": 4,
        "mk_name": "표시명(센서명)",
        "grid_x": 10.12,
        "grid_y": 98.99,
        "attached_target": 1,
        "ref_sensor_idx" : 14,
        "ap_sensor_info" : {
          "si_idx" : 14,
          "si_type" : "위험센서",
          "sd_name" : "센서 구역명",
          "si_place1" : "위치1",
          "si_place2" : "위치2",
          "equipment_icon_url_list" :  [],
          "default_color" : "기본 색상",
          "support_flash" : "flash 지원여부",
          "flash_color" : "flash 색상",
          "worker_count" : 40,
          "danger_worker_count" : 5,
          "caution_count" : 1,
          "marker" : 1
        },
        "option": {
          "show_name" : 1
        },
        "style": {
        }
      },
      {
        "mk_no": 5,
        "mk_type": 5,
        "mk_name": "표시명(디바이스 표시명)",
        "grid_x": 10.12,
        "grid_y": 98.99,
        "attached_target": 1,
        "ref_device_idx" : 14,
        "device_info" : {
          "idx" : 14,
          "display_name" : "디바이스명",
          "device_type" : 14,
          "device_type_name" : "디바이스 유형명",
          "status" : 1,
          "dv_status" : 1
        },
        "option": {
          "show_icon" : 1,
          "auto_hide" : 1
        },
        "style":{
          "font_color" : "font 색상",
          "bg_color" : "백그라운드 색상"
        }
      },
      {
        "mk_no": 6,
        "mk_type": 6,
        "mk_name": "표시명(qr sticker 명)",
        "grid_x": 10.12,
        "grid_y": 98.99,
        "attached_target": 1,
        "ref_qr_stk_no" : 14,
        "qr_stk_info" : {
          "qr_stk_no" : 14,
          "qr_stk_name" : "qr sticker 명",
          "qr_type" : 1,
          "inout_type" : 1
        },
        "option": {
          "show_name" : 1,
          "show_count" : 1
        },
        "style":{
          "font_color" : "font 색상",
          "bg_color" : "백그라운드 색상"
        }
      },
      {
        "mk_no": 7,
        "mk_type": 7,
        "mk_name": "표시명(CCTV 명)",
        "grid_x": 10.12,
        "grid_y": 98.99,
        "attached_target": 1,
        "ref_cctv_no" : 14,
        "cctv_info" : {
          "cctv_no" : 14,
          "cctv_name" : "CCTV명",
          "cctv_kind" : 1,
          "install_type" : 1
        },
        "option": {
          "show_name" : 1
        },
        "style":{
        }
      }
    ],
    "progressbar": {
      "bar_no": 1,
      "items": [
        {
          "bar_no": 1,
          "item_idx": 1,
          "show_item": 1,
          "start_position": 22.22,
          "ref_cstrt_no" : 3,
          "prg_info" : {
            "cstrt_no" : 3,
            "cstrt_name" : "공사구간명",
            "construct_distance" : 3212,
            "progress_distance" : 122,
            "depth" : 1.22
          },
          "tbm_front_cctv_no": 1,
          "tbm_front_cctv_info" : {
            "cctv_no" : 14,
            "cctv_name" : "CCTV명",
            "cctv_kind" : 1,
            "install_type" : 1
          },
          "tbm_back_cctv_no": 1,
          "tbm_back_cctv_info" : {
            "cctv_no" : 14,
            "cctv_name" : "CCTV명",
            "cctv_kind" : 1,
            "install_type" : 1
          },
          "option": {
            "direction": 1,
            "show_distance": 1,
            "show_tbm": 1
          },
          "style": {
            "height": "높이",
            "color": "색상",
            "font_size": "font 사이즈"
          }
        }
      ]
    }
  },
  "return_code": 0,
  "return_message": "string"
}
```

## 현장 공사구간 내 표시 정보 조회

현장 공사구간 영역에 표시될 마커 및 공사 진행 정보를 제공한다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20BLE%20Mode%20API%20/constructSiteCoordinateUsingGET)


### HTTP Request

`POST /imoa/api/monitor/4.3/workplace/{wp_no}/ble/{cstrt_no}`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입          | 설명
--------- |------------|-----------------| -----------
wp_no | M          | number | 현장 관리번호
cstrt_no | M          | number | 공사구간 번호

### Request Parameter

항목 | 필수 여부(M/O) | 데이터 타입 | 설명설명
--------- |------------|--------| -----------
marker_mb_no | O          | number | AP 센서 디텍딩 마킹대상 근로자 관리번호

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입          | 설명
--------- |------------|-----------------| -----------
cstrt_no | M          | number          | 공사구간 관리번호
cstrt_name | M          | string          | 공사구간명
image_url | M          | string          | 공사구간 이미지 URL
marker_list | O          | List<BleMarker> | 표시될 마커 리스트.  [BleMarker](#blemarker)
progressbar | O          | BleProgressBar | 공사 진행 현황 정보. [BleProgressBar](#bleprogressbar)


## 현장 메인(조감도) 내 표시 정보 조회 ( 현장 관리번호 기반 )

현장 관리번호 기반 현장 메인 영역(조감도)에 표시될 마커 및 공사 진행현황바 정보를 제공한다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20BLE%20Mode%20API%20/mainCoordinateUsingGET)

기존 API Deprecated ( 사용 불가 )

1. BLE (조감도) Monitoring Data 검색 [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.1%5D%20IMOS%20%EC%9D%BC%EB%B0%98%20%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81%20%EA%B4%80%EB%A6%AC/workplaceBleMonitoringDataUsingGET)


### HTTP Request

`POST /imoa/api/monitor/4.3/workplace/{wp_no}/ble`


### Path variable

항목 | 필수 여부(M/O) | 데이터 타입          | 설명
--------- |------------|-----------------| -----------
wp_no | M          | number | 현장 관리번호


### Request Parameter

항목 | 필수 여부(M/O) | 데이터 타입 | 설명설명
--------- |------------|--------| -----------
marker_mb_no | O          | number | AP 센서 디텍딩 마킹대상 근로자 관리번호

### Response Body

현장 공사구간 내 표시 정보 조회 결과와 동일


## 현장 빌딩(단면도/구획도) 내 표시 정보 조회 ( 빌딩 관리번호 기반 )

빌딩 관리번호를 이용한 현장 공사구간 내 표시 정보 조회 제공. 불가피한 경우 사용


<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20BLE%20Mode%20API%20/constructSiteCoordinateByBuildingUsingGET_1)

기존 API Deprecated ( 사용 불가 )

1. BLE (단면도) Monitoring Data 검색 [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.1%5D%20IMOS%20%EC%9D%BC%EB%B0%98%20%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81%20%EA%B4%80%EB%A6%AC/workplaceBleBuildingMonitoringDataUsingGET)

### HTTP Request

`POST /imoa/api/monitor/4.3/workplace/{wp_no}/ble/old/{building_no}`


### Path variable

항목 | 필수 여부(M/O) | 데이터 타입          | 설명
--------- |------------|-----------------| -----------
wp_no | M          | number | 현장 관리번호
building_no | M          | number | 빌딩 관리번호


### Request Parameter

항목 | 필수 여부(M/O) | 데이터 타입 | 설명설명
--------- |------------|--------| -----------
marker_mb_no | O          | number | AP 센서 디텍딩 마킹대상 근로자 관리번호

### Response Body

현장 공사구간 내 표시 정보 조회 결과와 동일


## 현장 층(평면도) 내 표시 정보 조회 ( 층 관리번호 기반 )

층 관리번호를 이용한 현장 공사구간 내 표시 정보 조회 제공. 불가피한 경우 사용

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20BLE%20Mode%20API%20/constructSiteCoordinateByBuildingUsingGET_1)

기존 API Deprecated ( 사용 불가 )
 
1. BLE (평면도) Monitoring Data 검색 [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.1%5D%20IMOS%20%EC%9D%BC%EB%B0%98%20%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81%20%EA%B4%80%EB%A6%AC/workplaceBleBuildingFloorMonitoringDataUsingGET)


### HTTP Request

`POST /imoa/api/monitor/4.3/workplace/{wp_no}/ble/old/{building_no}/{floor}`


### Path variable

항목 | 필수 여부(M/O) | 데이터 타입          | 설명
--------- |------------|-----------------| -----------
wp_no | M          | number | 현장 관리번호
building_no | M          | number | 빌딩 관리번호
floor | M          | number | 층번호

### Request Parameter

항목 | 필수 여부(M/O) | 데이터 타입 | 설명설명
--------- |------------|--------| -----------
marker_mb_no | O          | number | AP 센서 디텍딩 마킹대상 근로자 관리번호


### Response Body

현장 공사구간 내 표시 정보 조회 결과와 동일


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
slr_datetime | O          | number | 센서 접근 시간


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

### Request Path

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호
mb_no | M          | number | 사용자 관리번호

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
wp_no | M          | number | 현장 관리번호
wp_name | M          | string | 현장명
cstrt_no | M          | number | 공사구간 관리번호
cstrt_name | M          | string | 공사구간명
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
slr_datetime | O          | number | 센서 접근 시간


