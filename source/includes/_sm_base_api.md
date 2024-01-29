# 현장관제 진입

<로그인 진입 - 이전 현장 정보가 없는 경우 > 호출순서는 아래와 같습니다.

1. 권한있는 현장 리스트 조회
2. 현장 메인 정보 조회
3. 현장 정보 조회 - 현장 리스트 상의 첫 현장 정보
4. 현장에 지정된 메인 화면 및 컴포넌트 API 차례대로 호출

<새로고침/링크 통한 진입 - 이전 현장 정보가 있거나 현장이 지정된 경우 > 호출순서는 아래와 같습니다.

1. 현장 정보 조회 ( 현장 아이디 이용 )
2. 권한있는 현장 리스트 조회
3. 현장 메인 정보 조회
4. 현장에 지정된 메인 화면 및 컴포넌트 API 차례대로 호출

## 권한있는 현장 리스트 조회 

> 응답 전문 예시.  현장 정보 상세는 [WorkplaceInfo](#workplaceinfo) 참고

```json
{
  "context": {
    "google_key": "string",
    "icon_url": "string",
    "kakao_key": "string",
    "list": [
      {
        "wp_no": 0,
        "wp_id": "string",
        "wp_name": "string",
        "hcmpt_id": "string",
        "support_ble": true,
        "support_gps": true,
        "use_health_comp": true,
        .......
      }
    ]
  },
  "return_code": 0,
  "return_message": "string"
}
```

웹에서 사용하는 외부 API 연동키값과 로그인한 사용자에 따라 권한있는 현장 리스트 정보를 제공합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

[Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.2%5D%20IMOS%20%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81%20%EA%B4%80%EB%A6%AC/imosMainUsingPOST)

### HTTP Request

`POST /imoa/api/monitor/4.2/main`

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
google_key | M          | String | Google 연동을 위한 Key
kakao_key | M          | String | Kakao 연동을 위한 Key
icon_url | M          | String | 상단 타이틀에 보여질 로고 이미지 URL
list | M | List<WorkplaceInfo> | 지원 가능 현장 리스트. 현장 정보 상세는 [WorkplaceInfo](#workplaceinfo) 참고



## 현장 정보 조회 ( 현장 아이디 이용 )

> 응답 전문 예시

```json
{
  "return_code": 0,
  "return_message": "string",
  "context": {
    "wp_no": 0,
    "wp_id": "string",
    "wp_name": "string",
    "hcmpt_id": "string",
    "support_ble": 0,
    "support_gps": 0,
    "use_health_comp": true,
    .......
  }
}
```

현장 정보를 제공하며 새로고침이나 재접속시 접속 URL 을 통해 현장 아이디(wp_id)는 추출 후 현장 정보 조회시 이용합니다.  

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

[Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%ED%98%84%EC%9E%A5%20%EA%B4%80%EB%A6%AC/workplaceDetailUsingGET)

### HTTP Request

`GET /imoa/api/workplace/manage/detail/{wp_id}`

### Request Path

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_id | M          | string | 현장 아이디

### Response Body

현장 정보 상세는 [WorkplaceInfo](#workplaceinfo) 참고


## 현장 메인 구성 정보 조회

> 요청 전문 예시

```json
{
  "workplace":true,
  "deploy_page":1,
  "weather":true,
  "notice":true,
  "dust":true
}
```

> 응답 전문 예시

```json
{
  "return_code": 0,
  "return_message": "string",
  "context": {
    "icon_url": "string",
    "bg_img_url" : "string",
    "bg_color" : "string",
    "monitoring_workplace": {
      "wp_no": 0,
      "wp_id": "string",
      "wp_name": "string",
      "gps_center_lat": 0,
      "gps_center_long": 0,
      "support_3d": true,
      "support_ble": true,
      "support_gps": true,
      "use_health_comp": true,
      "view_file_download_url": "string"
    },
    "notice": {
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
    },
    "ui_component_list": [
      {
        "custom_data": "string",
        "custom_data_json": {},
        "deploy_page": 0,
        "hcmpt_id": "string",
        "hcmpt_name": "string",
        "hcmpt_type": 0,
        "height": 0,
        "imuc_no": 0,
        "mb_no": 0,
        "pos_x": 0,
        "pos_y": 0,
        "ui_type": 0,
        "width": 0,
        "wp_no": 0
      }
    ],
    "weather": {
      "base_date": "string",
      "base_time": "string",
      "humidity": "string",
      "humidity_unit": "string",
      "precipitation": "string",
      "precipitation_form": "string",
      "precipitation_form_name": "string",
      "precipitation_unit": "string",
      "rainfall": "string",
      "rainfall_unit": "string",
      "sky_form": "string",
      "sky_form_name": "string",
      "temperature": "string",
      "temperature_unit": "string",
      "wind_direction": "string",
      "wind_speed": "string",
      "wind_speed_unit": "string",
      "wp_no": 0
    },
    "wp_data_list": [
      {
        "custom_data": "string",
        "hcmpt_id": "string",
        "wp_no": 0
      }
    ]
  }
}
```

현장관제 화면 표시를 위한 기본적인 정보 ( 현장 및 UI 컴포넌트, 날씨, 최근 공지사항 정보 ) 를 제공합니다.


<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

[Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.2%5D%20IMOS%20%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81%20%EA%B4%80%EB%A6%AC/workplaceMainUsingPOST)


### HTTP Request

`POST /imoa/api/monitor/4.2/workplace/{wp_no}/main`

### Request Path

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
wp_no | M          | number | 현장 관리번호

### Request Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
workplace | M       | number | 현장 정보 포함 여부. 0: 미포함, 1: 포함
deploy_page | M          | number | 접속 메인 페이지 번호. 메인 페이지는 1
dust | M       | number | 미세먼지 정보 포함 여부. 0: 미포함, 1: 포함
notice | M       | number | 공지사항 정보 포함 여부. 0: 미포함, 1: 포함
weather | M       | number | 날씨 정보 포함 여부. 0: 미포함, 1: 포함

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입              | 설명
--------- |------------|---------------------| -----------
icon_url | M          | string              | 현장관제 ICON url ( 서비스 로고 )
weather | M          | WeatherInfo         | 현장 날씨 정보
ui_component_list | M          | List<UiComponent>   | 설정된 UI 컴포넌트 리스트
notice | M          | WorkplaceNoticeInfo | 최근 공지사항 정보. 정보 상세는 [WorkplaceNoticeInfo](#workplacenoticeinfo) 참고
monitoring_workplace | M          | List<WorkplaceInfo> | 현장 정보. 현장 정보 상세는 [WorkplaceInfo](#workplaceinfo) 참고
wp_data_list | O          | List<WpData>        | 현장 컴포넌트 부가 정보 리스트. 정보 상세는 [WpData](#wpData) 참고


#### 현장 날씨 정보

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
base_date | M          | string | 기준일자(yyyyMMdd)
base_time | M          | string | 기준시간(HHmm)
humidity | M          | string | 습도
humidity_unit	 | M          | string | 습도 단위
precipitation | M          | string | 강수량
precipitation_unit | M          | string | 강수량 단위
precipitation_form | M          | string | 강수형태 코드
precipitation_form_name | M          | string | 강수형태명
rainfall | M          | string | 강수확률
rainfall_unit | M          | string | 강수확률 단위
sky_form | M          | string | 하늘형태 코드
sky_form_name | M          | string | 하늘형태명
temperature | M          | string | 온도
temperature_unit | M          | string | 온도 단위
wind_direction	 | M          | string | 풍향
wind_speed | M          | string | 풍속
wind_speed_unit | M          | string | 풍속 단위
temperature | M          | string | 온도


#### UI 컴포넌트 정보

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
imuc_no	 | M          | number | 컴포넌트 배치 번호
deploy_page | M          | number | 배포 페이지
hcmpt_id	 | M          | string | 컴포넌트 아이디
hcmpt_name	 | M          | string | 컴포넌트명
hcmpt_type		 | M          | number | 컴포넌트 유형. 1: 안전관리, 2: 출역관리, 3: 현장관리, 4: 보건관리
height	 | M          | number | 컴포넌트 높이
width		 | M          | number | 컴포넌트 길이
pos_x	 | M          | number | 컴포넌트의 시작 x 좌표
pos_y	 | M          | number | 컴포넌트의 시작 y 좌표
ui_type	 | M          | number | 컴포넌트 타입. 1: 메인 UI, 2: 컴포넌트 UI

#### 현장별 컴포넌트 부가 정보

항목 | 필수 여부(M/O) | 데이터 타입     | 설명
--------- |------------|------------| -----------
wp_no | M | number     | 현장 관리번호
hcmpt_id	 | M          | string | 컴포넌트 아이디   
custom_data_json	 | M          | string | 부가 정보 JSON 

