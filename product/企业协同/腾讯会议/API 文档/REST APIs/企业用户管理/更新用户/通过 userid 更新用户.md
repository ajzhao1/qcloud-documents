## 接口描述
**描述**：使用 userid 更新企业用户，目前暂不支持 OAuth2.0 鉴权访问。
**调用方式**：PUT
**接口请求域名**：
```Plaintext
https://api.meeting.qq.com/v1/users/{userid}
```

## 输入参数
以下请求参数列表仅列出了接口请求参数，HTTP 请求头公共参数请参见签名验证章节的 [公共参数说明](https://cloud.tencent.com/document/product/1095/42413#.E5.85.AC.E5.85.B1.E5.8F.82.E6.95.B0)。

| 参数名称   | 必选 | 参数类型 | 参数描述                                                     |
| ---------- | ---- | -------- | ------------------------------------------------------------ |
| email      | 否   | String   | 邮箱地址，同企业内须保证唯一。                                              |
| area      | 否  | String   | 地区编码（默认值为86）。 |
| username   | 否   | String   | 新的用户昵称。                                                 |
| phone      | 否   | String   | 手机号码。                                                     |
| userid     | 否   | String   | 调用方用于标示用户的唯一 ID。<br>企业唯一用户标识说明：企业调用创建用户接口时传递的 userid 参数。 |
| avatar_url | 否   | String   | 头像地址。                                                     |
| staff_id        | 否   | String     | 员工工号。                                                     |
| job_title       | 否   | String     | 员工职位，长度范围为[0,96]个字符。                                     |
| entry_time      | 否   | Integer    | 入职时间。                                                     |
| department_list | 否   | String 数组 | 员工部门，暂只支持为用户分配1个部门。  |    


## 输出参数
无输出参数，成功返回空消息体，失败返回 [错误码](https://cloud.tencent.com/document/product/1095/43704) 和错误信息。


## 示例
#### 输入示例
```plaintext
PUT https://api.meeting.qq.com/v1/users/9527
{
  "username": "testusername"
}
```

#### 输出示例
更新用户成功，返回 Body 为空。
