# ApiDoc

ระบบใช้ WebSocket ในการรับส่งข้อมูลระหว่าง Client กับ Server

ตัวอย่างโครงสร้างข้อมูล JSON

```json
{
  "nonlive-data":
  [{
    "league":" UEFA CHAMPIONS LEAGUE QUALIFIERS",
    "tblNo":"02",
    "MATCH":
      [
        {
          "home":"ฮาโปเอล เบียร์ ชีวา","away":"ดินาโม ซาเกร็บ",
          "homeColor":"Red","awayColor":"Blue",
          "Score":"","time":"00:00",
          "MatchId":"rid_202045_3","row":"1",
          "hdp":{
            "hdp":"0-0.5","row":"1","home":"2.00","away":"1.80","homeStatus":"-","awayStatus":"-"
          },
          "goal":{
            "goal":"2.5-3","row":"1","over":"2.00","under":"1.80","overStatus":"-","underStatus":"-"
          },
          "fhdp":{
            "fhdp":"0.0","row":"1","home":"1.72","away":"2.11","homeStatus":"-","awayStatus":"-"
          },
          "fgoal":{
            "fgoal":"1.0","row":"1","over":"1.0","under":"1.80","overStatus":"-","underStatus":"-"
          }
        },{
          "home":"ฮาโปเอล เบียร์ ชีวา","away":"ดินาโม ซาเกร็บ","homeColor":"Red","awayColor":"Blue","score":"","time":"00:00","MatchId":"rid_202080_3","row":"2",
          "hdp":{"hdp":"0.0","row":"2","home":"1.60","away":"2.20","homeStatus":"-","awayStatus":"-"},
          "goal":{"goal":"2.5","row":"2","over":"1.72","under":"2.11","overStatus":"-","underStatus":"-"}
        },{
          "home":"เชริฟฟ์ ทิราโพล","away":"สเคนดิย่า","homeColor":"Red","awayColor":"Blue","score":"","time":"00:00","MatchId":"rid_202047_3","row":"3",
          "hdp":{"hdp":"1.0","row":"3","home":"1.90","away":"1.90","homeStatus":"-","awayStatus":"-"},
          "goal":{"goal":"2-2.5","row":"3","over":"2.00","under":"1.80","overStatus":"-","underStatus":"-"},
          "fhdp":{"fhdp":"0.5","row":"3","home":"2.11","away":"1.72","homeStatus":"-","awayStatus":"-"},
          "fgoal":{"fgoal":"0.5-1","row":"3","over":"0.5-1","under":"1.72","overStatus":"-","underStatus":"-"}
        }
      ]},
    {
      "league":"International Champions Cup",
      "tblNo":"03",
      "MATCH":"..."
    }]
}
```

สำหรับ Client ที่ใช้ต่อ API แนะนำให้ใช้ [WebSocket](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API/Writing_WebSocket_client_applications) ของ JavaScript

ตัวอย่าง Code Javascript WebSocket
```javascript
if ("WebSocket" in window) {
   console.log("WebSocket is supported by your Browser!");

   // ใส่ link สำหรับต่อ Socket
   var ws = new WebSocket("ws://localhost:9998/echo");

   ws.onopen = function() {
      // Web Socket is connected
      console.log("Message is sent...");
   };

   ws.onmessage = function (evt) { 
      let received_msg = evt.data;
      let objApi = JSON.parse(received_msg)
      // เอา objApi ไปใช้งานได้เลยครับ
      console.log(objApi);
   };

   ws.onclose = function() { 
      // websocket is closed.
      console.log("Connection is closed..."); 
   };
  } else {
     // The browser doesn't support WebSocket
     console.log("WebSocket NOT supported by your Browser!");
  }
}
```
