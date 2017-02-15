
1.子账号是壹耘平台提供给会员管理其客户的账号，会员可以使用子账号的各个功能，轻松地管理每一个独立的客户。
2.子账号与指定的应用关联，请勿跨应用使用。
3.您可以使用主账号和子账号调用API,但是子账号不能访问主账号或者其他子账号的资源。

## 新增子账号

### 请求URL

```
POST ${BASE_URL}/management/subaccount
```

### 请求参数列表

| 参数                   | 有效值范围               | 说明                                       |
| ---------------------- | ------------------------ | ---------------------------------------- |
| `callbackUrl`          | *http url*                |用于子账号接收平台事件的url,必填|
| `remark`              | *字符串*                |备注，例如：备注您的客户的名称|


### 响应参数列表

| 参数     | 有效值范围   | 说明                            |
| ------ | ------- | ----------------------------- |
| `code` | 数字文本    | 状态码，全0表示正确                    |
| `msg`  | 文本        | 返回情况说明                        |
| `data` | JSON 对象   | 返回数据对象，参见[data对象属性列表](#data对象属性列表)|

### 参数详解

#### data对象属性列表

| 属性       | 有效值范围        | 说明       |
| -------- | ------------ | -------- |
| `id` | UUID | 子账号id |
| `certId` | 字符串 | 鉴权子账号 |
| `secretKey` | 字符串 | 鉴权密钥 |
| `appId` | UUID | 关联的应用Id |
| `parentId` | UUID | 主账号Id |
| `callbackUrl` | http url | 子账号回调地址 |
| `remark` | 字符串 | 备注 |

#### 示例

请求:
```http
POST ${BASE_URL}/management/subaccount HTTP/1.1
Host: api.yunhuni.com
Content-Type: application/json
Accept-Type: application/json
Content-Length: xxx
{
   "callbackUrl":"http://api.yoururl.com/callback",
   "remark":"客户1"
}
```

响应:
```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: xxx

{
  "code": "000000",
  "msg": "请求成功",
  "data": {
    "id":"rhreherherhgwgweg1304561",
    "certId":"erhehejtrtj",
    "secretKey":"gwer4h56e4h1eh",
    "appId":"gwegwegwehwherherh",
    "parentId":"41586tytymtyrth",
    "callbackUrl":"http://api.yoururl.com/callback",
    "remark":"客户1"
  }
}
```

## 修改子账号

### 请求URL

```
PUT ${BASE_URL}/management/subaccount/{id}
```

### 请求参数列表

| 参数                   | 有效值范围               | 说明                                       |
| ---------------------- | ------------------------ | ---------------------------------------- |
| `callbackUrl`          | *http url*                |用于子账号接收平台事件的url,必填|
| `remark`              | *字符串*                |备注，例如：备注您的客户的名称|


### 响应参数列表

| 参数     | 有效值范围   | 说明                            |
| ------ | ------- | ----------------------------- |
| `code` | 数字文本    | 状态码，全0表示正确                    |
| `msg`  | 文本        | 返回情况说明                        |
| `data` | JSON 对象   | 返回数据对象，参见[data对象属性列表](#data对象属性列表)|

### 参数详解

#### data对象属性列表

| 属性       | 有效值范围        | 说明       |
| -------- | ------------ | -------- |
| `id` | UUID | 子账号id |
| `certId` | 字符串 | 鉴权子账号 |
| `secretKey` | 字符串 | 鉴权密钥 |
| `appId` | UUID | 关联的应用Id |
| `parentId` | UUID | 主账号Id |
| `callbackUrl` | http url | 子账号回调地址 |
| `remark` | 字符串 | 备注 |

#### 示例

请求:
```http
PUT ${BASE_URL}/management/subaccount/rhreherherhgwgweg1304561 HTTP/1.1
Host: api.yunhuni.com
Content-Type: application/json
Accept-Type: application/json
Content-Length: xxx
{
   "callbackUrl":"http://api.yoururl.com/callback",
   "remark":"客户1"
}
```

响应:
```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: xxx

{
  "code": "000000",
  "msg": "请求成功",
  "data": {
    "id":"rhreherherhgwgweg1304561",
    "certId":"erhehejtrtj",
    "secretKey":"gwer4h56e4h1eh",
    "appId":"gwegwegwehwherherh",
    "parentId":"41586tytymtyrth",
    "callbackUrl":"http://api.yoururl.com/callback",
    "remark":"客户1"
  }
}
```


## 删除子账号

### 请求URL

```
DELETE ${BASE_URL}/management/subaccount/{id}
```

### 响应参数列表

| 参数     | 有效值范围   | 说明                            |
| ------ | ------- | ----------------------------- |
| `code` | 数字文本    | 状态码，全0表示正确                    |
| `msg`  | 文本        | 返回情况说明                        |
| `data` | boolean   | 成功true,失败false|

#### 示例

请求:
```http
DELETE ${BASE_URL}/management/subaccount/rhreherherhgwgweg1304561 HTTP/1.1
Host: api.yunhuni.com
Content-Type: application/json
Accept-Type: application/json
Content-Length: xxx
```

响应:
```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: xxx

{
  "code": "000000",
  "msg": "请求成功",
  "data": true
}
```