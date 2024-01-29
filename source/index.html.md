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
  - cctv_api
  - device_api
  - ap_sensor_api
  - qrsticker_api
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
--------- |----------|--------- 
return_code | M | Number | 결과 코드. 0 : 성공, 그외 설패  
return_message | M | String | 결과 상세 설명             
context | O |   | 요청에 대한 응답 정보. 단순 value, Object, List 등 API 에 따라 타입이 다르며 없을 수도 있다.  






