---
layout: post
title: 天眼查接口文档
---

* 目录
{:toc #chenxsan}

<!-- #天眼查接口文档 -->
## <a name="_1" id="_1">错误代码说明</a>

|     代码    | 说明	  |
| ------------ |:--------:|
| 0      |  请求成功 |
| -1     |  请求返回结果无数据 |
| 300000     | 请求警告  |
| 300001     |  请求失败 |


## 按企业关键字模糊查询返回列表

### url

<http://api.tianyancha.com/services/v3/open/search.json>

### sample

<http://api.tianyancha.com/services/v3/open/search.json?keyword=百度>

### 支持格式

	JSON

### HTTP请求方式

	GET

### 是否需要授权

	是
	需要进入ip白名单

### 访问授权限制

	访问级别：普通接口

### 请求参数

|         | 必选   | 类型及范围	  | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| keyword      | true | String |搜索的关键词					|


### 注意事项

	请求参数需要URLEncode。

### 返回结果
	JSON示例

```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "total": 9622,
    "num": 20,
    "items": [
      {
        "id": 22822,
        "name": "北京<em>百度</em>网讯科技有限公司",
        "estiblishTime": "2001-06-05",
        "legalPersonName": "梁志祥"
      },
      {
        "id": 23289175,
        "name": "<em>百度</em>在线网络技术（北京）有限公司",
        "estiblishTime": "2000-01-18",
        "legalPersonName": "向海龙"
      },
      {
        "id": 11364828,
        "name": "<em>百度</em>（香港）有限公司",
        "estiblishTime": "1970-01-01",
        "legalPersonName": ""
      },
	...
    ]
  }
}
```

#### 关于错误返回值与错误代码，参见<a href="#_1">错误代码说明</a>

### 返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码			|
| reason     | String |错误原因|
| result     | Object| 返回内容|
| total     | int |查询总条数|
| num     | int |本次查询返回条数|

#### items 中字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| id   | long |公司的id标识，用于查询			|
| name     | String |公司名，其中<em>标签中是命中的关键字|
| estiblishTime     | String |注册时间|
| legalPersonName     | String |法人名称|

### 相关问题

关键字可以为公司注册号，统一信用代码，组织结构代码


## 按企业关键字模糊查询返回列表（version2）

### url

<http://api.tianyancha.com/services/v3/open/searchV2.json>

### sample

<http://api.tianyancha.com/services/v3/open/searchV2.json?keyword=百度>

### 支持格式

	JSON

### HTTP请求方式

	GET

### 是否需要授权

	是
	需要进入ip白名单

### 访问授权限制

	访问级别：普通接口

### 请求参数

|         | 必选   | 类型及范围	  | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| keyword      | true | String |搜索的关键词					|


### 注意事项

	请求参数需要URLEncode。

### 返回结果
	JSON示例

```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "total": 10208,
    "num": 20,
    "items": [
      {
        "webSite": [
          "www.<em>百度</em>网站.cn",
          "www.baidu-jpg.com",
          "www.baiduhui.com",
          "www.baidu-bank.com",
          "www.baidu.mobi",
          "www.bdysite.com",
          "www.cloudajs.org",
          "www.duapp.com",
          "www.umaz.cn",
          "..."
        ],
        "regStatus": "开业",
        "creditCode": "91110000802100433B",
        "companyName": "北京百度网讯科技有限公司"
      },
      {
        "webSite": [
          "www.baidu.com"
        ],
        "regStatus": "开业",
        "creditCode": "91110108717743469K",
        "companyName": "百度在线网络技术（北京）有限公司"
      },
      {
        "webSite": [
          "www.duokoo.com.cn",
          "www.duokoo.net",
          "www.duokoo.mobi",
          "www.duoku.com",
          "www.duokoo.cn",
          "www.kk.com",
          "www.duoku.com.cn"
        ],
        "regStatus": "开业",
        "creditCode": "91110108080482723H",
        "companyName": "北京百度多酷科技有限公司"
      },
      ...
    ]
  }
}
```

#### 关于错误返回值与错误代码，参见<a href="#_1">错误代码说明</a>

### 返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码			|
| reason     | String |错误原因|
| result     | Object| 返回内容|
| total     | int |查询总条数|
| num     | int |本次查询返回条数|

#### items 中字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| id   | Long |公司id（用于其他查询）      |
| webSite   | JsonArray |公司的网址			|
| companyName     | String |公司名，其中<em>标签中是命中的关键字|
| regStatus     | String |状态|
| creditCode     | String |统一信用代码|

### 相关问题

关键字可以为公司注册号，统一信用代码，组织结构代码



## 公司详情,（根据id）

### url

<http://api.tianyancha.com/services/v3/open/w/companydetail.json>

### sample

正常:<http://api.tianyancha.com/services/v3/open/w/companydetail.json?id=22822>
带经营异常：<http://api.tianyancha.com/services/v3/open/w/companydetail.json?id=1073117874>
带分支机构：<http://api.tianyancha.com/services/v3/open/w/companydetail.json?id=376321715>

### 支持格式

	JSON

### HTTP请求方式

	GET

### 是否需要授权

	是
	需要进入ip白名单

### 访问授权限制

	访问级别：普通接口

### 请求参数

|         | 必选   | 类型及范围	  | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| id      | true | long |公司id，通过查询接口获取					|

### 注意事项

	请求参数需要URLEncode。


### 返回结果

	JSON示例

```
{
    "baseInfo": {
        "fromTime": "Jul 28, 2003 12:00:00 AM",
        "type": 1,
        "categoryScore": 6522,
        "regNumber": "510900000021844",
        "percentileScore": 9625,
        "phoneNumber": "0825-5807992",
        "regCapital": "2000 万",
        "regInstitute": "遂宁市工商局",
        "name": "遂宁市中通实业集团有限公司",
        "regLocation": "遂宁市开发区明月路139号永耀大厦二楼",
        "approvedTime": "Apr 28, 2016 12:00:00 AM",
        "industry": "商务服务业",
        "businessScope": "项目投资（国家有专项规定的除外）；商业贸易；机械设备租赁。(不得从事非法集资、吸收公众资金等金融活动)。",
        "estiblishTime": "Jul 28, 2003 12:00:00 AM",
        "regStatus": "存续",
        "legalPersonName": "杨耀华",
        "toTime": "Dec 31, 2999 12:00:00 AM",
        "actualCapital": "",
        "websiteList": [
            "http://www.snztjt.com/"
        ],
        "companyOrgType": "有限责任公司(自然人投资或控股)",
        "base": "sc",
        "updateTimes": "Aug 23, 2016 3:12:15 PM",
        "companyType": 201,
        "creditCode": "91510900752317692H",
        "companyId": 6318270
    },
    "investorList": [
        {
            "amount": 20,
            "name": "秦霞"
        },
    ...
    ],
    "investList": [
        {
            "amount": 400,
            "id": 7292014,
            "category": "商务服务业",
            "name": "四川坤道资产管理有限公司",
            "base": "sc",
            "regStatus": "存续",
            "legalPersonName": "段吉瑞",
            "pencertileScore": 8042
        },
        ...
    ],
    "staffList": [
        {
            "name": "赵冰",
            "typeJoin": [
                "董事"
            ]
        },
        ...
    ],
    "branchList": [],
    "comChanInfoList": [
        {
            "changeItem": "经营范围变更（含业务范围变更）",
            "contentBefore": "经营范围:项目投资（国家有专项规定的除外）;商业贸易;机械设备租赁。（以上经营范围不含前置许可项目;后置许可项目凭许可证或审批文件经营）。",
            "contentAfter": "经营范围:项目投资（国家有专项规定的除外）;商业贸易;机械设备租赁。(不得从事非法集资、吸收公众资金等金融活动)。",
            "changeTime": "2016-04-28"
        }
    ],
    "comAbnoInfoList": [],
    "annuRepYearList": [
        {
            "id": 249277235,
            "phoneNumber": "0825-5807992",
            "reportYear": "2015"
        },
        ...
    ]
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码			|
| reason     | String |错误原因|
| result     | Object| 返回内容|

#### baseInfo返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| updatetime   | long |更新时间			|
| fromTime     | long |营业期限开始时间|
| type     | int |类型（1为公司，2为自然人）|
| categoryScore     | int |行业评分|
| id     | long |公司id（查询用）|
| regNumber|String|工商注册号|
| percentileScore| int |公司评分|
| allCount| map |公司信息中包含的各个list的数量|
| branchCount| int |分支机构数量|
| investCount| int |投资数量|
| comAbnoInfo| int |经营异常数量|
| companyBidCount| int |招投标数量|
| copyrightRegCount| int |著作权数量|
| empCount| int |招聘数量|
| investorCount| int |股东数量|
| staffCount| int |高管数量|
| comChanInfoCount| int |变更信息数量|
| annuRepYear| int |年报数量|
| patentCount| int |专利数量|
| lawSuitCount| int |诉讼数量|
| bondCount| int |债券数量|
| tmCount| int |商标数量|
| phoneNumber| String |联系电话|
| regCapital| String |注册资金|
| regInstitute| String |登记机关|
| name| String |公司名称|
| regLocation| String |注册地址|
| industry| String |行业|
| approvedTime| long |核准时间|
| orgApprovedInstitute| String |组织结构代码证颁发机关|
| businessScope| String |经营范围|
| orgNumber| String |组织结构代码|
| estiblishTime| long |注册时间|
| regStatus| String |状态|
| legalPersonName| String |法人名称|
| toTime| long |营业时间结束时间|
| legalPersonId| long |法人id|
| sourceFlag| String |暂无|
| actualCapital| String |暂无|
| websiteList| array |网址列表|
| flag| String |暂无|
| companyOrgType| String |公司类型|
| base| String |地址|
| updateTimes| String |更新时间|
| companyType| String |暂无|
| creditCode| String |统一信用代码|
| companyId| String |公司id|

#### investorList（股东）返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| id   | long |股东id			|
| amount     | double |投资金额（万元）|
| name     | String |股东名|
| type     | int |类型（1为公司，2为自然人）|

#### investList（投资公司）返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| id   | long |投资公司id			|
| amount     | double |投资金额（万元）|
| name     | String |投资公司名|
| type     | int |类型（1为公司，2为自然人）|
| category | String |行业|
| base     | String |地区|
| legalPersonName     | String |法人姓名|

#### staffList（高管）返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| id   | long |投资公司id			|
| name     | String |高管姓名|
| typeJoin     | array |职位|
| type     | int |类型（1为公司，2为自然人）|

#### branchList（分支机构）返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| id   | long |分支公司id			|
| name     | String |分支机构名|
| type     | int |类型（1为公司，2为自然人）|

#### tmList（商标）返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| name     | String |商标名|
| url     | String |商标图片地址|

#### lawSuitList（诉讼）返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| title     | String |标题|
| submittime     | long |提交时间|
| court     | String |法院|
| uuid     | String |唯一id用于获取诉讼详情|
| doctype     | String |诉讼类型|
| url     | String |原文地址|
| caseno     | String |案件号|

#### comChanInfoList（变更信息）返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| changeItem     | String |变更项目|
| contentBefore     | String |变更前内容|
| contentAfter     | String |变更后内容|
| changeTime     | String |变更时间|

#### comAbnoInfoList（经营异常信息）返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| putReason     | String |列入经营异常名录原因|
| putDate     | String |列入日期|
| putDepartment     | String |列入部门|
| removeReason     | String |移出原因|
| removeDate     | String |移出日期|
| removeDepartment     | String |移出部门|

#### annuRepYearList（年报信息）返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| id     | long |年报id|
| phoneNumber     | String |企业联系电话|
| reportYear     | String |年份|
| email     | String |电子邮箱|

### 相关问题

## 公司详情,根据公司名称获得

### url

<http://api.tianyancha.com/services/v3/open/w/detail.json>

### sample

正常:<http://api.tianyancha.com/services/v3/open/w/detail.json?name=北京百度网讯科技有限公司>
带经营异常：<http://api.tianyancha.com/services/v3/open/w/detail.json?name=湖南瑞源生物医药科技有限公司>
带分支机构：<http://api.tianyancha.com/services/v3/open/w/detail.json?name=重庆金夫人实业有限公司>

### 支持格式

	JSON

### HTTP请求方式

	GET

### 是否需要授权

	是
	需要进入ip白名单

### 访问授权限制

	访问级别：普通接口

### 请求参数

|         | 必选   | 类型及范围	  | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| name      | true | String |公司全名，可通过查询接口获取					|

### 注意事项

	请求参数需要URLEncode。


### 返回结果

	JSON示例

```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "baseInfo": {
      "updatetime": 1472225375301,
      "fromTime": 991670400000,
      "type": 1,
      "categoryScore": 9436,
      "id": 22822,
      "regNumber": "110108002734659",
      "percentileScore": 9937,
      "allCount": {
        "branchCount": 0,
        "investCount": 38,
        "comAbnoInfo": 0,
        "companyBidCount": 2,
        "copyrightRegCount": 91,
        "empCount": 136,
        "investorCount": 2,
        "staffCount": 3,
        "comChanInfoCount": 13,
        "annuRepYear": 3,
        "ComAbnoInfoCount": 0,
        "patentCount": 980,
        "lawSuitCount": 348,
        "bondCount": 0,
        "tmCount": 250
      },
      "phoneNumber": "010-59928888",
      "regCapital": "89000 万元",
      "regInstitute": "北京市工商行政管理局",
      "name": "北京百度网讯科技有限公司",
      "regLocation": "北京市海淀区上地十街10号百度大厦2层",
      "industry": "电信、广播电视和卫星传输服务",
      "approvedTime": 1462896000000,
      "orgApprovedInstitute": "北京市质量技术监督局",
      "businessScope": "因特信息服务业务（除出版、教育、医疗保健以外的内容）；第一类增值电信业务中的在线数据处理与交易处理业务、国内因特网虚拟专用网业务、因特网数据中心业务；第二类增值电信业务中的因特网接入服务业务、呼叫中心业务、信息服务业务（不含固定网电话信息服务和互联网信息服务）；利用互联网经营音乐娱乐产品，游戏产品运营，网络游戏虚拟货币发行，美术品，演出剧（节）目，动漫（画）产品，从事互联网文化产品展览、比赛活动（网络文化经营许可证有效期至2016年11月21日）；图书、电子出版物、音像制品批发、零售、网上销售；设计、开发、销售计算机软件；技术服务、技术培训、技术推广；经济信息咨询；利用www.baidu.com、www.hao123.com(www.hao222.net、www.hao222.com)、网站发布广告；设计、制作、代理、发布广告；货物进出口、技术进出口、代理进出口；医疗软件技术开发；委托生产电子产品、玩具、照相器材；销售家用电器、机械设备、五金交电、电子产品、文化用品、照相器材、计算机、软件及辅助设备、化妆品、卫生用品、体育用品、纺织品、服装、鞋帽、日用品、家具、首饰、避孕器具、工艺品、钟表、眼镜、玩具、汽车及摩托车配件、仪器仪表、塑料制品、花、草及观赏植物、建筑材料、通讯设备；预防保健咨询；公园门票、文艺演出、体育赛事、展览会票务代理。（企业依法自主选择经营项目，开展经营活动；增值电信业务以及依法须经批准的项目，经相关部门批准后依批准的内容开展经营活动；不得从事本市产业政策禁止和限制类项目的经营活动。）",
      "orgNumber": "802100433",
      "estiblishTime": 991670400000,
      "regStatus": "开业",
      "legalPersonName": "梁志祥",
      "toTime": 1622736000000,
      "legalPersonId": 2020172991,
      "sourceFlag": "http://qyxy.baic.gov.cn/",
      "actualCapital": "",
      "websiteList": [
        "www.baidu.com"
      ],
      "flag": 1,
      "companyOrgType": "有限责任公司(自然人投资或控股)",
      "base": "bj",
      "updateTimes": 1472225374000,
      "companyType": 32767,
      "creditCode": "91110000802100433B",
      "companyId": 431
    },
    "investorList": [
      {
        "id": 1984012283,
        "amount": 0,
        "name": "李彦宏",
        "type": 2
      },
      {
        "id": 2074091018,
        "amount": 0,
        "name": "王湛",
        "type": 2
      }
    ],
    "investList": [
      {
        "id": 174626493,
        "amount": 804.2333,
        "category": "互联网和相关服务",
        "name": "上海齐家网信息科技股份有限公司",
        "base": "sh",
        "regStatus": "存续（在营、开业、在册）",
        "type": 1,
        "legalPersonName": "邓华金",
        "pencertileScore": 9875
      },
      ...
    ],
    "staffList": [
      {
        "id": 2074091018,
        "name": "王湛",
        "typeJoin": [
          "监事"
        ],
        "type": 2
      },
      ...
    ],
    "branchList": [],
    "tmList": [
      {
        "name": "DU",
        "url": "http://tm-image.tianyancha.com/tm/d27459d0477c53b1eb2fecffb0dd96d8.jpg"
      },
      ...
    ],
    "lawSuitList": [
      {
        "title": "刘馨予上诉北京百度网讯科技有限公司隐私权纠纷一案",
        "submittime": "1469721600000",
        "court": "北京市第一中级人民法院",
        "uuid": "de3cd10eeba64f998566601b2d4a19cd",
        "doctype": "民事判决书",
        "url": "http://wenshu.court.gov.cn/content/content?DocID=32556ef0-094c-42e7-8f54-2e25e3023182",
        "caseno": "（2016）京01民终3862号"
      },
      ...
    ],
    "comChanInfoList": [
      {
        "changeItem": "经营范围",
        "contentBefore": "因特信息服务业务（除出版、教育、医疗保健以外的内容）；第一类增值电信业务中的在线数据处理与交易处理业务、国内因特网虚拟专用网业务、因特网数据中心业务；第二类增值电信业务中的因特网接入服务业务、呼叫中心业务、信息服务业务（不含固定网电话信息服务和互联网信息服务）；利用互联网经营音乐娱乐产品，游戏产品运营，网络游戏虚拟货币发行，美术品，演出剧（节）目，动漫（画）产品，从事互联网文化产品展览、比赛活动（网络文化经营许可证有效期至2016年11月21日）；设计、开发、销售计算机软件；技术服务、技术培训、技术推广；经济信息咨询；利用www.baidu.com、www.hao123.com(www.hao222.net、www.hao222.com)、网站发布广告；设计、制作、代理、发布广告；货物进出口、技术进出口、代理进出口；医疗软件技术开发；委托生产电子产品、玩具、照相器材；销售家用电器、机械设备、五金交电、电子产品、文化用品、照相器材、计算机、软件及辅助设备、化妆品、卫生用品、体育用品、纺织品、服装、鞋帽、日用品、家具、首饰、避孕器具、工艺品、钟表、眼镜、玩具、汽车及摩托车配件、仪器仪表、塑料制品、花、草及观赏植物、建筑材料、通讯设备；预防保健咨询。企业依法自主选择经营项目，开展经营活动；增值电信业务以及依法须经批准的项目，经相关部门批准后依批准的内容开展经营活动；不得从事本市产业政策禁止和限制类项目的经营活动。",
        "contentAfter": "因特信息服务业务（除出版、教育、医疗保健以外的内容）；第一类增值电信业务中的在线数据处理与交易处理业务、国内因特网虚拟专用网业务、因特网数据中心业务；第二类增值电信业务中的因特网接入服务业务、呼叫中心业务、信息服务业务（不含固定网电话信息服务和互联网信息服务）；利用互联网经营音乐娱乐产品，游戏产品运营，网络游戏虚拟货币发行，美术品，演出剧（节）目，动漫（画）产品，从事互联网文化产品展览、比赛活动（网络文化经营许可证有效期至2016年11月21日）；图书、电子出版物、音像制品批发、零售、网上销售；设计、开发、销售计算机软件；技术服务、技术培训、技术推广；经济信息咨询；利用www.baidu.com、www.hao123.com(www.hao222.net、www.hao222.com)、网站发布广告；设计、制作、代理、发布广告；货物进出口、技术进出口、代理进出口；医疗软件技术开发；委托生产电子产品、玩具、照相器材；销售家用电器、机械设备、五金交电、电子产品、文化用品、照相器材、计算机、软件及辅助设备、化妆品、卫生用品、体育用品、纺织品、服装、鞋帽、日用品、家具、首饰、避孕器具、工艺品、钟表、眼镜、玩具、汽车及摩托车配件、仪器仪表、塑料制品、花、草及观赏植物、建筑材料、通讯设备；预防保健咨询；公园门票、文艺演出、体育赛事、展览会票务代理。企业依法自主选择经营项目，开展经营活动；增值电信业务以及依法须经批准的项目，经相关部门批准后依批准的内容开展经营活动；不得从事本市产业政策禁止和限制类项目的经营活动。",
        "changeTime": "2016-05-11"
      },
      ...
    ],
    "comAbnoInfoList": [],
    "annuRepYearList": [
      {
        "id": 317794031,
        "phoneNumber": "010-59928888",
        "reportYear": "2015",
        "email": "无"
      },
      ...
    ],
    "lawSuitTotal": 348
  }
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码			|
| reason     | String |错误原因|
| result     | Object| 返回内容|


