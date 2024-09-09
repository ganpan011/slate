# Map(지도기반) Marker 셋팅

지도기반 설정 화면에서 Marker 셋팅을 수행하기 위한 API 를 제공한다.

## 화면 설정(마커 메뉴)을 위한 정보 조회

> 응답 전문 예시

```json
{
    "context": {
        "wp_no": 19337,
        "wp_name": "현장관제 리뉴얼(지도기반 테스트)",
        "hcmpt_id": "I_MAIN",
        "hcmpt_name": "IMOS 메인화면",
        "width": 3,
        "height": 2,
        "map_coordinate": {
            "gps_map_type": 1,
            "gps_map_level": 4,
            "gps_center_lat": 37.73398853063353,
            "gps_center_long": 128.86830269559175
        },
        "registered_count": {
            "qr_count": 1,
            "cctv_count": 1,
            "menu_list": [
                {
                    "device_menu_list": [
                        {
                            "menu_name": "유해물질 측정 센서",
                            "sensor_kind": "DV",
                            "device_type": 4,
                            "sensor_count": 1
                        },
                        {
                            "menu_name": "기울기 센서",
                            "sensor_kind": "DV",
                            "device_type": 6,
                            "sensor_count": 1
                        },
                        {
                            "menu_name": "개구부 센서",
                            "sensor_kind": "DV",
                            "device_type": 7,
                            "sensor_count": 1
                        },
                        {
                            "menu_name": "풍속계",
                            "sensor_kind": "DV",
                            "device_type": 8,
                            "sensor_count": 0
                        },
                        {
                            "menu_name": "온습도 센서",
                            "sensor_kind": "DV",
                            "device_type": 10,
                            "sensor_count": 0
                        },
                        {
                            "menu_name": "소음측정기",
                            "sensor_kind": "DV",
                            "device_type": 11,
                            "sensor_count": 0
                        },
                        {
                            "menu_name": "미세먼지 측정기",
                            "sensor_kind": "DV",
                            "device_type": 12,
                            "sensor_count": 0
                        },
                        {
                            "menu_name": "화재 감지기",
                            "sensor_kind": "DV",
                            "device_type": 15,
                            "sensor_count": 0
                        },
                        {
                            "menu_name": "수질 측정기",
                            "sensor_kind": "DV",
                            "device_type": 19,
                            "sensor_count": 0
                        },
                        {
                            "menu_name": "누전차단기",
                            "sensor_kind": "DV",
                            "device_type": 20,
                            "sensor_count": 0
                        },
                        {
                            "menu_name": "AI 사각지대감지 센서",
                            "sensor_kind": "DV",
                            "device_type": 21,
                            "sensor_count": 0
                        },
                        {
                            "menu_name": "복합 환경 센서",
                            "sensor_kind": "DV",
                            "device_type": 22,
                            "sensor_count": 0
                        },
                        {
                            "menu_name": "열차 접근 감지기",
                            "sensor_kind": "DV",
                            "device_type": 23,
                            "sensor_count": 0
                        },
                        {
                            "menu_name": "타워크레인",
                            "sensor_kind": "DV",
                            "device_type": 24,
                            "sensor_count": 0
                        }
                    ],
                    "menu_name": "IoT센서",
                    "sensor_count": 3
                },
                {
                    "device_menu_list": [
                        {
                            "menu_name": "AP센서",
                            "sensor_kind": "AP",
                            "device_type": null,
                            "sensor_count": 2
                        },
                        {
                            "menu_name": "BLE GW",
                            "sensor_kind": "DV",
                            "device_type": 16,
                            "sensor_count": 1
                        }
                    ],
                    "menu_name": "위치센서",
                    "sensor_count": 3
                }
            ],
            "sensor_count": 6
        }
    },
    "return_code": 0,
    "return_message": "Success"
}

```

설정 화면 진입시 화면 설정 마커 메뉴 구성을 위한 정보 제공 

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요

기획서 Page-10
- 센서 메뉴 구성 정보 및 카운트
- QR 및 CCTV 카운트 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%EC%A7%80%EB%8F%84%EA%B8%B0%EB%B0%98%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20%EC%84%A4%EC%A0%95%20%ED%99%94%EB%A9%B4%20%EA%B5%AC%EC%84%B1%20%EB%B0%8F%20%EC%84%A4%EC%A0%95%20API%20/settingInitInfoUsingGET_1)


### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}}/gps/setting`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입           | 설명
--------- |------------|------------------| -----------
wp_no | M          | Number |현장 관리번호


### Response Body

항목 | 필수 여부(M/O) | 데이터 타입           | 설명
--------- |------------|------------------| -----------
wp_no | M          | string           | 현장 관리번호
wp_name | M          | string           | 현장명
hcmpt_id | M          | string           | 현장의 메인 컴포넌트 아이디
hcmpt_name | M          | string           | 현장의 메인 컴포넌트명
width | M          | number           | 메인 컴포넌트 길이(1~4)
height | M          | number           | 메인 컴포넌트 높이(1~3)
map_coordinate | M          | MapCoordinate    | Map 설정 정보
registered_count | M          | RegisteredCount  | 센서 메뉴 구성 정보 및 각 등록수 정보

