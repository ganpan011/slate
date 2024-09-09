# Map(지도기반) 모니터링 API

GPS(맵/지도) mode 화면 표시를 위한 API 입니다.


## Map설정, Geojson, Fence 및 주요지점 정보 조회 API

> 응답 전문 예시

```json
{
  "context": {
    // 지도 설정 정보 ( 지도 중심 좌표 및 지도 유형, 지도 표시 레벨 ) 
    "map_coordinate": {
      "gps_map_type": 1,
      "gps_map_level": 4,
      "gps_center_lat": 37.73398853063353,
      "gps_center_long": 128.86830269559175
    },
    // Geojson  
    "geojsons": [
      {
        "cc_no": 37,
        "cc_name": "맵기반 건설사1",
        "geojson": "{\"type\":\"FeatureCollection\",\"features\":[{\"type\":\"Feature\",\"geometry\":{\"type\":\"LineString\",\"coordinates\":[[127.31243539799125,37.16561965318349],[127.31038243082061,37.16467894163606],[127.31060609195322,37.164308923601574],[127.31138082761443,37.16379328984185],[127.3116736968801,37.16382856211558]]},\"properties\":{\"name\":\"road0\",\"color\":\"#0bf3f8\"}}]}"
      }
    ],
    // Fence ( Polygon ) 구성 정보
    "gps_fences": [
      {
        "csg_no": 23,
        "cc_no": 37,
        "cc_name": "맵기반 건설사1",
        "center_latitude": 37.734637270541704,
        "center_longitude": 128.8694306194166,
        "fence_name": "펜스#2",
        "fence_coordinates": [
          {
            "seq": 1,
            "latitude": 37.73678247838621,
            "longitude": 128.86594545158087
          },
          {
            "seq": 2,
            "latitude": 37.732516598643095,
            "longitude": 128.86454529013028
          },
          {
            "seq": 3,
            "latitude": 37.73099499159189,
            "longitude": 128.8730139759173
          },
          {
            "seq": 4,
            "latitude": 37.73627651836462,
            "longitude": 128.87398647409037
          },
          {
            "seq": 5,
            "latitude": 37.73848344713134,
            "longitude": 128.8700264870466
          }
        ]
      }
    ],
    // 주요 지점 정보
    "infowindows": [
      {
        "iw_no": 192,
        "cc_no": 37,
        "iw_name": "라벨 - 클릭없음",
        "iw_ntype": 1,
        "iw_display_type": 1,
        "action": 1,
        "action_url": null,
        "milestone": "라벨 표시 내용\n 줄바꿈 지원",
        "point_icon": null,
        "img_files": [],
        "iw_coordinate": 1,
        "latitude": 37.75285300000000,
        "longitude": 128.87605740000000,
        "ord_weight": 1,
        "option": {},
        "style": {
          "bg_color": "blue",
          "font_size": "12",
          "font_color": "red"
        }
      },
      {
        "iw_no": 194,
        "cc_no": 37,
        "iw_name": "라벨 - 이미지 팝업",
        "iw_ntype": 1,
        "iw_display_type": 1,
        "action": 2,
        "action_url": null,
        "milestone": "이미지 팝업\n 줄바꿈 지원",
        "point_icon": null,
        "img_files": [
          {
            "iw_img_no": 367,
            "ord_weight": 1,
            "img_url": "//new-api.hulandev.co.kr/static/infowindow/20240821163508353_QEjnMW8r3p.png"
          },
          {
            "iw_img_no": 368,
            "ord_weight": 2,
            "img_url": "//new-api.hulandev.co.kr/static/infowindow/20240821164635867_yXIwISfiZ7.jpg"
          }
        ],
        "iw_coordinate": 1,
        "latitude": 37.75185300000000,
        "longitude": 128.87605740000000,
        "ord_weight": 1,
        "option": {},
        "style": {
          "bg_color": "red",
          "font_size": "12",
          "font_color": "blue"
        }
      },
      {
        "iw_no": 195,
        "cc_no": 37,
        "iw_name": "라벨 - 링크",
        "iw_ntype": 1,
        "iw_display_type": 1,
        "action": 3,
        "action_url": "http://naver.com",
        "milestone": "링크\n 줄바꿈 지원",
        "point_icon": null,
        "img_files": [],
        "iw_coordinate": 4,
        "latitude": 37.75185300000000,
        "longitude": 128.88605740000000,
        "ord_weight": 1,
        "option": {},
        "style": {
          "bg_color": "yellow",
          "font_size": "12",
          "font_color": "blue"
        }
      },
      {
        "iw_no": 196,
        "cc_no": 37,
        "iw_name": "이미지 - 이미지 팝업",
        "iw_ntype": 2,
        "iw_display_type": 1,
        "action": 2,
        "action_url": null,
        "milestone": null,
        "point_icon": null,
        "img_files": [
          {
            "iw_img_no": 369,
            "ord_weight": 1,
            "img_url": "//new-api.hulandev.co.kr/static/infowindow/20240821163508353_QEjnMW8r3p.png"
          },
          {
            "iw_img_no": 370,
            "ord_weight": 2,
            "img_url": "//new-api.hulandev.co.kr/static/infowindow/20240821164635867_yXIwISfiZ7.jpg"
          }
        ],
        "iw_coordinate": 4,
        "latitude": 37.75185300000000,
        "longitude": 128.85605740000000,
        "ord_weight": 1,
        "option": {},
        "style": {
          "width": "150",
          "height": "150"
        }
      },
      {
        "iw_no": 197,
        "cc_no": 37,
        "iw_name": "이미지 - 링크",
        "iw_ntype": 2,
        "iw_display_type": 1,
        "action": 3,
        "action_url": "http://daum.net",
        "milestone": null,
        "point_icon": null,
        "img_files": [
          {
            "iw_img_no": 372,
            "ord_weight": 1,
            "img_url": "//new-api.hulandev.co.kr/static/infowindow/20240821164635867_yXIwISfiZ7.jpg"
          }
        ],
        "iw_coordinate": 4,
        "latitude": 37.75185300000000,
        "longitude": 128.65605740000000,
        "ord_weight": 1,
        "option": {
          "display_name": 1
        },
        "style": {
          "width": "200",
          "height": "200"
        }
      },
      {
        "iw_no": 198,
        "cc_no": 37,
        "iw_name": "이미지 - 화면 기반",
        "iw_ntype": 2,
        "iw_display_type": 2,
        "action": 3,
        "action_url": "http://daum.net",
        "milestone": null,
        "point_icon": null,
        "img_files": [
          {
            "iw_img_no": 373,
            "ord_weight": 1,
            "img_url": "//new-api.hulandev.co.kr/static/infowindow/20240821163508353_QEjnMW8r3p.png"
          }
        ],
        "iw_coordinate": 2,
        "latitude": null,
        "longitude": null,
        "ord_weight": 1,
        "option": {
          "display_name": 1
        },
        "style": {
          "width": "200",
          "height": "200"
        }
      },
      {
        "iw_no": 199,
        "cc_no": 37,
        "iw_name": "포인트",
        "iw_ntype": 3,
        "iw_display_type": 1,
        "action": 1,
        "action_url": null,
        "milestone": null,
        "point_icon": "icon명",
        "img_files": [],
        "iw_coordinate": 1,
        "latitude": 37.74185300000000,
        "longitude": 128.67605740000000,
        "ord_weight": 1,
        "option": {
          "display_name": 1
        },
        "style": {
          "size": 100
        }
      }
    ]
  },
  "return_code": 0,
  "return_message": "Success"
}
```

