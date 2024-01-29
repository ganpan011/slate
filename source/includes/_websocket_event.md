# WebSocket Event

## Websocket 접속

> Websocket 접속 샘플

```javascript
var sock = new SockJS("/ima/websocket");
sock.onclose = function(e) {
  console.info('winsock is close', e);
};
sock.onerror = function(e) {
  console.info('winsock is error', e);
}
var ws = Stomp.over(sock);

// 1. Websocket 접속
ws.connect({
    "X-Authorization": "[AccessToken 정보]"
  }, function(frame) {
  
    // 2. 특정 현장 이벤트 수신이 필요한 경우 설정
    ws.subscribe("/sub/workplace/"+[현장 관리번호(wp_no)], function(message) {
      // 메시지 수신 처리 추가
    });
  
    // 세션 아이디 얻어오기
    var url = ws.ws._transport.url;
    url = url.replaceAll("/websocket", "");
    url = url.substring(url.lastIndexOf('/') + 1);
    var session_id = url.replace(/^[0-9]+\//, "");
  
    // 3. 해당 세션으로 전달되는 이벤트 수신이 필요한 경우 설정
    ws.subscribe("/sub/user/"+session_id+"/alarm", function(message) {
      // 메시지 수신 처리 추가
    });

    // 4. (구) 이벤트 대상 해당 세션으로 전달되는 이벤트 수신이 필요한 경우 설정
    ws.subscribe("/sub/user/"+session_id, function(message) {
      // 메시지 수신 처리 추가
    });
  }.bind(this), function(error) {
    console.info("error", error);
    // DISCONNECTED.  필요에 따라 재접속 로직 필요
  }.bind(this)
);
```

로그인을 수행하여 얻은 인증키 ( Token ) 를 이용하여 websocket 접속을 수행합니다. websocket storm 을 지원

### Websocket URL

`/ima/websocket`

### Websocket 메세지 기본 포맷

> Websocket 메세지 기본 포맷

```json
{
  "msg_type" : 1,
  "action_type": 1,
  "publish_time" : 1683599451000,
  "context" : {
  }
}
```

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
msg_type	| M          | 메시지 타입
action_type | M          | 행위 유형. 0: 해제, 1: 발생, 2: 진행중
publish_time | M          | 이벤트 발행 시간
context | M          | 이벤트 관련 정보

#### 메세지 타입 

메세지 타입 코드 | 설명
--------- |------------
2	| 지능형 CCTV 이벤트
3	| 근로자 SOS 요청
4	| 유해물질 측정 센서 위험/해제 알림
6	| 기울기 위험/해제 알림
7	| 개구부 위험/해제 알림
8	| 풍속계 위험/해제 알림
11	| 소음측정기 위험/해제 알림
12	| 미세먼지 위험/해제 알림
13	| 불꽃감지기 위험/해제 알림
100	| 방송 장치 상태 변경 이벤트
201	| 근로자 긴급호출 요청
301 | 새로고침 요청 이벤트


## 새로고침 요청 이벤트

> 새로고침 요청 이벤트 전문 예시

```json
{
  "msg_type" : 301,
  "action_type": 1,
  "publish_time" : 1683599451000,
  "context" : {
    "force_refresh" : 1,
    "reason" : "패치에 의한 새로고침",
    "wp_no" : 1
  }
}
```

새로고침 요청 이벤트 수신시 브라우저 새로고침 수행 여부를 사용자에게 confirm 후 수행합니다.
수신시 옵션에 따라 질의없이 강제 수행도 가능하여야 합니다. 

<aside class="warning">
이벤트 미구현 
</aside>

항목 | 필수 여부(M/O) | 설명
--------- |------------| -----------
force_refresh | M          | 강제 새로고침 옵션. 0: 질의 후 수행, 1: 질의없이 수행
reason | M          | 새로고침 사유
wp_no | O          | 현장 관리번호. 지정된 경우 해당 현장에 접속해 있는 경우만 수행




