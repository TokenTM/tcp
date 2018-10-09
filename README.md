# tcp
TokenTM共识链盟

## acess_token获取说明
合作方通过联系工作人员拿到相应的client_id和client_secret后，调用认证接口获取acess_token。

### 接口样例
> http://api.dj.gl/api/v1/oauth/token?grant_type=client_credentials&scope=select&client_id=${id}&client_secret=${secret}

**access_token规范服务oauth2规范，请参考标准规范。**

### 请求参数
|字段|类型|说明|
|----|----|----|
|client_id|string|客户端id|
|client_secret|string|客户端密钥|

### 响应参数
|字段|类型|说明|
|----|----|----|
|access_token|string|表示访问令牌，必选项。|
|token_type|string|表示令牌类型，该值大小写不敏感，必选项，可以是bearer类型或mac类型。|
|expires_in|long|表示过期时间，单位为秒。|
|scope|string|表示权限范围|

## 频道流接口
合作方根据提供的JS获取用户id，调用频道流接口可以获取相应频道内容列表。

### 接口样例
>http://api.dj.gl/api/v1/news_feed/index.json?userId=123&page=1&pageSize=6&access_token=${access_token}

### 请求参数
|字段|类型|说明|
|----|----|----|
|userId|string|用户id|
|page|int|页码|
|pageSize|int|条数|
|access_token|string|访问令牌|

### 响应参数
|字段|类型|说明|
|----|----|----|
|newsId|string|新闻id|
|templateType|int|模板类型，图文新闻是1|
|title|string|新闻标题|
|summary|string|新闻摘要|
|articleUrl|string|正文页url|
|publishTime|long|发布时间|
|shareImage|string|分享图|
|media|string|媒体|
|zhTitle|string|中文标题|
|translation|string|中文翻译|
|userInfo|string|用户信息，包括avatarUrl(头像), nickName(昵称)等属性|

### 正文的获取方式
1. 通过频道流接口中的正文url来直接进入正文页
2. 如果合作方希望自己定制正文页，可以使用我们提供的JS，获取正文页数据


