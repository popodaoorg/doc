# 🔎 代付查询

> 该接口供商户主动查询提现状态。

请求地址：https://web.upay.ink/api/df/search

请求方式：POST

传参方式：数组

请求参数：

<table><thead><tr><th width="129">字段名称</th><th width="114">字段类型</th><th width="109">必填参数</th><th>说明</th></tr></thead><tbody><tr><td>appid</td><td>string(16)</td><td>必填</td><td>商户号</td></tr><tr><td>df_sn</td><td>string(50)</td><td>必填</td><td>商户代付订单号</td></tr><tr><td>signature</td><td>string(32)</td><td>必填</td><td>数据签名 详见<a href="../introduction/signature.md">签名算法</a></td></tr></tbody></table>

**返回参数：**

<table><thead><tr><th width="112">字段名称</th><th>参数含义</th><th width="106">必填参数</th><th>说明</th></tr></thead><tbody><tr><td>code</td><td>请求状态</td><td>必填</td><td>1表示查询成功，其它表示查询失败</td></tr><tr><td>msg</td><td>消息描述</td><td>必填</td><td>失败原因</td></tr><tr><td>data</td><td>订单信息（数据类型：集合）</td><td>必填</td><td>返回数据，查看下表</td></tr></tbody></table>

返回值data参数：

<table><thead><tr><th width="194">字段名称</th><th>参数含义</th></tr></thead><tbody><tr><td>appid</td><td>商户号</td></tr><tr><td>df_sn</td><td>商户代付订单号</td></tr><tr><td>money</td><td>代付金额，单位：USDT</td></tr><tr><td>status</td><td>代付状态：查看下表</td></tr><tr><td>success_time</td><td>成功时间</td></tr><tr><td>signature</td><td>安全校验签名串</td></tr></tbody></table>

**代付状态：**

<table data-full-width="true"><thead><tr><th width="308">status</th><th>描述</th></tr></thead><tbody><tr><td>0</td><td>处理中</td></tr><tr><td>1</td><td>代付成功</td></tr></tbody></table>