#### baseInfo返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| updatetime   | long |更新时间			|
| fromTime     | long |营业期限开始时间|
| type     | int |类型（1为公司，2为自然人）|
| categoryScore     | int |行业评分|
| id     | long |公司id（查询用）|
| regNumber|String|工商注册号|
| percentileScore| int |公司评分|
| allCount| map |公司信息中包含的各个list的数量|
| branchCount| int |分支机构数量|
| investCount| int |投资数量|
| comAbnoInfo| int |经营异常数量|
| companyBidCount| int |招投标数量|
| copyrightRegCount| int |著作权数量|
| empCount| int |招聘数量|
| investorCount| int |股东数量|
| staffCount| int |高管数量|
| comChanInfoCount| int |变更信息数量|
| annuRepYear| int |年报数量|
| patentCount| int |专利数量|
| lawSuitCount| int |诉讼数量|
| bondCount| int |债券数量|
| tmCount| int |商标数量|
| phoneNumber| String |联系电话|
| regCapital| String |注册资金|
| regInstitute| String |登记机关|
| name| String |公司名称|
| regLocation| String |注册地址|
| industry| String |行业|
| approvedTime| long |核准时间|
| orgApprovedInstitute| String |组织结构代码证颁发机关|
| businessScope| String |经营范围|
| orgNumber| String |组织结构代码|
| estiblishTime| long |注册时间|
| regStatus| String |状态|
| legalPersonName| String |法人名称|
| toTime| long |营业时间结束时间|
| legalPersonId| long |法人id|
| sourceFlag| String |暂无|
| actualCapital| String |暂无|
| websiteList| array |网址列表|
| flag| String |暂无|
| companyOrgType| String |公司类型|
| base| String |地址|
| updateTimes| String |更新时间|
| companyType| String |暂无|
| creditCode| String |统一信用代码|
| companyId| String |公司id|

