# GPS Monitor API

GPS mode 화면 표시를 위한 구성 정보 조회 API 입니다.


## 현장 GPS 내 표시 fence 및 주요지점 정보 조회

> 응답 전문 예시

```json
{
  "return_code" : 0,
  "return_message" : "Success",
  "context" : {
    "gps_center_lat" : 37.381195354391956,
    "gps_center_long" : 126.64235510716414,
    "group_list" : [ {
      "fence_name" : "string",
      "center_latitude" : 37.38117259017983,
      "center_longitude" : 126.64227617802338,
      "fence_locations" : [ {
        "wp_no" : 1,
        "wp_seq" : 1,
        "seq" : 1,
        "latitude" : 37.3837092533823,
        "longitude" : 126.6408865751926
      }]
    }],
    "infowindows" : [
      {
        "iw_no" : 1,
        "iw_name" : "string",
        "iw_type" : 1,
        "ui_type" : 1,
        "action" : 2,
        "action_url" : "string",
        "milestone" : "string",
        "color" : "string",
        "img_files" : [ {
          "iw_img_no" : 1,
          "ord_weight" : 1,
          "img_url" : "string"
        }],
        "image_coordinate" : 1,
        "width" : 100,
        "height" : 100,
        "latitude" : 37.37716503885257,
        "longitude" : 126.64593073250983,
        "loc_type" : 1,
        "ord_weight" : 1,
        "ref_iw_no" : 1,
        "ref_latitude" : 37.37716503885257,
        "ref_longitude" : 126.64593073250983
      }
    ]
  }
}
```

현장 GPS Map 내 표시될 fence 및 주요지점 정보 제공합니다.

1시간마다 정보 호출하여 적용하여야 합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>



### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/gps/coordinate`

### Response Body

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
gps_center_lat | M          | 지도 Map 의 중심좌표 위도
gps_center_long | M          | 지도 Map 의 중심좌표 경도
group_list | O          | fence 정보 리스트
infowindows | O          | 주요지점 정보 리스트



## 장비 및 근로자 GPS 위치 정보 조회

> 응답 전문 예시

```json
{
  "return_code" : 0,
  "return_message" : "Success",
  "context": {
    "current_worker_count": 0,
    "drivers": [
      {
        "coop_name": "string",
        "data_key": "string",
        "data_name": "string",
        "data_type": "string",
        "equipment": {
          "coop_name": "string",
          "coop_no": 0,
          "device_id": "string",
          "equipment_name": "string",
          "equipment_no": "string",
          "equipment_type": 0
        },
        "icon_url": "string",
        "location": {
          "accuracy": 0,
          "altitude": 0,
          "battery": 0,
          "bearing": 0,
          "latitude": 0,
          "longitude": 0,
          "measure_time": "2024-02-02T08:49:23.031Z",
          "speed": 0
        },
        "marker": 0,
        "owner": {
          "coop_name": "string",
          "coop_no": 0,
          "mb_level_name": "string",
          "mb_name": "string",
          "mb_no": 0,
          "telephone": "string",
          "work_section_name_b": "string",
          "wp_name": "string",
          "wp_no": 0
        },
        "telephone": "string"
      }
    ],
    "equipments": [
      {
        "coop_name": "string",
        "data_key": "string",
        "data_name": "string",
        "data_type": "string",
        "equipment": {
          "coop_name": "string",
          "coop_no": 0,
          "device_id": "string",
          "equipment_name": "string",
          "equipment_no": "string",
          "equipment_type": 0
        },
        "icon_url": "string",
        "location": {
          "accuracy": 0,
          "altitude": 0,
          "battery": 0,
          "bearing": 0,
          "latitude": 0,
          "longitude": 0,
          "measure_time": "2024-02-02T08:49:23.031Z",
          "speed": 0
        },
        "marker": 0,
        "owner": {
          "coop_name": "string",
          "coop_no": 0,
          "mb_level_name": "string",
          "mb_name": "string",
          "mb_no": 0,
          "telephone": "string",
          "work_section_name_b": "string",
          "wp_name": "string",
          "wp_no": 0
        },
        "telephone": "string"
      }
    ],
    "gps_trackers": [
      {
        "cctv": {
          "cctv_name": "string",
          "cctv_no": 0,
          "conn_type": "string",
          "install_type": 0,
          "install_type_name": "string"
        },
        "device": {
          "device_id": "string",
          "device_idx": 0,
          "device_type": 0,
          "device_type_name": "string"
        },
        "device_name": "string",
        "device_type_name": "string",
        "equipment": {
          "coop_name": "string",
          "equipment_idx": 0,
          "equipment_name": "string",
          "equipment_no": "string",
          "equipment_type": "string"
        },
        "gps_device_id": "string",
        "gps_idx": 0,
        "icon_url": "string",
        "lat": "string",
        "lng": "string",
        "ref_key": "string",
        "ref_target": 0
      }
    ],
    "map_air_view_list": [
      {
        "cc_no": 0,
        "file_download_url": "string",
        "latitude": "string",
        "longitude": "string",
        "mav_name": "string",
        "mav_no": 0,
        "wp_no": 0
      }
    ],
    "total_worker_count": 0,
    "workers": [
      {
        "coop_name": "string",
        "data_key": "string",
        "data_name": "string",
        "data_type": "string",
        "equipment": {
          "coop_name": "string",
          "coop_no": 0,
          "device_id": "string",
          "equipment_name": "string",
          "equipment_no": "string",
          "equipment_type": 0
        },
        "icon_url": "string",
        "location": {
          "accuracy": 0,
          "altitude": 0,
          "battery": 0,
          "bearing": 0,
          "latitude": 0,
          "longitude": 0,
          "measure_time": "2024-02-02T08:49:23.031Z",
          "speed": 0
        },
        "marker": 0,
        "owner": {
          "coop_name": "string",
          "coop_no": 0,
          "mb_level_name": "string",
          "mb_name": "string",
          "mb_no": 0,
          "telephone": "string",
          "work_section_name_b": "string",
          "wp_name": "string",
          "wp_no": 0
        },
        "telephone": "string"
      }
    ]
  }
}
```

