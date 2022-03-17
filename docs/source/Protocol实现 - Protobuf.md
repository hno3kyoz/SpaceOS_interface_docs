# Protocol实现 - Protobuf协议格式

为了方便实现protobuf通讯。CarProto提供了一组 protobuf 文件。使用这些文件，您可以生成与 CarProto JSON 模式和 XVIZ 客户端兼容的 JSON 数据。

## TrasnferData

|           | 类型           | 说明     |
| --------- | -------------- | -------- |
| timeStamp | double         | 时间戳   |
| type      | string         | 类型     |
| datas     | TransferObject | 传输数据 |

## TransferObject

|              | 类型           | 说明     |
| ------------ | -------------- | -------- |
| functionName | string         | 方法名称 |
| attributes   | AttributesData | 成员数据 |

## AttributesData

|               | 类型   | 说明       |
| ------------- | ------ | ---------- |
| attributeName | string | 成员名称   |
| type          | string | 类型       |
| value         | string | 值         |
| imageData     | bytes  | 二进制数据 |
