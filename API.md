# API 文档

### 注册
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



### 登录
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



### 获取用户信息
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


### 用户浏览记录
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



### 上传头像
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


### 用户交易记录
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

### 退出登录
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

// 提交提问
export const SUBMIT_QUESTION = params => { return axios.post(`${base}/question/ask_question`,qs.stringify(params));};

// 问题列表
export const QUESTION_LIST = params => {return axios.get(`${base}/question/question_list`, {params:params});};

// 获取问题详情
export const QUESTION_DETAIL = params => { return axios.get(`${base}/question/question_detail`,{params:params});};

http://localhost:3000/question/question_detail?q_id=65

// 回答问题
export const ANSWER = params => { return axios.post(`${base}/question/answer`,qs.stringify(params));};

// 回答问题
export const REPLY = params => { return axios.post(`${base}/question/reply`,qs.stringify(params));};

// 问题/答案 投票
export const VOTE = params => { return axios.post(`${base}/question/vote`,qs.stringify(params));};


//修改信息
export const CHANGE_INFO = params =>{ return axios.post(`${base}/users/changeinfo`,qs.stringify(params));};

//查询余额
export const GET_BALANCE = params =>{ return axios.get(`${base}/users/getbalance`,{params:params});};

//发表回访 
export const RETURNVISIT = params =>{ return axios.post(`${base}/returnvisit/returnvisit`,qs.stringify(params));};

//参加回访
export const JOIN_RETURNVISIT = params =>{ return axios.post(`${base}/returnvisit/join_returnvisit`,qs.stringify(params));};

//取消回访
export const CANCLE_RETURNVISIT = params =>{ return axios.post(`${base}/returnvisit/cancel_returnvisit`,qs.stringify(params));};

//回复列表
export const REPLY_LIST = params =>{ return axios.get(`${base}/question/reply_list`,{params:params});};


// 获取用户列表
export const GET_USER_LIST = params=>{ return axios.get(`${base}/users/getlist`,{params:params});};

// 提交文件
export const UPLOAD = params=> { return axios.post(`${base}/question/upload`),qs.stringify(params)};