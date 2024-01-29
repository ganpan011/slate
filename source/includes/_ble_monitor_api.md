# BLE Monitor API

BLE mode 화면 표시를 위한 구성 정보 조회 API 입니다.

## 현장 메인(조감도) 내 표시 정보 조회

> 응답 전문 예시

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
        "lnk_cstrt_no": 2,
        "label_text": "라벨 표시 텍스트",
        "lnk_cstrt_no": 1,
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
        "lnk_cstrt_no": 3,
        "icon_type" : 1,
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
        "ref_device_idx" : 14,
        "device_state" : {
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
        "ref_sensor_idx" : 14,
        "ap_sensor_state" : {
          "marker" :  1,
          "si_type" : "위험센서",
          "worker_count" : 40,
          "caution_count" : 1,
          "equipment_icon_url_list" :  [],
          "default_color" : "gray",
          "support_flash" : "flash 지원여부",
          "flash_color" : "gray",
          "sd_name" : "센서 구역명",
          "si_place1" : "위치1",
          "si_place2" : "위치2",
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
        "ref_device_idx" : 14,
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
        "ref_qr_stk_no" : 14,
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
        "ref_cctv_no" : 14,
        "option": {
          "show_name" : 1
        },
        "style":{
        }
      }
    ],
    "progressbar": {
      "pgrbar_no": 1,
      "items": [
        {
          "bar_idx": 1,
          "show_item": 1,
          "start_position": 1,
          "ref_cstrt_no" : 3,
          "tbm_front_cctv_no": 1,
          "tbm_back_cctv_no": 1,
          "pgr_info" : {
            "total_distance" : 1111,
            "progress_distance" : 80,
            "depth" : 5
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

현장 메인 영역에 표시될 마커 및 공사 진행 정보를 제공한다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

<aside class="warning">
API 미구현 
</aside>

기존 API 대체 ( Deprecated )

1. BLE (조감도) Monitoring Data 검색 [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.1%5D%20IMOS%20%EC%9D%BC%EB%B0%98%20%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81%20%EA%B4%80%EB%A6%AC/workplaceBleMonitoringDataUsingGET)

### HTTP Request

`POST /imoa/api/monitor/4.3/workplace/{wp_no}/ble`

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입          | 설명
--------- |------------|-----------------| -----------
cstrt_no | M          | number          | 공사구간 관리번호
cstrt_name | M          | string          | 공사구간명
image_url | M          | string          | 공사구간 이미지 URL
marker_list | O          | List<BleMarker> | 표시될 마커 리스트.  [BleMarker](#blemarker)
progressbar | O          | BleProgressBar | 공사 진행 현황 정보. [BleProgressBar](#bleprogressbar)   


## 현장 공사구간 내 표시 정보 조회

> 응답 전문 예시

```json
{
  "return_code": 0,
  "return_message": "Success",
  "context": {
    "cstrt_no": 1,
    "cstrt_name": "상단",
    "image_url": "공사 구간 이미지 URL",
    "parent_cstrt": 2,
    "marker_list": [
      {
        "mk_type" : 1,
        "mk_name" : "마커명",
        "lnk_cstrt_no" : 2,
        "label_text" : "라벨 표시 텍스트",
        "icon_type" : "아이콘 URL",
        "icon_type_name" : "아이콘 URL",
        "icon_url" : "아이콘 URL",
        "grid_x" : 10.12,
        "grid_y" : 98.99,
        "ref_cstrt_no" : 1,
        "ref_device_idx" : 14,
        "ref_sensor_idx" : 3,
        "ref_qr_stk_no" : 11,
        "ref_cctv_no" : 44,
        "option" : {
          "show_name" : 1,
          "show_icon" : 1,
          "show_count" : 1,
          "auto_hide" : 1
        },
        "style" : {
          "font_size" : "font 사이즈",
          "font_color" : "font 색상",
          "bg_color" : "백그라운드 색상",
          "icon_size" : 10
        }
      }
    ],
    "progressbar" : {
      "pgrbar_no" : 1,
      "items" : [
        {
          "bar_idx" : 1,
          "show_item" : 1,
          "start_position" : 1,
          "tbm_front_cctv_no" : 1,
          "tbm_back_cctv_no" : 1,
          "option" : {
            "direction" : 1,
            "show_distance" : 1,
            "show_tbm" : 1
          },
          "style" : {
            "height" : "높이",
            "color" : "색상",
            "font_size" : "font 사이즈"
          }
        }
      ]
    }
  }
}
```

현장 공사구간 영역에 표시될 마커 및 공사 진행 정보를 제공한다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

<aside class="warning">
API 미구현 
</aside>


기존 API 대체 ( Deprecated )

1. BLE (조감도) Monitoring Data 검색 [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.1%5D%20IMOS%20%EC%9D%BC%EB%B0%98%20%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81%20%EA%B4%80%EB%A6%AC/workplaceBleMonitoringDataUsingGET)
2. 
3. BLE (단면도) Monitoring Data 검색 [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.1%5D%20IMOS%20%EC%9D%BC%EB%B0%98%20%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81%20%EA%B4%80%EB%A6%AC/workplaceBleBuildingMonitoringDataUsingGET)
4. 
5. BLE (평면도) Monitoring Data 검색 [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.1%5D%20IMOS%20%EC%9D%BC%EB%B0%98%20%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81%20%EA%B4%80%EB%A6%AC/workplaceBleBuildingFloorMonitoringDataUsingGET)


### HTTP Request

`POST /imoa/api/monitor/4.3/workplace/{wp_no}/ble/{cstrt_no}`

`POST /imoa/api/monitor/4.3/workplace/{wp_no}/ble/old/{building_no}`

`POST /imoa/api/monitor/4.3/workplace/{wp_no}/ble/old/{building_no}/{floor}`

### Path variable

#### 신규 공사기간 관리번호로 조회시

항목 | 필수 여부(M/O) | 데이터 타입          | 설명
--------- |------------|-----------------| -----------
wp_no | M          | number | 현장 관리번호
cstrt_no | M          | number | 공사구간 번호

#### 기존 빌딩번호로 조회시  ( 기존 단면도/구획도 )

항목 | 필수 여부(M/O) | 데이터 타입          | 설명
--------- |------------|-----------------| -----------
wp_no | M          | number | 현장 관리번호
building_no | M          | number | 빌딩번호

#### 기존 빌딩번호와 층번호로 조회시 ( 기존 평면도 )

항목 | 필수 여부(M/O) | 데이터 타입          | 설명
--------- |------------|-----------------| -----------
wp_no | M          | number | 현장 관리번호
building_no | M          | number | 빌딩번호
floor | M          | number | 층번호

### Response Body

현장 메인(조감도) 과 결과 구성은 동일하나 추가 정보가 존재

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
parent_cstrt | O          | 상위 공사구간 번호. 메인인 경우 존재하지 않는다.


## BLE 근로자 위치 검색

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success",
  "context" : [{
    "cstrt_no" : 1,
    "cstrt_name" : "string",
    "si_idx" : 1,
    "si_type" : "string",
    "si_place1" : "string",
    "si_place2" : "string"
  }]
}
```

BLE 근로자 검색하여 감지된 AP 센서 및 AP 센서가 위치한 공사구간 정보를 제공한다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

<aside class="warning">
API 미구현 
</aside>

기존 API 대체 ( Deprecated )

1. BLE 스마트 안전모니터 근로자 위치 검색 [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.1%5D%20IMOS%20%EC%9D%BC%EB%B0%98%20%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81%20%EA%B4%80%EB%A6%AC/searchWorkerLocationUsingGET)


### HTTP Request

`POST /imoa/api/monitor/4.3/workplace/{wp_no}/ble/user/{mb_no}`

### Request Path

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호
mb_no | M          | number | 사용자 관리번호


### Response Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
cstrt_no | M          | number | 공사구간 관리번호
cstrt_name | M          | string | 공사구간명
si_idx | M          | number | AP 센서 관리번호
sd_name | M         | string | AP 센서 구역 이름
si_type | O          | string | AP 센서 유형
si_place1 | O          | string | 위치1
si_place2 | O          | string | 위치2