현장 지도(Map) 영역 표시를 위한 Map 설정 정보와 주요지점, Fence, Geojson(Overray) 정보를 제공한다.

처음 지도(Map) 표출시 Map 설정 정보가 있을 경우 GPS 좌표로 중심을 이동하여야 하며 맵 타입 및 레벨 설정을 하여야 한다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 

현 iMOS 상용 Fence 정보는 동일
주요지점(infowindow) 정보 변경
Geojson 추가 ( 기존 포맷은 버리고 Geojson 으로 대체 )

</aside>

[Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20GPS%20Mode%20API%20/indicationUsingGET)

### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wpNo}/gps/indication`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입           | 설명
--------- |------------|------------------| -----------
wp_no | M          | Number |현장 관리번호


### Response Body

항목 | 필수 여부(M/O) | 데이터 타입           | 설명
--------- |------------|------------------| -----------
map_coordinate | O          | MapCoordinate    |Map 설정 정보  
geojsons | O          | List<Geojson>    | geojson ( overray ) 리스트
gps_fences | O          | List<GpsFence>   | GPS Fence 리스트
infowindows | O          | List<InfoWindow> | 주요지점 정보 리스트


#### MapCoordinate

항목 | 필수 여부(M/O) | 데이터 타입      | 설명
--------- |------------|-------------| -----------
gps_map_type | O          | Number      | GPS Map 접속시 초기 Map 타입. 1: 일반, 2: 위성지도
gps_map_level | O          | Number      | GPS 모니터링시 초기 지도 맵 레벨
gps_center_lat | O          | Double      | 지도 중심 GPS latitude
gps_center_long | O          | Double | 지도 중심 GPS longitude