#### RegisteredCount

항목 | 필수 여부(M/O) | 데이터 타입       | 설명
--------- |------------|--------------| -----------
qr_count | M          | Number       | 등록 qr 전체수
cctv_count | M         | Number       | 등록 cctv 전체수
menu_list | M   | List<Object> | 센서 메뉴 리스트
menu_list[].menu_name | M          | Number       | 메뉴명
menu_list[].sensor_count | M          | Number       | 해당 메뉴 내 전체 센서수
menu_list[].device_menu_list | M          | List<Object> | 장치 메뉴 리스트
menu_list[].device_menu_list[].menu_name | M          | Number       | 하위 메뉴명
menu_list[].device_menu_list[].sensor_kind | M          | Number       | 센서 종류. DV: 디바이스류 ( IoT + BLW GW ), AP: AP Sensor
menu_list[].device_menu_list[].device_type | O          | Number       | 디바이스 유형. 센서 종류가 DV 인 경우 유효
menu_list[].device_menu_list[].sensor_count | M          | Number       | 해당 메뉴 내 전체 센서수

* sensor_kind 가 DV 인 경우 등록/수정시 디바이스 선택 리스트 ( IoT/BLE GW ) 를 이용하여야 하며   
  AP 인 경우 AP Sensor 선택 리스트를 이용하여야 한다.


#### MapCoordinate

항목 | 필수 여부(M/O) | 데이터 타입      | 설명
--------- |------------|-------------| -----------
gps_map_type | O          | Number      | GPS Map 접속시 초기 Map 타입. 1: 일반, 2: 위성지도
gps_map_level | O          | Number      | GPS 모니터링시 초기 지도 맵 레벨
gps_center_lat | O          | Double      | 지도 중심 GPS latitude
gps_center_long | O          | Double | 지도 중심 GPS longitude


## 화면 설정을 위한 기 지정된 마커 및 주요지점등 구성 정보 조회

> 응답 전문 예시

```json
{
  "context": {
    "validate_token": "XXXX",
    "geojsons": [
      {
        "cc_no": 37,
        "cc_name": "맵기반 건설사1",
        "geojson": "{\"type\":\"FeatureCollection\",\"features\":[{\"type\":\"Feature\",\"geometry\":{\"type\":\"LineString\",\"coordinates\":[[127.31243539799125,37.16561965318349],[127.31038243082061,37.16467894163606],[127.31060609195322,37.164308923601574],[127.31138082761443,37.16379328984185],[127.3116736968801,37.16382856211558]]},\"properties\":{\"name\":\"road0\",\"color\":\"#0bf3f8\"}}]}"
      }
    ],
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
    "infowindows": [
      {
        "iw_no": 192,
        "cc_no": 37,
        "iw_name": "라벨 테스트3",
        "iw_ntype": 1,
        "iw_display_type": 1,
        "action": 1,
        "action_url": null,
        "milestone": "라벨 표시 내용\n 줄바꿈2",
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
        "iw_name": "라벨 테스트4-이미지",
        "iw_ntype": 1,
        "iw_display_type": 1,
        "action": 2,
        "action_url": null,
        "milestone": "이미지 팝업\n 줄바꿈",
        "point_icon": null,
        "img_files": [
          {
            "iw_img_no": 367,
            "img_url": "//new-api.hulandev.co.kr/static/infowindow/20240821163508353_QEjnMW8r3p.png"
          },
          {
            "iw_img_no": 368,
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
        "iw_name": "라벨 네이버 링크",
        "iw_ntype": 1,
        "iw_display_type": 1,
        "action": 3,
        "action_url": "http://naver.com",
        "milestone": "네이버 링크\n 줄바꿈",
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
        "iw_name": "이미지",
        "iw_ntype": 2,
        "iw_display_type": 1,
        "action": 2,
        "action_url": null,
        "milestone": null,
        "point_icon": null,
        "img_files": [
          {
            "iw_img_no": 369,
            "img_url": "//new-api.hulandev.co.kr/static/infowindow/20240821163508353_QEjnMW8r3p.png"
          },
          {
            "iw_img_no": 370,
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
        "iw_name": "이미지 다음 링크",
        "iw_ntype": 2,
        "iw_display_type": 1,
        "action": 3,
        "action_url": "http://daum.net",
        "milestone": null,
        "point_icon": null,
        "img_files": [
          {
            "iw_img_no": 372,
            "img_url": "//new-api.hulandev.co.kr/static/infowindow/20240821164635867_yXIwISfiZ7.jpg"
          },
          {
            "iw_img_no": 371,
            "img_url": "//new-api.hulandev.co.kr/static/infowindow/20240821163508353_QEjnMW8r3p.png"
          }
        ],
        "iw_coordinate": 4,
        "latitude": 37.75185300000000,
        "longitude": 128.65605740000000,
        "ord_weight": 1,
        "option": {},
        "style": {
          "width": "200",
          "height": "200"
        }
      },
      {
        "iw_no": 198,
        "cc_no": 37,
        "iw_name": "우상단 이미지-다음링크",
        "iw_ntype": 2,
        "iw_display_type": 2,
        "action": 3,
        "action_url": "http://daum.net",
        "milestone": null,
        "point_icon": null,
        "img_files": [
          {
            "iw_img_no": 373,
            "img_url": "//new-api.hulandev.co.kr/static/infowindow/20240821163508353_QEjnMW8r3p.png"
          },
          {
            "iw_img_no": 374,
            "img_url": "//new-api.hulandev.co.kr/static/infowindow/20240821164635867_yXIwISfiZ7.jpg"
          }
        ],
        "iw_coordinate": 2,
        "latitude": null,
        "longitude": null,
        "ord_weight": 1,
        "option": {},
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
        "point_icon": "1.png",
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
    ],
    "iot_devices": [
      {
        "lat": "37.771853",
        "lng": "128.8960574",
        "idx": 1853,
        "device_type": 4,
        "display_name": "유해물질#1",
        "option": {
          "show_name": 1
        },
        "style": {}
      }
    ],
    "ap_sensors": [
      {
        "lat": "37.781853",
        "lng": "128.9060574",
        "si_idx": 20052,
        "display_name": "[출입구]출입구/입구",
        "option": {
          "show_name": 1
        },
        "style": {}
      }
    ],
    "cctvs": [
      {
        "lat": "37.791853",
        "lng": "128.9060574",
        "cctv_no": 386,
        "cctv_name": "생활가압장#1",
        "install_type": 0,
        "install_type_name": "고정형",
        "ptz_status": 1,
        "option": {
          "show_name": 1
        },
        "style": {}
      }
    ],
    "qr_stickers": [
      {
        "lat": "37.801853",
        "lng": "128.9060574",
        "qr_stk_no": 18,
        "qr_stk_name": "QR",
        "option": {
          "show_name": 1
        },
        "style": {}
      }
    ],
    "ble_gw": [
      {
        "lat": "37.781853",
        "lng": "128.8960574",
        "idx": 1856,
        "device_type": 16,
        "display_name": "BLE GW#1",
        "option": {
          "show_name": 1
        },
        "style": {}
      }
    ]
  },
  "return_code": 0,
  "return_message": "Success"
}
```

