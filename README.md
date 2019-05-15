# survivalrunapi
the documentations for survival run



**return tag** `wallet_update`- **to user connection only** 资金信息更新, 这将被广播到所有连接器
**return data**

|字段|类型|空|默认|注释|
|:----    |:-------    |:--- |-- -|------      |
|data    |object  |否       | {}     | [Wallet Object](https://www.showdoc.cc/214668919119866?page_id=1289611891984243 "Wallet Object") |
|code    |int    |否 |  |1     |


** request tag** `start`

**简要描述：** 
- 将启动所有活动并通知该新用户的服务器。
- 注册接口

**参数：** 


**return  tag** `init`
 **返回示例**
 ```
{wid: "967226d3-8d7d-4910-9f00-963d46cad384", username: "Sentrypolar Shriek",…}
gp: {t: "x0x0x0x0x0x0x0x0x", e: 0, msg: "", msg_code: 100}
h: "3dd1bdb17fa85d8f3a48a80346895699518399d310a49ea879e864bd49ddde3407190b1f3bee9e1d0a1dc98a9ba0960d13077791635d7dd178a7b0ebc2969710"
history: {wins: 0, loss: 0, totalbets: 0, rate: 0}
i: 4714714635480448000
sq: {c1: 0, c2: 0, c3: 0, c4: 0, c5: 0}
username: "Sentrypolar Shriek"
wallet: [{c: "bbr", b: 0, l: 0}, {c: "thpc", b: 0, l: 0}, {c: "eth", b: 0, l: 0}]
wid: "967226d3-8d7d-4910-9f00-963d46cad384"
}
```


```
{

code: 1
data: {wid: "NAtpPduBCGPqAiIgfuNIUjEldFxjKSCejDlZHfhuwPqfsPcOCmZFcocDVuIdepnR", username: "SURE BIGX",…}
message: "success"

}
```


服务器将把标记ping推到客户端，以确保客户端仍然在线。如果客户端没有响应“pong”消息，则连接将自动解除。
>断网增加弹窗—目前断网是有5次重连机制的，5次重连不是，就会弹窗弹窗。但是问题是很多时候我检测不到是否断网。按理说应该是客户端像服务器定时发送ping的，服务器无返回就是断网了。但是这个项目是服务器端像客户端发送ping, 所以需要你来确定好方案。
6.选择币种—修复

Please make sure you have used the given js websocket script to handle websocket connection. By default there is a listener to detection connection stability. When is server is disconnected the reflected tag should board-cast to the entire app. The notification window should pop up to show the related information. During this pop up window, the attempt of tries on connection is 5. Until the connection is successful otherwise the pop up window should remain shown.

请确保已使用给定的JSWebSocket脚本处理WebSocket连接。默认情况下，有一个侦听器来检测连接稳定性。当服务器断开连接时，反射的标签将被强制转换到整个应用程序。应弹出通知窗口以显示相关信息。在此弹出窗口中，尝试连接的次数为5次。除非连接成功，否则弹出窗口应保持显示。



**New requirement** Only receive the "pong" from the socket and respond "ping" to the server. There is no need to make active "ping" request the server. 

*新要求**只接收来自套接字的“ping”，并对服务器响应“pong”。

**push tag**  `ping`

**request tag**  `pong`



此数据包与

- 比赛结束时
- 需要更新所有玩家钱包数据

**push tag** `profile_update`
**return data** 请参考详细结构  please refer to the detail structure for [Profile Update.](https://www.showdoc.cc/214668919119866?page_id=1220480815195825 "Profile Update.")