#### Geojson

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
cc_no | M          | Number | 건설사 관리번호
cc_name | M          | String | 건설사명
geojson | M        | String | Geojson String.  값을 Object 로 변환하여 사용하여야 한다.


#### GpsFence


항목 | 필수 여부(M/O) | 데이터 타입       | 설명
--------- |------------|--------------|-----------
csg_no | O          | Number       | Fence 관리번호. 등록시는 null. 수정시 필수
cc_no | M          | Number       | 건설사 관리번호
cc_name | M          | String       | 건설사명
fence_name | M          | String       | Fence 명
center_latitude | M          | Double       | Fence 중심 좌표 latitude
center_longitude | M          | Double       | Fence 중심 좌표 longitude
fence_coordinates | M          | List<Object> | Fence 구성 GPS 좌표 리스트. drawing 연결순서대로 정렬되어 있어야 한다.
fence_coordinates[].seq | M          | Number       | drawing 순서
fence_coordinates[].latitude | M          | Double       | Fence 구성 GPS 좌표 latitude
fence_coordinates[].longitude | M          | Double       | Fence 구성 GPS 좌표 longitude


#### InfoWindow


항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
iw_no | O          | Number | 주요지점 관리번호.
cc_no | M          | Number | 건설사 관리번호
iw_name | M          | String | 주요지점명
iw_ntype | M          | Number | 주요지점 유형. 1: 라벨, 2: 이미지, 3: 포인트
iw_display_type | M          | Number | 주요지점 표시 유형. 1: GPS 기준, 2: 화면 기준
action | M          | Number | 링크.  1: 없음, 2: 이미지 팝업, 3: 새창 오픈
action_url | O          | String | 링크 URL. action 이 3 일 경우 필수
milestone | O          | String | 라벨 텍스트. iw_ntype 이 1 인 경우 필수
point_icon | O          | String | 포인트 아이콘명. iw_ntype 이 3 인 경우 필수
img_files | O          | List   | 이미지 리스트. iw_ntype 이 2 혹은 action 이 2 인 경우 필수 ( 이미지가 필요한 경우 ). 가장 마지막 이미지가 대표 이미지
img_files[].iw_img_no | O          | Number | 주요지점 이미지 관리번호.  신규 이미지 일 경우 null. 기존 이미지인 경우 필수
img_files[].img_url | O          | String | 이미지 URL
iw_coordinate | O          | String | 위치 기준. 1: 좌상단, 2: 우상단, 3: 좌하단, 4: 우하단
latitude | O          | Double | 라벨 위치 GPS latitude
longitude | O          | Double | 라벨 위치 GPS longitude
ord_weight | O          | Number | 순서 가중치(asc). 화면 기준일 경우 해당 위치 기준에서 가장 낮은 숫자의 주요지점을 먼저 표시
option | O          | Option | option 정보
style | O          | Style  | style 정보

#### Option

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
display_name | O          | Number | 명 표시 여부. 1: 표시
display_count | O          | Number | 카운트 표시 여부. 1: 표시

#### Style

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
size | O          | Number | 크기(%)
width | O          | Number | 크기 폭
height | O          | Number | 크기 높이
bg_color | O          | String | 배경색
font_size | O          | Number | 글자 크기
font_color | O          | String | 글자색


## 근로자/디바이스/CCTV/AP센서/QR 마커 정보 조회

> 응답 전문 예시