화면 설정을 위한 기 지정된 마커 및 주요지점등 구성 정보를 제공한다.

Geojson, Fence, 주요지점은 현장에 편입된 건설사별 설정 사항이다.
최고 관리자/서비스 관리자/발주사 관리자는 모든 Geojson, Fence, 주요지점을 등록/수정 가능하나 
등록시 해당 항목이 보여질 건설사를 선택해서 등록하여야 한다.
수정시 Geojson, Fence, 주요지점의 건설사 정보는 변경할 수 없다.

Geojson 는 건설사별 하나만 설정할 수 있다.

건설사 관리자/현장 관리자는 본인이 소속된 건설사의 Geojson, Fence, 주요지점만을 등록/수정 가능하다.

디바이스( IoT 장치 + BLE GW ), AP 센서, QR, CCTV 는 현장 설정사항으로 모든 관리자가 자유롭게 등록/수정 가능하다. 

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%EC%A7%80%EB%8F%84%EA%B8%B0%EB%B0%98%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20%EC%84%A4%EC%A0%95%20%ED%99%94%EB%A9%B4%20%EA%B5%AC%EC%84%B1%20%EB%B0%8F%20%EC%84%A4%EC%A0%95%20API%20/settingDataInfoUsingGET)


### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/gps/setting/main`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입           | 설명
--------- |------------|------------------| -----------
wp_no | M          | Number |현장 관리번호


### Response Body

항목 | 필수 여부(M/O) | 데이터 타입                  | 설명
--------- |------------|-------------------------| -----------
validate_token | M          | String             | 저장시 검증을 위한 검증 토큰. 사용자 계정 변경 및 권한 변경에 대응하기 위한 값
geojsons | M          | List<SettingGeojson>    | Geojson 정보 
gps_fences | M          | List<SettingGpsFence>   | Fence 리스트
infowindows | O          | List<SettingInfoWindow> | 주요지점 정보 리스트
iot_devices | M          | List<SettingDevice>     | IoT 디바이스 리스트
ble_gw  | M          | List<SettingDevice>     | BLE GW 리스트
ap_sensors | M          | List<SettingApSensor>   | AP Sensor 리스트
cctvs | M          | List<SettingCctv>       | CCTV 리스트
qr_stickers | M          | List<SettingQrSticker>  | QR 리스트



#### SettingGeojson

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
cc_no | M          | Number | 건설사 관리번호
cc_name | M          | String | 건설사명
geojson | M        | String | Geojson String.  값을 Object 로 변환하여 사용하여야 한다.

#### SettingGpsFence

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