현장 GPS Map 영역에 표시될 장비 및 근로자 위치 정보를 제공합니다.

10초마다 정보 호출하여 적용하여야 합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

기존 API 사용. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.1%5D%20IMOS%20%EC%9D%BC%EB%B0%98%20%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81%20%EA%B4%80%EB%A6%AC/workplaceGpsMonitoringDataUsingGET)

### HTTP Request

`GET /imoa/api/monitor/4.1/workplace/{wp_no}/gps`

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
current_worker_count | M          | number | 현재인원
drivers | M          | List<Drivers> | 장비운전자 리스트
equipments | O          | List<Equipment> | 장비 데이터 리스트
gps_trackers | O          | List<GpsTracker> | GPS Tracker 정보
workers | O          | List<Worker> | 근로자 데이터 리스트


## GPS 근로자 검색

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success",
  "context" : [
    {
      "wp_no": 1,
      "wp_name": "현장명",
      "coop_no": 1,
      "coop_name": "협력사명",
      "mb_no": 1,
      "mb_name": "근로자명",
      "mb_level_name": "근로자 등급명",
      "telephone": "전화번호",
      "longitude": 126.643978,
      "latitude": 37.3834973,
      "measure_time": "2024-02-20T07:32:00.000+00:00"
    }
  ]
}
```

GPS 근로자 검색하여 위치 정보를 제공한다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

기존 API 사용. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.1%5D%20IMOS%20%EC%9D%BC%EB%B0%98%20%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81%20%EA%B4%80%EB%A6%AC/searchGpsUserByNameUsingGET)


### HTTP Request

`GET /imoa/api/monitor/4.1/workplace/{wp_no}/gps/user`

### Path Variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호


### Request Parameter

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
mb_name | M          | string | 근로자명

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입        | 설명
--------- |------------|---------------| -----------
wp_no | M          | number | 현장 관리번호
wp_name | M          | string | 현장명
coop_no | M          | number | 협력사 관리번호
coop_name | M          | string | 협력사명
mb_no | M          | number | 사용자 관리번호
mb_name | M          | string | 사용자명
telephone | M          | string | 전화번호
mb_level_name | M          | string       | 사용자 등급명
longitude | M          | decimal       | 경도
latitude | M          | decimal | 위도
measure_time | M          | number | 측정시간


## GPS 근로자 위치 조회

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success",
  "context" : {
    "longitude" : 127.1471356,
    "latitude" : 37.5357359,
    "altitude" : 59.30000305175781,
    "accuracy" : 12.661999702453613,
    "speed" : 0.0,
    "bearing" : 0.0,
    "battery" : -1.0,
    "measure_time" : "2024-02-02T08:55:39.000+00:00"
  }
}
```

GPS 근로자 GPS 위치 정보를 제공한다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

기존 API 사용. [Swagger](http://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.1%5D%20IMOS%20%EC%9D%BC%EB%B0%98%20%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81%20%EA%B4%80%EB%A6%AC/searchWorkerGpsLocationUsingGET)


### HTTP Request

`POST /imoa/api/monitor/4.1/workplace/{wp_no}/gps/user/{mb_no}`

### Request Path

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호
mb_no | M          | number | 사용자 관리번호


### Response Body

항목 | 필수 여부(M/O) | 데이터 타입  | 설명
--------- |------------|---------| -----------
longitude | M          | decimal | 경도
latitude | M          | decimal | 위도
measure_time | M          | number  | 측정시간