```json
{
  "context": {
    // 근로자
    "workers": [
      {
        "data_key": "336",
        "data_name": "허중헉",
        "data_type": "worker",
        "icon_url": "https://cnt.hulan.co.kr/static/image/new_icon/worker.png",
        "location": {
          "longitude": 128.9274274,
          "latitude": 37.823373,
          "altitude": 0.0,
          "accuracy": 0.0,
          "speed": 0.0,
          "bearing": 0.0,
          "battery": -1.0,
          "measure_time": "2024-08-28T05:47:00.000+00:00"
        },
        "owner": {
          "wp_no": 19337,
          "wp_name": "맵기반 통합관제 현장1(수도)",
          "coop_no": 1,
          "coop_name": "(주)휴랜 협력사",
          "mb_no": 336,
          "mb_name": "허중헉",
          "mb_level_name": null,
          "telephone": "01326945491",
          "work_section_name_b": "스마트안전시스템"
        },
        "equipment": {
          "equipment_type": null,
          "equipment_name": null,
          "equipment_no": null,
          "device_id": null,
          "coop_no": 1,
          "coop_name": "(주)휴랜 협력사"
        },
        "marker": 0,
        "coop_no": 1,
        "coop_name": "(주)휴랜 협력사",
        "telephone": "01326945491"
      }
    ],
    // 장비기사
    "drivers": [
      {
        "data_key": "30",
        "data_name": "QA근로자01",
        "data_type": "worker",
        "icon_url": "https://cnt.hulan.co.kr/static/image/new_icon/green.png",
        "location": {
          "longitude": 128.9265574,
          "latitude": 37.824813,
          "altitude": 59.10000228881836,
          "accuracy": 11.916000366210938,
          "speed": 0.0,
          "bearing": 0.0,
          "battery": -1.0,
          "measure_time": "2024-08-28T05:47:00.000+00:00"
        },
        "owner": {
          "wp_no": 19337,
          "wp_name": "맵기반 통합관제 현장1(수도)",
          "coop_no": 1,
          "coop_name": "(주)휴랜 협력사",
          "mb_no": 30,
          "mb_name": "QA근로자01",
          "mb_level_name": null,
          "telephone": "01512334455",
          "work_section_name_b": "안전시설물"
        },
        "equipment": {
          "equipment_type": 3,
          "equipment_name": "굴삭기",
          "equipment_no": "휴랜-가1234",
          "device_id": null,
          "coop_no": 1,
          "coop_name": "(주)휴랜 협력사"
        },
        "marker": 0,
        "coop_no": 1,
        "coop_name": "(주)휴랜 협력사",
        "telephone": "01512334455"
      }
    ],
    // 장비 및 차량
    "equipments": [
      {
        "data_key": "31",
        "data_name": "크레인(휴랜-나1234)",
        "data_type": "worker",
        "icon_url": "https://cnt.hulan.co.kr/static/image/new_icon/crane-truck.png",
        "location": {
          "longitude": 128.9263274,
          "latitude": 37.827353,
          "altitude": 59.10000228881836,
          "accuracy": 11.916000366210938,
          "speed": 0.0,
          "bearing": 0.0,
          "battery": -1.0,
          "measure_time": "2024-08-28T05:47:00.000+00:00"
        },
        "owner": {
          "wp_no": 19337,
          "wp_name": "맵기반 통합관제 현장1(수도)",
          "coop_no": 1,
          "coop_name": "(주)휴랜 협력사",
          "mb_no": 31,
          "mb_name": "QA 근로자 02",
          "mb_level_name": "장비기사",
          "telephone": "01534578881",
          "work_section_name_b": "입주청소"
        },
        "equipment": {
          "equipment_type": 10,
          "equipment_name": "크레인",
          "equipment_no": "휴랜-나1234",
          "device_id": null,
          "coop_no": 1,
          "coop_name": "(주)휴랜 협력사"
        },
        "marker": 0,
        "coop_no": 1,
        "coop_name": "(주)휴랜 협력사",
        "telephone": "01534578881"
      },
      {
        "data_key": "GPSDV",
        "data_name": "굴삭기(휴랜-가1234)",
        "data_type": "device",
        "icon_url": "https://cnt.hulan.co.kr/static/image/new_icon/new_pork.png",
        "location": {
          "longitude": 128.9267374,
          "latitude": 37.829733,
          "altitude": 59.10000228881836,
          "accuracy": 12.70199966430664,
          "speed": 0.0,
          "bearing": 0.0,
          "battery": -1.0,
          "measure_time": "2024-08-28T05:47:00.000+00:00"
        },
        "owner": {
          "wp_no": 19337,
          "wp_name": "맵기반 통합관제 현장1(수도)",
          "coop_no": 1,
          "coop_name": "(주)휴랜 협력사",
          "mb_no": 30,
          "mb_name": "QA근로자01",
          "mb_level_name": "장비기사",
          "telephone": "01512334455",
          "work_section_name_b": "안전시설물"
        },
        "equipment": {
          "equipment_type": 3,
          "equipment_name": "굴삭기",
          "equipment_no": "휴랜-가1234",
          "device_id": "GPSDV",
          "coop_no": 1,
          "coop_name": "(주)휴랜 협력사"
        },
        "marker": 0,
        "coop_no": 1,
        "coop_name": "(주)휴랜 협력사",
        "telephone": "01512334455"
      }
    ],
    // 디바이스 및 CCTV, AP 센서, QR
    "gps_trackers": [
      // 단일 AP 센서
      {
        "tracker_idx": 1858,
        "tracker_name": "출입구/입구 GPS",
        "lat": "37.781853",
        "lng": "128.9060574",
        "gps_measure_time": "2024-08-28T05:47:00.000+00:00",
        "tracker_dv_status": 1,
        "ap_sensor_list": [
          {
            "si_idx": 20052,
            "sd_name": "출입구",
            "si_type": "출입용",
            "si_type_cd": 1,
            "si_place1": "출입구",
            "si_place2": "입구",
            "default_color": "#3eea17",
            "flash_color": "#3eea17",
            "support_flash": 0,
            "gps_tracker": 1858,
            "display_name": "출입구/입구",
            "option": {
              "show_name": 1
            },
            "style": {}
          }
        ],
        "state": 1,
        "display_name": "출입구/입구",
        "state_name": "안전",
        "ref_target": 6,
        "total_attached_count": 1,
        "measure_time": null,
        "ref_target_type_name": "출입용",
        "ref_target_type": 1,
        "tracker_dv_status_name": "정상",
        "show_in_map": true
      },
      // 단일 QR
      {
        "tracker_idx": 1860,
        "tracker_name": "QR#1 GPS",
        "lat": "37.801853",
        "lng": "128.9060574",
        "gps_measure_time": "2024-08-28T05:47:00.000+00:00",
        "tracker_dv_status": 1,
        "qr_sticker_list": [
          {
            "qr_stk_no": 18,
            "qr_stk_name": "QR#1",
            "qr_type": 1,
            "inout_type": 3,
            "inout_count": 0,
            "gps_tracker": 1860,
            "option": {
              "show_name": 1
            },
            "style": {},
            "inout_type_name": "출/퇴근(진/출입) 선택"
          }
        ],
        "state": 1,
        "display_name": "QR#1",
        "state_name": "안전",
        "ref_target": 5,
        "total_attached_count": 1,
        "measure_time": null,
        "ref_target_type_name": "출/퇴근(진/출입) 선택",
        "ref_target_type": 3,
        "tracker_dv_status_name": "정상",
        "show_in_map": true
      },
      // 단일 CCTV
      {
        "tracker_idx": 1859,
        "tracker_name": "생활가압장#1 GPS",
        "lat": "37.791853",
        "lng": "128.9060574",
        "gps_measure_time": "2024-08-28T05:47:00.000+00:00",
        "tracker_dv_status": 1,
        "cctv_list": [
          {
            "cctv_no": 386,
            "cctv_name": "생활가압장#1",
            "install_type": 0,
            "conn_type": "NVR",
            "gps_tracker": 1859,
            "install_type_name": "고정형 CCTV"
          }
        ],
        "state": 1,
        "display_name": "생활가압장#1",
        "state_name": "안전",
        "ref_target": 2,
        "total_attached_count": 1,
        "measure_time": null,
        "ref_target_type_name": "고정형 CCTV",
        "ref_target_type": 0,
        "tracker_dv_status_name": "정상",
        "show_in_map": true
      },
      // 단일 디바이스
      {
        "tracker_idx": 1855,
        "tracker_name": "유해물질#1 VRT TRC",
        "lat": "37.771853",
        "lng": "128.8960574",
        "gps_measure_time": "2024-08-28T05:47:00.000+00:00",
        "tracker_dv_status": 1,
        "device_list": [
          {
            "device_idx": 1853,
            "device_id": "유해물질#1",
            "device_type": 4,
            "gps_tracker": 1855,
            "supported_data_list": [
              {
                "device_type": 4,
                "display_name": null,
                "dv_status": null,
                "rct_status": null,
                "measure_time": null,
                "dashboard_popup": null,
                "state": 99,
                "state_name": "비정상",
                "device_type_name": "유해물질",
                "exist_recent_data": false,
                "measure_data": {}
              }
            ],
            "state": 99,
            "state_name": "비정상",
            "device_type_name": "유해물질",
            "measure_time": null,
            "need_check": true
          }
        ],
        "state": 99,
        "display_name": "유해물질#1",
        "state_name": "비정상",
        "ref_target": 1,
        "total_attached_count": 1,
        "measure_time": null,
        "ref_target_type_name": "유해물질",
        "ref_target_type": 4,
        "tracker_dv_status_name": "정상",
        "show_in_map": true
      },
      // 복합장치 ( 디바이스, CCTV, QR, AP 센서 모두 포함될 수 있다. )
      {
        "tracker_idx": 1861,
        "tracker_name": "복합장치 트래커",
        "lat": "37.811853",
        "lng": "128.9160574",
        "gps_measure_time": "2024-08-28T05:47:00.000+00:00",
        "tracker_dv_status": 1,
        "device_list": [
          {
            "device_idx": 1862,
            "device_id": "기울기",
            "device_type": 6,
            "gps_tracker": 1861,
            "supported_data_list": [
              {
                "device_type": 6,
                "display_name": null,
                "dv_status": null,
                "rct_status": null,
                "measure_time": null,
                "dashboard_popup": null,
                "state": 99,
                "state_name": "비정상",
                "device_type_name": "기울기",
                "exist_recent_data": false,
                "measure_data": {}
              }
            ],
            "state": 99,
            "state_name": "비정상",
            "device_type_name": "기울기",
            "measure_time": null,
            "need_check": true
          },
          {
            "device_idx": 1863,
            "device_id": "개구부",
            "device_type": 7,
            "gps_tracker": 1861,
            "supported_data_list": [
              {
                "device_type": 7,
                "display_name": null,
                "dv_status": null,
                "rct_status": null,
                "measure_time": null,
                "dashboard_popup": null,
                "state": 99,
                "state_name": "비정상",
                "device_type_name": "개구부",
                "exist_recent_data": false,
                "measure_data": {}
              }
            ],
            "state": 99,
            "state_name": "비정상",
            "device_type_name": "개구부",
            "measure_time": null,
            "need_check": true
          }
        ],
        "state": 99,
        "display_name": "복합장치 트래커",
        "state_name": "비정상",
        "ref_target": 4,
        "total_attached_count": 2,
        "measure_time": null,
        "ref_target_type_name": "복합형",
        "ref_target_type": -1,
        "tracker_dv_status_name": "정상",
        "show_in_map": true
      }
    ],
    "need_check_count": 3,
    "total_count": 6
  },
  "return_code": 0,
  "return_message": "Success"
}
```

