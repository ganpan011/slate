# BLE Monitor API

BLE mode 화면 표시를 위한 구성 정보 조회 API 입니다.


## 현장 공사구간 내 표시 정보 조회 ( 공사구간 관리번호 이용 )


> 전체 응답 전문 예시. [BleMarker](#blemarker)  및 [BleProgressBar](#bleprogressbar) 참고

```json
{
  "context": {
    "cstrt_no": 1,
    "cstrt_name": "공사구간명",
    "full_name": "상위명 / 공사구간명",
    "up_cstrt_no": 2,
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
          "rct_status": 1,
          "dv_status": 1,
          "state": 1,
          "state_name": "장치 상태명",
          "show_popup": true,
          "popup_display_items": [
            {
              "code": "DEVICE_TYPE",
              "name": "구분",
              "value": "기울기 센서"
            },
            {
              "code": "MEASURE_TIME",
              "name": "데이터 수신시각",
              "value": "2024-02-16T01:30:00.000+00:00"
            },
            {
              "code": "DASHIBOARD_POPUP",
              "name": "알림 상태",
              "value": 1
            }
          ]
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
          "rct_status": 1,
          "dv_status": 1,
          "state": 1,
          "state_name": "장치 상태명",
          "show_popup": false,
          "popup_display_items": []
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
          "inout_type" : 1,
          "inout_count" : 12
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
          "blank_item": 0,
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
          "direction": 1,
          "show_distance": 1,
          "show_tbm": 1,
          "option": {
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
full_name | M          | string          | 공사구간 full 명 ( 상위 공사구간이 있을 경우 상위공사구간명 + '/' + 공사구간명 ) 
up_cstrt_no | M          | number          | 상위 이동을 위한 상위 공사구간 관리번호 
image_url | M          | string          | 공사구간 이미지 URL
marker_list | O          | List<BleMarker> | 표시될 마커 리스트.  [BleMarker](#blemarker)
progressbar | O          | BleProgressBar  | 공사 진행 현황 정보. [BleProgressBar](#bleprogressbar)


## 현장 최상위 공사구간 내 표시 정보 조회 ( 현장 관리번호 기반 )

현장 관리번호 기반으로 현장 내 최상위 공사구간에 표시될 마커 및 공사 진행현황바 정보를 제공한다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20BLE%20Mode%20API%20/mainCoordinateUsingGET)

기존 API Deprecated ( 사용 불가 )

1. BLE (조감도) Monitoring Data 검색 [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.1%5D%20IMOS%20%EC%9D%BC%EB%B0%98%20%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81%20%EA%B4%80%EB%A6%AC/workplaceBleMonitoringDataUsingGET)


### HTTP Request

`POST /imoa/api/monitor/4.3/workplace/{wp_no}/ble/main`


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



## CCTV 플로팅 팝업 리스트 조회 

> 응답 전문 예시

```JSON
{
  "return_code": 0,
  "return_message": "Success",
  "context": [
    {
      "mk_no": 1,
      "cctv_no": 1,
      "cctv_name": "카메라",
      "cctv_url": "CCTV URL",
      "cctv_kind": 0,
      "conn_type": "NVR",
      "install_type": 0,
      "id": "계정 아이디",
      "pwd": "계정 패스워드",
      "floating_popup": {
        "grid_x": 10.00,
        "grid_y": 20.00,
        "height": 200.00,
        "width": 500.00
      }
    }
  ]
}
```

BLE 공사구간 화면에 플로팅 되어야 하는 CCTV Play 팝업 리스트를 제공한다. 

해당 리스트 조회 후 CCTV Play 를 위한 플로팅 팝업 화면 생성 후 CCTV Play 를 시작하여야 한다. 

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20BLE%20Mode%20API%20/cctvFloatingListUsingGET)


### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/ble/{cstrt_no}/cctv/floating`

### Path Variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호
cstrt_no | M          | number | 공사구간 관리번호

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|-------------| -----------
cctv_no | M          | number | CCTV 관리번호
cctv_name | M          | string | CCTV명
cctv_kind | M          | number | CCTV 유형. 0: 일반, 1: IntelliVix, 2: Emstone
cctv_url | M          | string | CCTV 연동을 위한 URL. ( MJPEG 방식 플레이 필요 정보 )
conn_type | M          | string | CCTV 연동 방식
install_type | M          | number | 설치 유형. 0: 고정형, 1: 이동형                        
id | M          | number | CCTV Play 를 위한 계정 아이디
pwd | M          | number | CCTV Play 를 위한 계정 패스워드
floating_popup | M          | Object | 플로팅 팝업 위치 및 사이즈

#### floating_popup

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|-------------| -----------
grid_x	 | M          | decimal | 팝업 x 축 좌표
grid_y | M          | decimal | 팝업 y 축 좌표
height	 | M          | decimal | 팝업 높이
width | M          | decimal | 팝업 길이




## CCTV 플로팅 팝업 오폰(위치 이동시) 요청

> 요청 전문 예시

```JSON
{
  "grid_x": 10.00,
  "grid_y": 20.00,
  "height": 200.00,
  "width": 500.00
}
``` 

> 응답 전문 예시

```JSON
{
  "return_code": 0,
  "return_message": "Success",
  "context": {
    "mk_no": 1,
    "cctv_no": 1,
    "cctv_name": "카메라",
    "cctv_url": "CCTV URL",
    "cctv_kind": 0,
    "conn_type": "NVR",
    "install_type": 0,
    "id": "계정 아이디",
    "pwd": "계정 패스워드",
    "floating_popup": {
      "grid_x": 10.00,
      "grid_y": 20.00,
      "height": 200.00,
      "width": 500.00
    }
  }
}
```

BLE 공사구간 CCTV 마커 클릭시 플로팅 팝업 화면 생성 후 플로팅 팝업 위치 지정 및 CCTV Play 를 위한 정보 요청을 위해 이용하는 API 입니다.

플로팅 팝업의 위치를 이동시에도 해당 API 를 호출하여야 합니다.  

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20BLE%20Mode%20API%20/openCctvFloatingUsingPOST)


### HTTP Request

`POST /imoa/api/monitor/4.3/workplace/{wp_no}/ble/{cstrt_no}/cctv/floating/{mk_no}`

### Path Variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호
cstrt_no | M          | number | 공사구간 관리번호
mk_no | M          | number | 마커 관리번호

### Request Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|-------------| -----------
grid_x	 | M          | decimal | 팝업 x 축 좌표
grid_y | M          | decimal | 팝업 y 축 좌표
height	 | M          | decimal | 팝업 높이
width | M          | decimal | 팝업 길이

### Response Body

CCTV 플로팅 팝업 리스트 조회의 항목 참고


## CCTV 플로팅 팝업 종료 요청

BLE 공사구간 CCTV 플로팅 팝업 종료시 해당 API 를 호출하여야 합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20BLE%20Mode%20API%20/updateCctvFloatingInfoUsingDELETE)


### HTTP Request

`DELETE /imoa/api/monitor/4.3/workplace/{wp_no}/ble/{cstrt_no}/cctv/floating/{mk_no}`

### Path Variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호
cstrt_no | M          | number | 공사구간 관리번호
mk_no | M          | number | 마커 관리번호