#### SettingInfoWindow

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


#### SettingDevice

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
lat | M          | Double | 위도
ing | M          | Double | 경도
option | M          | Option | option 정보
style | M          | Style  | style 정보
idx | M          | Number | 디바이스 관리번호
device_type | M          | Number | 디바이스 유형
display_name | M          | String | 표시명

#### SettingApSensor

항목 | 필수 여부(M/O) | 데이터 타입  | 설명
--------- |------------|---------| -----------
lat | M          | Double  | 위도
ing | M          | Double  | 경도
option | M          | Option  | option 정보
style | M          | Style   | style 정보
si_idx | M          | Number | AP 센서 관리번호
display_name | M          | String | 표시명

#### SettingCctv

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
lat | M          | Double | 위도
ing | M          | Double | 경도
option | M          | Option | option 정보
style | M          | Style  | style 정보
cctv_no | M          | Number | CCTV 관리번호
cctv_name | M          | String | CCTV명
install_type | M          | Number | 설치 유형
install_type_name | M          | String | 설치 유형명
ptz_status | M          | String | PTZ 지원여부


#### SettingQrSticker

항목 | 필수 여부(M/O) | 데이터 타입  | 설명
--------- |------------|---------| -----------
lat | M          | Double  | 위도
ing | M          | Double  | 경도
option | M          | Option  | option 정보
style | M          | Style   | style 정보
qr_stk_no | M          | Number | QR 관리번호




## 화면 설정 마커 및 주요지점등 구성 정보 저장

> 요청 전문 예시

