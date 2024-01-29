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
  "support_ble": true,
  "support_gps": true,
  "use_health_comp": true
}
```

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
wp_no | M          | 현장 관리번호
wp_id | M          | 현장 아이디
wp_name | M          | 현장명
hcmpt_id | M          | 메인 컴포넌트 아이디
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
  "lnk_cstrt_no" : 2,
  "label_text" : "라벨 표시 텍스트",
  "icon_type" : "아이콘 타입코드",
  "icon_url" : "아이콘 URL",
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
```

마커 정보

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
mk_no	 | M          | 마커 관리번호
mk_type	 | M          | 마커 유형 
mk_name	 | M          | 마커명
grid_x	 | M          | 마커 위치 x 축 좌표  
grid_y | M          | 마커 위치 y 축 좌표
attached_target | M          | 마커 부착 목표물. 1: 공사구간, 2: 진행현황바
lnk_cstrt_no	 | O          | 링크 공사구역 관리번호. 마커 유형이 라벨(1), 아이콘(2) 인 경우 사용
label_text	 | O          | 라벨 표시 텍스트. 마커 유형이 라벨(1) 인 경우 사용
icon_type	 | O          | 아이콘 유형. 마커 유형이 아이콘(2) 인 경우 사용
icon_url	 | O          | icon_url.  마커 유형이 아이콘(2) 인 경우 사용
ref_device_idx | O          | 디바이스 관리번호. 마커 유형이 IOT센서(4), BLE GW(6) 인 경우 사용
ref_sensor_idx | O          | AP 센서 관리번호. 마커 유형이 AP센서(5) 인 경우 사용
ref_qr_stk_no | O          | 진출/입 QR 관리번호. 마커 유형이 QR(7) 인 경우 사용
ref_cctv_no | O          | CCTV 관리번호. 마커 유형이 CCTV(8) 인 경우 사용
option | O          | 마커 옵션 설정 정보
style | O          | 마커 style 설정 정보

### 마커 유형

유형 코드 |  설명
--------- |------------
1 | 라벨
2 | 아이콘
3 | IOT센서(디바이스)
4 | AP센서
5 | BLE GW
6 | QR
7 | CCTV 

### 마커 옵션 설정 정보

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

마커 옵션과 style 은 따로 정의된 규격이 없기에 필요시 자유롭게 추가/삭제하여도 무방합니다.


## BleProgressBar

> 진행현황 바 정보 예시

```json
{
  "pgrbar_no" : 1,
  "items" : [
    {
      "pitem_no" : 1,
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
```

진행현황 바 정보

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
pgrbar_no	 | M          | 진행현황바 관리번호
items	 | M          | 진행현황 정보 리스트

#### 진행현황 아이템 정보 리스트

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
pitem_no  | M          | 진행현황 아이템 관리번호
bar_idx	 | M          | 진행현황 바 내 순번. 1부터 시작
ref_cstrt_no | M          | 표시될 진행현황 공사 구간 관리번호
show_item	 | M          | 진행현황 표시 여부.  0: 표시하지 않음(blank item). 1: 진행형황 표시
start_position	 | M          | 진행현황 바 내 시작 위치. 0 ~ 100.00
tbm_front_cctv_no | M          | TBM 전방 CCTV 관리번호
tbm_back_cctv_no | M          | TBM 후방 CCTV 관리번호
option | O          | 진행현황 아이템 옵션 설정 정보
style | O          | 진행현황 아이템 style 설정 정보

### 진행현황 아이템 옵션 설정 정보

옵션 |  설명
--------- |------------
direction | 공사방향. 1: 좌->우,  2: 우->좌
show_distance | 진행거리 표시 여부
show_tbm | TBM 표시 여부

#### 진행현황 아이템 style 정보

style명 |  설명
--------- |------------
font_size | 폰트 사이즈
color | 색상
height | 좊이

옵션과 style 은 자유롭게 추가/삭제하여도 무방합니다.




## WpData

// TODO