#### investorList（股东）返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| id   | long |股东id			|
| amount     | double |投资金额（万元）|
| name     | String |股东名|
| type     | int |类型（1为公司，2为自然人）|

#### investList（投资公司）返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| id   | long |投资公司id			|
| amount     | double |投资金额（万元）|
| name     | String |投资公司名|
| type     | int |类型（1为公司，2为自然人）|
| category | String |行业|
| base     | String |地区|
| legalPersonName     | String |法人姓名|

#### staffList（高管）返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| id   | long |高管id			|
| name     | String |高管姓名|
| typeJoin     | array |职位|
| type     | int |类型（1为公司，2为自然人）|

#### branchList（分支机构）返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| id   | long |分支公司id			|
| name     | String |分支机构名|
| type     | int |类型（1为公司，2为自然人）|

#### tmList（商标）返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| name     | String |分支机构名|
| url     | String |商标图片地址|

#### lawSuitList（诉讼）返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| title     | String |标题|
| submittime     | long |提交时间|
| court     | String |法院|
| uuid     | String |唯一id用于获取诉讼详情|
| doctype     | String |诉讼类型|
| url     | String |原文地址|
| caseno     | String |案件号|

#### comChanInfoList（变更信息）返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| changeItem     | String |变更项目|
| contentBefore     | String |变更前内容|
| contentAfter     | String |变更后内容|
| changeTime     | String |变更时间|

#### comAbnoInfoList（经营异常信息）返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| putReason     | String |列入经营异常名录原因|
| putDate     | String |列入日期|
| putDepartment     | String |列入部门|
| removeReason     | String |移出时间|
| removeDate     | String |移出日期|
| removeDepartment     | String |移出部门|

#### annuRepYearList（年报信息）返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| id     | long |年报id|
| phoneNumber     | String |企业联系电话|
| reportYear     | String |年份|
| email     | String |电子邮箱|

## 获取公司商标信息

### url

<http://api.tianyancha.com/services/v3/open/tm.json>

### sample

<http://api.tianyancha.com/services/v3/open/tm?id=22822&pageNum=1>

### 支持格式

	JSON

### HTTP请求方式

	GET

### 是否需要授权

	是
	需要进入ip白名单

### 访问授权限制

	访问级别：普通接口

### 请求参数

|         | 必选   | 类型及范围	  | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| id      | true | long |公司id，通过查询接口获取					|
| pageNum     | false | int |返回结果的页码，默认为1。|

### 注意事项

	请求参数需要URLEncode。


### 返回结果
	JSON示例

```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "viewtotal": "415",
    "items": [
      {
            "intCls": "38-电讯、通信服务",
            "tmPic": "http://tm-image.tianyancha.com/tm/607e1a0ad03a92fdc0a4cae2ae2c4a7d.jpg",
            "status": "有效",
            "pid": "4607842",
            "regNo": "5916522",
            "appDate": "1171296000000",
            "applicantCn": "北京百度网讯科技有限公司",
            "tmName": "百度"
        },
        {
            "intCls": "38-电讯、通信服务",
            "tmPic": "http://tm-image.tianyancha.com/tm/39899ed3d965a6b686e62a63f645b318.jpg",
            "status": "有效",
            "pid": "2509352",
            "regNo": "4096718",
            "appDate": "1086019200000",
            "applicantCn": "北京百度网讯科技有限公司",
            "tmName": "百度"
        },
        ...
    ],
    "pageSize": "10"
  }
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码			|
| reason     | String |错误原因|
| result     | Object| 返回内容|
| viewtotal     | int |查询总条数|
| pageSize     | int |本次查询返回条数|

#### items 字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| id   | long |商标id			|
| intCls     | String |类别|
| tmPic     | String |商标图片链接|
| appdate     | string |注册时间（毫秒）|
| status     | String |状态|
| regNo     | String |注册号|
| applicantCn     | String |申请人|
| tmName     | String |商标名称|

####

### 相关问题

无

## 获取公司专利信息

### url

<http://api.tianyancha.com/services/v3/open/patents.json>

### sample

<http://api.tianyancha.com/services/v3/open/patents?name=北京百度网讯科技有限公司&pageNum=1>

### 支持格式

	JSON

### HTTP请求方式

	GET

### 是否需要授权

	是
	需要进入ip白名单

### 访问授权限制

	访问级别：普通接口


### 请求参数

|         | 必选   | 类型及范围	  | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| name      | true | String |公司全名，可通过查询接口获取					|
| pageNum     | false | int |返回结果的页码，默认为1。|

### 注意事项

	请求参数需要URLEncode。

### 返回结果
	JSON示例

```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "total": 980,
    "items": [
      {
        "mainCatNum": "",
        "applicationPublishNum": "CN105893159A",
        "agency": "北京英赛嘉华知识产权代理有限责任公司11204",
        "inventor": "欧阳剑; 漆维; 王勇",
        "agent": "王达佐; 马晓亚",
        "applicationPublishTime": 1471968000000,
        "imgUrl": "http://epub.sipo.gov.cn/pic/ws9100/PUBXML/3234/FMGB/FMGB_DZGBD/2016104544831/100005/EDA0001024690630000011_thumb.jpg",
        "patentNum": "2016104544831",
        "allCatNum": "G06F9/50(2006.01)I",
        "patentName": "数据处理方法和装置",
        "abstracts": "本申请公开了数据处理方法和装置。所述方法的一具体实施方式包括：对接收到的待处理输入数据进行预处理；根据预处理的结果以及通过线性拟合激活函数得到的结果获得所述待处理输入数据的配置参数的存储地址，其中，配置参数是根据激活函数的曲线特性预先设置的；根据所述存储地址获取所述待处理输入数据的配置参数；根据所述待处理输入数据的配置参数以及预先设定的电路结构对所述待处理输入数据的预处理结果进行处理，得到处理结果。该实施方式实现了使用配置参数和预先设定的电路结构实现对待处理输入数据的处理，不需要使用用于实现激活函数的专用电路，从而简化了电路结构，且同时可以支持多种激活函数，提高了灵活性。",
        "address": "100085北京市海淀区上地十街10号百度大厦2层",
        "twoDimCodeUrl": "http://epub.sipo.gov.cn/qrcode/CN105893159A.png",
        "applicationTime": 1466438400000,
        "uuid": "e2c1981538c14ae29f29f1231425032a",
        "patentType": "发明公布",
        "applicantName": "北京百度网讯科技有限公司"
      },
      ...
    ]
  }
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码			|
| reason     | String |错误原因|
| result     | Object| 返回内容|
| total     | int |查询总条数|

#### items 字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| mainCatNum     | String |主分类号|
| applicationPublishNum| String |申请公布号			|
| agency     | String |代理机构|
| inventor     | String |发明人|
| agent     | String |代理人|
| applicationPublishTime | long |申请公布日|
| imgUrl     | String |图片路径|
| patentNum     | String |申请号/专利号|
| allCatNum     | String |全部分类号|
| patentName     | String |专利名称|
| abstracts     | String |摘要|
| address     | String |地址|
| twoDimCodeUrl     | String |二维码路径|
| applicationTime     | long |申请日|
| uuid     | String |唯一标识id|
| patentType     | String |专利类型|
| applicantName     | String |申请人|

### 相关问题

无

## 获取公司招投标信息

### url

<http://api.tianyancha.com/services/v3/open/bids>

### sample

<http://api.tianyancha.com/services/v3/open/bids?name=北京百度网讯科技有限公司&pageNum=1>

### 支持格式

	JSON

### HTTP请求方式

	GET

### 是否需要授权

	是
	需要进入ip白名单

### 访问授权限制

	访问级别：普通接口


### 请求参数

|         | 必选   | 类型及范围	  | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| name      | true | String |公司全名，通过查询接口获取					|
| pageNum     | false | int |返回结果的页码，默认为1。|

### 注意事项

	请求参数需要URLEncode。

### 返回结果
	JSON示例