```json
{
  "validate_token" : "XYZ",
  "qr_stickers" : [
    {
      "qr_stk_no": 18,
      "lat": 37.801853,
      "lng": 128.9060574,
      "option" :{
        "show_name" : 1,
        "display_count" : 1
      },
      "style" :{}
    }
  ],
  "cctvs" : [
    {
      "cctv_no": 386,
      "lat": 37.791853,
      "lng": 128.9060574,
      "option" :{
        "show_name" : 1
      },
      "style" :{}
    }
  ],
  "ap_sensors" : [
    {
      "si_idx": 20052,
      "lat": 37.781853,
      "lng": 128.9060574,
      "option" :{
        "show_name" : 1
      },
      "style" :{}
    }
  ],
  "ble_gws" : [
    {
      "idx": 1856,
      "lat": 37.781853,
      "lng": 128.8960574,
      "option" :{
        "show_name" : 1
      },
      "style" :{}
    }
  ],
  "iot_devices" : [
    {
      "idx": 1853,
      "lat": 37.771853,
      "lng": 128.8960574,
      "option" :{
        "show_name" : 1
      },
      "style" :{}
    }
  ],
  "geojsons": [
    {
      "cc_no" : 37,
      "geojson": "{\"type\":\"FeatureCollection\",\"features\":[{\"type\":\"Feature\",\"geometry\":{\"type\":\"LineString\",\"coordinates\":[[127.31243539799125,37.16561965318349],[127.31038243082061,37.16467894163606],[127.31060609195322,37.164308923601574],[127.31138082761443,37.16379328984185],[127.3116736968801,37.16382856211558]]},\"properties\":{\"name\":\"road0\",\"color\":\"#0bf3f8\"}}]}"
    }
  ],
  "gps_fences" : [
    {
      "csg_no": 23,
      "cc_no" : 37,
      "fence_name":"펜스#2",
      "center_latitude":37.734637270541704,
      "center_longitude":128.8694306194166,
      "fence_coordinates":[
        {
          "latitude":37.73678247838621,
          "longitude":128.86594545158087
        },
        {
          "latitude":37.732516598643095,
          "longitude":128.86454529013028
        },
        {
          "latitude":37.73099499159189,
          "longitude":128.8730139759173
        },
        {
          "latitude":37.73627651836462,
          "longitude":128.87398647409037
        },
        {
          "latitude":37.73848344713134,
          "longitude":128.8700264870466
        }
      ]
    }
  ],
  "infowindows": [
    {
      "iw_no" : 192,
      "cc_no" : 37,
      "iw_name" : "라벨 테스트3",
      "iw_ntype" : 1,
      "iw_display_type" : 1,
      "action" : 1,
      "action_url" : null,
      "milestone" : "라벨 표시 내용\n 줄바꿈2",
      "iw_coordinate" : 1,
      "point_icon" : null,
      "ord_weight" : 1,
      "latitude" : 37.752853,
      "longitude" : 128.8760574,
      "img_files" :  [

      ],
      "option" : {},
      "style" : {
        "bg_color": "blue",
        "font_size": "12",
        "font_color": "red"
      }
    },
    {
      "iw_no" : 194,
      "cc_no" : 37,
      "iw_name" : "라벨 테스트4-이미지",
      "iw_ntype" : 1,
      "iw_display_type" : 1,
      "action" : 2,
      "action_url" : null,
      "milestone" : "이미지 팝업\n 줄바꿈",
      "iw_coordinate" : 1,
      "point_icon" : null,
      "ord_weight" : 1,
      "latitude" : 37.751853,
      "longitude" : 128.8760574,
      "img_files" :  [
        {
          "iw_img_no" : 367,
          "file_name": "20240821163508353_QEjnMW8r3p.png",
          "file_original_name": "지상1층.png",
          "ord_weight" : 1
        },
        {
          "iw_img_no" : 368,
          "file_name": "20240821164635867_yXIwISfiZ7.jpg",
          "file_original_name": "02.용수-01.jpg",
          "ord_weight" : 2
        }
      ],
      "option" : {},
      "style" : {
        "bg_color": "red",
        "font_size": "12",
        "font_color": "blue"
      }
    },
    {
      "iw_no" : 195,
      "cc_no" : 37,
      "iw_name" : "라벨 네이버 링크",
      "iw_ntype" : 1,
      "iw_display_type" : 1,
      "action" : 3,
      "action_url" : "http://naver.com",
      "milestone" : "네이버 링크\n 줄바꿈",
      "iw_coordinate" : 4,
      "point_icon" : null,
      "ord_weight" : 1,
      "latitude" : 37.751853,
      "longitude" : 128.8860574,
      "img_files" :  [
      ],
      "option" : {},
      "style" : {
        "bg_color": "yellow",
        "font_size": "12",
        "font_color": "blue"
      }
    },
    {
      "iw_no" : 196,
      "cc_no" : 37,
      "iw_name" : "이미지",
      "iw_ntype" : 2,
      "iw_display_type" : 1,
      "action" : 2,
      "action_url" : null,
      "milestone" : null,
      "iw_coordinate" : 4,
      "point_icon" : null,
      "ord_weight" : 1,
      "latitude" : 37.751853,
      "longitude" : 128.8560574,
      "img_files" :  [
        {
          "iw_img_no" : 369,
          "file_name": "20240821163508353_QEjnMW8r3p.png",
          "file_original_name": "이미지1.png",
          "ord_weight" : 1
        },
        {
          "iw_img_no" : 370,
          "file_name": "20240821164635867_yXIwISfiZ7.jpg",
          "file_original_name": "이미지2.jpg",
          "ord_weight" : 2
        }

      ],
      "option" : {},
      "style" : {
        "width" : "150",
        "height" : "150"
      }
    },
    {
      "iw_no" : 197,
      "cc_no" : 37,
      "iw_name" : "이미지 다음 링크",
      "iw_ntype" : 2,
      "iw_display_type" : 1,
      "action" : 3,
      "action_url" : "http://daum.net",
      "milestone" : null,
      "iw_coordinate" : 4,
      "point_icon" : null,
      "ord_weight" : 1,
      "latitude" : 37.751853,
      "longitude" : 128.6560574,
      "img_files" :  [
        {
          "iw_img_no" : 371,
          "file_name": "20240821163508353_QEjnMW8r3p.png",
          "file_original_name": "이미지링크1.png",
          "ord_weight" : 2
        },
        {
          "iw_img_no" : 372,
          "file_name": "20240821164635867_yXIwISfiZ7.jpg",
          "file_original_name": "이미지링크2.jpg",
          "ord_weight" : 1
        }

      ],
      "option" : {},
      "style" : {
        "width" : "200",
        "height" : "200"
      }
    },
    {
      "iw_no" : 198,
      "cc_no" : 37,
      "iw_name" : "우상단 이미지-다음링크",
      "iw_ntype" : 2,
      "iw_display_type" : 2,
      "action" : 3,
      "action_url" : "http://daum.net",
      "milestone" : null,
      "iw_coordinate" : 2,
      "point_icon" : null,
      "ord_weight" : 1,
      "latitude" : null,
      "longitude" : null,
      "img_files" :  [
        {
          "iw_img_no" : 373
        },
        {
          "file_name": "20240821164635867_yXIwISfiZ7.jpg",
          "file_original_name": "이미지우상단링크2.jpg",
        }

      ],
      "option" : {},
      "style" : {
        "width" : "200",
        "height" : "200"
      }
    },
    {
      "iw_no" : 199,
      "cc_no" : 37,
      "iw_name" : "포인트",
      "iw_ntype" : 3,
      "iw_display_type" : 1,
      "action" : 1,
      "action_url" : null,
      "milestone" : null,
      "iw_coordinate" : 1,
      "point_icon" : "1.png",
      "ord_weight" : 1,
      "latitude" : 37.741853,
      "longitude" : 128.6760574,
      "img_files" :  [

      ],
      "option" : {
        "display_name" : 1
      },
      "style" : {
        "size" : 100
      }
    }
  ]
}
```

지도기반 주요 구성 정보 저장을 위한 API 이다.  구성 정보 내 없는 기존 구성 정보는 모두 삭제된다.



<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%EC%A7%80%EB%8F%84%EA%B8%B0%EB%B0%98%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20%EC%84%A4%EC%A0%95%20%ED%99%94%EB%A9%B4%20%EA%B5%AC%EC%84%B1%20%EB%B0%8F%20%EC%84%A4%EC%A0%95%20API%20/saveSettingDataInfoUsingPUT)


