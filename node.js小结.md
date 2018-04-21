## nodejs模块化开发
### 服务端API
1. server.js：用于开启服务器

```
// 服务器的开关：引入服务器，且开启服务器
const router = require('./router')
router.start();
```

2. router：根路由文件夹
- index.js：程序主入口模块
> 负责创建一个服务器,配置全局文件、session、body-parser模块，引入功能模块，并暴露端口。
- user.js：用户模块
> 负责用户的登陆、注册、修改个人信息等。将数据写入对应的数据库。
- product.js：上传文件模块
> 负责文件的上传，将数据写入对应的数据库。
- 待续...
3. utils：公共模块文件夹
- db.js：操作mongodb数据库的模块
> 负责数据库的增删查改功能，供其他模块调用。
- apiResult.js：向前端返回信息的模块

```
// 暴露状态的模块，供其他模块调用
module.exports = function(status, data, message){
    return {status, data, message};
}
```
### 端户端API
1. libs：公共js文件夹
- httpclient.js：Ajax的二次封装
> 负责http的请求方式和类型以及url的判定，供其他 js 调用。
