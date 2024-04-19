# 💰 余额查询

> 商户可调用该接口，查询账户余额信息。

**请求地址：**https://web.upay.ink/api/df/balance

**请求方式：**POST

**传参方式：**数组

**请求参数：**

<table data-full-width="true"><thead><tr><th>字段名称</th><th width="167">字段类型</th><th width="129">必填参数</th><th>说明</th></tr></thead><tbody><tr><td>appid</td><td>string(16)</td><td>必填</td><td>商户号</td></tr><tr><td>signature</td><td>string(32)</td><td>必填</td><td>数据签名 详见<a href="../introduction/signature.md">签名算法</a></td></tr></tbody></table>

**返回参数：**

<table data-full-width="true"><thead><tr><th width="116">字段名称</th><th width="226">参数含义</th><th width="99">必填参数</th><th>说明</th></tr></thead><tbody><tr><td>code</td><td>请求状态</td><td>必填</td><td>1表示查询成功，其它表示查询失败</td></tr><tr><td>msg</td><td>消息描述</td><td>必填</td><td>失败原因</td></tr><tr><td>data</td><td>订单信息 (数据类型：集合)</td><td>必填</td><td>返回数据，查看下表</td></tr></tbody></table>

**返回值data参数：**

<table data-full-width="true"><thead><tr><th width="296">字段名称</th><th>参数含义</th></tr></thead><tbody><tr><td>appid</td><td>商户号</td></tr><tr><td>usdt_balance</td><td>USDT余额，单位：USDT</td></tr><tr><td>signature</td><td>安全校验签名串</td></tr></tbody></table>

