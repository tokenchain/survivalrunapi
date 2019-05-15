# survivalrunapi
the documentations for survival run

### wallet data

**return tag** `wallet_update`- **to user connection only** 资金信息更新, 这将被广播到所有连接器
**return data**

|字段|类型|空|默认|注释|
|---|---|---|---|---|
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


**return tag** `logout_passive`- 通过让其他具有相同帐户访问信息的人登录同一帐户来强制注销的信号。

The signal about the force log out by having other people having the same account access information to login the same account.

**return data**

|字段|类型|空|默认|注释|
|---|---|---|---|---|
|code |array  |是   |message code | 1331 |
|t |timestamp  |否       | int     | timestamp  |
|message    |string    |否 |  |"updated"      |


**return tag** `pot_ls_update`- **to all connections** 资金信息更新,这将被广播到所有连接器
**return data**

|字段|类型|空|默认|注释|
|---|---|---|---|---|
|p |array  |是   |PotStatus |累积奖金清单信息  the jackpot list information, see [Jackpot](https://www.showdoc.cc/214668919119866?page_id=1221150377505858 "Jackpot") |
|hash |string  |否       | int     | result hash 结果哈希  |
|xf |string  |否       | int     | factor  爆炸系数 |
|period |int  |否       | int     | period ID  游戏期间ID |
|t |timestamp  |否       | int     | timestamp  |
|message    |string    |否 |  |"updated"      |


This is the websocket interface api manual.

**request tag**  `snapshot_load`
the snapshot of the players. This request will have a limit return time of 10 seconds. It also means this request will be limited for 10s when this request is made.
球员的快照。 此请求的限制返回时间为10秒。 这也意味着在提出此请求时，此请求将限制为10秒。

**request content**
没有具体要求


**return tag**  `snapshot_load`
**return data**

|字段|类型|空|默认|注释|
|---|---|---|---|---|
|r |array |否   | []   |  玩家列表信息 the player list information, see** BDPlayer struct**   类型 [player struct](https://www.showdoc.cc/214668919119866?page_id=1222480864141365 "player struct")|
|p |array |否   | []   |  锅名单信息 the pot list information, see [**Pots struct **](https://www.showdoc.cc/214668919119866?page_id=1221150377505858 "**Pots struct **")  |
|s |integer |否   | []   | 当前状态 the current status, see  [**Status > Game status**](https://www.showdoc.cc/214668919119866?page_id=1220991323202801 "**Status > Game status**")|
|n |integer |否   | []   | the next game play period 下一个游戏时期 |
|h|array |否   | []   | the [history](https://www.showdoc.cc/214668919119866?page_id=1268176379946994 "history") consist of the game play from the recent 500 bets 历史包括最近500个赌注的游戏  |
|t    |timestamp    |否 |  |timestamp    时间戳     |
|message    |string    |否 |  |updated    更新     |

This is the websocket interface api manual.
这是websocket接口api手册。
**request tag**  无
**return tag** `bb_status`
when the game changes its state. all players will receive this message from the server. 当游戏改变其状态时。 所有玩家都将从服务器收到此消息。

**return data**

|字段|类型|空|默认|注释|
|---|---|---|---|---|
|s    |int(10)     |否 |  |  status, see Status      状态    |
|n   |int(10)     |否 |  | next game period number    下一场比赛期间的数字     |
|w    |int(10)     |否 |  |waiting interval number in seconds until the next status update    等待间隔数，以秒为单位，直到下一次状态更新     |
|t |timestamp |否   |    |   timestamp   |
|extras |array |否   |    |   only when s = 88, the array list of information about the button will display. see  **[Bet Control struct](https://www.showdoc.cc/214668919119866?page_id=1262387794891664 "Bet Control struct")** |

- 备注：When s = 88, BET_OPEN, a special key will show to reveal the button control
- 只有当s=88时，才会显示按钮的信息数组列表。看见**[Bet Control struct](https://www.showdoc.cc/214668919119866?page_id=1262387794891664 "Bet Control struct")** 
- 当s = 88，BET_OPEN时，将显示一个特殊键以显示按钮控件
- when each game is finish the new hash result will be generated from the pool and push to ws


This is the websocket interface api manual.
**request tag**   无
**return tag** `bb_tick`
when the user is successfully login to the game and the subscription of data is successful.
当用户成功登录游戏并且数据订阅成功时。

**return data**

|字段|类型|空|默认|注释|
|---|---|---|---|---|
|f |varchar(20) |否 |    |   bao dian factor  |

- 备注：自动推送

This is the websocket interface api manual.
**request tag**   无
**return tag** `bb_fx_ticker`
duration the course of the game there are special effects to be triggered by the serverside randomly. The given effect ID will be stated from 90 - 99. This will be given in the json data package along with the seed number.

备注
- 当用户成功登录游戏并且数据订阅成功时。
- 在游戏过程中，服务器端会随机触发一些特殊效果。给定的效果ID将从90-99声明。这将在json数据包中连同种子编号一起给出。

**return data**

|字段|类型|空|注释|
|---|---|---|---|
|fxx |integer |否 |    特殊效果编号  |
|seed |integer |否 |       种子编号  |

- 备注：自动推送

This is the websocket interface api manual.

### Subcription and unsubscription

**request tag**  `sub`

**request content**
```
{
 "add":"bb"
}
```
to start the game ticker subscription this command will automatically subscribe the following pushes: 开始游戏自动收录机订阅, 此命令将自动订阅以下推送:

- `bb_tick`
- `bb_fx_ticker`
- `pot_ls_update`
- `pot_update`
- `bb_status`

**return tag**  无
**return data**  无

**request tag** `unsub`
to stop the game ticker subscription. This command will cancel the following pushes. 停止游戏自动收报机订阅,此命令将取消以下推送:

- `bb_tick`
- `bb_fx_ticker`
- `pot_ls_update`
- `pot_update`
- `bb_status`



**return tag**  无
**return data**  无

### Ticker
This is the websocket interface api manual.
**request tag**   无
**return tag** `bb_tick`
when the user is successfully login to the game and the subscription of data is successful.
当用户成功登录游戏并且数据订阅成功时。

**return data**

|字段|类型|空|默认|注释|
|---|---|---|---|---|
|f |varchar(20) |否 |    |   bao dian factor  |

- 备注：自动推送

This is the websocket interface api manual.
**request tag**   无
**return tag** `bb_fx_ticker`
duration the course of the game there are special effects to be triggered by the serverside randomly. The given effect ID will be stated from 90 - 99. This will be given in the json data package along with the seed number.

备注
- 当用户成功登录游戏并且数据订阅成功时。
- 在游戏过程中，服务器端会随机触发一些特殊效果。给定的效果ID将从90-99声明。这将在json数据包中连同种子编号一起给出。

**return data**

|字段|类型|空|注释|
|---|---|---|---|
|fxx |integer |否 |    特殊效果编号  |
|seed |integer |否 |       种子编号  |

- 备注：自动推送

This is the websocket interface api manual.

**request tag**  `sub`

**request content**
```
{
 "add":"bb"
}
```
to start the game ticker subscription this command will automatically subscribe the following pushes: 开始游戏自动收录机订阅, 此命令将自动订阅以下推送:

- `bb_tick`
- `bb_fx_ticker`
- `pot_ls_update`
- `pot_update`
- `bb_status`

**return tag**  无
**return data**  无

**request tag** `unsub`
to stop the game ticker subscription. This command will cancel the following pushes. 停止游戏自动收报机订阅,此命令将取消以下推送:

- `bb_tick`
- `bb_fx_ticker`
- `pot_ls_update`
- `pot_update`
- `bb_status`



**return tag**  无
**return data**  无


### 投注 / 逃跑操作 / User Updates

This is the websocket interface api manual.

**request tag**  `bet`
to make the bet in the game will return 2 tags `bet_request` and `player_update`

在游戏中下注将返回2个标签`bet_request`和`player_update`

**request data**

|字段|类型|空|默认|注释|
|---|---|---|---|---|
|Amount |float |否   | []   |   the player list information, see BDPlayer struct   |
|Currency |string |否   | []   | the name of the coin |
|Time    |timestamp    |否 |  |timestamp         |


**return tag**  `bet_request`
**return data**

|字段|类型|空|默认|注释|
|---|---|---|---|---|
|code    |int    |否 |  | 1 = success , != 1 failure..         |
|message  |string    |否 |  | success/failure         |

- see the code. 

**request  tag** `escape`
to make the bet in the game will return 2 tags `escape_request` and `player_update`

在游戏中下注将返回2个标签`bet_request`和`player_update`


**return tag** `escape_request`
**return data**

|字段|类型|空|默认|注释|
|---|---|---|---|---|
|f    |float(10)      |否 |  | the factor or ticker when the escape is successful   逃脱成功时的因素或自动收报机   |
|message    |string    |否 |  |the message from the result "success/failure"  来自结果“成功/失败”的消息     |


