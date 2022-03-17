# Protocol实现 - JSON

JSON 格式是 CarProto 协议模式的直接映射。

## Data Type Conversion

The table below provides guidelines on how to convert the types specified in this document into JSON.

| Type                             | JSON 表示                                    |
| -------------------------------- | -------------------------------------------- |
| 所有核心类型（原始、注释、样式） | Object `{}`                                  |
| list<>                           | Array []                                     |
| map<>                            | Object `{"key": "value"}`                    |
| optional<T>                      | `null` or absent if not present, otherwise T |

## WebSocket Data Envelope

This bundles the CarProto messages in additional layer, allowing you to tell what type the message is, as well pass application specific messages on the same WebSocket connection as XVIZ data.

The fields of the message:

| Name   | Type     | Description                              |
| ------ | -------- | ---------------------------------------- |
| `type` | `string` | `namespace/type`                         |
| `data` | `Object` | The actual message CarProto or otherwise |

Name	Type	Description
type	string	namespace/type
data	Object	The actual message XVIZ or otherwise
Known namespaces:

xviz
The valid XVIZ message types are:

start - Sent from the client upon connection
metadata - Sent from the server upon connection or reconfiguration
transform_log - Sent from client to the server to request data
state_update - Sent from the server to the client, contains XVIZ the data
transform_log_done - Sent from server to the client to indicate completion
error - Sent from server to client indicate a failure of some kind

## Examples

The start message sent from the server to the client:

```json
{
    "type": "xviz/start",
    "data": {
        "version": "2.0.0",
        "session_type": "LIVE",
        "message_format": "JSON"
    }
}
```

The metadata message, the first message sent from the server to the client:

```
{
    "type": "xviz/metadata",
    "data": {
        "version": "2.0.0",
        ...
    }
}
```

A state update message sent from the server to the client:

```
{
    "type": "xviz/state_update",
    "data": {
        "update_type": "snapshot",
        "updates": [
            ...
        ]
    }
}
```



