# opcode

所有opcode列表如下：

| CODE | 名称            | 客户端操作   | 描述                                                       |
| ---- | --------------- | ------------ | ---------------------------------------------------------- |
| 0    | Dispatch        | Receive      | 服务端进行消息推送                                         |
| 1    | Heartbeat       | Send/Receive | 客户端或服务端发送心跳                                     |
| 2    | Identify        | Send         | 客户端发送鉴权                                             |
| 6    | Resume          | Send         | 客户端恢复连接                                             |
| 7    | Reconnect       | Receive      | 服务端通知客户端重新连接                                   |
| 9    | Invalid Session | Receive      | 当identify或resume的时候，如果参数有错，服务端会返回该消息 |
| 10   | Hello           | Receive      | 当客户端与网关建立ws连接之后，网关下发的第一条消息          |
| 11   | Heartbeat ACK   | Receive      | 当发送心跳成功之后，就会收到该消息                         |