### HTTP Request

`PUT /imoa/api/monitor/4.3/workplace/{wp_no}}/gps/setting/main`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입           | 설명
--------- |------------|------------------| -----------
wp_no | M          | Number |현장 관리번호


### Request Body

항목 | 필수 여부(M/O) | 데이터 타입                 | 설명
--------- |------------|------------------------| -----------
validate_token | M          | String             | 조회시 받은 검증토큰을 그대로 올려주어야 한다
geojsons | M          | List<SaveGeojson>          | Geojson 리스트
gps_fences | M          | List<SaveGpsFence>         | Fence 리스트
infowindows | O          | List<SaveInfoWindow>       | 주요지점 정보 리스트
iot_devices | M          | List<SaveDevice>    | IoT 디바이스 리스트
ble_gw  | M          | List<SaveDevice>       | BLE GW 리스트
ap_sensors | M          | List<SaveApSensor>  | AP Sensor 리스트
cctvs | M          | List<SaveCctv>      | CCTV 리스트
qr_stickers | M          | List<SaveQrSticker> | QR 리스트


geojsons
- 등록/수정시 cc_no 는 필수

gps_fence
- 신규 등록시 wp_seq 는 null.  수정시 wp_seq 는 필수

infowindows
- 신규 등록시 iw_no 는 null.  수정시 iw_no 는 필수


#### SaveGeojson

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
cc_no | M          | Number | 건설사 관리번호
geojson | M        | String | Geojson String.  값을 Object 로 변환하여 사용하여야 한다. 

#### SaveGpsFence

항목 | 필수 여부(M/O) | 데이터 타입       | 설명
--------- |------------|--------------|-----------
csg_no | O          | Number       | Fence 관리번호. 등록시는 null. 수정시 필수
cc_no | M          | Number       | 건설사 관리번호
fence_name | M          | String       | Fence 명
center_latitude | M          | Double       | Fence 중심 좌표 latitude
center_longitude | M          | Double       | Fence 중심 좌표 longitude
fence_coordinates | M          | List<Object> | Fence 구성 GPS 좌표 리스트. drawing 연결순서대로 정렬되어 있어야 한다.
fence_coordinates[].latitude | M          | Double       | Fence 구성 GPS 좌표 latitude
fence_coordinates[].longitude | M          | Double       | Fence 구성 GPS 좌표 longitude

#### SaveInfoWindow

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
iw_no | O          | Number | 주요지점 관리번호. 등록시는 null. 수정시 필수
cc_no | M          | Number | 건설사 관리번호
iw_name | M          | String | 주요지점명
iw_ntype | M          | Number | 주요지점 유형. 1: 라벨, 2: 이미지, 3: 포인트
iw_display_type | M          | Number | 주요지점 표시 유형. 1: GPS 기준, 2: 화면 기준
action | M          | Number | 링크.  1: 없음, 2: 이미지 팝업, 3: 새창 오픈
action_url | O          | String | 링크 URL. action 이 3 일 경우 필수
milestone | O          | String | 라벨 텍스트. iw_ntype 이 1 인 경우 필수
point_icon | O          | String | 포인트 아이콘명. iw_ntype 이 3 인 경우 필수
img_files | O          | List   | 이미지 리스트. iw_ntype 이 2 혹은 action 이 2 인 경우 필수 ( 이미지가 필요한 경우 ). ord_weight 가 높은 순부터. 신규 이미지는 가장 마지막으로 정렬하여 요청 
img_files[].iw_img_no | O          | Number | 주요지점 이미지 관리번호.  신규 이미지 일 경우 null. 기존 이미지인 경우 필수 
img_files[].fileName | O          | String | 업로드 이미지명. 신규 이미지인 경우 필수 
img_files[].fileOriginalName | O          | String | 업로드 이미지 원본명. 신규 이미지인 경우 필수 
iw_coordinate | O          | String | 위치 기준. 1: 좌상단, 2: 우상단, 3: 좌하단, 4: 우하단
latitude | O          | Double | 라벨 위치 GPS latitude
longitude | O          | Double | 라벨 위치 GPS longitude
ord_weight | O          | Number | 순서 가중치(asc). 화면 기준일 경우 해당 위치 기준에서 가장 낮은 숫자의 주요지점을 먼저 표시
option | O          | Option | option 정보
style | O          | Style  | style 정보


#### SaveDevice 

항목 | 필수 여부(M/O) | 데이터 타입  | 설명
--------- |------------|---------| -----------
lat | M          | Double  | 위도
ing | M          | Double  | 경도
option | M          | Option  | option 정보
style | M          | Style   | style 정보
idx | M          | Style   | 디바이스 관리번호

#### SaveApSensor

