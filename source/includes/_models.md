# Models

## TokenInfo

> Token 전문 예시. member_info 는 [MemberInfo](#memberinfo) 참고 

```json
{
    "access_token" : "String",
    "token_type" : "bearer",
    "refresh_token" : "String",
    "expires_in" : 31535999,
    "jti" : "String",
    "scope" : "web",
    "member_info" : {},
    "authorities" : [ ],
    "authorities_info" : {},
    "former_member" : false
  }

```

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
access_token | M          | String | 사용자 인증키
refresh_token | M          | String | Refresh Token. 인증 정보 갱신을 위한 키
expires_in | M          | Number | 만료까지 남은 시간
member_info | M          | MemberInbfo | 로그인 사용자의 기본 정보. 상세내용은 [MemberInfo](#memberinfo) 참고
authorities | M          | List<String> | 사용자 권한 리스트
authorities_info | M          | Map | 특정 권한과 관련된 상세 권한 정보
former_member | M          | boolean | (구) 건설업 사용자 여부


## MemberInfo

> 사용자 전문 예시.

```json
{
  "coop_no" : 1,
  "cc_no" : 1,
  "mb_no" : 1,
  "mb_name" : "String",
  "office_no" : 1,
  "mb_id" : "String",
  "grd_cd" : "String"
}
```

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
mb_no | M          | Number   | 사용자 관리번호
mb_id | M          | String | 사용자 아이디
mb_name | M          | String | 사용자명
grd_cd | M          | String | 사용자 등급
coop_no | O          | Number   | 협력사 관리번호 ( 협력사 관리자인 경우 )
cc_no | O          | Number   | 건설사 관리번호 ( 건설사 관리자/현장 관리자인 경우 )
office_no | O          | Number | 발주처 관리번호 ( 발주사 관리자인 경우 )


## WorkplaceInfo

> 현장 정보 전문 예시

```json
{
  "wp_no": 0,
  "wp_id": "string",
  "wp_name": "string",
  "hcmpt_id": "string",
  "cstrt_no" : 1,
  "view_map_file_download_url" : "string",
  "gps_center_lat" : 13.1111,
  "gps_center_long" : 111.1111,
  "gps_map_type" : 1,
  "support_ble": true,
  "support_gps": true,
  "support_3d": true,
  "use_health_comp": true
}
```

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
wp_no | M          | 현장 관리번호
wp_id | M          | 현장 아이디
wp_name | M          | 현장명
hcmpt_id | M          | 메인 컴포넌트 아이디
cstrt_no | M          | 메인 공사구간 관리번호
gps_center_lat | O          | GPS 현장 중심좌표 위도 
gps_center_long | O          | GPS 현장 중심좌표 경도
gps_map_type | O          | GPS Map 접속시 초기 Map 타입. 1: 일반, 2: 위성지도
support_ble | M          | BLE 모니터링 사용 여부
support_gps | M          | GPS 모니터링 사용 여부
use_health_comp | M          | 건강현황 정보 지원 여부


## WorkplaceNoticeInfo

> 공지사항 전문 예시

```json
{
  "all_workplace_worker_notice": "string",
  "file_list": [
    {
      "bf_datetime": "2024-01-30T01:40:05.831Z",
      "bf_file": "string",
      "bf_file_download_url": "string",
      "bf_filesize": 0,
      "bf_height": 0,
      "bf_no": 0,
      "bf_source": "string",
      "bf_type": 0,
      "bf_width": 0,
      "bo_table": "string",
      "wr_id": 0
    }
  ],
  "mb_no": 0,
  "wr1": "string",
  "wr2": 0,
  "wr3": "string",
  "wr4": 0,
  "wr_content": "string",
  "wr_datetime": "2024-01-30T01:40:05.831Z",
  "wr_file": 0,
  "wr_hit": 0,
  "wr_id": 0,
  "wr_ip": "string",
  "wr_name": "string",
  "wr_notice": "string",
  "wr_subject": "string"
}
```

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
wr_id	 | O          | 공지사항 번호
wr_name	 | O          | 작성자명
wr_subject	 | O | 공지사항 제목
wr_content	 | M          | 공지사항 내용
wr_datetime | M          | 생성일
mb_no	 | M          | 작성자 번호
wr_file | M          | 첨부 파일 수
wr_hit | M          | 조회수
all_workplace_worker_notice | M          | 현장 전체 근로자 공지여부
wr_notice | O          | 공지여부
wr1	 | M          | 긴급 알림 여부
wr2 | M          | 현장 번호
wr3 | M          | 현장명
wr4 | M          | 협력사 번호



## BleMarker

> 마커 정보 예시

```json
{
  "mk_no" : 1,
  "mk_type" : 1,
  "mk_name" : "마커명",
  "grid_x" : 10.12,
  "grid_y" : 98.99,
  "attached_target" : 1,
  "actual_location" : 1,
  "label_text" : "라벨 표시 텍스트",
  "lnk_cstrt_no" : 2,
  "ap_sensor_stat" : {
    "caution_count" : 3,
    "danger_worker_count" : 1,
    "worker_count" : 2
  },
  "icon_type" : 1,
  "icon_info" : {
    "icon_type" : 1,
    "icon_usage" : 1,
    "icon_type_name" : "아이콘명",
    "icon_url" : "아이콘 URL"
  },
  "ref_device_idx" : 14,
  "device_info" : {
    "idx" : 14,
    "display_name" : "디바이스명",
    "device_type" : 14,
    "device_type_name" : "디바이스 유형명",
    "mac_address" : "Mac address",
    "rct_status": 1,
    "dv_status": 1,
    "worker_count" : 0,
    "state": 1,
    "state_name": "장치 상태명",
    "show_popup": true,
    "popup_display_items": [
      {
        "code": "DEVICE_TYPE",
        "name": "구분",
        "value": "센서"
      }
    ]
  },
  "ref_sensor_idx" : 3,
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
  "ref_qr_stk_no" : 11,
  "qr_stk_info" : {
    "qr_stk_no" : 14,
    "qr_stk_name" : "qr sticker 명",
    "qr_type" : 1,
    "inout_type" : 1
  },
  "ref_cctv_no" : 44,
  "cctv_info" : {
    "cctv_no" : 14,
    "cctv_name" : "CCTV명",
    "cctv_kind" : 1,
    "install_type" : 1,
    "ptz_status" : 1
  },
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

```

### 마커 정보

항목 | 필수 여부(M/O) | 데이터 타입  | 설명
--------- |------------|---------| -----------
mk_no	 | M          | number  | 마커 관리번호
mk_type	 | M          | number  | 마커 유형 
mk_name	 | M          | string  | 마커명
grid_x	 | M          | decimal | 마커 위치 x 축 좌표 ( 0.00 ~ 100.00. x 축 좌표 내  % 값을 이용 )  
grid_y | M          | decimal | 마커 위치 y 축 좌표 ( 0.00 ~ 100.00. y 축 좌표 내  % 값을 이용 )
attached_target | M          | number  | 마커 부착 목표물. 1: 공사구간, 2: 진행현황바
actual_location | M          | number  | 실제 위치 여부. 0: 아님 ( 표시 용도 ), 1: 실제 위치. IOT센서, AP센서, QR, CCTV 등 기기류의 실제 위치 지정 여부
lnk_cstrt_no	 | O          | number  | 링크 공사구역 관리번호. 마커 유형이 라벨(1), 아이콘(2) 인 경우 사용
label_text	 | O          | string  | 라벨 표시 텍스트. 마커 유형이 라벨(1) 인 경우 사용
ap_sensor_stat| O          | object  | Ap 센서 감지 근로자 현황. 마커 유형이 라벨(1) 이고 링크된 공사구역이 있는 경우 사용. 설정화면에서는 미사용
icon_type	 | O          | number  | 아이콘 유형. 마커 유형이 아이콘(2) 인 경우 사용
icon_info | O          | object  | 아이콘 정보. 마커 유형이 아이콘(2) 인 경우 사용
ref_device_idx | O          | number  | 디바이스 관리번호. 마커 유형이 IOT센서(3), BLE GW(5) 인 경우 사용
device_info | O          | object  | 디바이스 정보. 마커 유형이 IOT센서(3), BLE GW(5) 인 경우 사용
ref_sensor_idx | O          | number  | AP 센서 관리번호. 마커 유형이 AP센서(4) 인 경우 사용
ap_sensor_info | O          | object  | AP 센서 정보 및 디텍팅 근로자 수 정보. 마커 유형이 AP센서(4) 인 경우 사용
ref_qr_stk_no | O          | number  | 진출/입 QR 관리번호. 마커 유형이 QR(6) 인 경우 사용
ref_cctv_no | O          | number  | CCTV 관리번호. 마커 유형이 CCTV(7) 인 경우 사용
option | O          | object  | 마커 옵션 설정 정보
style | O          | object  | 마커 style 설정 정보

### ap_sensor_stat ( Ap 센서 감지 근로자 현황 )

항목 | 필수 여부(M/O) | 데이터 타입  | 설명
--------- |------------|---------| -----------
worker_count	 | M          | number  | 근로자 감지수
danger_worker_count	 | M          | number  | 위험센서 근로자 감지수
caution_count	 | M          | number  | 건강유의 근로자 감지수

### icon_info ( ICON 정보 )

항목 | 필수 여부(M/O) | 데이터 타입  | 설명
--------- |------------|---------| -----------
icon_type | M          | number | 아이콘 타입 관리번호
icon_usage | M          | number | 아이콘 사용처 코드 ( 0: 미지정, 1: 마커 )
icon_type_name | M          | number | 아이콘 타입명
icon_url | M          | string | 아이콘 URL


### device_info ( 디바이스 정보 )

항목 | 필수 여부(M/O) | 데이터 타입  | 설명
--------- |------------|---------| -----------
idx | M          | number  | 디바이스(장치) 관리번호
display_name | M          | string  | 디바이스 표시명
device_type | M          | number  | 디바이스 유형
device_type_name | M          | string  | 디바이스 유형명
rct_status | M          | number  | 디바이스 데이터 위험 상태. 1: 정상, 2: 주의 , 3: 위험
dv_status | M          | number  | 디바이스 동작 상태. 1: 정상, 2:OFF, 3: 측정불가, 4: 수집 지연
state | M          | number  | 디바이스 상태. 1: 정상, 2: 주의, 3: 위험, 4:OFF, 5: 측정불가, 6: 수집 지연
state_name | M          | string  | 디바이스 상태명
show_popup | M          | boolean | 디바이스 상세 팝업 지원 유무
popup_display_items | M          | List   | 상세 팝업 표시 데이터 항목
popup_display_items.code | M          | List   | 항목 코드
popup_display_items.name | M          | List   | 항목명
popup_display_items.value | M          | List   | 항목값
worker_count	 | O          | number  | 근로자 감지수

show_popup 이 true 인 경우 해당 디바이스 마커 클릭시 팝업 노출 

1. 팝업 제목은 "장치정보 - ${device_type_name}"
 
2. 팝업 표시 정보는 popup_display_items 의 정보를 ${name} | ${value} 로 차례대로 표시 
 
3. popup_display_items.code 가 DASHIBOARD_POPUP 인 경우는 알림 ON/OFF 기능이 들어간 항목이어야 한다.
 - 기존 화재 감지기 상세 팝업 참고 


<aside class="notice">
state 에 따라 정상/위험/비정상(정상과 위험을 제외한 모든 상태) 아이콘으로 변경되어 표시되어야 한다. ( 현재는 화재 감지기만 가능 )
</aside>


### ap_sensor_info ( AP 센서 정보 )


항목 | 필수 여부(M/O) | 데이터 타입      | 설명
--------- |------------|-------------| -----------
si_idx | M          | number      | AP 센서 관리번호
si_type | M          | string      | AP 센서 유형
sd_name | M          | string      | AP 센서 구역명
si_place1  | M          | string      | 위치1
si_place2  | M          | string      | 위치2
worker_count	 | M          | number  | 근로자 감지수
danger_worker_count	 | M          | number  | 위험센서 근로자 감지수
caution_count	 | M          | number  | 건강유의 근로자 감지수
default_color  | M          | number | 디폴트 색상
flash_color | M          | number | flash 색상
support_flash | M          | number | flash 지원여부
marker | M          | number | marker 표시 여부. 0: 미표시, 1: 표시

### qr_stk_info ( QR 스티커 정보 )

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
qr_stk_no | M          | number | QR 스티커 관리번호
qr_stk_name | M          | string | QR 스티커명
qr_type | M          | number | QR 스티커 유형. 1: 출/퇴근, 2: 진/출입
inout_type | M          | number | 진/출입유형. 1: 진입, 2: 진출, 3: 진/출입 선택
inout_count | O | number | 당일 진/출입 수

### cctv_info ( CCTV 정보 )

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------|--------| -----------
cctv_no | M          | number  | CCTV 관리번호
cctv_name | M          | string | CCTV명                                        
cctv_kind | M          | number | CCTV 유형. 0: 일반, 1: IntelliVix, 2: Emstone    
install_type | M          | number | 설치 유형. 0: 고정형, 1: 이동형
ptz_status | M          | number | PTZ 지원 여부. 0: 미지원, 1: 지원

#### 마커 유형

유형 코드 |  설명
--------- |------------
1 | 라벨
2 | 아이콘
3 | IOT센서(디바이스)
4 | AP센서
5 | BLE GW
6 | QR
7 | CCTV 


#### 디바이스 유형(device_type)

유형 코드 |  카테고리 | 사용 여부 | 설명
--------- |------------|------------|------------
0 | 0 | Y | 출입게이트
1 | 0 | N | 출입표출장치 ( X )
2 | 0 | N | 고정형 GPS ( X )
3 | 0 | N | 영상분석 서버 ( X )
4 | 1 | Y |  유해물질 측정센서
5 | 0 | N |  유해물질 경보기 ( X )
6 | 1 | Y |  기울기 센서
7 | 1 | Y |  개구부 센서
8 | 1 | Y |  풍속계
9 | 0 | Y |  LoRa 게이트웨이
10 | 1 | Y |  온습도 센서 
11 | 1 | Y |  소음 측정기
12 | 1 | Y |  미세먼지 측정기
13 | 0 | N |  불꽃감지기 ( X )
14 | 0 | Y |  GPS 트래커
15 | 1 | Y |  화재 감지기
16 | 2 | Y |  BLE G/W
17 | 0 | Y |  사이렌 (경보기)
18 | 0 | Y |  TBM

디바이스 카테고리값 0: 미지정, 1: Iot, 2: 위치

#### AP 센서 유형(si_type)

유형 코드 | 위험 여부 | 설명
--------- |-------|------------
안전조회 | X     | 안전조회장 이용
위험감시  | X     | 사용 안함
위험지역 | O     | 위험지역
위험지역 인접구역 | X     | 사용 안함
일반 | X     | 일반 
출입용 | X     | 출입구 이용

'위험지역' AP 센서만 위험센서로 이용하며 나머지는 일반 센서로 모두 동일하게 취급

#### 마커 옵션 설정 정보

 옵션 |  설명
--------- |------------
show_name | 이름 표시 여부
show_icon | ICON 표시 여부
show_count | 카운트 표시 여부
auto_hide | 미감지시 자동 숨김 여부 

#### 마커 style 정보

style명 |  설명
--------- |------------
font_size | 폰트 사이즈
font_color | 폰트 색상
bg_color | 배경 색상
icon_size | 아이콘 사이즈

마커 옵션과 style 은 필요시 자유롭게 추가하여도 무방합니다.


## BleProgressBar

> 진행현황 바 정보 예시

```json
{
  "bar_no": 1,
  "items": [
    {
      "bar_no": 1,
      "item_idx": 1,
      "blank_item": 0,
      "start_position": 22.22,
      "ref_cstrt_no" : 3,
      "pgr_info" : {
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
        "install_type" : 1,
        "ptz_status" : 1
      },
      "tbm_back_cctv_no": 1,
      "tbm_back_cctv_info" : {
        "cctv_no" : 14,
        "cctv_name" : "CCTV명",
        "cctv_kind" : 1,
        "install_type" : 1,
        "ptz_status": 1
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
```

진행현황 바 정보

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
bar_no	 | M          | 진행현황바 관리번호
items	 | M          | 진행현황 정보 리스트

#### 진행현황 아이템 정보 리스트

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
item_idx	 | M          | 진행현황 바 내 순번. 1부터 시작
ref_cstrt_no | M          | 표시될 공사 구간 관리번호
pgr_info | M | 표시될 공사 구간의 진행현황 정보
blank_item	 | M          | 비어있는 구간(Blank Item) 여부. 0: 아님, 1: Blank item
start_position	 | M          | 진행현황 바 내 시작 위치. 0 ~ 100.00
tbm_front_cctv_no | M          | TBM 전방 CCTV 관리번호
tbm_front_cctv_info | M          | TBM 전방 CCTV 정보 ( cctv_info 참고 )
tbm_back_cctv_no | M          | TBM 후방 CCTV 관리번호
tbm_back_cctv_info | M          | TBM 후방 CCTV 정보. ( cctv_info 참고 )
direction | O | 공사방향. 1: 좌->우,  2: 우->좌 ( 진행현황 표시시 필수 )
show_distance | O |  진행거리 표시 여부. 0: 표시 안함, 1: 표시함. ( 진행현황 표시시 필수 )
show_tbm | O | TBM 표시 여부. 0: 표시 안함, 1: 표시함.  ( 진행현황 표시시 필수 )
option | O          | 진행현황 아이템 옵션 설정 정보
style | O          | 진행현황 아이템 style 설정 정보


#### pgr_info ( 진행 현황 ) 정보

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
cstrt_no	 | M          | 공사 구간 관리번호
cstrt_name | M          | 공사 구간 관리번호명
construct_distance | M | 총 공사 거리
progress_distance	 | M          | 진행 거리
depth	 | M          | 심도


#### 진행현황 아이템 style 정보

style명 |  설명
--------- |------------
font_size | 폰트 사이즈
color | 색상
height | 좊이

옵션과 style 은 자유롭게 추가/삭제하여도 무방합니다.