```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "total": 2,
    "items": [
      {
        "title": "中国科学技术馆中国数字科技馆公有云迁移改造重新招标项目中标公告",
        "link": "http://www.ccgp.gov.cn/cggg/zygg/zbgg/201606/t20160606_6869131.htm",
        "intro": "中机国际招标有限公司受中国科学技术馆的委托，就中国科学技术馆中国数字科技馆公有云迁移改造重新招标项目项目（项目编号：0702-1641CITC7062）组织采购，评标工作已经结束，中标结果如：一、项目信息项目编号：0",
        "abs": "<div class=\"table\">\n <h5>公告概要：</h5>\n <table width=\"600\" border=\"0\" cellspacing=\"1\" bgcolor=\"#bfbfbf\" style=\"text-align:left;\">\n  <tbody>\n   <tr>\n    <td colspan=\"4\"><b>公告信息：</b></td>\n   </tr>\n   <tr>\n    <td class=\"title\" width=\"128\">采购项目名称</td>\n    <td colspan=\"3\" width=\"430\">中国科学技术馆中国数字科技馆公有云迁移改造重新招标项目</td>\n   </tr>\n   <tr>\n    <td class=\"title\">品目</td>\n    <td colspan=\"3\"><p>服务/信息技术服务/运行维护服务/软件运维服务,服务/信息技术服务/信息系统集成实施服务/安全集成实施服务,服务/信息技术服务/信息系统集成实施服务/软件集成实施服务</p></td>\n   </tr>\n   <tr>\n    <td class=\"title\">采购人</td>\n    <td colspan=\"3\">中国科学技术馆</td>\n   </tr>\n   <tr>\n    <td class=\"title\">行政区域</td>\n    <td width=\"168\">北京市</td>\n    <td class=\"title\" width=\"128\">公告时间</td>\n    <td width=\"168\">2016年06月06日 12:50</td>\n   </tr>\n   <tr>\n    <td class=\"title\">本项目招标公告日期</td>\n    <td width=\"168\">2016年05月12日</td>\n    <td class=\"title\" width=\"128\">中标日期</td>\n    <td width=\"168\">2016年06月06日</td>\n   </tr>\n   <tr>\n    <td class=\"title\">评标委员会成员名单</td>\n    <td colspan=\"3\">陈志国、丁军、王凤霞、王京春、张大成、张建国、赵兵兵</td>\n   </tr>\n   <tr>\n    <td class=\"title\">总中标金额</td>\n    <td colspan=\"3\">￥517.9175 万元（人民币）</td>\n   </tr>\n   <tr>\n    <td colspan=\"4\"><b>联系人及联系方式：</b></td>\n   </tr>\n   <tr>\n    <td class=\"title\">项目联系人</td>\n    <td colspan=\"3\">张沛、仪传记、李文士</td>\n   </tr>\n   <tr>\n    <td class=\"title\">项目联系电话</td>\n    <td colspan=\"3\">010-63348471/8436/8418</td>\n   </tr>\n   <tr>\n    <td class=\"title\" width=\"128\">采购人</td>\n    <td width=\"430\" colspan=\"3\">中国科学技术馆</td>\n   </tr>\n   <tr>\n    <td class=\"title\">采购人地址</td>\n    <td colspan=\"3\">北京市北辰东路5号</td>\n   </tr>\n   <tr>\n    <td class=\"title\">采购人联系方式</td>\n    <td colspan=\"3\">仲凯/010-59041204</td>\n   </tr>\n   <tr>\n    <td class=\"title\">代理机构名称</td>\n    <td colspan=\"3\">中机国际招标有限公司</td>\n   </tr>\n   <tr>\n    <td class=\"title\">代理机构地址</td>\n    <td colspan=\"3\">北京市丰台区西三环中路90号通用技术大厦</td>\n   </tr>\n   <tr>\n    <td class=\"title\">代理机构联系方式</td>\n    <td colspan=\"3\">仪传记/010-63348436</td>\n   </tr>\n   <tr>\n    <td colspan=\"4\"><b>附件：</b></td>\n   </tr>\n   <tr>\n    <td class=\"title\">附件1</td>\n    <td colspan=\"3\" width=\"430\"><a class=\"bizDownload\" href=\"\" id=\"A10F4C6A06D7F7E89962D3738052F7\" title=\"点击下载\">迁移改造项目重新招标招标文件-2016.5.12.pdf</a></td>\n   </tr>\n   <tr>\n    <td class=\"title\">附件2</td>\n    <td colspan=\"3\" width=\"430\"><a class=\"bizDownload\" href=\"\" id=\"47CF3BC39E8F5ABDBD31F48F5E209D\" title=\"点击下载\">中国数字科技馆公有云迁移改造重新招标项目技术需求2016.5.12.pdf</a></td>\n   </tr>\n  </tbody>\n </table>\n</div>",
        "content": "<div class=\"vT_detail_content w760c\"> \n <p>　　中机国际招标有限公司受中国科学技术馆的委托，就中国科学技术馆中国数字科技馆公有云迁移改造重新招标项目项目（项目编号：0702-1641CITC7062）组织采购，评标工作已经结束，中标结果如下：</p>\n <p></p>\n <p>&nbsp;</p>\n <p><strong>一、项目信息</strong></p>\n <p>项目编号：0702-1641CITC7062</p>\n <p>项目名称：中国科学技术馆中国数字科技馆公有云迁移改造重新招标项目</p>\n <p>项目联系人：张沛、仪传记、李文士</p>\n <p>联系方式：010-63348471/8436/8418</p>\n <p>&nbsp;</p>\n <p><strong>二、采购人信息</strong></p>\n <p>采购人名称：中国科学技术馆</p>\n <p>采购人地址：北京市北辰东路5号</p>\n <p>采购人联系方式：仲凯/010-59041204</p>\n <p>&nbsp;</p>\n <p><strong>三、项目用途、简要技术要求及合同履行日期：</strong></p>\n <p></p>\n <p align=\"left\" style=\"text-align: left; line-height: 21pt\">项目用途、简要技术要求：详见招标文件。</p>\n <p>合同履行日期：项目服务期为5年9个月（其中系统迁移改造服务9个月，公有云服务期5年），甲乙双方首次签署期限为3年9个月的服务合同（其中系统迁移改造9个月，公有云服务期3年）。服务合同期满后进行考核验收，考核验收合格后续签剩余2年公有云服务合同，如考核验收不合格，甲方有权终止续签剩余2年合同，乙方应免费协助甲方进行相关系统及数据的迁移工作。</p>\n <p></p>\n <p>&nbsp;</p>\n <p></p>\n <p><strong>四、采购代理机构信息</strong></p>\n <p>采购代理机构全称：中机国际招标有限公司</p>\n <p>采购代理机构地址：北京市丰台区西三环中路90号通用技术大厦</p>\n <p>采购代理机构联系方式：仪传记/010-63348436</p>\n <p>&nbsp;</p>\n <p><strong>五、中标信息</strong></p>\n <p>招标公告日期：2016年05月12日</p>\n <p>中标日期：2016年06月06日</p>\n <p>总中标金额：\n  <fmt:formatnumber type=\"currency\" pattern=\"￥.000000#\">\n   517.9175\n  </fmt:formatnumber> 万元（人民币）</p>\n <p>中标供应商名称、联系地址及中标金额：</p>\n <p></p>\n <table border=\"1\" cellpadding=\"0\" cellspacing=\"0\"> \n  <tbody> \n   <tr> \n    <td>序号</td> \n    <td>中标供应商名称</td> \n    <td>中标供应商联系地址</td> \n    <td>中标金额(万元)</td> \n   </tr> \n   <tr> \n    <td>1</td> \n    <td>北京百度网讯科技有限公司</td> \n    <td>北京市海淀区上地十街10号百度大厦</td> \n    <td>517.9175</td> \n   </tr> \n  </tbody>\n </table>\n <p></p>\n <p>&nbsp;</p>\n <p>评标委员会成员名单：</p>\n <p>陈志国、丁军、王凤霞、王京春、张大成、张建国、赵兵兵</p>\n <p>&nbsp;</p>\n <p>中标标的名称、规格型号、数量、单价、服务要求：</p>\n <p></p>\n <p align=\"left\" style=\"text-align: left; line-height: 21pt\">标的名称：中国科学技术馆中国数字科技馆公有云迁移改造重新招标项目</p>\n <p align=\"left\" style=\"text-align: left; line-height: 21pt\">规格型号、数量、单价：不适用</p>\n <p align=\"left\" style=\"text-align: left; line-height: 21pt\">服务要求：详见招标文件</p>\n <p></p>\n <p>&nbsp;</p>\n <p><strong>六、其它补充事宜</strong></p>\n <p></p>\n <p>无</p>\n <p></p> \n <p>&nbsp;</p> \n <p></p> \n <p></p> \n <p></p> \n <p></p> \n <p>&nbsp;</p> \n <p></p> \n</div>",
        "publishTime": 1465188628000,
        "purchaser": "中国科学技术馆",
        "proxy": "中机国际招标有限公司",
        "uuid": "5e101d88419b11e6a050288023a1a420"
      }
    ]
  }
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码			|
| reason     | String |错误原因|
| result     | Object| 返回内容|
| total     | int |查询总条数|

#### items 字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| intro     | String |简述|
| title     | long |标题|
| uuid     | String |唯一标识id|
| publishTime     | long |发布日期|
| purchaser     | String |采购人|
| proxy     | String |代理机构|
| link     | String |来源链接|
| abs     | String |摘要信息|
| content     | String |正文信息|

### 相关问题

无

## 获取公司著作权信息

### url

<http://api.tianyancha.com/services/v3/open/copyrights.json>

### sample

<http://api.tianyancha.com/services/v3/open/copyrights?name=北京百度网讯科技有限公司&pageNum=1>

### 支持格式

	JSON

### HTTP请求方式

	GET

### 是否需要授权

	是
	需要进入ip白名单

### 访问授权限制

	访问级别：普通接口


### 请求参数

|         | 必选   | 类型及范围	  | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| name      | true | String |公司全名，通过查询接口获取					|
| pageNum     | false | int |返回结果的页码，默认为1。|

### 注意事项

	请求参数需要URLEncode。

### 返回结果
	JSON示例

```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "total": 91,
    "items": [
      {
        "id": 75288,
        "regnum": "2016SR052419",
        "catnum": "30200-0000",
        "fullname": "度秘软件iOS终端软件",
        "simplename": "度秘",
        "version": "V1.0",
        "authorNationality": "北京百度网讯科技有限公司:中国",
        "publishtime": 1452355200000,
        "regtime": 1457884800000,
        "createTime": 1463996704000,
        "updateTime": 1463996704000,
        "isdelete": null
      },
      {
        "id": 100285,
        "regnum": "2016SR024724",
        "catnum": "30200-0000",
        "fullname": "百度高考android终端软件",
        "simplename": "百度高考",
        "version": "V2.5.1",
        "authorNationality": "北京百度网讯科技有限公司:中国",
        "publishtime": 1449504000000,
        "regtime": 1454256000000,
        "createTime": 1463996860000,
        "updateTime": 1463996860000,
        "isdelete": null
      }
      ...
    ]
  }
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码			|
| reason     | String |错误原因|
| result     | Object| 返回内容|
| total     | int |查询总条数|

#### items 字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| regnum     | String |登记号|
| catnum     | String |分类号|
| fullname     | String |全称|
| simplename     | String |简称|
| version     | String |版本号|
| authorNationality     | String |著作权人|
| publishtime     | long |首次发表日期|
| regtime     | long |登记日期|

### 相关问题

无

## 获取公司招聘信息

### url

<http://api.tianyancha.com/services/v3/open/employments.json>

### sample

<http://api.tianyancha.com/services/v3/open/employments?name=北京百度网讯科技有限公司&pageNum=1>

### 支持格式

  JSON

### HTTP请求方式

  GET

### 是否需要授权

  是
  需要进入ip白名单

### 访问授权限制

  访问级别：普通接口


### 请求参数

|         | 必选   | 类型及范围    | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| name      | true | String |公司全名，通过查询接口获取          |
| pageNum     | false | int |返回结果的页码，默认为1。|

### 注意事项

  请求参数需要URLEncode。

### 返回结果
  JSON示例  