현장 지도(Map) 영역 표시를 위한 디바이스/CCTV/근로자/QR/AP 센서/장비 및 차량 정보를 제공한다.

10초 간격으로 조회 후 정보를 갱신하여야 한다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

[Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20GPS%20Mode%20API%20/gpsDataUsingGET)

### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wpNo}/gps`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입           | 설명
--------- |------------|------------------| -----------
wp_no | M          | Number |현장 관리번호

### Request Parameter

항목 | 필수 여부(M/O) | 데이터 타입           | 설명
--------- |------------|------------------| -----------
marker | O          | Number | 마킹 근로자 번호

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입           | 설명
--------- |------------|------------------| -----------
total_count | M          | Number           | 전체 디바이스, CCTV, QR, AP 센서 수
need_check_count | M          | Number           | 전체 디바이스 중 점검 필요수 
workers | M          | List<GpsData>     | 근로자 리스트
drivers | M          | List<GpsData>    | 장비운전자 리스트
equipments | O          | List<GpsData>  | 장비 및 차량 리스트
gps_trackers | O          | List<GpsTracker> | 디바이스, CCTV, QR, AP 센서 Tracker 정보


#### GpsData

항목 | 필수 여부(M/O) | 데이터 타입    | 설명                                
--------- |------------|-----------|-----------------------------------
data_key | M          | String    | 마커 키                              
data_name | M          | String    | 마커명                               
data_type | M          | String    | 마커 유형. worker: 근로자, device : 장비 및 차량 
icon_url | M          | String    | Icon URL. data_type 이 worker 인 경우 icon 사용하지 않는다. 
location | O          | Location  | 근로자 위치 정보                         
owner | O          | Owner     | 근로자 정보                            
equipment| O          | Equipment | 장비 및 차량 정보                        
marker | O          | Number    | 마커 마킹 여부. 1: 마킹                   
coop_no | O          | Number     | 마커 관련 협력사 관리번호                    
coop_name | O          | String     | 마커 관련 협력사 정보                      
telephone | O          | String     | 마커 관련 근로자 전화번호                    