항목 | 필수 여부(M/O) | 데이터 타입  | 설명
--------- |------------|---------| -----------
lat | M          | Double  | 위도
ing | M          | Double  | 경도
option | M          | Option  | option 정보
style | M          | Style   | style 정보
si_idx | M          | Number | AP 센서 관리번호

#### SaveCctv

항목 | 필수 여부(M/O) | 데이터 타입  | 설명
--------- |------------|---------| -----------
lat | M          | Double  | 위도
ing | M          | Double  | 경도
option | M          | Option  | option 정보
style | M          | Style   | style 정보
cctv_no | M          | Number | CCTV 관리번호

#### SaveQrSticker

항목 | 필수 여부(M/O) | 데이터 타입  | 설명
--------- |------------|---------| -----------
lat | M          | Double  | 위도
ing | M          | Double  | 경도
option | M          | Option  | option 정보
style | M          | Style   | style 정보
qr_stk_no | M          | Number | QR 관리번호

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


### Response Body

화면 설정을 위한 마커 및 주요지점등 구성 정보 조회 응답과 동일



## 건설사 SelectList - 주요지점/Geojson/Fence 설정

> 응답 전문 예시

```json
{
    "context": [
        {
            "code": "37",
            "value": "맵기반 건설사1",
            "code_int": 37
        },
        {
            "code": "38",
            "value": "맵기반 건설사2",
            "code_int": 38
        }
    ],
    "return_code": 0,
    "return_message": "Success"
}
```


주요지점의 경우 현장에 소속된 건설사별로 구성된다.

최고 서비스 관리자는 주요지점 등록시 해당 현장에 편입된 건설사 중 하나를 선택해서 등록하여야 하며
건설사 관리자와 현장관리자는 본인이 소속된 건설사가 선택되어야 한다.

해당 API 호출시 현장 편입된 건설사가 1 개뿐이거나 건설사/현장 관리자인 경우 1 개만 제공되며 1개만 제공될시 
해당 건설사가 자동선택되고 변경불가로 표시되어야 한다. 


<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%EC%A7%80%EB%8F%84%EA%B8%B0%EB%B0%98%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20%EC%84%A4%EC%A0%95%20%ED%99%94%EB%A9%B4%20%EA%B5%AC%EC%84%B1%20%EB%B0%8F%20%EC%84%A4%EC%A0%95%20API%20/exportConCompanyUsingGET)


### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/gps/setting/concompany`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입           | 설명
--------- |------------|------------------| -----------
wp_no | M          | Number |현장 관리번호


### Response Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
code | M          | Number | 건설사 관리번호 
value | M          | String | 건설사명

## 디바이스 SelectList - IoT/BLE GW  


> 응답 전문 예시

```json
{
  "context": [
    {
      "idx": 1853,
      "display_name": "유해물질#1",
      "selectable": false
    }
  ],
  "return_code": 0,
  "return_message": "Success"
}
```

IoT 및 BLE GW 마커 등록/수정시 선택 리스트 조회

selectable 이 false 인 경우 이미 위치 지정이 되었음을 의미하며 선택할 수 없는 항목으로 표기되어야 한다.
예외적으로, 수정시 이전 선택 항목은 선택할 수 있어야 한다.


<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%EC%A7%80%EB%8F%84%EA%B8%B0%EB%B0%98%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20%EC%84%A4%EC%A0%95%20%ED%99%94%EB%A9%B4%20%EA%B5%AC%EC%84%B1%20%EB%B0%8F%20%EC%84%A4%EC%A0%95%20API%20/exportSelectDeviceUsingGET)


### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/gps/setting/device/{device_type}`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입           | 설명
--------- |------------|------------------| -----------
wp_no | M          | Number |현장 관리번호
device_type| M          | Number |디바이스 유형


### Response Body

항목 | 필수 여부(M/O) | 데이터 타입  | 설명
--------- |------------|---------| -----------
idx | M          | Number  | 디바이스 관리번호
display_name | M          | String  | 디바이스명
selectable | M          | Boolean | 선택 가능 여부 ( 이미 위치 지정된 경우 false )


## CCTV SelectList


> 응답 전문 예시

```json
{
  "context": [
    {
      "cctv_no": 386,
      "display_name": "생활가압장#1",
      "selectable": false
    }
  ],
  "return_code": 0,
  "return_message": "Success"
}
```

CCTV 마커 등록/수정시 선택 리스트 조회

selectable 이 false 인 경우 이미 위치 지정이 되었음을 의미하며 선택할 수 없는 항목으로 표기되어야 한다.
예외적으로, 수정시 이전 선택 항목은 선택할 수 있어야 한다.


<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%EC%A7%80%EB%8F%84%EA%B8%B0%EB%B0%98%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20%EC%84%A4%EC%A0%95%20%ED%99%94%EB%A9%B4%20%EA%B5%AC%EC%84%B1%20%EB%B0%8F%20%EC%84%A4%EC%A0%95%20API%20/exportSelectCctvUsingGET)


### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/gps/setting/cctv/{install_type}`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입           | 설명
--------- |------------|------------------| -----------
wp_no | M          | Number |현장 관리번호
install_type| M          | Number |CCTV 설치 유형


