# Marker 셋팅

설정화면에서 Marker 셋팅을 수행하기 위한 API 를 제공한다.

## 화면 설정을 위한 구성 정보 조회

> 응답 전문 예시

```json
{
  "return_code": 0,
  "return_message": "Success",
  "context": {
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

<aside class="warning">
API 미구현 
</aside>


### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/setting`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입           | 설명
--------- |------------|------------------| -----------
wp_no | M          | Number |현장 관리번호

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입           | 설명
--------- |------------|------------------| -----------
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
full_name | M          | string | 전체 공사구간명 ( 상위 공사구간이 있는 경우 공사구간명 + '/' + 공사구간명. 없으면 공사구간명 ) 



## 공사 구간 마커 및 진행현황 구성 정보 조회

> 응답 전문 예시

```json
{
  "return_code": 0,
  "return_message": "Success",
  "context": {
    "cstrt_no": 1,
    "cstrt_name": "상단",
    "image_url": "공사 구간 이미지 URL",
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
          "ref_cstrt_no" : 3,
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

설정을 위해 이미 지정된 마커 및 진행현황 구성 정보를 제공합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

<aside class="warning">
API 미구현 
</aside>


### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/setting/{cstrt_no}`

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
      "lnk_cstrt_no": 2,
      "label_text": "라벨 표시 텍스트",
      "lnk_cstrt_no": 1,
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
}
```

재설정된 공사 구간 마커 및 진행현황 구성 정보를 모두 저장합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

<aside class="warning">
API 미구현 
</aside>


### HTTP Request

`PUT /imoa/api/monitor/4.3/workplace/{wp_no}/setting/{cstrt_no}`

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

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

<aside class="warning">
API 미구현 
</aside>


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
