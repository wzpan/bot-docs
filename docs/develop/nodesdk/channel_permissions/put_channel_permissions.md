# 修改子频道权限

修改子频道权限。

## 使用示例

```javascript
async function demo() {
  let { data } = await client.channelPermissionsApi.putChannelPermissions(
    channelId,
    userId,
    // channelPermissions
    {
      remove: '1',
      add: '0',
    },
  );
}
```

::: warning 注意

- 要求操作人具有管理子频道的权限，如果是机器人，则需要将机器人设置为管理员。
- 参数包括 add 和 remove 两个字段，分别表示授予的权限以及删除的权限。要授予用户权限即把 add 对应位置 1，删除用户权限即把 remove 对应位置 1。当两个字段同一位都为 1，表现为删除权限。
- 本接口不支持修改可管理子频道权限。
  :::

## 参数说明

| 字段名             | 必填 | 类型                                      | 描述      |
| ------------------ | ---- | ----------------------------------------- | --------- |
| channelId          | 是   | string                                    | 子频道 ID |
| userId             | 是   | string                                    | 用户 ID   |
| channelPermissions | 是   | [ChannelPermissions](#channelpermissions) | 权限参数  |

### ChannelPermissions

| 字段名      | 类型                        | 描述                              |
| ----------- | --------------------------- | --------------------------------- |
| channel_id  | string                      | 子频道 ID                         |
| user_id     | string                      | 用户 ID                           |
| permissions | [permissions](#permissions) | 用户拥有的子频道权限，是个 string |

### Permissions

权限是 QQ 频道管理频道成员的一种方式，管理员可以对不同的人、不同的子频道设置特定的权限。用户的权限包括**个人权限**和**身份组权限**两部分，最终生效是取两种权限的并集。

权限使用位图表示，传递时序列化为十进制数值字符串。如权限值为`0x6FFF`，会被序列化为十进制`"28671"`。

| 权限         | 值                    | 描述                                                 |
| ------------ | --------------------- | ---------------------------------------------------- |
| 可查看子频道 | 0x0000000001 (1 << 0) | 目前仅支持`指定成员`可见类型，不支持`身份组`可见类型 |
| 可管理子频道 | 0x0000000002 (1 << 1) | 创建者、管理员、子频道管理员都具有此权限             |

##### 参数参考

| 字段名 | 类型   | 描述                               |
| ------ | ------ | ---------------------------------- |
| add    | string | 字符串形式的位图表示赋予用户的权限 |
| remove | string | 字符串形式的位图表示删除用户的权限 |

## 返回说明

返回 [ChannelPermissions](#channelpermissions) 对象。

## 返回示例

`data`：

```js
{
    channel_id: 'CHANNEL_ID',
    user_id: 'USER_ID',
    permissions: '0'
}
```
