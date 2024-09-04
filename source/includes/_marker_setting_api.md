# BLE(도면기반) Marker 셋팅

설정화면에서 Marker 셋팅을 수행하기 위한 API 를 제공한다.

## 화면 설정을 위한 구성 정보 조회

> 응답 전문 예시

```json
{
  "return_code": 0,
  "return_message": "Success",
  "context": {
    "hcmpt_id": "I_MAIN",
    "hcmpt_name": "메인화면",
    "width": 3,
    "height": 2,
    "construct_section_list": [
      {
        "cstrt_no": 1,
        "cstrt_name": "상단",
        "full_name": "암센터/상단"
      }
    ],
    "registered_count" : {
      "iot" : [
        {
          "device_type": 1,
          "device_type_name": 2,
          "count" : 5
        }
      ],
      "ap_sensor_count": 11,
      "ble_gw_count": 2,
      "qr_count" : 12,
      "cctv_count" : 11
    }
  }
}
```

설정 화면 진입시 센서 등 유형별 등록 수와 공사 구간 리스트 정보를 제공합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20%EC%84%A4%EC%A0%95%20%ED%99%94%EB%A9%B4%20%EA%B5%AC%EC%84%B1%20%EB%B0%8F%20%EC%84%A4%EC%A0%95%20API%20/settingInitInfoUsingGET)


### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/ble/setting`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입           | 설명
--------- |------------|------------------| -----------
wp_no | M          | Number |현장 관리번호

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입           | 설명
--------- |------------|------------------| -----------
hcmpt_id | M          | string             | 현장의 메인 컴포넌트 아이디
hcmpt_name | M          | string             | 현장의 메인 컴포넌트명
width | M          | number             | 메인 컴포넌트 길이(1~4)
height | M          | number             | 메인 컴포넌트 높이(1~3)
construct_section_list | M          | List             | 공사구간 리스트
registered_count | M          | Object           | 등록 센서수 정보
registered_count.iot | M          | List             | 등록 IOT 센서 유형별 등록수 정보
registered_count.iot.device_type | M   | Number           | 등록 IOT 센서 유형           
registered_count.iot.device_type_name | M  | String           | 등록 IOT 센서 유형명    
registered_count.iot.count | M          | Number | 등록 IOT 센서 유형 등록수 
registered_count.ap_sensor_count | M    | Number       | AP 센서 전체수        
registered_count.ble_gw_count | M       | Number    | BLE GW 전체수       
registered_count.qr_count | M          | Number | 등록 qr 전체수        
registered_count.cctv_count | M         | Number  | 등록 cctv 전체수      


#### 공사구간 리스트 정보

항목 | 필수 여부(M/O) | 데이터 타입                                                     | 설명
--------- |------------|------------------------------------------------------------| -----------
cstrt_no | M          | number                                                     | 공사구간 관리번호
cstrt_name | M          | string                                                     | 공사구간명
full_name | M          | string          | 공사구간 full 명 ( 상위 공사구간이 있을 경우 상위공사구간명 + '/' + 공사구간명 ) 


## 공사 구간 마커 및 진행현황 구성 정보 조회

> 응답 전문 예시. 상세 정보는  [BleMarker](#blemarker)  및 [BleProgressBar](#bleprogressbar) 참고

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
        "lnk_url": "외부 링크 URL",
        "lnk_cstrt_no": 1,
        "actual_location": 1,
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
          "ref_cstrt_no": 3,
          "pgr_info": {
            "cstrt_no": 3,
            "cstrt_name": "공사구간명",
            "construct_distance": 3212,
            "progress_distance": 122,
            "depth": 1.22
          }
        }
      ]
    }
  },
  "return_code": 0,
  "return_message": "string"
}
```

설정을 위해 이미 지정된 마커 및 진행현황 구성 정보를 제공합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20%EC%84%A4%EC%A0%95%20%ED%99%94%EB%A9%B4%20%EA%B5%AC%EC%84%B1%20%EB%B0%8F%20%EC%84%A4%EC%A0%95%20API%20/findSettingDataUsingGET)


### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/ble/setting/{cstrt_no}`

### Path variable

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
wp_no | M          | 현장 관리번호
cstrt_no | M          | 공사 구간 관리번호

### Response Body

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
cstrt_no | M          | 공사구간 관리번호
cstrt_name | M          | 공사구간명
image_url | M          | 공사구간 이미지 URL
marker_list | M          | 설정된 marker 정보 리스트. 상세내용은 [BleMarker](#blemarker) 참고
progressbar | M          | 진행현황 바 정보. 상세내용은 [BleProgressBar](#bleprogressbar) 참고



## 공사 구간 마커 및 진행현황 구성 정보 저장

> 요청 전문 예시

```json
{
  "marker_list": [
    {
      "mk_no": 1,      
      "mk_type": 1,
      "grid_x": 10.12,
      "grid_y": 98.99,
      "attached_target" : 1,
      "actual_location" : 1,
      "lnk_url": "http://naver.com",
      "lnk_cstrt_no": 2,
      "label_text": "라벨 표시 텍스트",
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
      "mk_type": 2,
      "grid_x": 10.12,
      "grid_y": 98.99,
      "attached_target" : 1,
      "actual_location" : 1,
      "lnk_url": "http://naver.com",
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
      "mk_type": 3,
      "grid_x": 10.12,
      "grid_y": 98.99,
      "attached_target" : 1,
      "actual_location" : 1,
      "ref_device_idx" : 14,
      "option": {
        "show_name" : 1        
      },
      "style": {
      }
    },
    {
      "mk_no": 4,
      "mk_type": 4,
      "grid_x": 10.12,
      "grid_y": 98.99,
      "attached_target" : 1,
      "actual_location" : 1,
      "ref_sensor_idx" : 14,
      "option": {
        "show_name" : 1
      },
      "style": {
      }
    },
    {
      "mk_no": 5,
      "mk_type": 5,
      "grid_x": 10.12,
      "grid_y": 98.99,
      "attached_target" : 1,
      "actual_location" : 1,
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
      "grid_x": 10.12,
      "grid_y": 98.99,
      "attached_target" : 1,
      "actual_location" : 1,
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
      "grid_x": 10.12,
      "grid_y": 98.99,
      "attached_target" : 1,
      "actual_location" : 1,
      "ref_cctv_no" : 14,
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
        "item_idx": 1,
        "blank_item": 0,
        "start_position": 1,
        "ref_cstrt_no" : 3,
        "tbm_front_cctv_no": 1,
        "tbm_back_cctv_no": 1,
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
}
```

재설정된 공사 구간 마커 및 진행현황 구성 정보를 모두 저장합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20%EC%84%A4%EC%A0%95%20%ED%99%94%EB%A9%B4%20%EA%B5%AC%EC%84%B1%20%EB%B0%8F%20%EC%84%A4%EC%A0%95%20API%20/saveSettingDataUsingPUT)


### HTTP Request

`PUT /imoa/api/monitor/4.3/workplace/{wp_no}/ble/setting/{cstrt_no}`

### Path variable

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
wp_no | M          | 현장 관리번호
cstrt_no | M          | 공사 구간 관리번호

### Response Body

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
marker_list | M          | 설정 marker 정보 리스트. 상세내용은 [BleMarker](#blemarker) 참고
progressbar | M          | 진행현황 바 정보. 상세내용은 [BleProgressBar](#bleprogressbar) 참고



