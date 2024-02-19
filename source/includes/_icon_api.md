# ICON

ICON 조회를 제공합니다.

## 마커 ICON 리스트 조회

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success",
  "context" : [ {
    "icon_type" : 1,
    "icon_usage" : 1,
    "icon_type_name" : "아이콘명",
    "icon_url" : "URL"
  } ]
}
```

마커 링크 아이콘 리스트 제공합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

신규 API 구현. [Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/%5B4.3%5D%20IMOS%20%ED%98%84%EC%9E%A5%EA%B4%80%EC%A0%9C%20ICON%20API%20/qrstickerListUsingGET_1)

### HTTP Request

`GET /imoa/api/icon/marker`

### Response Body

항목 | 필수 여부(M/O) | 데이터 타입 | 설명
--------- |------------| -----------| -----------
icon_type | M          | number | 아이콘 타입 관리번호
icon_usage | M          | number | 아이콘 사용처 코드 ( 0: 미지정, 1: 마커 )
icon_type_name | M          | number | 아이콘 타입명
icon_url | M          | string | 아이콘 URL


