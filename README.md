# tcp
TokenTM共识链盟

## acess_token获取说明
合作方通过联系工作人员拿到相应的client_id和client_secret后，调用认证接口获取acess_token。

### 接口样例
```
http://api.dj.gl/api/v1/oauth/token?grant_type=client_credentials&scope=select&client_id=${id}&client_secret=${secret}
```
**access_token规范服务oauth2规范，请参考标准规范，access_token有过期时间限制，请定时获取。**

## 频道流接口
合作方根据提供的JS获取用户id，调用频道流接口可以获取相应频道内容列表。

### 接口样例
```
http://api.dj.gl/api/v1/news_feed/index.json?userId=123&page=1&pageSize=6&access_token=a8eedf59-48db-49ec-897e-14bc84f0564a
```

### 正文的获取方式
1. 通过频道流接口中的正文url来直接进入正文页
2. 如果合作方希望自己定制正文页，可以使用我们提供的JS，获取正文页数据