```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "total": 183,
    "items": [
      {
        "id": 17988553,
        "title": "iOS研发工程师(北京百度网讯科技有限公司)",
        "city": "北京",
        "district": "北京",
        "companyName": "北京百度网讯科技有限公司",
        "oriSalary": "15000-30000元",
        "urlPath": "http://www.lagou.com/jobs/2227884.html",
        "startdate": 1473696000000,
        "enddate": 1478966400000,
        "source": "拉勾网",
        "education": "本科",
        "employerNumber": "",
        "experience": "1-3年",
        "createTime": 1473758112000,
        "updateTime": 1473758156000,
        "description": "工作职责：1、参与作业帮项目维护及研发；2、跟进了解新的技术点及跨平台项目研究；职位要求：1.对Objective-C和CocoaTouch框架有丰富的经验和深入的理解。2.熟练掌握iOS常用开发工具、调试工具，有性能调优经验优先。3.熟悉iOSapp的开发、测试，发布等一列系流程优先4.1年以上iOS开发经验，有互联网公司背景优先5.设计良好的代码结构,不断迭代重构"
      },
      ...
    ]
  }
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码      |
| reason     | String |错误原因|
| result     | Object| 返回内容|
| total     | int |查询总条数|

#### items 字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| title     | String |招聘职称,题目|
| city     | String |所在城市|
| district     | String |所在区|
| companyName     | String |公司名字|
| oriSalary     | String |薪资|
| urlPath     | String |外网链接|
| startdate     | long |招聘开始日期|
| enddate     | long |招聘截止日期|
| source     | String |来源|
| education     | String |教育水平|
| employerNumber     | String |招聘人数|
| experience     | String |经验|
| description     | String |职位描述|

### 相关问题

无

## 获取公司失信信息

### url

<http://api.tianyancha.com/services/v3/open/dishonest.json>

### sample

<http://api.tianyancha.com/services/v3/open/dishonest?name=天津信裕房地产发展有限公司&pageNum=1>

### 支持格式

	JSON

### HTTP请求方式

	GET

### 是否需要授权

	是
	需要进入ip白名单

### 访问授权限制

	访问级别：普通接口


### 请求参数

|         | 必选   | 类型及范围	  | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| name      | true | String |公司全名，通过查询接口获取					|
| pageNum     | false | int |返回结果的页码，默认为1。|

### 注意事项

	请求参数需要URLEncode。

### 返回结果
	JSON示例

```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "total": 1,
    "num": 1,
    "items": [
      {
        "iname": "天津信裕房地产发展有限公司",
        "casecode": "(2013)西法执字第01218号",
        "cardnum": "60056316-5",
        "businessentity": "徐永清",
        "areaname": "天津",
        "courtname": "天津市河西区人民法院",
        "gistid": "(2013)西民二初字224号",
        "regdate": "1372262400000",
        "gistunit": "河西法院",
        "duty": "一、被告天津信裕房地产发展有限公司于本判决生效之日起十日内支付原告天津和平建工集团有限公司工程款1800000元。\n二、被告天津信裕房地产发展有限公司于本判决生效之日起十日内支付原告天津和平建工集团有限公司滞纳金449800元（从2011年6月31日起至2013年1月30日止）及从2013年2月1日开始实际给付工程款1800000元之日止的滞纳金，每延期一日按万分之五计算\n案件受理费24798元由被告天津信裕房地产发展有限公司负担\n",
        "performance": "全部未履行",
        "disrupttypename": "其他有履行能力而拒不履行生效法律文书确定义务",
        "publishdate": "1381248000000",
        "type": "1"
      }
    ],
    "pageSize": 20
  }
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码			|
| reason     | String |错误原因|
| result     | Object| 返回内容|
| total     | int |查询总条数|
| num     | int |实际返回条数|
| pageSize     | int |单页返回的记录条数|

#### items 字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| iname     | String |失信人名|
| casecode     | String |案号|
| cardnum     | String |身份证号／组织机构代码|
| businessentity     | String |法定代表人|
| areaname     | String |省份|
| courtname     | String |执行法院|
| gistid     | String |案号|
| regdate     | String |立案时间|
| gistunit     | String |做出执行依据单位|
| duty     | String |法律生效文书确定的义务|
| performance     | String |被执行人的履行情况|
| publishdate     | String |发布时间|

### 相关问题

无

## 获取公司债券信息

### url

<http://api.tianyancha.com/services/v3/open/bonds.json>

### sample

<http://api.tianyancha.com/services/v3/open/bonds?name=中国人民银行&pageNum=1>

### 支持格式

	JSON

### HTTP请求方式

	GET

### 是否需要授权

	是
	需要进入ip白名单

### 访问授权限制

	访问级别：普通接口


### 请求参数

|         | 必选   | 类型及范围	  | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| name      | true | String |公司全名，通过查询接口获取					|
| pageNum     | false | int |返回结果的页码，默认为1。|

### 注意事项

	请求参数需要URLEncode。

### 返回结果
	JSON示例

```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "total": 963,
    "items": [
      {
        "id": 745,
        "bondName": "97融资01",
        "bondNum": "5003",
        "publisherName": "中国人民银行",
        "bondType": "央行票据",
        "publishTime": 858009600000,
        "publishExpireTime": 952704000000,
        "bondTimeLimit": "3年",
        "bondTradeTime": 858096000000,
        "calInterestType": "",
        "bondStopTime": 952704000000,
        "creditRatingGov": null,
        "debtRating": "",
        "faceValue": 100,
        "refInterestRate": null,
        "faceInterestRate": null,
        "realIssuedQuantity": 0,
        "planIssuedQuantity": 0,
        "issuedPrice": 100,
        "interestDiff": null,
        "payInterestHZ": "",
        "startCalInterestTime": 858009600000,
        "exeRightType": "",
        "exeRightTime": null,
        "escrowAgent": "中央国债登记结算公司",
        "flowRange": "公开发行",
        "remark": "",
        "tip": "对于含权债，票面利率/利差指行权前的票面利率/利差。",
        "createTime": 1464174022000,
        "updateTime": 1464174022000,
        "isDelete": null
      },
      {
        "id": 32998,
        "bondName": "10央票99续",
        "bondNum": "1001099N",
        "publisherName": "中国人民银行",
        "bondType": "央行票据",
        "publishTime": 1384099200000,
        "publishExpireTime": 1478880000000,
        "bondTimeLimit": "3年",
        "bondTradeTime": 1384185600000,
        "calInterestType": "固定利率",
        "bondStopTime": 1478620800000,
        "creditRatingGov": null,
        "debtRating": "",
        "faceValue": 100,
        "refInterestRate": null,
        "faceInterestRate": 3.5,
        "realIssuedQuantity": 100,
        "planIssuedQuantity": 100,
        "issuedPrice": 100,
        "interestDiff": null,
        "payInterestHZ": "年",
        "startCalInterestTime": 1384185600000,
        "exeRightType": "",
        "exeRightTime": null,
        "escrowAgent": "中央国债登记结算公司",
        "flowRange": "公开发行",
        "remark": "",
        "tip": "对于含权债，票面利率/利差指行权前的票面利率/利差。",
        "createTime": 1464246262000,
        "updateTime": 1464246262000,
        "isDelete": null
      }...
    ]
  }
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码			|
| reason     | String |错误原因|
| result     | Object| 返回内容|
| total     | int |查询总条数|
| num     | int |实际返回条数|
| pageSize     | int |单页返回的记录条数|

#### items 字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| bondName     | String |债券名称|
| bondNum     | String |债券代码|
| publisherName     | String |发行人|
| bondType     | String |债券类型|
| publishTime     | String |债劵发行日|
| publishExpireTime     | String |债劵到期日|
| bondTimeLimit     | String |债劵期限|
| bondTradeTime     | String |上市交易日|
| calInterestType     | String |计息方式|
| bondStopTime     | String |债劵摘牌日|
| creditRatingGov     | String |信用评级机构|
| debtRating     | String |债项评级|
| faceValue     | String |面值|
| refInterestRate     | String |参考利率|
| faceInterestRate     | String |票面利率(%)|
| realIssuedQuantity     | String |实际发行量(亿)|
| planIssuedQuantity     | String |计划发行量(亿)|
| issuedPrice     | String |发行价格(元)|
| interestDiff     | String |利差(BP)|
| payInterestHZ     | String |付息频率|
| startCalInterestTime     | String |债券起息日|
| exeRightType     | String |行权类型|
| exeRightTime     | String |行权日期|
| escrowAgent     | String |托管机构|
| flowRange     | String |流通范围|
| remark     | String |备注|

### 相关问题

无

## 获取公司备案信息

### url

<http://api.tianyancha.com/services/v3/open/icp.json>

### sample

<http://api.tianyancha.com/services/v3/open/icp?id=22822>

### 支持格式

	JSON

### HTTP请求方式

	GET

### 是否需要授权

	是
	需要进入ip白名单

### 访问授权限制

	访问级别：普通接口


### 请求参数

|         | 必选   | 类型及范围	  | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| id      | true | long |公司id，通过查询接口获取					|

### 注意事项

	请求参数需要URLEncode。

### 返回结果
	JSON示例

```
{
  "error_code": 0,
  "reason": "ok",
  "result": [
    {
      "webSite": [
        "www.baidu.com"
      ],
      "examineDate": "2016-08-02 ",
      "companyType": "企业 ",
      "webName": "百度 ",
      "liscense": " 京ICP证030173号-1",
      "companyName": "北京百度网讯科技有限公司 "
    },
    {
      "webSite": [
        "www.baidu-tech.com"
      ],
      "examineDate": "2016-08-02 ",
      "companyType": "企业 ",
      "webName": "搜索研发部官方网站 ",
      "liscense": " 京ICP证030173号-11",
      "companyName": "北京百度网讯科技有限公司 "
    }
    ...
  ]
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码			|
| reason     | String |错误原因|
| result     | Object| 返回内容|

#### items 字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| webSite     | array |网站|
| examineDate     | String |检查时间|
| companyType     | String |公司类型|
| webName     | String |网站名称|
| liscense     | String |许可证|
| companyName     | String |公司名称|

### 相关问题

无

## 获取公司诉讼信息

### url

<http://api.tianyancha.com/services/v3/open/lawsuit.json>

### sample

<http://api.tianyancha.com/services/v3/open/lawsuit?name=北京百度网讯科技有限公司&pageNum=1>

### 支持格式

	JSON

### HTTP请求方式

	GET

### 是否需要授权

	是
	需要进入ip白名单

### 访问授权限制

	访问级别：普通接口


### 请求参数

|         | 必选   | 类型及范围	  | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| name      | true | String |公司全名，可通过查询接口获取					|
| pageNum     | false | int |返回结果的页码，默认为1。|

### 注意事项

	请求参数需要URLEncode。

### 返回结果
	JSON示例

```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "total": 348,
    "pagesize": 20,
    "items": [
      {
        "title": "刘馨予上诉北京百度网讯科技有限公司隐私权纠纷一案",
        "submittime": "1469721600000",
        "court": "北京市第一中级人民法院",
        "uuid": "de3cd10eeba64f998566601b2d4a19cd",
        "doctype": "民事判决书",
        "url": "http://wenshu.court.gov.cn/content/content?DocID=32556ef0-094c-42e7-8f54-2e25e3023182",
        "caseno": "（2016）京01民终3862号"
      },
      {
        "title": "巩传亚与北京百度网讯科技有限公司买卖合同纠纷二审民事裁定书",
        "submittime": "1469721600000",
        "court": "河北省唐山市中级人民法院",
        "uuid": "0847b624f7fc42fcb7b957069683d561",
        "doctype": "民事裁定书",
        "url": "http://wenshu.court.gov.cn/content/content?DocID=35785a29-1593-48a9-8648-138427426625",
        "caseno": "（2016）冀02民辖终424号"
      }
      ...
    ]
  }
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码			|
| reason     | String |错误原因|
| result     | Object| 返回内容|
| total     | int |查询总条数|
| num     | int |实际返回条数|
| pageSize     | int |单页返回的记录条数|

#### items 字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| title     | String |标题|
| submittime     | long |提交时间|
| court     | String |法院|
| doctype     | String |诉讼类型|
| url     | String |原文链接地址|
| caseno     | String |案件号|

### 相关问题

无

## 获取公司法院公告信息

### url

<http://api.tianyancha.com/services/v3/open/court.json>

### sample

<http://api.tianyancha.com/services/v3/open/court?id=22822&pageNum=1>

### 支持格式

	JSON

### HTTP请求方式

	GET

### 是否需要授权

	是
	需要进入ip白名单

### 访问授权限制

	访问级别：普通接口


### 请求参数

|         | 必选   | 类型及范围	  | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| id	      | true | long |公司id，可通过查询接口获取					|
| pageNum     | false | int |返回结果的页码，默认为1。|



### 注意事项

	请求参数需要URLEncode。

### 返回结果
	JSON示例

```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "total": 6,
    "num": 6,
    "items": [
      {
        "id": 622473,
        "announce_id": 4580042,
        "bltnno": "1016042000234",
        "bltnstate": "1050",
        "bltntype": "132",
        "bltntypename": "起诉状副本及开庭传票",
        "caseno": "",
        "content": "郭伟、沙坪坝区天喜四层火锅：\n本院受理北京百度网讯科技有限公司诉郭伟、 天喜四层火锅服务合同纠纷一案，现依法向你公告送达起诉书副本、开庭传票及证据材料，限你自公告之日起六十日内来本院五层第十九法庭领取，逾期则视为送达。提出答辩状的期限为公告送达期满后十五日内。本院定于答辩期满后的第三日上午九时（遇节假日顺延），在本院五层第十九法庭公开开庭审理此案，逾期本院将依法缺席裁判。\n",
        "courtflag": "",
        "courtcode": "北京市朝阳区人民法院",
        "customno": "",
        "dealgrade": "7",
        "dealgradename": "普通",
        "judge": "民一陈扬",
        "judgephone": "",
        "mobilephone": "",
        "party1": "北京百度网讯科技有限公司",
        "party2": "郭伟、沙坪坝区天喜四层火锅",
        "province": "北京",
        "publishdate": "2016-04-27",
        "publishpage": "G31",
        "reason": "",
        "showtxtdate": "",
        "tmpsaversn": ""
      },
      {
        "id": 457346,
        "announce_id": 4529950,
        "bltnno": "1016032800800",
        "bltnstate": "1050",
        "bltntype": "132",
        "bltntypename": "起诉状副本及开庭传票",
        "caseno": "",
        "content": "石家庄千岛餐饮服务有限公司、索海涛：\n本院受理原告北京百度网讯科技有限公司与你们合同纠纷一案，现依法向你们公告送达起诉状副本及开庭传票。自本公告发出之日起60日即视为送达。提出答辩状的期限为公告送达期满后15日内，并定于答辩期满后的第3日上午9时（遇节假日顺延）在本院4层第9法庭开庭审理此案，逾时本院将依法缺席审理。\n",
        "courtflag": "",
        "courtcode": "北京市朝阳区人民法院",
        "customno": "",
        "dealgrade": "7",
        "dealgradename": "普通",
        "judge": "民一王阳",
        "judgephone": "",
        "mobilephone": "",
        "party1": "北京百度网讯科技有限公司",
        "party2": "石家庄千岛餐饮服务有限公司、索海涛",
        "province": "北京",
        "publishdate": "2016-04-02",
        "publishpage": "G83",
        "reason": "",
        "showtxtdate": "",
        "tmpsaversn": ""
      }
      ...
    ]
  }
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码			|
| reason     | String |错误原因|
| result     | Object| 返回内容|
| total     | int |查询总条数|
| num     | int |实际返回条数|

