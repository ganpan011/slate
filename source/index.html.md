---
title: API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - shell
  - javascript

toc_footers:
  -   

includes:
  - auth_login_out
  - sm_base_api
  - ble_monitor_api
  - gps_monitor_api
  - marker_setting_api
  - construct_section_api
  - cctv_api
  - device_api
  - ap_sensor_api
  - qrsticker_api
  - icon_api
  - models
  - websocket_event 


search: false

code_clipboard: true

meta:
  - name: description
    content: Documentation for iMOS API
---

# iMOS 현장관제 Renewal

휴랜 iMOS 현장관제 Renewal 을 위한 API 입니다.

## 변경 이력

버전 | 변경일        | 변경 내용
--------- |------------|----------
V0.1 | 2024-02-06 | 초안 배포
V0.2 | 2024-02-14 | 진행현황 바 정보 변경 ( pgrbar_no -> bar_no, bar_idx -> item_idx, pitem_no 삭제 )
   - | -          | 화면 설정을 위한 구성 정보 조회 구현 및 Swagger 추가
   - | -          | 공사 구간 마커 및 진행현황 구성 정보 조회/저장 구현 및 Swagger 추가 ( URL 변경 )
   - | -          | 기존 API 여부 및 미구현 여부 추가
   - | -          | 공사 구간 및 현황 API 섹션 분리 추가
V0.3 | 2024-02-15 | QR Sticker 리스트 및 정보 조회 구현. ( API 변경 )
   - | -          | AP Sensor 리스트 및 정보 조회 구현. ( API 변경 )
   - | -          | 디바이스 리스트 및 정보 조회 구현. ( API 변경 )
   - | -          | CCTV 리스트 및 정보 조회 구현. ( API 변경 )
   - | -          | 공사 현황 정보 리스트 조회 및 수정 구현 ( API 변경 )
V0.4 | 2024-02-19 | 현장 GPS 내 표시 fence 및 주요지점 정보 조회 구현 ( API 변경 )
   - | -          | 마커 아이콘 리스트 조회 API 추가 ( 신규 추가 )
   - | -          | BLE mode 화면 표시를 위한 구성 정보 조회 API 추가 ( API 변경 )
   - | -          | AP 센서 감지 근로자 검색 및 위치 조회 API 추가 ( API 변경 )
   - | -          | Model 내 마커 정보 상세 변경
V0.5 | 2024-02-20 | 현장 메인(조감도) 내 표시 정보 조회 HTTP Request URL 오류 수정 ( /ble -> /ble/main )
   - | -          | 현장 GPS 내 표시 fence 및 주요지점 정보 조회 HTTP Request method 오류 수정 ( POST -> GET )
   - | -          | 장비 및 근로자 GPS 위치 정보 조회 HTTP Request method 및 URL 오류 수정 ( POST -> GET, /monitor/4.2 -> monitor/4.1 )
   - | -          | 공사 진행 현황 정보 조회 API 추가, GPS 근로자 검색 추가
V0.6 | 2024-02-21 | IOT 장치(마커) 정보 내 state 및 상세 팝업을 위한 정보 추가. ( models 내 BleMarker > device_info 참고 )   
   - | -          | 진행현황바 정보 내 진행현황 수치 및 TBM 전/후방 cctv 정보 추가. ( models 내 BleProgressBar 참고 )
V0.7 | 2024-02-23 | IOT 장치(마커) 의 BLE 위치 정보 조회 API 추가 ( Device 내 위치 정보 조회 참고 )
   - | -          | BLE Mode 에서 CCTV Play 를 위한 CCTV 플로팅 팝업 관련 API 추가 ( BLE Monitor API 내 CCTV 플로팅 팝업 참고 ) 
   - | -          | Marker 셋팅시 화면 설정을 위한 구성 정보에 해당 현장의 메인 컴포넌트 정보 ( 이름 및 height, width ) 추가


## 미구현 리스트

1. QR 클릭시 당일 접근 이력 팝업을 위한 API 추가

## 인증 방식

### HTTP Basic 인증

로그인(token 정보 획득) 및 token 유효성 체크 등을 위해서는 HTTP Basic 인증을 수행하여야 합니다.

인증키는 전달받은 계정 정보를 통해 `Base64.encode(아아디:패스워드)` 수행하여 얻을 수 있습니다.

`Authorization: Basic {인증키}`

<aside class="success">
인증을 위한 Account 는 휴랜 개발팀에 문의하세요. 
</aside>

### 사용자 인증 ( Oauth2 )

사용자가 token 정보를 획득한 이후 권한이 필요한 API 호출시 access token 을 이용한 HTTP Bearer 인증을 수행하여야 합니다.

`Authorization: Bearer {사용자 accessToken}`

## API 기본 응답 Body

> 기본 응답 구조. 

```json
{
  "return_code": 0,
  "return_message": "SUCCESS",
  "context": {}
}
```

기본적인 API 의 응답 포맷은 JSON 입니다.

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |----------|--------- |---------
return_code | M | Number | 결과 코드. 0 : 성공, 그외 설패  
return_message | M | String | 결과 상세 설명             
context | O |   | 요청에 대한 응답 정보. 단순 value, Object, List 등 API 에 따라 타입이 다르며 없을 수도 있다.  

