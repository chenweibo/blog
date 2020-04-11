---
title: 后台接口文档
date: 2020-04-10
---


::: tip 介绍
一个没有感情的文档。<br>

:::

## 用户授权

### 管理员登录

#### 请求URL:

- http://xx.com/api/admin/login

#### 请求方式：

- POST

#### 请求头：

|参数名|是否必须|类型|说明|
|:----    |:---|:----- |-----   |
|Content-Type |是  |string |请求类型： application/json   |


#### 请求参数:

|参数名|是否必须|类型|说明|
|:----    |:---|:----- |-----   |
|email |是  |string |邮箱格式   |
|password |是  |string | 密码    |
|device_name |是  |string | 设备类型 ，例：web   |


#### 返回示例:


```json
{
    "as": "Bearer",
    "token": "xxxxx"
}
```

#### 错误时返回:


```json
{
    "message": "The given data was invalid.",
    "errors": {
        "password": [
            "密码 不能为空。"
        ]
    }
}
```


### 用户信息


#### 请求URL:

- http://xx.com/api/admin/me

#### 请求方式：

- GET

#### 请求头：

|参数名|是否必须|类型|说明|
|:----    |:---|:----- |-----   |
|Content-Type |是  |string |请求类型： application/json   |
|Authorization |是  |string |Bearer + TOKEN  注意：Bearer 后要带一个空格   |




#### 返回示例:


```json
{
    "id": 1,
    "name": "admin",
    "email": "xxxx",
    "email_verified_at": null,
    "is_admin": true,
    "created_at": "2020-03-20T23:18:43.000000Z",
    "updated_at": "2020-03-20T23:18:43.000000Z"
}
```

#### 授权未通过返回:


```json
{
    "message": "Unauthenticated."
}
```
### 登出


#### 请求URL:

- http://xx.com/api/admin/loginOut/{id}


#### 请求方式：

- GET

#### 请求头：

|参数名|是否必须|类型|说明|
|:----    |:---|:----- |-----   |
|Content-Type |是  |string |请求类型： application/json   |


#### 请求参数:

|参数名|是否必须|参数|类型|说明|
|:---- |:---  |:---|:----- |-----   |
|id |是 |path |string |用户id   |

#### 返回示例:


```json
{
    "message": "ok"
}
```

## 上传管理


### 公共上传

 仅支持 'image/jpeg', 'image/png', 'image/bmp', 'image/gif'，最大限制4m.

#### 请求URL:

- http://xx.com/api/admin/upload/common

#### 请求方式：

- POST

#### 请求头：

|参数名|是否必须|类型|说明|
|:----    |:---|:----- |-----   |
|Content-Type |是  |string |请求类型： application/json   |
|Authorization |是  |string |Bearer + TOKEN  注意：Bearer 后要带一个空格   |

#### 请求参数:

|参数名|是否必须|类型|说明|
|:----    |:---|:----- |-----   |
|file |是  |form-data |   |

#### 返回示例:


```json
{
    "status": "success",
    "url": "http://127.0.0.1:8000/storage/file/2020/04/11/f75026fb647fe3e76ba69f9870cf1469.jpg",
    "origin_name": "QQ20190520-0.jpg"
}
```



### 文件上传

 支持 'image/jpeg', 'image/png', 'image/bmp', 'image/gif','pdf','zip','xlsx'最大限制5m

#### 请求URL:

- http://xx.com/api/admin/upload/file

#### 请求方式：

- POST

#### 请求头：

|参数名|是否必须|类型|说明|
|:----    |:---|:----- |-----   |
|Content-Type |是  |string |请求类型： application/json   |
|Authorization |是  |string |Bearer + TOKEN  注意：Bearer 后要带一个空格   |

#### 请求参数:

|参数名|是否必须|类型|说明|
|:----    |:---|:----- |-----   |
|file |是  |form-data |  |

#### 返回示例:


```json
{
    "status": "success",
    "url": "http://127.0.0.1:8000/storage/file/2020/04/11/f75026fb647fe3e76ba69f9870cf1469.jpg",
    "origin_name": "QQ20190520-0.jpg"
}
```



### 编辑器上传

支持 'image/jpeg', 'image/png', 'image/bmp', 'image/gif','pdf','zip','xlsx'最大限制5m

#### 请求URL:

- http://xx.com/api/admin/upload/editor

#### 请求方式：

- POST

#### 请求头：

|参数名|是否必须|类型|说明|
|:----    |:---|:----- |-----   |
|Content-Type |是  |string |请求类型： application/json   |
|Authorization |是  |string |Bearer + TOKEN  注意：Bearer 后要带一个空格   |

#### 请求参数:

|参数名|是否必须|类型|说明|
|:----    |:---|:----- |-----   |
|file |是  |form-data |   |

#### 返回示例:


```json
{
    "status": "success",
    "url": "http://127.0.0.1:8000/storage/file/2020/04/11/f75026fb647fe3e76ba69f9870cf1469.jpg",
    "origin_name": "QQ20190520-0.jpg"
}
```



### 缩略图上传

支持 'image/jpeg', 'image/png', 'image/bmp', 'image/gif','pdf','zip','xlsx'最大限制5m

#### 请求URL:

- http://xx.com/api/admin/upload/thumbnailUpload

#### 请求方式：

- POST

#### 请求头：

|参数名|是否必须|类型|说明|
|:----    |:---|:----- |-----   |
|Content-Type |是  |string |请求类型： application/json   |
|Authorization |是  |string |Bearer + TOKEN  注意：Bearer 后要带一个空格   |

#### 请求参数:

|参数名|是否必须|类型|说明|
|:----    |:---|:----- |-----   |
|file |是  |form-data |   |

#### 返回示例:


```json
{
    "status": "success",
    "url": "http://127.0.0.1:8000/storage/file/2020/04/11/f75026fb647fe3e76ba69f9870cf1469.jpg",
    "origin_name": "QQ20190520-0.jpg"
}
```


## 文件管理

### 模版目录

获取模版所在目录所有文件，resources/views。

#### 请求URL:

- http://xx.com/api/admin/file/template

#### 请求方式：
GET


#### 返回示例:


```json
{
    "list": [
        ".",
        "..",
        "c.blade.php"
    ],
    "path": "/Users/代码/网站相关/lavarel7/resources/views/home"   //存储绝对路径
}
```


### 存储目录

获取文件存储所在目录所有文件，storage目录。

#### 请求URL:

- http://xx.com/api/admin/file/storage

#### 请求方式：
GET


#### 返回示例:


```json
{
    "list": [
        ".",
        "..",
        ".DS_Store",
        ".gitignore",
        "file",
        "uploads"
    ],
    "path": "/Users/代码/网站相关/lavarel7/storage/app/public"   //存储绝对路径
}
```


### 公共目录

获取公共目录所有文件，public目录。

#### 请求URL:

- http://xx.com/api/admin/file/public

#### 请求方式：
GET


#### 返回示例:


```json
{
    "list": [
        "..",
    ],
    "path": "/Users/代码/网站相关/lavarel7/xxxx/public"   //存储绝对路径
}
```