#### Location

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
longitude | M          | Double | 경도
latitude | M          | Double | 위도
altitude | M          | Double | 고도
accuracy | M          | Double | 정확도
speed | M          | Double | 속도
bearing | M          | Double | 목표각
battery | M          | Double | 배터리 충전(%)
measure_time | M          | Date   | GPS 측정 시간. 예) "2024-08-28T05:47:00.000+00:00"


#### Owner

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
wp_no | M          | Double | 현장 관리번호
wp_name | M          | Double | 현장명
coop_no | M          | Double | 협력사 관리번호
coop_name | M          | Double | 협력사명
mb_no | M          | Double | 근로자 관리번호
mb_name | M          | Double | 근로자명
mb_level_name | M          | Double | 근로자 직위명
telephone | M          | Double | 근로자 전화번호
work_section_name_b | M          | Double | 근로자 공종명

#### Equipment

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
equipment_type | M          | Double | 장비 유형
equipment_name | M          | Double | 장비 유형명
equipment_no | M          | Double | 장비 번호
device_id | M          | Double | 사용 GPS 디바이스명 ( X )
coop_no | M          | Double | 협력사 관리번호
coop_name | M          | Double | 협력사명


#### GpsTracker

항목 | 필수 여부(M/O) | 데이터 타입          | 설명
--------- |------------|-----------------| -----------
tracker_idx | M          | Number          | 장비 유형
tracker_name | M          | String          | 장비 유형명
lat | M          | Double          | 위도
lng | M          | Double          | 경도
gps_measure_time | O          | Date            | GPS 측정시간
tracker_dv_status | M          | Number          | Tracker 장치 상태
tracker_dv_status_name | M          | Double          | Tracker 장치 상태명
state | M          | Number          | 상태
state_name | M          | String          | 상태명
display_name | M          | String          | 표시명
ref_target | M          | Double          | 부착 장치 표시 종류.  1: 디바이스 (IoT + Ble GW), 2: CCTV, 3: 장비 및 차량(X), 4: 복합 ( 부착 장치가 다수일 경우 ), 5: QR, 6: AP 센서
ref_target_type | M          | Double          | 부착 장치의 유형. 부착 장치 표시 종류에 따라 유형의 종류는 상이 
ref_target_type_name | M          | Double          | 부착 장치의 유형명
measure_time | O          | Date            | 부착된 장치의 최근 데이터 측정(수신) 시간
total_attached_count | M          | Number          | 부착된 장치 수
show_in_map | M          | Boolean         | 지도에 표시 여부
ap_sensor_list | M          | List<ApSensor>  | 부착된 ApSensor 리스트
device_list | M          | List<Device>    | 부착된 Device(IoT + Blw GW) 리스트
cctv_list | M          | List<Cctv>      | 부착된 CCTV 리스트
qr_sticker_list | M          | List<QrSticker> | 부착된 QR 리스트


