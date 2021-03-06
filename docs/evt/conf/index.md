# 语音会议事件 (developing)

<!-- toc -->

## 会议创建事件

### 回调URL

```
POST {NOTIFY_URL}
```

### 参数列表

|参数                   | 有效值范围           | 说明
---------------------- | -------------------- | ----------------------------------------
| `action`               | **event_notify**         |事件标志：event_notify。 |
|`event`                | **conf.create.succ** |会议创建事件标志：conf.create.succ。可根据此字段识别不同事件
|`id`                   | UUID HEX 字符串      | 创建的会议id
| `subaccount_id`       | `UUID`           | 子账号id，事件所属子账号，如果为空表示是主账号的事件|
|`begin_time`           | 时间戳               | 开始时间
|`user_data`            | 字符串               | 用户自定义数据，内容由用户调用接口时上送，无内容时，返回`null`

## 会议结束事件

### 回调URL

```
POST {NOTIFY_URL}
```

### 参数列表

|参数                   | 有效值范围              | 说明
---------------------- | ----------------------- | ----------------------------------------
| `action`               | **event_notify**         |事件标志：event_notify。 |
|`event`                | **conf.end**            |会议创建事件标志：conf.end。可根据此字段识别不同事件
|`id`                   | UUID HEX 字符串         | 创建的会议id
| `subaccount_id`       | `UUID`           | 子账号id，事件所属子账号，如果为空表示是主账号的事件|
|`begin_time`           | 时间戳                  | 开始时间（会议创建出错时为`null`）
|`end_time`             | 时间戳                  | 结束时间（会议创建出错时为`null`）
|`error`                | 字符串                  | 会议创建失败的错误信息
|`user_data`            | 字符串                  | 用户自定义数据，内容由用户调用接口时上送，无内容时，返回`null`

## 加入会议事件

### 回调URL

```
POST {NOTIFY_URL}
```

### 参数列表

| 参数                     | 有效值范围                | 说明                                       |
| ---------------------- | -------------------- | ---------------------------------------- |
| `action`               | **event_notify**         |事件标志：event_notify。 |
| `event`                | **conf.joined**       |加入会议事件标志：conf.joined。可根据此字段识别不同事件 |
| `id`                   | UUID HEX 字符串         | 加入的会议id                               |
| `subaccount_id`       | `UUID`           | 子账号id，事件所属子账号，如果为空表示是主账号的事件|
| `join_time`            | 时间戳                  | 加入时间                                    |
| `call_id`              | UUID HEX 字符串         | 此次呼叫的 ID                           |
| `part_uri`             | 字符串                  | 手机号、座机号或VOIP帐号(未来)                           |
| `user_data`            | 字符串                  | 用户自定义数据，内容由用户调用接口时上送，无内容时，返回`null` 。     |

## 加入会议失败事件

### 回调URL

```
POST {NOTIFY_URL}
```

### 参数列表

| 参数                     | 有效值范围                | 说明                                       |
| ---------------------- | -------------------- | ---------------------------------------- |
| `action`               | **event_notify**         |事件标志：event_notify。 |
| `event`                | **conf.join.fail**       |加入会议事件标志：conf.join.fail。可根据此字段识别不同事件 |
| `id`                   | UUID HEX 字符串         | 会议id                               |
| `subaccount_id`       | `UUID`           | 子账号id，事件所属子账号，如果为空表示是主账号的事件|
| `time`                 | 时间戳                  | 时间                                    |
| `call_id`              | UUID HEX 字符串         | 此次呼叫的 ID                           |
| `part_uri`             | 字符串                  | 手机号、座机号或VOIP帐号(未来)                           |
| `user_data`            | 字符串                  | 用户自定义数据，内容由用户调用接口时上送，无内容时，返回`null` 。     |

## 离开会议事件

### 回调URL

```
POST {NOTIFY_URL}
```

### 参数列表

| 参数                     | 有效值范围                | 说明                                       |
| ---------------------- | -------------------- | ---------------------------------------- |
| `action`               | **event_notify**         |事件标志：event_notify。 |
| `event`                | **conf.quit**          |加入会议事件标志：conf.quit。可根据此字段识别不同事件 |
| `id`                   | UUID HEX 字符串          | 离开的会议id                               |
| `subaccount_id`       | `UUID`           | 子账号id，事件所属子账号，如果为空表示是主账号的事件|
| `join_time`            | 时间戳                   | 加入时间                                    |
| `quit_time`            | 时间戳                   | 离开时间                                    |
| `call_id`              | UUID HEX 字符串          | 欲离开会议返回的`呼叫的ID`                           |
| `part_uri`             | 字符串                   | 手机号、座机号或VOIP帐号(未来)                           |
| `user_data`            | 字符串                   | 用户自定义数据，内容由用户调用接口时上送，无内容时，返回`null` 。     |

## 会议放音结束事件

### 回调URL

```
POST {NOTIFY_URL}
```

### 参数列表

| 参数                     | 有效值范围                | 说明                                       |
| ---------------------- | -------------------- | ---------------------------------------- |
| `action`               | **event_notify**         |事件标志：event_notify。 |
| `event`                | **conf.play_end**      |会议放音结束事件标志：conf.play_end。可根据此字段识别不同事件 |
| `id`                   | UUID HEX 字符串          | 会议id                               |
| `subaccount_id`       | `UUID`           | 子账号id，事件所属子账号，如果为空表示是主账号的事件|
| `begin_time`           | 时间戳                   | 开始时间                                    |
| `end_time`             | 时间戳                   | 结束时间                                    |
| `user_data`            | 字符串                   | 用户自定义数据，内容由用户调用接口时上送，无内容时，返回`null` 。     |

## 会议录音结束事件

### 回调URL

```
POST {NOTIFY_URL}
```

### 参数列表

| 参数                     | 有效值范围                | 说明                                       |
| ---------------------- | -------------------- | ---------------------------------------- |
| `action`               | **event_notify**         |事件标志：event_notify。 |
| `event`                | **conf.record_end**      |会议放音结束事件标志：conf.record_end。可根据此字段识别不同事件 |
| `id`                   | UUID HEX 字符串          | 会议id                               |
| `subaccount_id`       | `UUID`           | 子账号id，事件所属子账号，如果为空表示是主账号的事件|
| `begin_time`           | 时间戳                   | 开始时间                                    |
| `end_time`             | 时间戳                   | 结束时间                                    |
| `user_data`            | 字符串                   | 用户自定义数据，内容由用户调用接口时上送，无内容时，返回`null` 。     |

