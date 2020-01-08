# API 文档
<!-- MarkdownTOC -->

- [1 用户](#1-用户)
    - [1.1 注册](#11-注册)
        - [1.1.1 Asch 注册](#111-asch-注册)
    - [1.2 登录](#12-登录)
    - [1.3 获取用户信息](#13-获取用户信息)
    - [1.4 用户浏览记录](#14-用户浏览记录)
    - [1.5 上传头像](#15-上传头像)
    - [1.6 用户交易记录](#16-用户交易记录)
    - [1.7 退出登录](#17-退出登录)
    - [1.8 修改信息](#18-修改信息)
    - [1.9 查询余额](#19-查询余额)
- [2 问题](#2-问题)
    - [2.1 提交问题](#21-提交问题)
    - [2.2 问题列表](#22-问题列表)
    - [2.3 获取问题详情](#23-获取问题详情)
    - [2.4 回答问题](#24-回答问题)
    - [2.5 回复列表](#25-回复列表)
    - [2.6 回复回答](#26-回复回答)
    - [2.7 问题/答案/回访 投票](#27-问题答案回访-投票)
- [3 回访](#3-回访)
    - [3.1 发表回访](#31-发表回访)
    - [3.2 参加回访](#32-参加回访)
    - [3.3 取消回访](#33-取消回访)

<!-- /MarkdownTOC -->

<a id="1-用户"></a>
## 1 用户
<a id="11-注册"></a>
### 1.1 注册
接口地址：/users/register  
请求方式：POST  
支持格式：JSON  
接口备注：  
请求参数说明：

名称    | 类型 | 必填 | 说明
--------|------|------|-----
name    |string| Y | 
pwd     |string| Y |
mobile  |string| \ |
email   |string| \ | email、mobile二选一即可
aschSecret|string| Y | 调用Asch接口生成或直接输入
aschAddress|string| Y |

返回参数说明：  

名称 | 类型 | 说明
-----|------|------
code |int   | 200为正确，其他为错误
msg  |string| 返回正确为sucess，否则为错误信息
errType|string| 错误类型

请求示例：  
```
# 请求行
localhost:3000\users\register
# 请求体
{
    "name":"122",
    "pwd":"123456",
    "email":"122@qq.com",
    "aschSecret":"stamp galaxy liquid right math wonder invest lucky rail clock force leg",
    "aschAddress":"AJ7P8NNPAAwPZmxsEB29ZQyEHWbKcs9gVT"
}
```
  
JSON返回示例：
```
# 响应体
{
    "code": 200,
    "msg": "success",
    "data": ""
}
```

<a id="111-asch-注册"></a>
#### 1.1.1 Asch 注册
接口地址：/api/accounts/new  
请求方式：GET  
支持格式：JSON  
接口备注： 注意端口是Asch的端口4096，不是后台端口3000

返回参数说明：  

名称 | 类型 | 说明
-----|------|------
success |bool   | 
secret  |string| Asch的私钥，对应aschSecret
publicKey|string| Asch的公钥
address|string|  Asch的地址，对应aschAddress

请求示例：  
```
# 请求行
localhost:4096/api/accounts/new
```
  
JSON返回示例：
```
# 响应体
{
    "success": true,
    "secret": "drop company tired movie runway hammer name stone target knee ribbon left",
    "publicKey": "b12ef971ac609783b448aeaf4fe8f9e101b86a2c681b95f67517d5881e48471c",
    "privateKey": "6273f2f105c7f7006f95c0e89c33116be564ae4637bec2352ea065c59abb629fb12ef971ac609783b448aeaf4fe8f9e101b86a2c681b95f67517d5881e48471c",
    "address": "A6yFrRMfoGqtMU7hMMAT3yRV33mbnynGxV"
}
```


<a id="12-登录"></a>
### 1.2 登录
接口地址：/users/login  
请求方式：POST  
支持格式：JSON  
接口备注：通过**cookie**来维持登录  
请求参数说明：

名称    | 类型 | 必填 | 说明
--------|------|------|-----
user    |string| Y | email和mobie登录，不能用用户名 
pwd     |string| Y |

返回参数说明：  

名称 | 类型 | 说明
-----|------|------
code |int   | 200为正确，其他为错误
msg  |string| 返回正确为sucess，否则为错误信息
data |string| 用户名

请求示例：  
```
# 请求行
localhost:3000\users\login
# 请求体
{
    "user":"122@qq.com",
    "pwd":"123456"
}
```
  
JSON返回示例：
```
# 响应头
connect.sid=s%3Asgz-gLJCBMSqtx3rYwIcFAXi6No_gU8e.A6JwN9OfHofg5YgsBPg1v2T2u5Nxm3qW%2BAW2s2UGxkE
# 响应体
{
    "code": 200,
    "msg": "success",
    "data": {
        "uid": 10,
        "username": "122"
    }
}
```



<a id="13-获取用户信息"></a>
### 1.3 获取用户信息
接口地址：/users/login  
请求方式：GET  
支持格式： 
接口备注：通过**cookie**来维持登录  

返回参数说明：  

名称 | 类型 | 说明
-----|------|------
code |int   | 200为正确，其他为错误
msg  |string| 返回正确为sucess，否则为错误信息
data |string| 手机，邮箱，用户名，用户头像地址，创建时间

请求示例：  
```
# 请求行
localhost:3000\users\userinfo
# 请求头
connect.sid=s%3Asgz-gLJCBMSqtx3rYwIcFAXi6No_gU8e.A6JwN9OfHofg5YgsBPg1v2T2u5Nxm3qW%2BAW2s2UGxkE
```
  
JSON返回示例：
```
# 响应体
{
    "code": 200,
    "msg": "success",
    "data": {
        "mobile": null,
        "email": "122@qq.com",
        "username": "122",
        "create_time": "2020-01-07T12:31:00.000Z",
        "img_url": null
    }
}
```


<a id="14-用户浏览记录"></a>
### 1.4 用户浏览记录
接口地址：/users/history  
请求方式：GET  
支持格式： 
接口备注：通过**cookie**来维持登录  

返回参数说明：  

名称 | 类型 | 说明
-----|------|------
code |int   | 200为正确，其他为错误
msg  |string| 返回正确为sucess，否则为错误信息
data |string| 提问列表，回访列表

请求示例：  
```
# 请求行
localhost:3000\users\history
# 请求头
connect.sid=s%3Asgz-gLJCBMSqtx3rYwIcFAXi6No_gU8e.A6JwN9OfHofg5YgsBPg1v2T2u5Nxm3qW%2BAW2s2UGxkE
```
  
JSON返回示例：
```
# 响应体
{
    "code": 200,
    "data": {
        "returnvisits": [
            {
                "q_id": 10,
                "questionTitle": "2131",
                "tagName": [
                    "css"   //问题标签
                ],
                "up_votes": 1,  //点赞数
                "answer": 0,    //回答数
                "views": 9,     //浏览量
                "lastRespondent": "RObert", //作者
                "least_rv_time": 1,         //最短回访间隔
                "has_joined": "true",       //是否已经发表回访
                "join_time": "2019-11-28T09:55:19.000Z" //参加回访时间
            }
        ],
        "questions": [
            {
                "q_id": 66, 
                "questionTitle": "sas",
                "tagName": [
                    "茶叶"
                ],
                "up_votes": 0,
                "answer": 0,
                "views": 2,
                "lastRespondent": "RObert"
            }
        ]
    },
    "msg": "success"
}
```



<a id="15-上传头像"></a>
### 1.5 上传头像
接口地址：/users/upload_user_img  
请求方式：POST  
支持格式：JSON  
接口备注：  
请求参数说明：通过**cookie**来维持登录

名称    | 类型 | 必填 | 说明
--------|------|------|-----
imgsrc  |string| Y | 图像的base64编码，请压缩图像后上传

返回参数说明：  

名称 | 类型 | 说明
-----|------|------
code |int   | 200为正确，其他为错误
msg  |string| 返回正确为sucess，否则为错误信息
data |string| 头像地址

请求示例：  
```
# 请求行
localhost:3000\users\upload_user_img
#请求头
connect.sid=s%3Asgz-gLJCBMSqtx3rYwIcFAXi6No_gU8e.A6JwN9OfHofg5YgsBPg1v2T2u5Nxm3qW%2BAW2s2UGxkE
# 请求体
{
    "imgsrc":"data:image/jpeg;base64,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"
}
```
  
JSON返回示例：
```
# 响应体
{
    "code": 200,
    "msg": "success",
    "data": "http://localhost:9000/static/user/2020-01-07/20-59-14-276.jpg"
}
```


<a id="16-用户交易记录"></a>
### 1.6 用户交易记录
接口地址：/users/record  
请求方式：GET  
支持格式： 
接口备注：通过**cookie**来维持登录  

返回参数说明：  

名称 | 类型 | 说明
-----|------|------
code |int   | 200为正确，其他为错误
msg  |string| 返回正确为sucess，否则为错误信息
data |string| 交易的记录

请求示例：  
```
# 请求行
localhost:3000\users\record
# 请求头
connect.sid=s%3Asgz-gLJCBMSqtx3rYwIcFAXi6No_gU8e.A6JwN9OfHofg5YgsBPg1v2T2u5Nxm3qW%2BAW2s2UGxkE
```
  
JSON返回示例：
```
# 响应体
{
    "code": 200,
    "data": [
        {
            "money": 20000000,  //获得（消费）的代币数量
            "currency": "TTT",  //代币单位
            "create_time": "2019-11-28T10:49:52.000Z", //交易产生时间
            "type": "ANSWER_DEDLAY_REWARD_0",   //交易类型
            "description": "answerId 1"         //交易描述
        }
    ],
    "msg": "success"
}
```

交易type | 解释
---------|-----
POST_QUESTION | 文章即时奖励
POST_RETURNVISIT| 回访即时奖励
ANSWER_DEDLAY_REWARD_0|回答第一轮奖励结算
QUESTION_DELAY_REWARD_0|文章第一轮奖励结算
ANSWER_DEDLAY_REWARD_1|回答第二轮奖励结算
QUESTION_DELAY_REWARD_1|文章第二轮奖励结算

<a id="17-退出登录"></a>
### 1.7 退出登录
接口地址：/users/logout  
请求方式：GET  
支持格式：  
接口备注：通过**cookie**来维持登录  

返回参数说明：  

名称 | 类型 | 说明
-----|------|------
code |int   | 200为正确，其他为错误
msg  |string| 返回正确为sucess，否则为错误信息

请求示例：  
```
# 请求行
localhost:3000\users\login
# 请求头
connect.sid=s%3Asgz-gLJCBMSqtx3rYwIcFAXi6No_gU8e.A6JwN9OfHofg5YgsBPg1v2T2u5Nxm3qW%2BAW2s2UGxkE
```
  
JSON返回示例：
```
# 响应体
{
    "code": 200,
    "msg": "success",
}
```


<a id="18-修改信息"></a>
### 1.8 修改信息
接口地址：/users/changeinfo  
请求方式：POST  
支持格式：JSON  
接口备注：通过**cookie**来维持登录  
请求参数说明：

名称    | 类型 | 必填 | 说明
--------|------|------|-----
name    |string| Y | 
mobile  |string| Y |
email   |string| Y | 

返回参数说明：  

名称 | 类型 | 说明
-----|------|------
code |int   | 200为正确，其他为错误
msg  |string| 返回正确为sucess，否则为错误信息

请求示例：  
```
# 请求行
localhost:3000\users\changeinfo
# 请求头
connect.sid=s%3Asgz-gLJCBMSqtx3rYwIcFAXi6No_gU8e.A6JwN9OfHofg5YgsBPg1v2T2u5Nxm3qW%2BAW2s2UGxkE
# 请求体
{
    "name":"robert",
    "email":"123456",
    "mobile":"123456"
}
```
  
JSON返回示例：
```
# 响应体
{
    "code": 200,
    "msg": "success",
    "data": ""
}
```

<a id="19-查询余额"></a>
### 1.9 查询余额
接口地址：/users/getbalance  
请求方式：GET  
支持格式： 
接口备注：通过**cookie**来维持登录  

返回参数说明：  

名称 | 类型 | 说明
-----|------|------
code |int   | 200为正确，其他为错误
msg  |string| 返回正确为sucess，否则为错误信息
data |string| 余额，货币类型，Asch地址

请求示例：  
```
# 请求行
localhost:3000\users\getbalance
# 请求头
connect.sid=s%3Asgz-gLJCBMSqtx3rYwIcFAXi6No_gU8e.A6JwN9OfHofg5YgsBPg1v2T2u5Nxm3qW%2BAW2s2UGxkE
```
  
JSON返回示例：
```
# 响应体
{
    "code": 200,
    "msg": "success",
    "data": {
        "address": "ABuH9VHV3cFi9UKzcHXGMPGnSC4QqT2cZ5",
        "balance": "999999999910000000",
        "currency": "TTT"
    }
}
```

<a id="2-问题"></a>
## 2 问题
<a id="21-提交问题"></a>
### 2.1 提交问题
接口地址：/question/ask_question  
请求方式：POST  
支持格式：JSON 
接口备注：通过**cookie**来维持登录  

请求参数说明：

名称    | 类型 | 必填 | 说明
--------|------|------|-----
title   |string| Y | 
tag     |string| Y | 多个标签用逗号隔开
content |string| Y | 
least_rv_time| int | Y | 最短回访间隔 

返回参数说明：  

名称 | 类型 | 说明
-----|------|------
code |int   | 200为正确，其他为错误
msg  |string| 返回正确为sucess，否则为错误信息
data |string| 余额，货币类型，Asch地址

请求示例：  
```
# 请求行
localhost:3000\question\ask_question
# 请求头
connect.sid=s%3Asgz-gLJCBMSqtx3rYwIcFAXi6No_gU8e.A6JwN9OfHofg5YgsBPg1v2T2u5Nxm3qW%2BAW2s2UGxkE
# 请求体
{
    "title":"robert",
    "content":"123456",
    "tag":"tag1,tag2,tag3",
    "least_rv_time":3
}
```
  
JSON返回示例：
```
# 响应体
{
    "code": 200,
    "msg": "success",
}
```

<a id="22-问题列表"></a>
### 2.2 问题列表
接口地址：/question/question_list  
请求方式：GET  
支持格式：url参数 
接口备注：  

请求参数说明：

名称    | 类型 | 必填 | 说明
--------|------|------|-----
page    | int  | Y |  第一个问题的位置
pageSize| int  | Y |  问题数量。page=2&pageSize=10，表示获取id为11-20的问题 
tags    |string| N | 筛选条件。问题的标签需要包含其中之一
s_content|string| N | 筛选条件。问题需要包含的内容
order_type| int | Y | 问题排序方式：1 发帖时间 2 浏览量 3 无回答 4 回复时间

返回参数说明：  

名称 | 类型 | 说明
-----|------|------
code |int   | 200为正确，其他为错误
msg  |string| 返回正确为sucess，否则为错误信息
data |string| 问题列表
total|int   | 问题总数

请求示例：  
```
# 请求行
localhost:3000\question\question_list?page=1&pageSize=10&tags&s_content&order_type=1
```
  
JSON返回示例：
```
# 响应体
{
    "code": 200,
    "msg": "success",
    "data": [
        {
            "q_id": 67,
            "questionTitle": "robert",
            "tagName": [
                "tag1",
                "tag2",
                "tag3"
            ],
            "up_votes": 0,  //点赞数
            "answer": 0,    //回答数
            "views": 0,     //浏览量
            "lastRespondent": "robert"
        },
        {
            "q_id": 66,
            "questionTitle": "sas",
            "tagName": [
                "茶叶"
            ],
            "up_votes": 0,
            "answer": 0,
            "views": 2,
            "lastRespondent": "robert"
        }
    ],
    "total": 20
}
```

<a id="23-获取问题详情"></a>
### 2.3 获取问题详情
接口地址：/question/question_detail  
请求方式：GET  
支持格式：url参数 
接口备注：  

请求参数说明：

名称    | 类型 |必填| 说明
--------|------|----|-----
q_id    | int  | Y  |  

返回参数说明：  

名称 | 类型 | 说明
-----|------|------
code |int   | 200为正确，其他为错误
msg  |string| 返回正确为sucess，否则为错误信息
data |string| 问题详情，回答列表，回访列表
join_time|string| null为未参加该问题的回访，否则为参加时间

请求示例：  
```
# 请求行
localhost:3000\question\question_detail?q_id=2
```
  
JSON返回示例：
```
# 响应体
{
    "code": 200,
    "message": "sucess",
    "data": {
        "questionDetail": {
            "title": "Question1",
            "content": "this is question one",
            "img_url": "http://localhost:9000/static/user/2020-01-07/20-59-14-276.jpg", //用户头像地址
            "username": "robert",
            "least_rv_time": 0,
            "tags": "what is it",
            "up_votes": 0,
            "down_votes": 0,
            "create_time": "1999-01-01T16:00:00.000Z",
            "last_res_time": "2000-08-07T16:00:00.000Z", //最后回复时间
            "last_res_id": 1
        },
        "answerList": [
            {
                "answerId": 1,
                "username": "robert",
                "img_url": "http://localhost:9000/static/user/2020-01-07/20-59-14-276.jpg",
                "answer": "errwerw", //回答内容
                "createTime": "2019-11-21T09:01:01.000Z",
                "up_votes": 100,
                "down_votes": 0  //点踩
            },
            {
                "answerId": 3,
                "username": "robert",
                "img_url": "http://localhost:9000/static/user/2020-01-07/20-59-14-276.jpg",
                "answer": "<p>12311456</p>",
                "createTime": "2019-10-11T07:05:32.000Z",
                "up_votes": 0,
                "down_votes": 0
            }
        ],
        "returnvisitList": [
            {
                "returnvisitId": 1,
                "username": "robert",
                "img_url": "http://localhost:9000/static/user/2020-01-07/20-59-14-276.jpg",
                "returnvisit": "123456",
                "createTime": "2018-01-09T08:00:00.000Z",
                "up_votes": 0,
                "down_votes": 0
            },
            {
                "returnvisitId": 5,
                "username": "robert",
                "img_url": "http://localhost:9000/static/user/2020-01-07/20-59-14-276.jpg",
                "returnvisit": "",
                "createTime": "2019-11-01T08:55:09.000Z",
                "up_votes": 0,
                "down_votes": 0
            }
        ],
        "join_time": "2019-11-03T02:09:11.000Z" 
    }
}
```


<a id="24-回答问题"></a>
### 2.4 回答问题
接口地址：/question/answer  
请求方式：POST  
支持格式：JSON 
接口备注：  **cookie**

请求参数说明：

名称    | 类型 |必填| 说明
--------|------|----|-----
q_id    | int  | Y  |  
content |string| Y  |

返回参数说明：  

名称 | 类型 | 说明
-----|------|------
code |int   | 200为正确，其他为错误
msg  |string| 返回正确为sucess，否则为错误信息

请求示例：  
```
# 请求行
localhost:3000\question\answer
# 请求头
connect.sid=s%3Asgz-gLJCBMSqtx3rYwIcFAXi6No_gU8e.A6JwN9OfHofg5YgsBPg1v2T2u5Nxm3qW%2BAW2s2UGxkE
# 请求体
{
    "content":"11111",
    "q_id":1
}
```
  
JSON返回示例：
```
# 响应体
{
    "code": 200,
    "message": "sucess"
}
```

<a id="25-回复列表"></a>
### 2.5 回复列表
接口地址：/question/reply_list  
请求方式：GET  
支持格式：url参数 
接口备注：  

请求参数说明：

名称    | 类型 |必填| 说明
--------|------|----|-----
a_id    | int  | Y  |  

返回参数说明：  

名称 | 类型 | 说明
-----|------|------
code |int   | 200为正确，其他为错误
msg  |string| 返回正确为sucess，否则为错误信息
data |string| 回复列表

请求示例：  
```
# 请求行
localhost:3000\question\reply_list?a_id=37
```
  
JSON返回示例：
```
# 响应体
{
    "code": 200,
    "msg": "success",
    "data": [
        {
            "username": "robert",
            "content": "11111",
            "createTime": "2020-01-08T04:36:21.000Z"
        }
    ],
    "total": 1
}  
```

<a id="26-回复回答"></a>
### 2.6 回复回答
接口地址：/question/reply  
请求方式：POST  
支持格式：JSON 
接口备注：   **cookie**

请求参数说明：

名称    | 类型 |必填| 说明
--------|------|----|-----
a_id    | int  | Y  |  
content |string| Y  |

返回参数说明：  

名称 | 类型 | 说明
-----|------|------
code |int   | 200为正确，其他为错误
msg  |string| 返回正确为sucess，否则为错误信息

请求示例：  
```
# 请求行
localhost:3000\question\reply
# 请求头
connect.sid=s%3Asgz-gLJCBMSqtx3rYwIcFAXi6No_gU8e.A6JwN9OfHofg5YgsBPg1v2T2u5Nxm3qW%2BAW2s2UGxkE
# 请求体
{
    "content":"11111",
    "a_id":1
}
```
  
JSON返回示例：
```
# 响应体
{
    "code": 200,
    "message": "sucess"
}
```

<a id="27-问题答案回访-投票"></a>
### 2.7 问题/答案/回访 投票
接口地址：/question/vote  
请求方式：POST  
支持格式：JSON 
接口备注：   **cookie**

请求参数说明：

名称    | 类型 |必填| 说明
--------|------|----|-----
q_id    | int  | \  | 
a_id    | int  | \  | 二选一，对应type
vote    | int | Y  | 1 为点赞，-1 为点踩
type | int | Y  | 1 为问题，2 为回答，3 为回访

返回参数说明：  

名称 | 类型 | 说明
-----|------|------
code |int   | 200为正确，其他为错误
msg  |string| 返回正确为sucess，否则为错误信息

请求示例：  
```
# 请求行
localhost:3000\question\vote
# 请求头
connect.sid=s%3Asgz-gLJCBMSqtx3rYwIcFAXi6No_gU8e.A6JwN9OfHofg5YgsBPg1v2T2u5Nxm3qW%2BAW2s2UGxkE
# 请求体
{
    "vote":1,
    "type":1,
    "q_id":1
}
```
  
JSON返回示例：
```
# 响应体
{
    "code": 200,
    "message": "sucess"
}
```

<a id="3-回访"></a>
## 3 回访
<a id="31-发表回访"></a>
### 3.1 发表回访 
接口地址：/returnvisit/returnvisit  
请求方式：POST  
支持格式：JSON 
接口备注：  **cookie**

请求参数说明：

名称    | 类型 |必填| 说明
--------|------|----|-----
q_id    | int  | Y  |  
content |string| Y  |

返回参数说明：  

名称 | 类型 | 说明
-----|------|------
code |int   | 200为正确，其他为错误
msg  |string| 返回正确为sucess，否则为错误信息

请求示例：  
```
# 请求行
localhost:3000\returnvisit\returnvisit
# 请求头
connect.sid=s%3Asgz-gLJCBMSqtx3rYwIcFAXi6No_gU8e.A6JwN9OfHofg5YgsBPg1v2T2u5Nxm3qW%2BAW2s2UGxkE
# 请求体
{
    "content":"11111",
    "q_id":1
}
```
  
JSON返回示例：
```
# 响应体
{
    "code": 200,
    "message": "sucess"
}
```

<a id="32-参加回访"></a>
### 3.2 参加回访
接口地址：/returnvisit/join_returnvisit  
请求方式：POST  
支持格式：JSON 
接口备注：  **cookie**

请求参数说明：

名称    | 类型 |必填| 说明
--------|------|----|-----
q_id    | int  | Y  |  

返回参数说明：  

名称 | 类型 | 说明
-----|------|------
code |int   | 200为正确，其他为错误
msg  |string| 返回正确为sucess，否则为错误信息

请求示例：  
```
# 请求行
localhost:3000\returnvisit\join_returnvisit
# 请求头
connect.sid=s%3Asgz-gLJCBMSqtx3rYwIcFAXi6No_gU8e.A6JwN9OfHofg5YgsBPg1v2T2u5Nxm3qW%2BAW2s2UGxkE
# 请求体
{
    "q_id":1
}
```
  
JSON返回示例：
```
# 响应体
{
    "code": 200,
    "message": "sucess"
}
```

<a id="33-取消回访"></a>
### 3.3 取消回访
接口地址：/returnvisit/cancel_returnvisit  
请求方式：POST  
支持格式：JSON 
接口备注：  **cookie**

请求参数说明：

名称    | 类型 |必填| 说明
--------|------|----|-----
q_id    | int  | Y  |  

返回参数说明：  

名称 | 类型 | 说明
-----|------|------
code |int   | 200为正确，其他为错误
msg  |string| 返回正确为sucess，否则为错误信息

请求示例：  
```
# 请求行
localhost:3000\returnvisit\cancel_returnvisit
# 请求头
connect.sid=s%3Asgz-gLJCBMSqtx3rYwIcFAXi6No_gU8e.A6JwN9OfHofg5YgsBPg1v2T2u5Nxm3qW%2BAW2s2UGxkE
# 请求体
{
    "q_id":1
}
```
  
JSON返回示例：
```
# 响应体
{
    "code": 200,
    "message": "sucess"
}
```


