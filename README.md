# vue-kequ
使用vue框架模仿可去app（旧版本），nodejs的express框架搭建后台服务

## 线上地址http://118.24.4.133:8888/

## 手机安装包下载地http://chenhaichao.cn/music.apk

## 目录结构
public----webpack打包后生成的文件

server----后台服务器

将webpack打包后生成的文件放进server文件夹中的upload文件夹内

## 开始
进入server文件夹执行命令
```
npm install
```

## 申请阿里云短信服务
https://dayu.aliyun.com/product/sms?spm=a3142.7791109.0.0.4eff69290s9sbZ

## 进入server/routes/message.js填写阿里云短信服务的秘钥
```js
// ACCESS_KEY_ID/ACCESS_KEY_SECRET 根据实际申请的账号信息进行替换
const accessKeyId = 'youKeyId'
const secretAccessKey = 'youAccessKey'
```

## 进入server/routes/send.js填写阿里云短信签名和使用的模板
```js
 //发送短信
smsClient.sendSMS({
    PhoneNumbers: req.body.phone,
    SignName: '阿里云短信签名',
    TemplateCode: '阿里云短信模板',
    TemplateParam: `{"code":"${num}"}`
})
```

## 运行
运行server.js文件
```
node server
```

## 浏览器预览
http://localhost:8888/