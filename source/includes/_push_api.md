# 기타 API


### PUSH 전송

> 요청 전문 예시

```JSON
{
  "mb_no_list" : [
    1
  ],
  "wp_no" : 1,
  "pu_subject" : "Push 제목",
  "pu_content" : "Push 내용",
  "pu_chk" : 0
}
```

> 응답 전문 예시

```JSON
{
  "return_code" : 0,
  "return_message" : "Success"
}
```

사용자에게 Push 전송 제공합니다.

<aside class="notice">
사용자 인증 ( HTTP Bearer ) 필요 
</aside>

[Swagger](https://ras.hulandev.co.kr/imoa/swagger-ui/index.html#/Push%20%EC%A0%84%EC%86%A1%20%EA%B4%80%EB%A6%AC/requestUsingPOST_1)

### HTTP Request

`POST /imoa/api/push/send`

### Request Body

항목 | 필수 여부(M/O) | 데이터 타입       | 설명
--------- |------------|--------------| -----------
mb_no_list | M          | List<number> | Push 수신 대상 mb_no 리스트
wp_no | M          | number       | 현장 관리번호
pu_subject | M          | string       | Push 제목
pu_content | M          | string       | Push 내용
pu_chk | M          | number       | 수신시 사이렌 여부. 0: 아님, 1: 사이렌