#### ApSensor

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
si_idx | M          | Number | AP 센서 관리번호
sd_name | M          | String | 구역명
si_type | M          | String | 센서 유형
si_type_cd | M          | Number | 센서 유형 코드
si_place1 | M          | String | 센서 설치 장소1
si_place2 | M          | String | 센서 설치 장소2
display_name | M          | String | 센서 표시명
default_color | M          | String | 센서 표시 색상
flash_color | M          | String | 센서 Flash 색상
support_flash | M          | Number | 센서 Flash 유무
gps_tracker | M          | Number | 부착 GPS Tracker 관리번호
option | O          | Option | option 정보
style | O          | Style  | style 정보

#### Device

항목 | 필수 여부(M/O) | 데이터 타입            | 설명
--------- |------------|-------------------| -----------
device_idx | M          | Number            | 디바이스 관리번호
device_id | M          | String            | 디바이스 표시명
device_type | M          | Number            | 디바이스 유형
device_type_name | M          | String            | 디바이스 유형명
gps_tracker | M          | Number            | 부착 GPS Tracker 관리번호
state | M          | Number            | 상태
state_name | M          | String            | 상태명
need_check | M          | Number            | 점검 필요 유무
measure_time | M          | Date              | 데이터 측정 시간
supported_data_list | M          | List<MeasureData> | 지원되는 측정 정보 리스트


##### MeasureData

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
device_type | M          | Number | 디바이스 유형
device_type_name | M          | String | 디바이스 유형명
display_name | M          | String | 표시명
dv_status | M          | Number | 디바이스 장치 상태
rct_status | M          | Number | 디바이스 위험 상태
measure_time | M          | Date   | 데이터 측정 시간
dashboard_popup | M          | Number | 위험 알림 팝업 표시 유무
state | M          | Number | 상태
state_name | M          | String | 상태명
exist_recent_data | M          | Number | 측정 데이터 존재 유무 
measure_data | M          | Object | 측정 데이터 정보. 디바이스 유형별로 상이

> 유해물질 측정 데이터 ( measure_data ) 전문 예시

```json
{"o2":20.6,"h2s":0,"co":0,"ch4":0,"co2":0,"feel_temperature":-100,"discomfort":46.3,"battery":-1,"hazard_phrase":"","temperature":0,"humidity":0}
```

> 기울기 측정 데이터 ( measure_data ) 전문 예시

```json
{"tilt_x":0.398,"tilt_y":0,"tilt_z":0.038}
```

> 기울기 측정 데이터 ( measure_data ) 전문 예시

```json
{"tilt_x":0.398,"tilt_y":0,"tilt_z":0.038}
```

> 풍속계 측정 데이터 ( measure_data ) 전문 예시

```json
{"speed":3.9,"latest_max":4.1,"latest_avg":4}
```

> 소음 측정 데이터 ( measure_data ) 전문 예시

```json
{"noise":6.07,"noise_avg":10,"noise_max":7.06}
```

> 미세먼지 측정 데이터 ( measure_data ) 전문 예시

```json
{"pm10":19,"pm2.5":12,"pm1.0":8}
```

> 화재감지 측정 데이터 ( measure_data ) 전문 예시