#### items 字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| announce_id     | long |公告id|
| bltnno     | String |公告号|
| bltnstate     | String |公告状态号|
| bltntype     | String |公告类型|
| bltntypename     | String |公告类型名称|
| caseno     | String |案件号|
| content     | String |案件内容|
| courtcode     | String |法院名|
| dealgrade     | String |处理等级|
| dealgradename     | String |处理等级名称|
| judge     | String |法官|
| judgephone     | String |法官电话|
| party1     | String |原告|
| party2     | String |当事人|
| province     | String |省份|
| publishdate     | String |刊登日期|
| publishpage     | String |刊登版面|

### 相关问题

无

## 获取公司变更信息

### url

<http://api.tianyancha.com/services/v3/open/changeinfo.json>

### sample

<http://api.tianyancha.com/services/v3/open/changeinfo?id=22822>

### 支持格式

	JSON

### HTTP请求方式

	GET

### 是否需要授权

	是
	需要进入ip白名单

### 访问授权限制

	访问级别：普通接口


### 请求参数

|         | 必选   | 类型及范围	  | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| id      | true | long |公司id，可通过查询接口获取	|

### 注意事项

	请求参数需要URLEncode。

### 返回结果
	JSON示例

```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "total": 13,
    "items": [
      {
        "changeItem": "经营范围",
        "contentBefore": "因特信息服务业务（除出版、教育、医疗保健以外的内容）；第一类增值电信业务中的在线数据处理与交易处理业务、国内因特网虚拟专用网业务、因特网数据中心业务；第二类增值电信业务中的因特网接入服务业务、呼叫中心业务、信息服务业务（不含固定网电话信息服务和互联网信息服务）；利用互联网经营音乐娱乐产品，游戏产品运营，网络游戏虚拟货币发行，美术品，演出剧（节）目，动漫（画）产品，从事互联网文化产品展览、比赛活动（网络文化经营许可证有效期至2016年11月21日）；设计、开发、销售计算机软件；技术服务、技术培训、技术推广；经济信息咨询；利用www.baidu.com、www.hao123.com(www.hao222.net、www.hao222.com)、网站发布广告；设计、制作、代理、发布广告；货物进出口、技术进出口、代理进出口；医疗软件技术开发；委托生产电子产品、玩具、照相器材；销售家用电器、机械设备、五金交电、电子产品、文化用品、照相器材、计算机、软件及辅助设备、化妆品、卫生用品、体育用品、纺织品、服装、鞋帽、日用品、家具、首饰、避孕器具、工艺品、钟表、眼镜、玩具、汽车及摩托车配件、仪器仪表、塑料制品、花、草及观赏植物、建筑材料、通讯设备；预防保健咨询。企业依法自主选择经营项目，开展经营活动；增值电信业务以及依法须经批准的项目，经相关部门批准后依批准的内容开展经营活动；不得从事本市产业政策禁止和限制类项目的经营活动。",
        "contentAfter": "因特信息服务业务（除出版、教育、医疗保健以外的内容）；第一类增值电信业务中的在线数据处理与交易处理业务、国内因特网虚拟专用网业务、因特网数据中心业务；第二类增值电信业务中的因特网接入服务业务、呼叫中心业务、信息服务业务（不含固定网电话信息服务和互联网信息服务）；利用互联网经营音乐娱乐产品，游戏产品运营，网络游戏虚拟货币发行，美术品，演出剧（节）目，动漫（画）产品，从事互联网文化产品展览、比赛活动（网络文化经营许可证有效期至2016年11月21日）；图书、电子出版物、音像制品批发、零售、网上销售；设计、开发、销售计算机软件；技术服务、技术培训、技术推广；经济信息咨询；利用www.baidu.com、www.hao123.com(www.hao222.net、www.hao222.com)、网站发布广告；设计、制作、代理、发布广告；货物进出口、技术进出口、代理进出口；医疗软件技术开发；委托生产电子产品、玩具、照相器材；销售家用电器、机械设备、五金交电、电子产品、文化用品、照相器材、计算机、软件及辅助设备、化妆品、卫生用品、体育用品、纺织品、服装、鞋帽、日用品、家具、首饰、避孕器具、工艺品、钟表、眼镜、玩具、汽车及摩托车配件、仪器仪表、塑料制品、花、草及观赏植物、建筑材料、通讯设备；预防保健咨询；公园门票、文艺演出、体育赛事、展览会票务代理。企业依法自主选择经营项目，开展经营活动；增值电信业务以及依法须经批准的项目，经相关部门批准后依批准的内容开展经营活动；不得从事本市产业政策禁止和限制类项目的经营活动。",
        "changeTime": "2016-05-11"
      },
      {
        "changeItem": "注册资本",
        "contentBefore": "10000 万元",
        "contentAfter": "89000 万元",
        "changeTime": "2016-04-27"
      }
      ...
    ]
  }
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码			|
| reason     | String |错误原因|
| result     | Object| 返回内容|
| total     | int |查询总条数|

#### items 字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| changeItem     | String |修改事项|
| contentBefore     | String |修改前|
| contentAfter     | String |修改后|
| changeTime     | String |修改时间|

### 相关问题

无

## 获取公司年报信息

### url

<http://api.tianyancha.com/services/v3/open/annualreport.json>

###sample

正常：<http://api.tianyancha.com/services/v3/open/annualreport.json?id=22822&pageNum=1>
带股权出质公司：<http://api.tianyancha.com/services/v3/open/annualreport?id=4693597&pageNum=1>

### 支持格式

	JSON

### HTTP请求方式

	GET

### 是否需要授权

	是
	需要进入ip白名单

### 访问授权限制

	访问级别：普通接口


### 请求参数

|         | 必选   | 类型及范围	  | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| id      | true | long |公司id，可通过查询接口获取					|

### 注意事项

	请求参数需要URLEncode。

### 返回结果
	JSON示例

```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "total": 3,
    "items": [
      {
        "baseInfo": {
          "reportYear": "2015",
          "companyName": "北京百度网讯科技有限公司",
          "creditCode": "91110000802100433B",
          "regNumber": "",
          "phoneNumber": "010-59928888",
          "postcode": "100085",
          "postalAddress": "北京市海淀区上地十街百度大厦",
          "email": "无",
          "manageState": "开业",
          "employeeNum": "企业选择不公示",
          "operatorName": "",
          "totalAssets": "企业选择不公示",
          "totalEquity": "企业选择不公示",
          "totalSales": "企业选择不公示",
          "totalProfit": "企业选择不公示",
          "primeBusProfit": "企业选择不公示",
          "retainedProfit": "企业选择不公示",
          "totalTax": "企业选择不公示",
          "totalLiability": "企业选择不公示"
        },
        "changeRecordList": [
          {
            "changeItem": "认缴出资额",
            "contentBefore": "375",
            "contentAfter": "50",
            "changeTime": "2016-06-28"
          },
          {
            "changeItem": "认缴出资日期",
            "contentBefore": "2015-12-22",
            "contentAfter": "2008-04-28",
            "changeTime": "2016-06-28"
          }
          ...
        ],
        "equityChangeInfoList": [],
        "outGuaranteeInfoList": [],
        "outboundInvestmentList": [
          {
            "outcompanyName": "百度鹏寰资产管理（北京）有限公司",
            "regNum": "",
            "creditCode": "91110108769934777T"
          },
          {
            "outcompanyName": "诺克萨斯（北京）科技有限公司",
            "regNum": "",
            "creditCode": "91110106059289814B"
          }
          ...
        ],
        "shareholderList": [
          {
            "investorName": "王湛",
            "subscribeAmount": "50",
            "subscribeTime": "2008-04-28",
            "subscribeType": "货币",
            "paidAmount": "50",
            "paidTime": "2008-04-28",
            "paidType": "货币"
          },
          {
            "investorName": "王湛",
            "subscribeAmount": "325",
            "subscribeTime": "2015-12-22",
            "subscribeType": "货币",
            "paidAmount": "325",
            "paidTime": "2015-12-22",
            "paidType": "货币"
          }
          ...
        ],
        "webInfoList": [
          {
            "webType": "网站",
            "name": "百度",
            "website": "www.baidu.com"
          }
        ]
      }
      ...
    ]
  }
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码			|
| reason     | String |错误原因|
| result     | Object| 返回内容|
| total     | int |查询总条数|
| num     | int |实际返回条数|

