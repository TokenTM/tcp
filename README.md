## 服务简介
区块链项目资讯流及舆情指数是投肯科技创建后打造的第一款产品。该产品充分发挥团队既有的互联网研发运营经验，收录近3000个全球范围内的区块链项目，抓取包括并不限于搜索引擎、垂直媒体、各大自媒体平台、社交网站、github、交易所等平台上与区块链相关的行业信息以及项目信息,通过内容智能处理,实现优质内容被结构化到每个项目中,每天更新近4000条中英文行业及项目资讯信息，输出项目资讯流和舆情波动指数，降低了区块链行业的信息不对称。

## 使用前必读[重要!!!]
### 所有使用该api产品的用户,如果选择调用jssdk来自行组装正文页的方式,务必在正文页文末显著位置标示版权:“平台合作方:TokenTM,领先的区块链信用分发管理平台”,否则将会被取消api权限!
此api属于免费产品,您可以将api中的内容嵌入到您合法的产品中,从而获取全面、准确并且免费的项目资讯服务.
投肯科技只负责提供内容智能处理技术,为行业的健康发展贡献力量,对可能涉及的版权或其它纠纷不负任何法律责任,请使用者自行斟酌其中的法律风险!
所有使用该api产品的用户,应自觉遵守规则,不恶意刷接口或者进行其它有损该产品的行为.


## acess_token获取说明
1.发邮件至 henryzheng@staff.token.tm ,1个工作日回复client_id和client_secret.发送邮件内容如下:

项目名称：您的项目名称

官网地址: 您的项目官网

联系方式： 您的手机号/微信

2.通过client_id和client_secret调用认证接口获取acess_token。


### 接口样例
> http://api.tokentm.net/api/v1/oauth/token?grant_type=client_credentials&scope=select&client_id=${id}&client_secret=${secret}

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

## 频道列表获取
获取频道列表，根据获取的频道信息，调用频道流接口获取对应的新闻。

### 接口样例
http://api.tokentm.net/api/v1/coin/list?access_token=${access_token}

### 请求参数
|字段|类型|说明|
|----|----|----|
|access_token|string|访问令牌|

### 响应参数
|字段|类型|说明|
|----|----|----|
|channelName|string|频道名|
|coinName|string|币种名称|
|coinNameCn|string|中文币种名称|
|coinNameEn|string|英文币种名称|
|symbol|string|标识符|

## 频道流接口
合作方根据下方提供的JSSDK获取用户id，调用频道流接口可以获取相应频道内容列表。

### 接口定义
>http://api.tokentm.net/api/v1/news_feed/${channelName}.json?userId=${userId}&page=${page}&pageSize=${pageSize}&access_token=${access_token}

### 请求参数
|字段|类型|说明|
|----|----|----|
|channelName|string|频道名，通过频道列表接口获取|
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

## 首页流接口
合作方根据下方提供的JSSDK获取用户id，调用频道流接口可以获取相应频道内容列表。

### 接口样例
>http://api.tokentm.net/api/v1/news_feed/index.json?userId=${userId}&page=${page}&pageSize=${pageSize}&access_token=${access_token}

## 频道流接口（英文版）
合作方根据下方提供的JSSDK获取用户id，调用频道流接口可以获取相应频道内容列表。

### 接口样例
>http://api.tokentm.net/api/v1/news_feed/en/index.json?userId=123&page=1&pageSize=6&access_token=${access_token}

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


## 正文的获取方式
1. 通过频道流接口中的正文url来直接进入正文页
2. 如果合作方希望自己定制正文页，可以使用我们下方提供的JSSDK，获取正文页数据

## jssdk使用文档
目前仅提供两个接口`getgluid`和`getArticle`
使用时请引入

```
<script type="text/javascript" src="https://h5uid.net/static/tcp/js/tokentm-sdk.js"></script>
```

### getgluid
用于获取用户id,
例如: window.userId = window.getgluid()

### getArticle(newsId, userId, access_token)(resolve, reject)
根据newsId获取文章详情
例: 
```
window.getArticle('ncced993270a84690b7cc7fa4eb23ed27', 'I5hAUrkL8ObpTqX/+hKUwg==', '4bc24b4d-a039-4e0d-8983-3fbe35f8b772')(console.log, console.error)
```

|字段|类型|说明|
|----|----|----|
|newsId|string|新闻id|
|userId|string|h5id请用`getgluid`获取并缓存|
|access_token|string|accessToken|
|resolve|function|成功回调|
|reject|function|失败回调|

### 正文字段说明
|字段|类型|说明|
|----|----|----|
|newsId|string|新闻id|
|templateType|int|模板类型，图文新闻是1|
|title|string|新闻标题|
|shareTitle|string|新闻标题|
|zhTitle|string|中文标题|
|summary|string|新闻摘要|
|articleUrl|string|正文页url|
|publishTime|long|发布时间|
|shareImage|string|分享图|
|media|string|媒体|
|content|string|正文，包含字段：[type(text, image, translation), info, imageInfo, tag]|