### Response Body

항목 | 필수 여부(M/O) | 데이터 타입  | 설명
--------- |------------|---------| -----------
cctv_no | M          | Number  | CCTV 관리번호
display_name | M          | String  | 디바이스명
selectable | M          | Boolean | 선택 가능 여부 ( 이미 위치 지정된 경우 false )


## QR SelectList


> 응답 전문 예시

```json
{
  "context": [
    {
      "qr_stk_no": 18,
      "display_name": "QR#1",
      "selectable": false
    }
  ],
  "return_code": 0,
  "return_message": "Success"
}
```

QR 마커 등록/수정시 선택 리스트 조회

selectable 이 false 인 경우 이미 위치 지정이 되었음을 의미하며 선택할 수 없는 항목으로 표기되어야 한다.
예외적으로, 수정시 이전 선택 항목은 선택할 수 있어야 한다.


<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%EC%A7%80%EB%8F%84%EA%B8%B0%EB%B0%98%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20%EC%84%A4%EC%A0%95%20%ED%99%94%EB%A9%B4%20%EA%B5%AC%EC%84%B1%20%EB%B0%8F%20%EC%84%A4%EC%A0%95%20API%20/exportSelectQRUsingGET)


### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/gps/setting/qrsticker`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입           | 설명
--------- |------------|------------------| -----------
wp_no | M          | Number |현장 관리번호


### Response Body

항목 | 필수 여부(M/O) | 데이터 타입  | 설명
--------- |------------|---------| -----------
qr_stk_no | M          | Number  | QR 관리번호
display_name | M          | String  | 디바이스명
selectable | M          | Boolean | 선택 가능 여부 ( 이미 위치 지정된 경우 false )



## ApSensor SelectList



> 응답 전문 예시

```json
{
  "context": [
    {
      "si_idx": 20052,
      "display_name": "출입구/입구",
      "selectable": false
    }
  ],
  "return_code": 0,
  "return_message": "Success"
}
```

QR 마커 등록/수정시 선택 리스트 조회

selectable 이 false 인 경우 이미 위치 지정이 되었음을 의미하며 선택할 수 없는 항목으로 표기되어야 한다.
예외적으로, 수정시 이전 선택 항목은 선택할 수 있어야 한다.


<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%EC%A7%80%EB%8F%84%EA%B8%B0%EB%B0%98%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20%EC%84%A4%EC%A0%95%20%ED%99%94%EB%A9%B4%20%EA%B5%AC%EC%84%B1%20%EB%B0%8F%20%EC%84%A4%EC%A0%95%20API%20/exportSelectApSensorUsingGET)


### HTTP Request

`GET /imoa/api/monitor/4.3/workplace/{wp_no}/gps/setting/qrsticker`

### Path variable

항목 | 필수 여부(M/O) | 데이터 타입           | 설명
--------- |------------|------------------| -----------
wp_no | M          | Number |현장 관리번호


### Response Body

항목 | 필수 여부(M/O) | 데이터 타입  | 설명
--------- |------------|---------| -----------
si_idx | M          | Number  | Ap 센서 관리번호
display_name | M          | String  | 디바이스명
selectable | M          | Boolean | 선택 가능 여부 ( 이미 위치 지정된 경우 false )


## 지도 검색

키워드를 이용한 장소 검색은 Kakao Map API 를 이용하여야 한다.

참고) https://apis.map.kakao.com/web/sample/keywordBasic/

<aside class="notice">
기획서 Page-15
</aside>


## Geojson 그리기

* 샘플 geojson 만들기 :  https://geojson.io

```javascript 
// 샘플 ( 카카오 맵에서 Geojson 그리기 )

var container = document.getElementById('map');
var options = { center: new kakao.maps.LatLng(37.5665, 126.9780), level: 10 };
var map = new kakao.maps.Map(container, options);

$.getJSON('data.geojson', function(data) {
    var features = data.features;
    for (var i = 0, len = features.length; i < len; i++) {
        var geometry = features\[i\].geometry;
        var properties = features\[i\].properties;
        if (geometry.type === 'Point') {
            var coords = new kakao.maps.LatLng(geometry.coordinates\[1\], geometry.coordinates\[0\]);
            var marker = new kakao.maps.Marker({ position: coords });
            marker.setMap(map);
        } else if (geometry.type === 'LineString') {
            var path = geometry.coordinates.map(function(coords) {
                return new kakao.maps.LatLng(coords\[1\], coords\[0\]);
            });
            var polyline = new kakao.maps.Polyline({
                path: path
            });
            polyline.setMap(map);
        } else if (geometry.type === 'Polygon') {
            var paths = geometry.coordinates.map(function(ring) {
                return ring.map(function(coords) {
                    return new kakao.maps.LatLng(coords\[1\], coords\[0\]);
                });
            });
            var polygon = new kakao.maps.Polygon({
                paths: paths
            });
            polygon.setMap(map);
        }
    }
});

```