#### baseInfo 字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| reportYear     | String |年报年度|
| companyName     | String |企业名称|
| creditCode     | String |统一社会信用代码|
| regNumber     | String |注册号|
| phoneNumber     | String |企业联系电话|
| postcode     | String |邮政编码|
| postalAddress     | String |企业通信地址|
| email     | String |电子邮箱|
| manageState     | String |企业经营状态|
| employeeNum     | String |从业人数|
| operatorName     | String |经营者名称|
| totalAssets     | String |资产总额|
| totalEquity     | String |所有者权益合计|
| totalSales     | String |销售总额(营业总收入)|
| totalProfit     | String |利润总额|
| primeBusProfit     | String |主营业务收入|
| retainedProfit     | String |净利润|
| totalTax     | String |纳税总额|
| totalLiability     | String |负债总额|

#### changeRecordList （年报变更记录） 字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| changeItem     | String |修改事项|
| contentBefore     | String |修改前|
| contentAfter     | String |修改后|
| changeTime     | String |修改时间|


#### equityChangeInfoList （股东股权变更信息） 字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| investorName     | String |股东（发起人）|
| ratioBefore     | String |变更前股权比例|
| ratioAfter     | String |变更后股权比例|
| changeTime     | String |股权变更日期|

#### outGuaranteeInfoList （对外提供保证担保信息） 字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| creditor     | String |债权人|
| obligor     | String |债务人|
| creditoType     | String |主债权种类|
| creditoAmount     | String |主债权数额|
| creditoTerm     | String |履行债务的期限|
| guaranteeTerm     | String |保证的期间|
| guaranteeWay     | String |保证的方式|
| guaranteeScope     | String |保证担保的范围|

#### outboundInvestmentList （对外投资信息） 字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| outcompanyName     | String |对外投资企业名称|
| regNum     | String |注册号|
| creditCode     | String |统一信用代码|

#### shareholderList （股东及出资信息） 字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| investorName     | String |股东名称|
| subscribeAmount     | String |认缴出资额|
| subscribeTime     | String |认缴出资时间|
| subscribeType     | String |认缴出资方式|
| paidAmount     | String |实缴出资额|
| paidTime     | String |实缴出资时间|
| paidType     | String |实缴出资方式|

#### webInfoList （网站或网店信息） 字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| webType     | String |网站类型|
| name     | String |名称|
| website     | String |网址|

### 相关问题

无

## 获取公司新闻信息

### url

<http://api.tianyancha.com/services/v3/open/news.json>

### sample

<http://api.tianyancha.com/services/v3/open/news.json?name=北京百度网讯科技有限公司>

### 支持格式

  JSON

### HTTP请求方式

  GET

### 是否需要授权

  是
  需要进入ip白名单

### 访问授权限制

  访问级别：普通接口


### 请求参数

|         | 必选   | 类型及范围    | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| name      | true | String |公司全名，可通过查询接口获取 |

### 注意事项

  请求参数需要URLEncode。

### 返回结果
  JSON示例  

```
{
  "error_code": 0,
  "reason": "ok",
  "result": [
    {
      "title": "新百度视频宣布完成A轮融资",
      "url": "http://www.36kr.com/p/5055826.html",
      "website": "36氪",
      "time": "2016-11-04 12:56:00"
    },
    {
      "title": "新文化投资百度视频缩水3亿",
      "url": "http://news.163.com/16/1104/01/C509C5Q7000187VI.html",
      "website": "网易新闻",
      "time": "2016-11-04 01:49:51"
    },
    ...
  ]
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码      |
| reason     | String |错误原因|
| result     | Object| 返回内容|

#### result 字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| title     | String |新闻标题|
| url     | String |链接|
| website     | String |来源|
| time     | String |时间|

### 相关问题

无

## 获取公司严重违法信息

### url

<http://api.tianyancha.com/services/v3/open/Illegal.json>

### sample

<http://api.tianyancha.com/services/v3/open/Illegal.json?name=陕西华庭酒店有限公司>

### 支持格式

  JSON

### HTTP请求方式

  GET

### 是否需要授权

  是
  需要进入ip白名单

### 访问授权限制

  访问级别：普通接口


### 请求参数

|         | 必选   | 类型及范围    | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| name      | true | String |公司全名，可通过查询接口获取 |
| pageNum     | false | int |返回结果的页码，默认为1。|

### 注意事项

  请求参数需要URLEncode。

### 返回结果
  JSON示例  

```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "count": 1,
    "items": [
      {
        "removeReason": "",
        "putDepartment": "陕西省工商行政管理局",
        "putReason": "提交虚假材料或者采取其他欺诈手段隐瞒重要事实，取得公司变更或者注销登记，被撤销登记的",
        "putDate": 1472745600000,
        "removeDepartment": ""
      }
    ]
  }
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码      |
| reason     | String |错误原因|
| result     | Object| 返回内容|
| count     | int| 总条数|

#### items 字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| putReason     | String |列入原因|
| putDate     | Date |列入日期|
| putDepartment     | String |决定列入部门(作出决定机关)|
| removeReason     | String |移除原因|
| removeDate     | Date |移除日期|
| removeDepartment     | String |决定移除部门|

### 相关问题

无

## 获取公司股权出质信息

### url

<http://api.tianyancha.com/services/v3/open/companyEquity.json>

### sample

<http://api.tianyancha.com/services/v3/open/companyEquity.json?name=北京逸璟物业管理有限公司>

### 支持格式

  JSON

### HTTP请求方式

  GET

### 是否需要授权

  是
  需要进入ip白名单

### 访问授权限制

  访问级别：普通接口


### 请求参数

|         | 必选   | 类型及范围    | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| name      | true | String |公司全名，可通过查询接口获取 |
| pageNum     | false | int |返回结果的页码，默认为1。|

### 注意事项

  请求参数需要URLEncode。

### 返回结果
  JSON示例  

```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "count": 0,
    "items": [
      {
        "pledgee": "兰州汇通投资担保有限公司",
        "equityAmount": "300",
        "state": "无效",
        "pledgor": "夏立江",
        "changeSituation": "<a href=\"#\" onclick=\"window.open（'/gsxygs/pub!getInfo.do?entcate=compan&amp;pripid=1389456&amp;parm=stock_rights&amp;invId=&amp;applyId=ff80808139e616e70139e75ee8ab14a1&amp;regno=620000200026732&amp;state=2'）\">详情</a>",
        "regDate": 1342800000000,
        "regNumber": "620000200026732001",
        "certifNumberR": "620100200008532"
      },
      ...
    ]
  }
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码      |
| reason     | String |错误原因|
| result     | Object| 返回内容|
| count     | int| 总条数|

#### items 字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| base     | String |省份|
| regNumber     | Date |登记编号|
| pledgor     | String |出质人|
| certifNumberL     | String |出质人证照/证件号码|
| equityAmount     | Date |出质股权数额|
| pledgee     | String |质权人|
| certifNumberR     | String |质权人证照/证件号码|
| regDate     | Date |股权出质设立登记日期|
| state     | String |状态|
| putDate     | String |公示日期|
| changeSituation     | String |变化情况|
| cancelDate     | String |注销日期|
| cancelReason     | String |注销原因|

### 相关问题

无

## 获取公司行政处罚信息

### url

<http://api.tianyancha.com/services/v3/open/punishment.json>

### sample

<http://api.tianyancha.com/services/v3/open/punishment.json?name=北京逸璟物业管理有限公司>

### 支持格式

  JSON

### HTTP请求方式

  GET

### 是否需要授权

  是
  需要进入ip白名单

### 访问授权限制

  访问级别：普通接口


### 请求参数

|         | 必选   | 类型及范围    | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| name      | true | String |公司全名，可通过查询接口获取 |
| pageNum     | false | int |返回结果的页码，默认为1。|

### 注意事项

  请求参数需要URLEncode。

### 返回结果
  JSON示例  

```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "count": 1,
    "items": [
      {
        "content": "罚款;没收违法所得;",
        "punishNumber": "北流工商处字[2015]240号",
        "publishDate": "2015-12-20",
        "description": "<p>北流市工商行政管理局</p><p>行政处罚决定书</p><p>北流工商处字〔2015〕240号</p><p>北流市隆盛供销社；法定代表人：陈家雄；经营场所：隆盛镇；邮政编码：537411；电话：6521377；统一社会信用代码/证照编号：450981000006273；企业类型：集体所有制；注册资本：壹佰柒拾柒万玖仟圆整；经营范围：百货，纺织、服装及日用品，文化体育用品及器材，五金家具及室内装饰材料，建筑材料、钢材、铁木农具，家用电器及电子产品、饲料，陶瓷、塑料制品；食品、饮料及烟草制品，农副土特产品，医药及医疗器械，石油制品，化肥、农药、农膜、不再分包装的杂交水稻种子，饮食、各种爆竹、小型烟花批发、零售。（以上项目在分支机构经营）；经营期限：长期；</p><p>北流市隆盛供销社农药门市部于2015年6月从玉林购进50KG/袋的中科复混肥料（生产企业名称：江苏中科肥业有限公司）2吨（共40袋），进货价格为2900元/吨。2015年9月15日，中国检验认证集团广西有限公司工作人员对北流市隆盛供销社农药门市部上述化肥进行抽样送检，抽样时，库存33袋。经中国检验认证集团广西有限公司检验，北流市隆盛供销社农药门市部销售的50KG/袋的中科复混肥料被判定不合格。执法人员于2015年11月20日将中国检验认证集团广西有限公司检验报告送达当事人，当事人表示没有异议，在规定的时间内没有提出申诉或复检要求。当事人在收到检验报告之前，已将上述50KG/袋的中科复混肥料全部销售给当地农户，销售价格为3400元/吨。</p><p>中华人民共和国产品质量法：第十三条可能危及人体健康和人身、财产安全的工业产品，必须符合保障人体健康和人身、财产安全的国家标准、行业标准；未制定国家标准、行业标准的，必须符合保障人体健康和人身、财产安全的要求。</p><p>中华人民共和国产品质量法：第四十九条生产、销售不符合保障人体健康和人身、财产安全的国家标准、行业标准的产品的，责令停止生产、销售，没收违法生产、销售的产品，并处违法生产、销售产品（包括已售出和未售出的产品，下同）货值金额等值以上三倍以下的罚款；有违法所得的，并处没收违法所得；情节严重的，吊销营业执照；构成犯罪的，依法追究刑事责任。</p><p>一、罚款11000元；</p><p>二、没收违法所得825元。</p><p>当事人于2015年12月14日到建设银行北流市支行（名称：北流市工商行政管理局，帐号：45001664145050502504）缴纳罚没款。</p><p>当事人可在2015年5月21日起六十日内向玉林市工商行政管理局或者北流市人民政府申请复议；也可以在六个月内依法向人民法院提起行政诉讼。</p><p> </p><p> </p><p>                    北流市工商行政管理局</p><p>2015年12月11日</p>",
        "name": "北流市隆盛供销社",
        "decisionDate": "2015-12-11",
        "base": "gx",
        "legalPersonName": "陈家雄",
        "departmentName": "北流市工商行政管理局",
        "type": "生产、销售不符合保障人体健康和人身、财产安全的国家标准、行业标准的产品",
        "regNumber": "450981000006273"
      }
    ]
  }
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码      |
| reason     | String |错误原因|
| result     | Object| 返回内容|
| count     | int| 总条数|