```json
{"detection_time":"2024-02-15T04:22:50.000+00:00"}
```

> 수질 측정 데이터 ( measure_data ) 전문 예시

```json
{"ph":9.87,"ss":47.91}
```


> 협착/열차 접근 감지 측정 데이터 ( measure_data ) 전문 예시

```json
{"detect":0}
```

> 복합환경센서 측정 데이터 ( measure_data ) 전문 예시

```json
{"pm25":29,"pm10":11,"leq":57.9,"lmax":1.7,"temperature":35,"feel_temperature":36.83,"humidity":75.1,"rainfall":29.8,"windspeed":7,"winddirection":120,"windspeed_latest_avg":31.35,"windspeed_latest_max":60,"windspeed_recently_avg":38.92,"windspeed_recently_max":115.4,"tsp":24}
```


#### Cctv

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
cctv_no | M          | Number | CCTV 관리번호
cctv_name | M          | String | CCTV 명
install_type | M          | Number | 설치 유형
install_type_name | M          | Number | 설치 유형명
conn_type | M          | String | CCTV 연동방식
gps_tracker | M          | Number | 부착 GPS Tracker 관리번호


#### QrSticker

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
qr_stk_no | M          | Number | QR 관리번호
qr_stk_name | M          | Number | QR 명
qr_type | M          | Number | QR 유형
inout_type | M          | Number | QR 진/출입 유형
inout_type_name | M          | Number | QR 진/출입 유형명
inout_count | M          | Number | 당일 진/출입 수
gps_tracker | M          | Number | 부착 GPS Tracker 관리번호
option | O          | Option | option 정보
style | O          | Style  | style 정보


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

해당 API 는 해당 근로자의 GPS 위치 정보가 있는지 유무 판단을 위한 목적으로 사용 

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

기존 API 사용. [Swagger](http://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.1%5D%20IMOS%20%EC%9D%BC%EB%B0%98%20%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81%20%EA%B4%80%EB%A6%AC/searchWorkerGpsLocationUsingGET)


### HTTP Request

`POST /imoa/api/monitor/4.1/workplace/{wp_no}/gps/user/{mb_no}`

### Path Variable

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





## 현장 지도(위치) 설정 정보 조회

> 응답 전문 예시

```JSON
{
  "context": {
    "gps_map_type": 1,
    "gps_map_level": 4,
    "gps_center_lat": 37.73398853063353,
    "gps_center_long": 128.86830269559175
  },
  "return_code": 0,
  "return_message": "Success"
}
```

현장 지도(위치) 설정 정보를 제공한다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

기존 API 사용. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20GPS%20Mode%20API%20/coordinateUsingGET)


### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/gps/coordinate`

### Path Variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입      | 설명
--------- |------------|-------------| -----------
gps_map_type | O          | Number      | GPS Map 접속시 초기 Map 타입. 1: 일반, 2: 위성지도
gps_map_level | O          | Number      | GPS 모니터링시 초기 지도 맵 레벨
gps_center_lat | O          | Double      | 지도 중심 GPS latitude
gps_center_long | O          | Double | 지도 중심 GPS longitude

* MapCoordinate 와 동일


## 현장 지도(위치) 설정 정보 저장


> 요청 전문 예시

```JSON
{
  "gps_map_type": 1,
  "gps_map_level": 4,
  "gps_center_lat": 37.73398853063353,
  "gps_center_long": 128.86830269559176
}
```

현장 지도(위치) 설정 정보 저장을 제공한다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

기존 API 사용. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20GPS%20Mode%20API%20/coordinateUsingGET)


### HTTP Request

`POST /imoa/api/monitor/4.3/workplace/{wp_no}/gps/coordinate`

### Path Variable

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호

### Request Body

항목 | 필수 여부(M/O) | 데이터 타입      | 설명
--------- |------------|-------------| -----------
gps_map_type | M          | Number      | GPS Map 접속시 초기 Map 타입. 1: 일반, 2: 위성지도
gps_map_level | M          | Number      | GPS 모니터링시 초기 지도 맵 레벨
gps_center_lat | M          | Double      | 지도 중심 GPS latitude
gps_center_long | M          | Double | 지도 중심 GPS longitude

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입      | 설명
--------- |------------|-------------| -----------
gps_map_type | M          | Number      | GPS Map 접속시 초기 Map 타입. 1: 일반, 2: 위성지도
gps_map_level | M          | Number      | GPS 모니터링시 초기 지도 맵 레벨
gps_center_lat | M          | Double      | 지도 중심 GPS latitude
gps_center_long | M          | Double | 지도 중심 GPS longitude


* MapCoordinate 와 동일