#### items 字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| base     | String |省份|
| regNumber     | String |注册号|
| name     | String |名称|
| punishNumber     | String |行政处罚决定书文号|
| legalPersonName     | String |法定代表人（负责人）姓名|
| type     | String |违法行为类型|
| content     | String |行政处罚内容|
| departmentName     | String |作出行政处罚决定机关名称|
| decisionDate     | Date |作出行政处罚决定日期|
| publishDate     | Date |公示日期|
| description     | String |描述|

### 相关问题

无

## 获取公司检查抽查信息

### url

<http://api.tianyancha.com/services/v3/open/checkInfoList.json>

### sample

<http://api.tianyancha.com/services/v3/open/checkInfoList.json?name=博乐市婷芳农资服务部>

### 支持格式

  JSON

### HTTP请求方式

  GET

### 是否需要授权

  是
  需要进入ip白名单

### 访问授权限制

  访问级别：普通接口


### 请求参数

|         | 必选   | 类型及范围    | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| name      | true | String |公司全名，可通过查询接口获取 |
| pageNum     | false | int |返回结果的页码，默认为1。|

### 注意事项

  请求参数需要URLEncode。

### 返回结果
  JSON示例  

```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "count": 1,
    "items": [
      {
        "checkType": "抽查",
        "checkResult": "正常",
        "checkOrg": "博乐市工商行政管理局",
        "checkDate": "2016-08-17"
      }
    ]
  }
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码      |
| reason     | String |错误原因|
| result     | Object| 返回内容|
| count     | int| 总条数|

#### items 字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| checkOrg     | String |检查实施机关|
| checkType     | Date |类型|
| checkDate     | String |日期|
| checkResult     | String |结果|


### 相关问题

无

## 获取公司动产抵押信息

### url

<http://api.tianyancha.com/services/v3/open/companyMortgage.json>

### sample

<http://api.tianyancha.com/services/v3/open/companyMortgage.json?name=讷河市丰盛现代农业农机专业合作社>

### 支持格式

  JSON

### HTTP请求方式

  GET

### 是否需要授权

  是
  需要进入ip白名单

### 访问授权限制

  访问级别：普通接口


### 请求参数

|         | 必选   | 类型及范围    | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| name      | true | String |公司全名，可通过查询接口获取 |
| pageNum     | false | int |返回结果的页码，默认为1。|

### 注意事项

  请求参数需要URLEncode。

### 返回结果
  JSON示例  

```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "count": 5,
    "items": [
      {
        "baseInfo": {
          "scope": "主债权、利息等，详见合同",
          "status": "无效",
          "remark": "",
          "regDate": 1420646400000,
          "type": "借款合同",
          "cancelReason": "合同履行完毕",
          "id": 32019,
          "amount": "300万元",
          "regDepartment": "大冶市工商行政管理局",
          "overviewTerm": "自 2014年5月16日 至 2015年5月16日",
          "regNum": "冶工商押登字[2014]646",
          "cancelDate": 1432742400000,
          "base": "hub",
          "publishDate": 1420646400000
        },
        "changeInfoList": [
          {
            "changeDate": "2015-01-08",
            "changeContent": "动产抵押登记编号有冶工商押登字[2014]646改为冶工商押登字[2014]66号"
          }
        ],
        "pawnInfoList": [
          {
            "detail": "共1台，价值40万元，其他同上",
            "ownership": "自有",
            "pawnName": "泥浆泵"
          },
          ...
        ],
        "peopleInfo": [
          {
            "licenseNum": "420281000007873",
            "peopleName": "黄石市中小企业信用担保有限责任公司大冶分公司",
            "liceseType": "营业执照"
          }
        ]
      },
      ...
    ]
  }
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| error_code   | int |错误代码      |
| reason     | String |错误原因|
| result     | Object| 返回内容|
| count     | int| 总条数|
| baseInfo    | Object| 基本信息|
| changeInfoList     | JsonArray| 总抵押变更|
| pawnInfoList     | JsonArray| 抵押物信息|
| peopleInfoList     | JsonArray| 抵押人信息|


#### baseInfo（基本信息） 字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| base     | String |省份|
| regNum     | Date |登记编号|
| regDate     | Date |登记日期|
| publishDate     | Date |公示日期|
| status     | String |状态|
| regDepartment     | String |登记机关|
| type     | String |被担保债权种类|
| amount     | String |被担保债权数额|
| term     | String |债务人履行债务的期限|
| scope     | String |担保范围|
| remark     | String |备注|
| overviewType     | String |概况种类|
| overviewAmount     | String |概况数额|
| overviewScope     | String |概况担保的范围|
| overviewTerm     | String |概况债务人履行债务的期限|
| overviewRemark     | String |概况备注|
| cancelDate     | String |注销日期|
| cancelReason     | String |注销原因|


#### changeInfoList（总抵押变更） 字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| changeDate     | String |变更日期|
| changeContent     | String |变更内容|


#### pawnInfoList 字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| pawnName     | String |名称|
| ownership     | String |所有权归属|
| detail     | String |数量、质量、状况、所在地等情况|
| remark     | String |备注|

#### peopleInfoList（抵押人信息） 字段说明


| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| peopleName     | String |抵押权人名称|
| liceseType     | String |抵押权人证照/证件类型|
| licenseNum     | String |证照/证件号码|


### 相关问题

无

## 获取公司关联发现信息

### url

<http://api.tianyancha.com/services/v3/open/oneKey/c.json>

### sample

<http://api.tianyancha.com/services/v3/open/oneKey/c.json?id=22822>

### 支持格式

  JSON

### HTTP请求方式

  GET

### 是否需要授权

  是
  需要进入ip白名单

### 访问授权限制

  访问级别：普通接口


### 请求参数

|         | 必选   | 类型及范围    | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| id      | true | long |公司id，通过查询接口获取          |

### 注意事项

  请求参数需要URLEncode。

### 返回结果
  JSON示例  

  暂无

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明

  暂无

### 相关问题

无

## 获取公司经营异常信息

### url

<http://api.tianyancha.com/services/v3/open/abnormalInfo.json>

### sample

<http://api.tianyancha.com/services/v3/open/abnormalInfo.json?name=湖南瑞源生物医药科技有限公司>

### 支持格式

  JSON

### HTTP请求方式

  GET

### 是否需要授权

  是
  需要进入ip白名单

### 访问授权限制

  访问级别：普通接口


### 请求参数

|         | 必选   | 类型及范围    | 说明  |
| ------------ |:----:|:--------:|:-------------:|
| name      | true | string |公司名称，可通过查询接口获取          |

### 注意事项

  请求参数需要URLEncode。

### 返回结果
  JSON示例  

```
{
    "error_code": 0,
    "reason": "ok",
    "result": {
        "total": 2,
        "items": [
            {
                "id": 138789881,
                "companyId": 21289551,
                "putReason": "未按照规定报送2013年度年度报告",
                "putDate": "2015-07-13",
                "putDepartment": "长沙市工商行政管理局天心分局",
                "removeReason": "依法补报了未报年份的年度报告并公示",
                "removeDate": "2016-04-15",
                "removeDepartment": "长沙市工商行政管理局天心分局",
                "createtime": "2017-01-05"
            },
            {
                "id": 138789882,
                "companyId": 21289551,
                "putReason": "未按照规定报送2014年度年度报告",
                "putDate": "2015-07-14",
                "putDepartment": "长沙市工商行政管理局天心分局",
                "removeReason": "依法补报了未报年份的年度报告并公示",
                "removeDate": "2016-04-15",
                "removeDepartment": "长沙市工商行政管理局天心分局",
                "createtime": "2017-01-05"
            }
        ]
    }
}
```

#### 关于错误返回值与错误代码，参见 <a href="#_1">错误代码说明</a>

### 返回字段说明

| 返回值字段|字段类型|字段说明|
| ------------ |:--------:|:-------------:|
| putReason     | String |列入经营异常名录原因|
| putDate     | String |列入日期|
| putDepartment     | String |列入部门|
| removeReason     | String |移出原因|
| removeDate     | String |移出日期|
| removeDepartment     | String |移出部门|

### 相关问题

无
